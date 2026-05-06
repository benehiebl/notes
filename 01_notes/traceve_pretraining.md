---
title: "TRACEVE Pretraining — InceptionTime Deep Ensemble Framework for Sentinel-2 Time Series (code repository)"
authors:
  - Hiebl, Benedikt
year: 2025
source: traceve_pretraining
tags:
  - deep-learning
  - remote-sensing
  - forest-ecology
status: read
---

# Title and Authors of the Codebase

**TRACEVE Pretraining — InceptionTime Deep Ensemble Framework for Sentinel-2 Time Series**
Benedikt Hiebl (University of Innsbruck / UIBK)
Repository: `00_literature/traceve_pretraining/`
Related publication: [[hiebl_2025_pretraining]]

---

## Quick Overview

- **Why is the code relevant in the context of the vault?** This is the primary codebase underlying [[hiebl_2025_pretraining]], implementing all pretraining and fine-tuning experiments for EVE cover mapping from Sentinel-2 time series with deep ensemble uncertainty.
- **What does it do?** Trains InceptionTimeEnsemble deep learning models on Sentinel-2 L2A reflectance time series for Time Series Classification (TSC) and Time Series extrinsic Regression (TSER), with support for supervised pretraining, self-supervised Masked Value Prediction (MVP) pretraining, and deep ensemble uncertainty quantification.
- **What is the main outcome?** A reproducible config-driven training framework that produces EVE cover maps with calibrated epistemic and aleatoric uncertainty estimates via a 15-head parallel ensemble architecture.

---

## Main Goal and Fundamental Concept

The repository addresses the core challenge of mapping evergreen broad-leaved (EVE) vegetation cover from Sentinel-2 time series when labelled ground truth is scarce. The fundamental concept is **supervised contextual pretraining**: first train the model on a large, spectrally diverse vegetation dataset (Italian Forest Vegetation Database, VDB), then fine-tune on a smaller target dataset. This transfers phenological representations learned from many sites to improve generalisation on the target task. A parallel ensemble of N=15 prediction heads shares a common InceptionTime backbone to simultaneously produce predictions and calibrated uncertainty estimates without full Bayesian inference.

---

## Technical Approach

**Architecture — InceptionTimePlusParallel (deep ensemble):**
- Shared backbone: InceptionTime (1D multi-scale CNN for time series; `nf=64, ks=60, depth=4`)
- 15 parallel heads branching from the backbone — each head independently predicts mean and variance
- Total model output: 15 (mean, variance) pairs per sample → ensemble mean as prediction, inter-head variance as epistemic uncertainty, average intra-head variance as aleatoric uncertainty

**Training agents:**
- `tser_deepensemble.py` (TSERBootAgent): bootstrapped TSER training; each head receives a different random data subsample; separate AdamW optimizers for mean-backbone and var-backbone; `BetaNLLLoss` for joint aleatoric + epistemic training
- `tsc_deepensemble.py`: classification variant
- `mvp_pretraining.py` (SelfMVPAgent): self-supervised MVP via `ts_learner` + fastai `MVP` callback; masking rate=25% with mean window length=16%; model learns to reconstruct original time series from corrupted input

**Dataloaders:**
- `SentinelTSER(_agg)`: loads Sentinel-2 time series (netCDF) + continuous cover labels; supports multi-annual aggregation
- `SentinelTSC(_agg)`: classification version with class labels
- `SentinelSelf_agg`: unsupervised dataloader for MVP; outputs (masked_input, original) pairs

**Time series preprocessing pipeline (`ts_utils/`):**
- `outlier.py`: IQR-based outlier detection with sliding window (`factor=0.5, window=140`)
- `smooth.py`: Whittaker smoother (`lmbd=40, d=1`) or Savitzky-Golay
- Resampling to configurable temporal resolution (e.g., 3-day)
- `TSPercNormalize`: percentile-based per-band normalisation (p=[0.02, 0.95])

**Spatial cross-validation:**
- `test_cluster`: leave-out spatial cluster for final test set
- `valid_size`: list of spatial clusters held out for validation
- Prevents spatial autocorrelation leakage between train/test

**Config-driven workflow:**
All experiment parameters — model, agent, dataloader, loss, preprocessing, split strategy — are defined in a single Python config file. Run: `python main.py config_file_name.py train`

---

## Distinctive Features

- **Deep ensemble with per-head bootstrapping:** each head trains on a different random subset, introducing diversity beyond random weight initialisation alone; the `TSERBootAgent` runs separate optimisers per head simultaneously
- **BetaNLLLoss:** a beta-weighted NLL loss (`L = β·log(σ²) + (y−μ)²/σ²`) that allows trading off aleatoric vs. epistemic uncertainty emphasis via the `beta` hyperparameter (β=0 → pure NLL; β>0 → downweights high-uncertainty samples)
- **Freeze strategies:** config option `freeze = "backbone"` / `"same"` / `"same backbone"` enables flexible pretrain-then-fine-tune workflows — backbone frozen or unfrozen, head replaced or retained
- **MVP self-supervised pretraining:** leverages the tsai `MVP` callback to corrupt Sentinel-2 time series (random masking) and train the backbone to reconstruct them, requiring zero labels; enables pretraining on large unlabelled archives

---

## Experimental Setup and Results

Experiments are specified via configs in `configs/`. Template config (`0_config_template.py`) defines:
- Target: `cover_eve_B` (EVE cover, 0–100%)
- Input bands: B03, B04, B05, B07, B08, B11, B12, NDMI, kNDVI, NIRv (10 spectral + index features)
- Time: multi-annual aggregation (2021–2023)
- Spatial split: leave-out cluster (`cl=[3]`) for test; hold-out clusters for validation

Outcomes documented in [[hiebl_2025_pretraining]]:
- Supervised VDB pretraining (mVDB_cover) achieves best generalisation, outperforming direct training and MVP pretraining
- MVP pretraining (mUPD) intermediate — improved over no pretraining but below supervised
- Spatial k-fold reveals that random splits overestimate performance vs. spatially-held-out evaluation
- Epistemic uncertainty is spatially coherent — high in OOD regions (conifer-dominated, north-facing slopes)

---

## Advantages and Limitations

**Advantages:**
- Modular config-driven design: easy to swap models, losses, dataloaders without changing pipeline code
- Supports three training paradigms (supervised pretraining, MVP, direct training) in one framework
- Deep ensemble provides calibrated uncertainty with no extra inference cost at test time
- Spatial k-fold prevents over-optimistic accuracy estimates common in RS studies

**Limitations:**
- Designed exclusively for Sentinel-2 1D time series — no multi-modal fusion support (→ see `ae_training`)
- tsai library dependency (version-sensitive); MVP callback tightly coupled to fastai ecosystem
- No automated hyperparameter optimisation (→ `ls_mapping` adds Optuna integration)
- Bootstrap training with 15 separate optimisers is memory-intensive for large batch sizes

---

## Conclusion

`traceve_pretraining` is the foundational codebase for [[hiebl_2025_pretraining]], providing a complete training framework for deep ensemble EVE cover mapping from Sentinel-2 time series. Its key contributions are the supervised contextual pretraining workflow, per-head bootstrapped deep ensembles with BetaNLL uncertainty decomposition, and spatially-aware cross-validation. The config-driven architecture makes it straightforward to run controlled pretraining ablations (VDB_cover vs. VDB_ftype vs. MVP vs. direct). It is the starting point from which `ae_training` (AlphaEarth fusion) and `ls_mapping` (Landsat extension) were developed.

## Related pages
- [[hiebl_2025_pretraining]]
- [[transfer_learning_remote_sensing]]
- [[transformers_time_series]]
- [[neural_network_training]]
- [[ae_training]]
- [[sentinel_2]]
