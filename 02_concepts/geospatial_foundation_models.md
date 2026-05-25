---
name: geospatial_foundation_models
description: Geospatial foundation models — AlphaEarth, PRESTO, Prithvi, SatMAE; pretrained representations of Earth observation data for downstream mapping tasks with minimal labels
type: reference
tags:
  - deep-learning
  - remote-sensing
  - machine-learning
---

# Geospatial Foundation Models

**Summary**: Geospatial foundation models are large neural networks pretrained on massive multi-modal Earth observation archives to produce **universal representations** of pixels or patches that transfer to downstream mapping tasks with minimal labels. AlphaEarth (480M parameters, ~3B observations) and PRESTO (lightweight pixel-time-series Transformer) represent two ends of the size-vs-spatial-context tradeoff. Both substantially reduce the data and compute requirements of new forest mapping projects.

**Sources**: [[brown_2025_alphaearth]], [[tseng_2024_presto]], [[hiebl_2026_alphaearth]], [[wang_2026_foundation]], [[lang_2024_canopy_height]], [[manas_2021_seasonal_contrast]], [[ball_2026_foundation_models]], [[feng_2026_tessera]]

**Last updated**: 2026-05-22

---

## Methodological Precursor: Seasonal Contrast (SeCo)

Before foundation models, **SeCo** (Mañas et al. 2021) established the key ideas that larger RS foundation models later scaled up (source: [[manas_2021_seasonal_contrast]]):
- **Temporal positive pairs**: same geographic location at different timestamps (~3 months apart) = valid contrastive positive pair — grounded in the inductive bias that *"land cover does not change with the seasons"*
- **In-domain RS pre-training beats ImageNet**: SeCo outperforms ImageNet pre-training on BigEarthNet (+4–6% mAP), EuroSAT (+6.7%) — confirmed the value of domain-specific SSL
- **Multi-head design** separates time-invariant and time-variant representations — precursor to modern multi-stream foundation architectures

SeCo is the canonical source for the assumption that **ecological stability over time enables temporal contrastive pre-training** — a principle inherited by PRESTO (temporal multi-sensor masking) and implicitly by AlphaEarth (multi-temporal training data at each location).

## The Paradigm

Task-specific transfer learning trains a model on a related labelled task (e.g. ImageNet → tree species) and fine-tunes on the target. Foundation models go further: train **once** on a huge multi-modal corpus via self-supervision, produce **embeddings** that transfer to **any** downstream task — often via simple linear / shallow heads on frozen features.

Why this matters for RS:
- Labels are scarce, expensive, and heterogeneous across regions
- Multi-modal EO data are abundant and largely unlabelled
- Few-shot mapping (1–10 labels per class) becomes feasible with good frozen features
- Same embedding can serve land cover, species, biomass, disturbance simultaneously

## AlphaEarth Foundations (Brown et al. 2025)

- ~480M parameters; trained on **> 3 billion observations** from 10 data sources: Sentinel-2, Landsat, Sentinel-1, ALOS PALSAR-2, DEM, GEDI LiDAR, ERA5 climate, GRACE, land cover, geotagged text (source: [[brown_2025_alphaearth]])
- **Space Time Precision (STP) encoder**: parallel spatial self-attention + time-axial self-attention + convolution branches; continuous-time conditioning for arbitrary date ranges
- Output: 64-dim embedding field at **10 m resolution globally for 2017–2024**
- Frozen embeddings outperform all designed featurisations (CCDC, MOSAIKS, composites) AND all prior learned models (SatCLIP, Prithvi, Clay) — error reduction ~23.9% vs next best across 15 mapping evaluations
- **Limitation**: training covers ~1.1% of Earth's land; annual temporal resolution of released embeddings too coarse for sub-annual phenology; weights not open-sourced

## PRESTO (Tseng et al. 2024)

Lightweight counterpoint to AlphaEarth (source: [[tseng_2024_presto]]):
- < few million parameters — **up to 1000× smaller** than ViT-based foundation models
- Pretrained on 21.5 M global pixel-time-series via masked-autoencoding
- Inputs: Sentinel-2, Sentinel-1, ERA5, NDVI, Dynamic World, DEM, location (7 data products)
- Pixel-time-series approach (no spatial context) — wins when temporal + multi-sensor matter more than spatial texture
- Trainable on CPU; orders-of-magnitude fewer FLOPs at inference
- Robust to missing data and variable input shapes
- Open-source code + weights

## TESSERA (Feng et al. 2026)

Pixel-wise multi-modal (S1+S2) foundation model with temporal sampling invariance (source: [[feng_2026_tessera]]):
- **45.7M parameters** — 10× smaller than AlphaEarth, comparable to PRESTO
- Pretrained on ~800M d-pixels (3,012 global MGRS tiles, 2017–2024) via **Barlow Twins** — enforces embedding invariance to which cloud-free observations are selected from a time series
- Two key regularizers: **global shuffling** (breaks spatial autocorrelation; most important, −9.2 F1 when removed) + **mix-based regulation** (invariance under extreme sparsity, −11.1 F1 when removed)
- Output: 128-dim pixel embeddings, compressed to **int8** via Quantization-Aware Training (4× storage reduction, negligible quality loss)
- **FAIR by design:** global annual 10 m int8 embeddings + open weights + GeoTessera Python library → https://github.com/ucam-eo/tessera
- Cloud-robust: stable until <20 valid S2 observations/year
- Best-in-class on: TreeSatAI-TS tree species (F1=79.23 full / 60.58 at 1%), Austrian Crop segmentation (mIoU=53.12), Borneo CHM regression (RMSE=13.1 m), Biomassters AGB (RMSE=27.43 t/ha)
- **Limitation vs AlphaEarth:** pixel-wise (no spatial context) → marginally weaker on full-label segmentation (PASTIS-R); annual cadence; sub-annual tasks need raw time series re-encoding

## Comparison

| Property | AlphaEarth (large) | TESSERA | PRESTO (lightweight) |
|---|---|---|---|
| Parameters | ~480 M | 45.7 M | < 10 M |
| Pretraining scale | 3 B observations | ~800 M d-pixels | 21.5 M pixel-series |
| Spatial context | Multi-scale, spatially aware | None (per-pixel) | None (per-pixel) |
| Multi-modal (S1+S2) | Yes | Yes | Yes |
| Output dim | 64 | 128 (int8) | Variable |
| Frozen-feature use | Designed for | Designed for | Possible |
| Open weights | No | Yes | Yes |
| Open global embeddings | No | Yes | No |
| Best when | Spatial texture + frozen; patch-level tasks | Temporal phenology + cloud robustness + compute-constrained | Temporal + multi-sensor + compute-constrained |

## Operational Use Cases

**Forest type and EVE cover (Italy)** — Hiebl et al. 2026 (source: [[hiebl_2026_alphaearth]]):
- AEF embeddings + Sentinel-2 SITS fused via Transformer cross-attention (TST_AEF,S2)
- RMSE 0.161, Acc 0.757 — best among tested models
- AEF matches S-2-only accuracy **10–24× faster** with no preprocessing

**Forest carbon stock loss (Hunan)** — Wang et al. 2026 (source: [[wang_2026_foundation]]):
- AEF + S-1/S-2 + GEDI → 10 m annual CHM
- VHR Siamese deep change detection → annual loss masks
- Combination → 3D forest change + carbon stock loss
- Open-source: github.com/wzp8023391/ForestCarbonEstimate

**Global canopy height** — Lang et al. 2024 (source: [[lang_2024_canopy_height]]):
- Not AEF but a related sparse-supervision deep ensemble fusing GEDI + S-2 at scale
- aRMSE 7.3 m globally; precursor to foundation-model-enabled CHM

## Tree Species Mapping with GFMs (Ball et al. 2026)

The most rigorous evaluation of GFMs for species-level mapping to date (source: [[ball_2026_foundation_models]]):
- **Task:** 18-class tree species classification in Trentino (northern Italy), using parcel-level forest inventories; Tessera vs AlphaEarth vs Sentinel-1+2 composites
- **Result:** GFM embeddings (WF1 = 0.83) consistently outperform conventional composites (WF1 = 0.80)
- **Label efficiency:** Near-asymptotic accuracy at **5% of training parcels** — strongest practical benefit for regions with sparse inventories
- **Classifier requirement:** Linear classifiers **fail** on GFM embeddings (underperform an MLP on composites); shallow MLP is sufficient and saturates; deeper networks add nothing
- **Terrain covariates:** Adding elevation/slope/aspect provides **no benefit** — abiotic gradients are implicitly encoded in phenological signals (Tessera) or auxiliary training objectives (AlphaEarth)
- **Soft labels:** Using species proportions from inventory as supervision targets outperforms hard per-pixel labels (Tessera macro F1: 0.551→0.586) — especially beneficial for minority species; conceptually resolves the resolution mismatch between 10 m pixels (spectral mixtures) and single-species hard labels
- **Temporal transfer:** Performance drops 9% (Tessera) and 15% (AlphaEarth) when training on 2018 embeddings and predicting on 2021 data — **rare species suffer disproportionate losses**
- **Model comparison:** Tessera (pixel-level Barlow Twins) excels at minority-species discrimination and parcel compositional fidelity; AlphaEarth (patch-level, multi-modal auxiliary targets) achieves marginally higher weighted F1 but over-smooths fine-grained within-parcel variation
- **Ecological coherence:** Errors follow taxonomic/functional axes (Abies↔Picea; pine cluster; broadleaf groups) — embeddings encode a hierarchical ecological signal, not arbitrary noise

**Key implication:** GFMs shift the bottleneck in species mapping from *feature engineering* to *reference data availability, quality, and temporal alignment*.

## How to Use Foundation Embeddings

Two common patterns:
1. **Frozen embedding + shallow head**: extract AEF 64-dim vectors; train a simple MLP or RF on top → few labels needed
2. **Cross-attention fusion**: combine foundation embeddings with task-specific features (e.g. Sentinel-2 time series) via Transformer cross-attention layers → captures synergies between general semantics and task-specific signals (cf. TST_AEF,S2 in [[hiebl_2026_alphaearth]])

Less common but viable:
3. **Fine-tune backbone**: only for very large target datasets — usually unnecessary
4. **Use foundation as feature initialisation** + light head training

## Lessons for Wiki Workflow

- Default to foundation embeddings when scarce-label regression / classification is the task
- AEF for spatial-context-rich problems (Italian forest type, fractional cover with texture)
- PRESTO for temporal-rich problems on compute budgets (per-pixel SITS regression)
- Combine with [[deep_ensemble_uncertainty]] for calibrated uncertainty
- Validate with **spatial CV** (see [[spatial_proxies_random_forest]]) — foundation models don't fix overfitting, only generalise feature extraction

## Limitations

- Foundation models can encode dataset biases at scale — under-represented biomes / climates remain hard
- Annual cadence of released AEF embeddings limits sub-annual phenology
- Closed weights (AEF) limit research reproducibility
- Foundation models are not magic for **out-of-distribution** regions — area of applicability ([[area_of_applicability]]) still applies
- Frozen embeddings can miss subtle signals that fine-tuning would catch

## Related concepts
- [[transfer_learning_remote_sensing]]
- [[transformer_sits]]
- [[transformers_time_series]]
- [[tree_species_mapping]]
- [[deep_ensemble_uncertainty]]
- [[sentinel_2]]
- [[sentinel_1_sar]]
