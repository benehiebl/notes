---
title: "Combining specialized Sentinel-2 time series features with AlphaEarth Foundations for forest type mapping"
authors:
  - Hiebl, Benedikt
  - Alessi, Nicola
  - Calvia, Giacomo
  - Bricca, Alessandro
  - Bonari, Gianmaria
  - Zangari, Giulio
  - Zerbe, Stefan
  - Rutzinger, Martin
year: 2026
source: hiebl_2026_alphaearth
tags:
  - deep-learning
  - remote-sensing
  - sentinel-2
  - forest-ecology
status: read
---

# Title and Authors of the Paper

**Combining specialized Sentinel-2 time series features with AlphaEarth Foundations for forest type mapping**
Benedikt Hiebl, Nicola Alessi, Giacomo Calvia, Alessandro Bricca, Gianmaria Bonari, Giulio Zangari, Stefan Zerbe, Martin Rutzinger
*ISPRS Annals of the Photogrammetry, Remote Sensing and Spatial Information Sciences*, 2026
Code: [[ae_training]] | Codebase for experiments

---

## Quick Overview

- **Why is it relevant?** Addresses the key trade-off in operational forest mapping between specialised S2 time series models (high accuracy, heavy preprocessing) and generalised foundation model embeddings (lightweight, no preprocessing), testing whether combining both is better than either alone.
- **What was done?** Four model architectures (RF, MLP on AlphaEarth Foundation embeddings, TST on Sentinel-2/CHELSA, and a Cross-Attention fusion of both) were compared on two Italian forest datasets in regression (evergreen broad-leaved tree cover, ETC) and classification (forest vegetation type, FVT) tasks using 5-fold cross-validation.
- **What is the main outcome?** The Cross-Attention fusion model (TST_AEF,S2) consistently outperforms all single-source models (ETC RMSE=0.161, FVT Acc=0.757), while AEF-only models match S2-only accuracy with an order-of-magnitude reduction in training time and no time series preprocessing required.

---

## Main Goal and Fundamental Concept

Specialised Sentinel-2 time series deep learning models achieve high accuracy for forest mapping but require extensive preprocessing (cloud masking, outlier detection, aggregation) and sensor-specific model development. AlphaEarth Foundations (AEF; [[brown_2025_alphaearth]]) offer precomputed 64-dimensional multi-modal embeddings globally from 2017–2024, encoding spectral, structural, and climatic information without any preprocessing. This paper asks: can AEF replace expensive S2 time series preprocessing while maintaining accuracy? And can combining both modalities via cross-attention further improve predictions beyond either alone?

The hypothesis is that AEF provides a stable, generalised baseline representation, while S2 time series adds phenology-rich detail — and a Cross-Attention mechanism where AEF queries the S2 time series for complementary information should leverage both strengths.

---

## Technical Approach

**Study area and datasets:**
- Italian forested regions across a latitudinal gradient
- **VDB** (Forest Vegetation Database): 9,854 plot observations (1995–2020), 6 forest vegetation type classes (FVT task; classification)
- **VPO2025**: 2,016 field plots (2023–2025) with evergreen broad-leaved tree cover (ETC; regression task)

**Input data sources:**
- **Sentinel-2 L2A annual time series:** 10 m observations extracted from Microsoft Planetary Computer (2022–2024), masked with Sen2Cor SCL, aggregated by day-of-year median into a single synthetic year, IQR outlier removal; 7 bands + NDVI; sparse (missing dates due to cloud)
- **CHELSA climate:** monthly climatologies (precipitation, tas, tasmin, tasmax) from 2022–2024 averaged; 1 km resolution, linearly interpolated to fill gaps
- **AlphaEarth Foundation embeddings (AEF):** 64-dimensional annual embeddings downloaded from GEE for 2022–2024, averaged across 3 years for stability; no further preprocessing

**Four model architectures:**

| Model | Input | Architecture |
|-------|-------|-------------|
| RF_S2 | S2 + CHELSA monthly medians (168 features) | Random Forest |
| MLP_AEF | AEF (64-dim) | 2-layer MLP |
| TST_S2 | Sparse S2 + CHELSA annual TS | Time Series Transformer (encoder-only); learnable time positional encoding; 64-dim attention output → MLP head |
| TST_AEF,S2 | AEF + sparse S2 + CHELSA | Cross-Attention: AEF as query, S2/CHELSA time steps as key/value; skip connection AEF → head; head init near 0 |

**Training:** AdamW, CrossEntropyLoss (class-weighted) / MSELoss, 200 epochs with early stopping; data augmentation via Whittaker smoothing + temporal shift + noise injection (S2); temporal shift only (CHELSA); Gaussian noise added to random AEF features; augmentation probability based on inverse kernel density of target distribution

**Evaluation:** 5-fold CV; 20% hold-out test per fold; Acc, F1m, F1w (FVT); RMSE, MAE, R² (ETC); spatial mapping of Cilento National Park for qualitative assessment; Integrated Gradients (IG) for feature attribution

---

## Distinctive Features

- **AEF as cross-attention query:** the model explicitly treats the stable, multi-modal AEF embedding as a query attending over task-specific S2 time series observations — conceptually treating AEF as contextual knowledge and S2 as detailed phenological evidence
- **Skip connection + head init near 0:** ensures the fusion model is initialised as "MLP_AEF with no S2 contribution," so S2 features only improve predictions if genuinely informative; prevents attention collapse early in training
- **IKD-based augmentation probability:** augmentation frequency is weighted by the inverse kernel density of the target label distribution, amplifying rare labels — a principled alternative to class-weighting applied at the data level
- **Integrated Gradients for AEF vs S2 attribution:** quantifies per-sample relative contribution of AEF vs S2/CHELSA to model output, revealing that AEF attends less to S2 when cloud gaps are high — demonstrating model robustness to missing data
- **Training time comparison:** MLP_AEF: 30 s vs. TST_S2: ~12 min vs. TST_AEF,S2: ~5 min (same batch size, 200 epochs) — AEF-based models are 10–24× faster before accounting for S2 preprocessing time

---

## Experimental Setup and Results

**ETC regression results (mean ± std across 5 folds):**

| Model | MAE | RMSE | R² |
|-------|-----|------|----|
| RF_S2 | 0.127±0.008 | 0.179±0.011 | 0.691±0.023 |
| MLP_AEF | 0.134±0.012 | 0.180±0.011 | 0.687±0.034 |
| TST_S2 | 0.125±0.012 | 0.177±0.015 | 0.698±0.032 |
| **TST_AEF,S2** | **0.110±0.014** | **0.161±0.016** | **0.724±0.041** |

**FVT classification results:**

| Model | Acc | F1m | F1w |
|-------|-----|-----|-----|
| RF_S2 | 0.712±0.011 | 0.662±0.022 | 0.717±0.019 |
| MLP_AEF | 0.734±0.012 | 0.678±0.029 | 0.733±0.012 |
| TST_S2 | 0.736±0.014 | 0.706±0.016 | 0.735±0.014 |
| **TST_AEF,S2** | **0.757±0.016** | **0.712±0.018** | **0.747±0.016** |

- Fusion model outperforms stand-alone models by +2.6% Acc and −0.018 RMSE
- Wilcoxon signed-rank test: TST_AEF,S2 always ranks best across all folds (p=0.031 for all pairs)
- MLP_AEF and TST_S2 achieve similar accuracy despite radically different input processing
- RF underperforms DL models at larger dataset (FVT, n=9854); competitive at smaller dataset (ETC, n=2016)

**Feature attribution (Integrated Gradients):**
- AEF contributes ~3× more to model output than S2/CHELSA (attribution ratio 22.1:8.0)
- S2/CHELSA attributions follow phenological cycle: positive/negative contributions alternate seasonally; high tasmax in summer contributes to mediterranean broad-leaved class
- Per-sample attribution varies (min 0.14, max 1.15, SD=0.16) — CA attends less to S2 when S2 observation density is low (cloud-heavy periods)

**Qualitative mapping (Cilento National Park):**
- MLP_AEF maps are spatially smooth but miss fine-scale forest type boundaries; high SD on north-facing slopes (topographic AEF bias suspected)
- TST_S2 maps have higher pixel noise but sharper forest edges; high SD on steep north-facing terrain (winter cloud gaps)
- TST_AEF,S2 maps show intermediate sharpness and topographic awareness; random-pattern SD suggests noise from S2 input rather than systematic topographic bias

---

## Advantages and Limitations

**Advantages:**
- AEF-only models match specialised S2 models while eliminating all time series preprocessing — a practical win for large-scale operational mapping
- Cross-attention fusion outperforms both individual approaches, capturing complementary phenological detail from S2 while maintaining AEF stability
- Skip connection + head initialisation provides training safety: model degrades gracefully to AEF-only baseline if S2 adds no information
- CA mechanism provides adaptive, sample-wise modality weighting — more robust to cloud gaps than hard-fused models
- Integrated Gradients explain which modality drives each prediction, supporting scientific interpretability

**Limitations:**
- High intra-model variability across CV folds due to small dataset sizes (2016–9854 plots) and class distribution imbalance between folds; spatial autocorrelation in random splits likely inflates metrics
- CA may underrepresent S2/CHELSA data — MLP_AEF and TST_S2 achieve similar accuracy, raising the question whether CA fully exploits S2 information
- Large inter-model spatial differences in mountainous terrain (>±20% ETC) despite comparable aggregate metrics — good CV metrics do not guarantee good spatial mapping
- North-facing slopes problematic for all models: AEF has topographic embedding bias; S2 suffers winter cloud/illumination gaps
- AEF embedding access requires GEE; model weights not open-sourced

---

## Conclusion

This paper demonstrates that AlphaEarth Foundation embeddings provide a competitive, preprocessing-free alternative to specialised Sentinel-2 time series models for Italian forest type and cover mapping — achieving comparable accuracy with a 10–24× reduction in training time and no sensor-specific preprocessing pipeline. The Cross-Attention fusion model (TST_AEF,S2) consistently outperforms all single-source approaches by leveraging AEF as a stable contextual baseline that adaptively queries S2 time series for phenological detail. Integrated Gradients analysis confirms that S2/CHELSA adds meaningful seasonal information on top of AEF, particularly for discriminating vegetation types with distinct phenologies. The study positions AEF-augmented fusion models as a practical path toward scalable, continental-scale forest mapping with reduced DL expertise requirements.

## Related pages
- [[ae_training]]
- [[hiebl_2025_pretraining]]
- [[brown_2025_alphaearth]]
- [[transfer_learning_remote_sensing]]
- [[transformers_time_series]]
- [[transformer_sits]]
- [[geospatial_foundation_models]]
- [[deep_ensemble_uncertainty]]
- [[tree_species_mapping]]
- [[sentinel_2]]
- [[sentinel_1_sar]]
- [[evergreen_broadleaved_expansion]]
- [[wang_2026_foundation]]
- [[tseng_2024_presto]]
- [[lang_2024_canopy_height]]
- [[zerveas_2020_framework_transformer]]
