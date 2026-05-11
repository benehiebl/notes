---
title: "ls_mapping — Landsat Time Series Forest Mapping with TSTpad (code repository)"
authors:
  - Hiebl, Benedikt
year: 2025
source: ls_mapping
tags:
  - deep-learning
  - remote-sensing
  - forest-ecology
status: read
---

# Title and Authors of the Codebase

**ls_mapping — Landsat Time Series Forest Mapping with TSTpad**
Benedikt Hiebl (University of Innsbruck / UIBK)
Repository: `00_literature/ls_mapping/`
Related publication: In preparation (extension of TRACEVE line to Landsat-based national forest mapping)

---

## Quick Overview

- **Why is the code relevant in the context of the vault?** Extends the TRACEVE deep learning framework from Sentinel-2 to multi-annual Landsat time series, enabling forest type classification and multi-target cover regression (EVE/deciduous/needle-leaf) at national scale over longer temporal windows.
- **What does it do?** Trains a Time Series Transformer (TSTpad) on compressed Zarr multi-annual Landsat time series (2019–2025) for both forest type classification (`class_v3`) and continuous cover regression (`cover_woody_eve/dec/nl`), with integrated Optuna hyperparameter optimisation.
- **What is the main outcome?** A production-grade training pipeline for Landsat-based forest composition mapping that supports multiple fine-tuning stages (pure → fine0 → fine1 → continuation) and systematic hyperparameter search across model variants.

---

## Main Goal and Fundamental Concept

While Sentinel-2 provides 10 m resolution and 5-day revisit, Landsat offers a 50+ year archive at 30 m and consistent global coverage. This repository applies the Transformer-based time series modelling approach to multi-annual Landsat reflectance stacks, enabling national-scale forest composition mapping with temporal depth unavailable from Sentinel-2 alone. The core concept is **multi-annual temporal modelling**: stacking multiple years of Landsat observations into a single time series and using a padded Transformer (TSTpad) that handles the irregular, gappy nature of Landsat acquisitions via sinusoidal timestamp encoding and key-padding masks.

---

## Technical Approach

**Primary model — TSTpad** (`graphs/models/TSTpad.py`):
- Encoder-only Transformer for irregular time series, supporting both TSC and TSER
- **Time encoding:** sinusoidal encoding on actual acquisition day indices (`time_encoding`: `pe[0::2]=sin(t·ω)`, `pe[1::2]=cos(t·ω)`); masked where times==-1 (missing/padded observations)
- Per-channel input projection `W_P`; optional sensor-type embedding `W_S`
- Mask token `nn.Parameter(zeros, std=0.02)` for absent observations
- Standard `_TSTEncoderLayer`: multi-head self-attention + dropout + LayerNorm + position-wise FFN (GELU)
- Attention pooling (`attn_pool=1`) aggregates temporal dimension before prediction head
- Task heads: `CrossEntropyLoss` (TSC) or `MSELoss` (TSER, multi-target)
- Architecture: `d_model=256, n_layers=4, n_attheads=4, d_ff=1024, embd_dim=256`

**Input features (14 Landsat bands + indices):**
`blue, green, red, nir08, swir16, swir22, NDVI, NIRv, NDMI, EVI, WDRVI, NBR, NDWI, GNDVI`

**Multi-annual time series:**
- `time_slice = slice("2019", "2025")` — 6-year Landsat archive
- `multi_annual_time_series = True` — concatenates all years into one temporal sequence
- Data stored in Zarr compressed format (`ls_pure_full_compressed_float.zarr`) for scalable I/O

**Experiment hierarchy (config naming):**
| Config pattern | Description |
|---|---|
| `tst_{task}_ls_pure_{seed}` | Train from scratch on pure-stand reference data |
| `tst_{task}_ls_fine0_{seed}` | Fine-tune from a pretrained checkpoint (run 0) |
| `tst_{task}_ls_fine1_{seed}` | Further fine-tune (run 1) from fine0 checkpoint |
| `tst_{task}_ls_cont_{seed}` | Continue training from a prior checkpoint |

Tasks: `class` (forest type classification) or `cov` (cover regression: EVE + deciduous + NL)

**Hyperparameter optimisation (`opt_model/`):**
- Optuna TPE sampler with multivariate/grouped search
- Multi-objective: minimise validation NLL + maximise CE accuracy + minimise overfitting gap
- Searches: learning rate (log-uniform 1e-5–1e-3), weight decay (0–0.01)
- Separate optimisation scripts per model variant: `run_tst_vpo_opt.py`, `run_tst_vdbalpha_opt.py`, `run_mlp_vpoalpha_eve_opt.py`, `run_tst_vpoalpha_opt.py`
- Results persisted in SQLite DBs for resumable multi-session search

**Preprocessing:**
- `TSRobustStandardize (q=[0.1, 0.9])` per band
- `sample_weight_power=0.5` — square-root sample weighting to reduce dominant-class bias
- `fillnan=0.0001` — NaN fill for cloud-contaminated observations
- `augment=True` — data augmentation during training

---

## Distinctive Features

- **Padded Transformer for irregular Landsat acquisitions:** TSTpad handles variable-length, gappy Landsat time series via timestamp encoding and attention masking — no gap-filling preprocessing required before the model
- **Multi-target regression:** simultaneously predicts EVE, deciduous, and needle-leaf cover fractions in a single forward pass, learning shared representations across the three cover types
- **Progressive fine-tuning pipeline:** the `pure → fine0 → fine1 → cont` config hierarchy enables staged training — train from scratch on clean reference data, then fine-tune incrementally on more diverse samples
- **Optuna multi-objective HPO:** uses a three-objective (NLL minimise + CE maximise + overfitting gap minimise) Optuna study with TPE sampler, persisted to SQLite for reproducible multi-session searches
- **Zarr data format:** compressed chunked arrays enable efficient streaming of large multi-annual Landsat archives without loading the full dataset into memory

---

## Experimental Setup and Results

**Reference data:**
- `ls_pure_full_compressed_float.zarr`: pure-stand Landsat reference plots with `class_v3` labels and `cover_woody_{eve,dec,nl}` targets
- `ls_purecleaned_full_compressed_float.zarr`: cleaned version for cover regression

**Validation:** polygon-based split (`pol_id`); random 20% validation within each polygon to prevent spatial leakage at polygon boundaries

**Training evidence:** `nohup_train.out` and `nohup_train_2.out` files indicate the framework has been used for production training runs. Analysis notebooks (`test.ipynb`, `test_classification.ipynb`, `test_regression.ipynb`, `test_model_analysis.ipynb`) are present for post-training evaluation.

Results are unpublished (manuscript in preparation); the framework is in active development as of 2025–2026.

---

## Advantages and Limitations

**Advantages:**
- Multi-annual Landsat archive provides temporal depth (6 years) capturing forest structural change patterns unavailable in single-year Sentinel-2 composites
- Zarr format + async loading scales to national-scale datasets without memory constraints
- Integrated Optuna HPO enables principled hyperparameter search rather than manual tuning
- Multi-target regression is more parameter-efficient than training three separate models

**Limitations:**
- No README (unlike `traceve_pretraining` and `ae_training`) — code organisation must be inferred from configs and file structure
- 30 m Landsat resolution limits fine-scale discrimination vs. 10 m Sentinel-2
- No red-edge bands (Landsat lacks the 705–783 nm range), reducing species-level discrimination capability
- Framework is actively evolving — config naming conventions differ from `traceve_pretraining` and `ae_training`
- No deep ensemble uncertainty support (unlike `traceve_pretraining`)

---

## Conclusion

`ls_mapping` adapts the TRACEVE Transformer architecture to multi-annual Landsat time series, providing a scalable production training pipeline for national-scale forest composition mapping. Its TSTpad model handles irregular, gappy Landsat acquisitions natively through timestamp encoding and attention masking. The progressive fine-tuning hierarchy, multi-target regression, and integrated Optuna HPO distinguish it from `traceve_pretraining`. The repository represents an ongoing expansion of the TRACEVE research line toward longer temporal windows and broader geographic coverage using the Landsat archive.

## Related pages
- [[hiebl_2025_pretraining]]
- [[landsat]]
- [[transfer_learning_remote_sensing]]
- [[transformers_time_series]]
- [[traceve_pretraining]]
- [[ae_training]]
