---
name: transfer_learning_remote_sensing
description: Transfer learning and pretraining strategies for remote sensing — supervised contextual pretraining, self-supervised MVP, and uncertainty quantification for small-data vegetation mapping
type: reference
---

# Transfer Learning in Remote Sensing

**Summary**: Transfer learning addresses the small data problem in remote sensing vegetation mapping by pretraining deep learning models on larger, related datasets before fine-tuning on scarce target observations, substantially improving generalisation to new regions.

**Sources**: hiebl_2025_pretraining.pdf

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
- Applied in Hiebl et al. (2025): pretraining on Italian Forest Vegetation Database (VDB, 16,908 plots) for EVE cover regression (mVDB_cover) or forest type classification (mVDB_ftype), both outperforming direct training; mVDB_cover (task-similar) outperforms mVDB_ftype (source: hiebl_2025_pretraining.pdf)

**Why it works:**
- Larger pretraining dataset covers more of the spectral-temporal feature space → backbone learns more generalisable phenological representations
- Saliency maps show pretrained models extract cleaner, more temporally coherent seasonal patterns than non-pretrained models

## Self-Supervised Pretraining: Masked Value Prediction (MVP)

MVP enables learning from **unlabeled** satellite time series:
- Data corruption: randomly mask a fraction of the input time series (16% mean window length, 25% total masking)
- Model learns to reconstruct the full phenological curve from partial observations
- Forces the model to learn temporal continuity and phenological coherence — relevant for cloud-affected RS data
- Applied in Hiebl et al. (2025): mUPD pretrained on 100,000 unlabeled Italian forest points; intermediate performance — did not match supervised pretraining because MVP-learned features were not directly transferable to EVE cover regression task (source: hiebl_2025_pretraining.pdf)

MVP vs contrastive learning: MVP leverages temporal continuity and phenological patterns typical of vegetation STS; contrastive methods use random masking which may not align with RS time series structure.

## Epistemic vs Aleatoric Uncertainty

Probabilistic DL models can quantify two distinct sources of uncertainty:

| Type | What it captures | How estimated | Spatial pattern |
|------|-----------------|--------------|----------------|
| **Epistemic (EU)** | Model/data uncertainty — lack of training data coverage | Variance across ensemble predictions | Spatially coherent — flags OOD regions |
| **Aleatoric (AU)** | Observation noise / label ambiguity | Learned per-pixel variance (NLL training) | Spatially incoherent — captures local label noise |

**Epistemic uncertainty in practice** (source: hiebl_2025_pretraining.pdf):
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
- In Hiebl et al. (2025): spatially-split model (mVPO2024_r) showed higher RMSE on validation — more honest estimate of generalisation (source: hiebl_2025_pretraining.pdf)
- Leave-one-park-out CV provides the most rigorous generalisation test

## Error Sources in Vegetation Mapping

Highest Pearson correlations with RMSE across test sites (source: hiebl_2025_pretraining.pdf):
- γ-diversity (Shannon-Index): r = 0.88
- β-diversity (Jensen-Shannon Divergence): r = 0.91
- Feature space distance: r = 0.47

**Implication**: taxonomic diversity of vegetation is the primary bottleneck for DL model accuracy — pretraining helps but cannot overcome fundamental heterogeneity limits.

## Related pages

- [[sentinel_2]]
- [[tree_species_mapping]]
- [[functional_diversity]]
- [[national_forest_inventory]]
- [[phenology]]
