---
name: transfer_learning_remote_sensing
description: Transfer learning and pretraining strategies for remote sensing — supervised contextual pretraining, self-supervised MVP, and uncertainty quantification for small-data vegetation mapping
type: reference
tags:
  - deep-learning
  - machine-learning
  - remote-sensing
---

# Transfer Learning in Remote Sensing

**Summary**: Transfer learning addresses the small data problem in remote sensing vegetation mapping by pretraining deep learning models on larger, related datasets before fine-tuning on scarce target observations, substantially improving generalisation to new regions.

**Sources**: [[hiebl_2025_pretraining]], [[chen_2020_contrastive_framework]], [[brown_2025_alphaearth]], [[sylvain_2024_tree_species_uncertainty]], [[safonova_2023_small_data]], [[reichstein_2019_deep_learning_earth_sciences]], [[kattenborn_2021_review_cnn_vegetation_monitoring]], [[wen_2023_transformers_time_series]], [[vaswani_2023_attention_is_all]], [[yuan_2025_sits_augmentation]], [[sze_2017_efficient_dnn_processing]], [[mila_2024_spatial_proxies]], [[bernico_2019_domain_similarity]], [[yuan_2022_sitsformer]], [[yuan_2023_pretraining]], [[zerveas_2020_framework_transformer]], [[tseng_2024_presto]], [[wang_2026_foundation]], [[klehr_2025_synthetic_data]], [[lakshminarayan_2017_uncertainty]], [[seitzer_2022_uncertainty]], [[manas_2021_seasonal_contrast]], [[tan_2025_deep_tree_species]]

**Last updated**: 2026-05-14

---

## The Small Data Problem

Deep learning (DL) models for vegetation RS analysis require substantial labeled training data, but high-quality in-situ observations are scarce and expensive to collect. The gap between available labeled data and model data requirements drives three strategies:

1. **Direct training**: use only available labeled target data → prone to overfitting, poor OOD generalisation
2. **Supervised pretraining** (transfer learning): pretrain on larger related dataset, fine-tune on target data
3. **Self-supervised pretraining**: learn from unlabeled satellite data, then fine-tune on labeled target data

## Supervised Contextual Pretraining

Key principle: pretraining task similarity to the target task determines how much benefit transfer provides.

- **High similarity** (same modality, similar target variable): largest performance gain; pretrained features transfer directly; **feature extraction ≈ fine-tuning** at small data sizes (source: [[bernico_2019_domain_similarity]])
- **Lower similarity** (same modality, different task): useful but partial transfer; **fine-tuning > feature extraction** consistently (source: [[bernico_2019_domain_similarity]])
- **High dissimilarity**: fine-tuning required; more target data needed; at some threshold, training from scratch may be preferable (source: [[bernico_2019_domain_similarity]])
- **Empirical scaling law**: accuracy improves **log-linearly with target data size** in every similarity regime (source: [[bernico_2019_domain_similarity]])
- Applied in Hiebl et al. (2025): pretraining on Italian Forest Vegetation Database (VDB, 16,908 plots) for EVE cover regression (mVDB_cover) or forest type classification (mVDB_ftype), both outperforming direct training; mVDB_cover (task-similar) outperforms mVDB_ftype (source: [[hiebl_2025_pretraining]])

**Why it works:**
- Larger pretraining dataset covers more of the spectral-temporal feature space → backbone learns more generalisable phenological representations
- Saliency maps show pretrained models extract cleaner, more temporally coherent seasonal patterns than non-pretrained models

## Self-Supervised Pretraining: Masked Value Prediction (MVP)

MVP enables learning from **unlabeled** satellite time series:
- Data corruption: randomly mask a fraction of the input time series (16% mean window length, 25% total masking)
- Model learns to reconstruct the full phenological curve from partial observations
- Forces the model to learn temporal continuity and phenological coherence — relevant for cloud-affected RS data
- Applied in Hiebl et al. (2025): mUPD pretrained on 100,000 unlabeled Italian forest points; intermediate performance — did not match supervised pretraining because MVP-learned features were not directly transferable to EVE cover regression task (source: [[hiebl_2025_pretraining]])

MVP vs contrastive learning: MVP leverages temporal continuity and phenological patterns typical of vegetation STS; contrastive methods (e.g., SimCLR; source: [[chen_2020_contrastive_framework]]) use random augmentations (cropping, colour distortion, blur) to create positive pairs — effective for natural images but may not align with RS time series structure where temporal coherence is the key signal (source: [[hiebl_2025_pretraining]]).

**Contrastive self-supervised learning (SimCLR framework):**
- SimCLR learns visual representations without labels by maximising similarity between two augmented views of the same image (positive pairs) while pushing apart different images (negatives) — no memory bank or specialised architecture required (source: [[chen_2020_contrastive_framework]])
- Key components: shared ResNet encoder → nonlinear projection head → NT-Xent (Normalised Temperature-scaled Cross Entropy) loss; the nonlinear projection head is critical (+10pp linear evaluation accuracy over no projection; source: [[chen_2020_contrastive_framework]])
- Augmentation composition is the most important design choice: random crop + colour distortion outperforms any single augmentation; colour distortion prevents shortcut learning from colour histograms (source: [[chen_2020_contrastive_framework]])
- Achieves 76.5% top-1 ImageNet accuracy (linear evaluation), matching supervised ResNet-50 (source: [[chen_2020_contrastive_framework]])
- RS application: contrastive pretraining on unlabelled satellite imagery could bootstrap classifiers for species-rich ecosystems where labelled data is scarce; however, RS-specific augmentation policies may be needed as natural-image augmentations do not transfer directly

**Temporal contrastive learning — Seasonal Contrast (SeCo):**
- SeCo replaces synthetic augmentation pairs with **temporal positive pairs**: images of the same geographic location at different timestamps (~3 months apart) as positive pairs (source: [[manas_2021_seasonal_contrast]])
- The key inductive bias (stated explicitly): *"encouraging the representation to be invariant to seasonal changes is a strong inductive bias"* for land-cover classification — ecological stability over time makes temporal pairs semantically similar (source: [[manas_2021_seasonal_contrast]])
- Multi-head design produces **three embedding sub-spaces**: Z₀ invariant to all transforms; Z₁ invariant to seasonal only; Z₂ invariant to artificial only — representations encode both time-varying and invariant information
- **Outperforms ImageNet pre-training** on BigEarthNet (+4–6% mAP), EuroSAT (+6.7% accuracy) — in-domain RS pre-training beats natural-image domain transfer; also beats MoCo-v2 + temporal positive pairs (TP) without multi-head design by ~4 pp
- **Critical for forest mapping**: this is the canonical source for the assumption that the same forest plot observed in two different year windows constitutes a valid contrastive positive pair (temporal ecological stability assumption)
- **Scope of assumption**: SeCo validates 3-month (seasonal) stability; multi-year stability (1–2 year windows used in forest mapping workflows) is an extension supported by forest ecology literature (forests change on decadal, not annual, timescales — [[herraiz_2025_phen_shifts_mediterranean]]; [[grabska_2024_tree_species_map]]) but not directly tested in SeCo

## Epistemic vs Aleatoric Uncertainty

Probabilistic DL models can quantify two distinct sources of uncertainty:

| Type | What it captures | How estimated | Spatial pattern |
|------|-----------------|--------------|----------------|
| **Epistemic (EU)** | Model/data uncertainty — lack of training data coverage | Variance across ensemble predictions | Spatially coherent — flags OOD regions |
| **Aleatoric (AU)** | Observation noise / label ambiguity | Learned per-pixel variance (NLL training) | Spatially incoherent — captures local label noise |

**Epistemic uncertainty in practice** (source: [[hiebl_2025_pretraining]]):
- High EU → non-forested areas, shaded north-facing slopes, underrepresented forest types (coniferous OOD)
- Can guide active learning: prioritise field data collection in high-EU areas
- 92% of pixels have inter-model std within ±15% coverage; only 2% below 5% std

**Aleatoric uncertainty in practice**:
- Captures label noise from plot-level measurement ambiguity
- Higher in mixed/heterogeneous stands where cover labels are less reliable
- Not spatially coherent — reflects inherent data variability rather than regional patterns

## Deep Ensemble Uncertainty

A practical approach to uncertainty quantification without full Bayesian inference:
- Share a common backbone (feature extractor); branch into M independently initialized prediction heads
- EU = variance across head predictions
- AU = average of per-head learned variances
- Gaussian NLL loss: ℒ_NLL = ½ log(σ²) + (y − μ)² / (2σ²)
- Applied with M=15 heads in Hiebl et al. (2025) on InceptionTime backbone

## Spatial Autocorrelation in Validation

A critical methodological issue in vegetation RS:
- Plot observations from the same area share spectral-temporal features → random train/test splits inflate validation accuracy
- **Cluster-based spatial split** (k-means clustering by coordinates) ensures test plots are spatially separated from training plots
- In Hiebl et al. (2025): spatially-split model (mVPO2024_r) showed higher RMSE on validation — more honest estimate of generalisation (source: [[hiebl_2025_pretraining]])
- Leave-one-park-out CV provides the most rigorous generalisation test
- **Random k-fold CV systematically mis-ranks models** with clustered samples or when assessing spatial-model transfer — it preferentially favours models that overfit spatial position (source: [[mila_2024_spatial_proxies]])
- **kNNDM CV** (Linnenbrink et al. 2023) matches the geographical distance distribution between train and test folds to that between training and prediction locations — correctly ranks models in both interpolation and extrapolation; available in R package `CAST` (source: [[mila_2024_spatial_proxies]])
- See [[spatial_proxies_random_forest]] for the broader pitfalls of adding spatial proxies as ML predictors, and [[area_of_applicability]] for predictor-space-based extrapolation diagnostics

## Error Sources in Vegetation Mapping

Highest Pearson correlations with RMSE across test sites (source: [[hiebl_2025_pretraining]]):
- γ-diversity (Shannon-Index): r = 0.88
- β-diversity (Jensen-Shannon Divergence): r = 0.91
- Feature space distance: r = 0.47

**Implication**: taxonomic diversity of vegetation is the primary bottleneck for DL model accuracy — pretraining helps but cannot overcome fundamental heterogeneity limits.

## Alternative Uncertainty Approach: CNN Ensemble Agreement

Sylvain et al. (2024) use a different ensemble uncertainty strategy — inter-model agreement among 9 CNN models — applicable when explicit probabilistic training is not used (source: [[sylvain_2024_tree_species_uncertainty]]):
- **Agreement %** = proportion of the 9 models predicting the dominant class per pixel; low agreement = high uncertainty
- ReLU CNNs produce overconfident softmax probabilities → agreement map preferred over raw class probabilities
- Validated: agreement % positively correlated with F1-score across 1,311 independent NFI plots — reliable spatially explicit uncertainty indicator
- Broadleaf species / mixed stands → lower agreement than pure coniferous or land cover classes; reflects real spectral heterogeneity
- Comparison with deep ensemble (Hiebl et al. 2025): both use ensemble variance as epistemic uncertainty proxy; Hiebl uses 15-head shared-backbone ensemble on 1D Sentinel-2 time series; Sylvain uses 9 fully separate CNN models on 2D aerial patches — complementary designs for different sensor modalities

**Sources**: [[hiebl_2025_pretraining]], [[sylvain_2024_tree_species_uncertainty]]

## Geospatial Foundation Models

A new paradigm beyond task-specific transfer learning: train a single large model on multi-modal, multi-source EO data to produce universal representations usable for any mapping task with minimal labels (source: [[brown_2025_alphaearth]]):

- **AlphaEarth Foundations (AEF)**: ~480M-parameter model trained on >3 billion observations from 10 data sources (Sentinel-2, Landsat, Sentinel-1, ALOS PALSAR-2, DEM, GEDI LiDAR, ERA5 climate, GRACE, land cover, geotagged text); outputs 64-dimensional embedding fields at 10m resolution globally for 2017–2024 (source: [[brown_2025_alphaearth]])
- **Architecture — Space Time Precision (STP) encoder**: parallel spatial self-attention, time-axial self-attention, and convolution branches; continuous-time conditioning enables arbitrary date range queries without retraining (source: [[brown_2025_alphaearth]])
- **Performance**: reduces error by ~23.9% vs next-best approach across 15 mapping evaluations (land cover, crop type, tree genera, biophysical variables); outperforms all designed featurizations (CCDC, MOSAIKS, composites) AND all prior learned models (SatCLIP, Prithvi, Clay); works best in few-shot regimes (1–10 labels per class) (source: [[brown_2025_alphaearth]])
- **Key advantage over task-specific transfer learning**: frozen embeddings require no backbone retraining for new tasks — a single feature space serves vegetation mapping, land cover classification, disturbance detection, and biophysical retrieval simultaneously (source: [[brown_2025_alphaearth]])
- **Limitation**: training covers only ~1.1% of Earth's land surface; annual temporal resolution of released embeddings too coarse for phenology/sub-annual change; model weights not open-sourced (source: [[brown_2025_alphaearth]])
- **Lightweight alternative — PRESTO**: pre-trained pixel-time-series Transformer with up to 1000× fewer parameters than ViT-based foundation models, ingests S1+S2+ERA5+NDVI+Dynamic World+DEM+location; competitive on global RS tasks (source: [[tseng_2024_presto]])
- **Operational use case**: AEF + S1/S2 + GEDI fusion → annual 10 m CHM with substantial gain over single-source models (source: [[wang_2026_foundation]])

## SITS-Specific Pretraining (Transformer Lineage)

A parallel line of work has developed **Transformer-based self-supervised pretraining specifically for SITS** — see [[transformer_sits]] for full treatment. Key references:
- **TST** (Zerveas et al. 2020): first MTS Transformer + masked-value prediction; outperforms supervised SOTA without extra data (source: [[zerveas_2020_framework_transformer]])
- **SITS-BERT** (Yuan & Lin 2022): pixel-based, sinusoidal DOY positional encoding, denoising proxy task; +1.91–6.69% accuracy gains (source: [[yuan_2023_pretraining]])
- **SITS-Former** (Yuan et al. 2022): patch-based extension with 3D-CNN embedding; +2.64–3.30% accuracy (source: [[yuan_2022_sitsformer]])

## Pseudo-labeling for Mixed-Stand Extension

A semi-supervised strategy that extends DL training beyond pure stands to mixed-species plots (source: [[tan_2025_deep_tree_species]]):

1. Train a binary/multi-class DL model on labeled **pure-stand** samples
2. Apply model to **unlabeled mixed-stand** pixels
3. Assign pseudo-labels to pixels where model confidence exceeds a threshold (e.g. 0.9)
4. Retrain final model on pure + pseudo-labeled combined

**Key findings** from Tan et al. (2025): pseudo-labeling for evergreen-deciduous mixed units improved generalisation to mixed-stand areas; threshold at 0.9 confidence prevents label noise propagation; using only pairs with large phenological contrast (evergreen vs deciduous) ensures reliable pseudo-label quality. Pretraining (SSL) + pseudo-labeling gave OA 0.847, macro-F1 0.836 vs OA 0.764 / macro-F1 0.737 without pretraining (source: [[tan_2025_deep_tree_species]]).

This pattern directly supports the **artificial label generation approach**: train a simple model (RF or DL) on existing plot observations to generate spatially explicit labels, then train a deeper time-series model on those labels. Published precedents for the principle include [[kang_2021_lai_landsat]] (MODIS as RF labels → 30m LAI) and the noisy-label family (see [[transfer_learning_remote_sensing]] — SinoLC-1, cross-resolution mapping).

## Synthetic Data Augmentation

A complementary "transfer learning" idea when pure-pixel reference data are scarce: **synthetic linear mixing of pure-pixel endmembers** generates large training sets for fractional regression (source: [[klehr_2025_synthetic_data]]):
- 30 pure pixels per class can suffice
- ANN regression on synthetic library + ensemble for uncertainty
- Particularly valuable for rare species where NFI sampling is sparse

## Uncertainty in Transfer Learning Pipelines

The wiki's transfer-learning workflow integrates **deep ensemble uncertainty** with **β-NLL** training — see [[deep_ensemble_uncertainty]] for full treatment:
- Proper scoring rule training (source: [[lakshminarayan_2017_uncertainty]])
- β-NLL fixes heteroscedastic NLL pitfall (source: [[seitzer_2022_uncertainty]])
- M=15 shared-backbone heads in [[hiebl_2025_pretraining]]

## Deep Learning Techniques for Small Data (RS-Specific Overview)

Ten techniques for addressing limited labelled data in RS deep learning (source: [[safonova_2023_small_data]]):
- **Transfer learning** (fine-tune from pretrained model) — most accessible first approach; see sections above
- **Self-supervised learning (SSL)** — learn from unlabelled data via MVP or contrastive learning
- **Semi-supervised** — combine small labelled + large unlabelled; pseudo-labelling strategies
- **Few-shot learning** — meta-learning for generalization from very few examples per class
- **Active learning** — iteratively select most informative samples for annotation
- **Ensemble learning** — multiple models for robustness and uncertainty quantification
- **Spatial k-fold CV** — critical for honest accuracy in spatially autocorrelated RS data (source: [[safonova_2023_small_data]])
- **Data augmentation** — label-preserving transformations to expand effective training set; see [[yuan_2025_sits_augmentation]] for SITS-specific techniques

## Hybrid Physics-Informed Deep Learning

Deep learning in geosciences must go beyond pattern matching to respect physical process constraints (source: [[reichstein_2019_deep_learning_earth_sciences]]):
- Purely data-driven DL fails at extrapolation beyond training distribution
- Hybrid models couple physical process models with DL: physics provides structure/constraints; DL fills gaps and corrects systematic errors
- Key challenge: uncertainty quantification — DL models are overconfident; calibrated uncertainty is needed for Earth science use
- Applications: carbon flux estimation, seasonal forecasting, land surface modelling

## Transformer Architecture and Attention for Time Series

The Transformer (Vaswani et al. 2017; source: [[vaswani_2023_attention_is_all]]) replaces recurrence with self-attention, enabling:
- Full parallelisation during training (vs. sequential LSTM computation)
- O(1) path length between any two sequence positions → effective long-range dependency modelling
- Multi-head attention captures multi-scale temporal patterns (seasonal, phenological, event-scale)

For SITS applications, adaptations address irregular sampling and missing data (source: [[wen_2023_transformers_time_series]]):
- Timestamp-based positional encoding replaces fixed sinusoidal encoding for irregular series
- Patch-based tokenisation (PatchTST) reduces quadratic attention cost for long series
- Pre-trained Transformers on large SITS archives substantially improve few-shot classification

**Key architectural components** (source: [[vaswani_2023_attention_is_all]]):
- Scaled dot-product attention: `Attention(Q,K,V) = softmax(QKᵀ/√d_k)V`
- Multi-head attention: H parallel heads → richer multi-scale representation
- Positional encoding: injects sequence order into the attention mechanism

## CNN Efficiency and Vegetation Remote Sensing

CNN architectures (review: source: [[kattenborn_2021_review_cnn_vegetation_monitoring]]) are particularly suited for vegetation RS because:
- Local receptive fields capture vegetation canopy spatial patterns at the right scale
- Translation invariance handles variation in canopy position within images
- Multi-scale convolution captures patterns from leaf to stand level
- VHR data (sub-meter UAV/aerial) gains the most from CNN spatial feature exploitation
- Spectral-temporal 1D CNNs (e.g., InceptionTime) are effective for pixel-wise SITS classification

DNN computational efficiency (source: [[sze_2017_efficient_dnn_processing]]):
- Energy and memory bandwidth dominate computation cost, not raw FLOP count
- Compression: pruning > weight sharing > quantisation > knowledge distillation in impact order
- Efficient architectures (MobileNet, SqueezeNet) enable deployment in resource-constrained contexts

## Related pages

- [[sentinel_2]]
- [[tree_species_mapping]]
- [[functional_diversity]]
- [[national_forest_inventory]]
- [[phenology]]
- [[vaswani_2023_attention_is_all]]
- [[wen_2023_transformers_time_series]]
