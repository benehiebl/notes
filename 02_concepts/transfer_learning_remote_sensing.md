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

**Sources**: [[hiebl_2025_pretraining]], [[chen_2020_contrastive_framework]], [[brown_2025_alphaearth]], [[sylvain_2024_tree_species_uncertainty]]

**Last updated**: 2026-05-05

---

## The Small Data Problem

Deep learning (DL) models for vegetation RS analysis require substantial labeled training data, but high-quality in-situ observations are scarce and expensive to collect. The gap between available labeled data and model data requirements drives three strategies:

1. **Direct training**: use only available labeled target data → prone to overfitting, poor OOD generalisation
2. **Supervised pretraining** (transfer learning): pretrain on larger related dataset, fine-tune on target data
3. **Self-supervised pretraining**: learn from unlabeled satellite data, then fine-tune on labeled target data

## Supervised Contextual Pretraining

Key principle: pretraining task similarity to the target task determines how much benefit transfer provides.

- **High similarity** (same modality, similar target variable): largest performance gain; pretrained features transfer directly
- **Lower similarity** (same modality, different task): useful but partial transfer; some features re-learned during fine-tuning
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

## Related pages

- [[sentinel_2]]
- [[tree_species_mapping]]
- [[functional_diversity]]
- [[national_forest_inventory]]
- [[phenology]]
