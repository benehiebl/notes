---
title: "Leveraging Sentinel-1/2 time series and deep learning for accurate forest tree species mapping"
authors:
  - Tan, Jun
  - Li, Jing
  - Ma, Tianyue
  - Yan, Xingguang
  - Huo, Ziye
year: 2025
source: tan_2025_deep_tree_species
tags:
  - deep-learning
  - remote-sensing
  - machine-learning
keywords:
  - tree species classification
  - Sentinel-1
  - Sentinel-2
  - satellite image time series
  - Transformer
  - self-supervised pretraining
  - pseudo-labeling
  - mixed species
  - red-edge
  - phenological separability
status: read
---

# Tan et al. 2025 — Deep Learning + Pseudo-labeling for Forest Tree Species from S1/S2 Time Series

## Title and Authors
**Leveraging Sentinel-1/2 time series and deep learning for accurate forest tree species mapping**
Jun Tan, Jing Li, Tianyue Ma, Xingguang Yan, Ziye Huo — *Frontiers in Forests and Global Change* 8: 1599510 (2025). DOI: 10.3389/ffgc.2025.1599510.

## Quick Overview
- **Why is it relevant?** Implements **pseudo-labeling** to extend pure-stand training data to mixed-species stands for DL tree species classification — the closest published parallel to the ls_mapping approach of generating artificial labels for mixed-cover scenarios, directly answering the knowledge gap at line 64 of the paper.
- **What was done?** Trained a Transformer on 24-month S1+S2 SITS with (1) SSL pretraining on unlabeled forest pixels and (2) pseudo-label generation for mixed-species plots using a binary DL classifier, then fine-tuned on the expanded dataset.
- **What is the main outcome?** OA 0.847, macro-F1 0.836 (7 species; Shanxi, China); pretraining adds +8.3pp macro-F1 over non-pretrained; longer time series consistently improves accuracy; red-edge indices + leaf-off periods are most discriminative.

## Main Goal and Fundamental Concept
Forest inventory data typically records dominant and secondary species by polygon, but: (1) pure stands are a simplification — most polygons are mixed; (2) relying only on pure-stand samples biases training toward homogeneous forests, reducing model generalisation to mixed areas and overestimating accuracy; (3) mapping wall-to-wall requires per-pixel labels. The paper addresses these limitations via two strategies:
1. **SSL pretraining** on unlabeled forest pixels to learn temporal spectral context without field surveys
2. **Pseudo-labeling** for mixed-species units: use a model trained on pure stands to probabilistically assign labels to mixed plots, then retrain with expanded dataset

## Technical Approach

**Study area**: Shanxi Province, China — 7,715 km², forests 50% of area, elevation 534–2564 m; 7 target species (3 deciduous, 4 evergreen conifers + broadleaves).

**Remote sensing**: S1+S2 SITS 2022–2023 via GEE; cloud removal + monthly median composites; resampled to 10m; 33 variables including raw bands + 20 vegetation indices (NDVI, GNDVI, LSWI, EVI, NDVIre1-3, NDre1-2, Clre, PSRI, MSAVI, MSRre, MTCI, CCCI, S2REP, RVI, VVVHR, NDIVV).

**Three-stage pipeline:**

*Stage 1 — SSL pretraining:*
- ESA WorldCover forest mask → 380,000 unlabeled samples at 100m intervals
- Pretext task (SITS-BERT / Yuan & Lin 2021): add uniform noise [-0.5, 0.5] to 4/24 monthly time points → train Transformer to reconstruct original values (MSE loss)
- Transformer: 3 layers, 8-head self-attention, embedding dim=512, sinusoidal positional encoding

*Stage 2 — Pseudo-labeling for mixed stands:*
- Pure-stand polygons → generate pure-species training samples
- Mixed evergreen-deciduous polygons → unlabeled samples
- **Binary Transformer classifier** trained on pure-stand samples of one evergreen + one deciduous species
- Apply to unlabeled mixed-stand pixels → assign pseudo-label = class with score > 0.9
- Result: ~13,000 pseudo-labeled samples across 6 species pairs (see Table 1)

*Stage 3 — Fine-tuning:*
- Pretrained backbone + classification head (output replaced with CrossEntropy)
- Train on pure + pseudo-labeled samples combined
- Stratified 60/40 test/train-val split; 5-fold CV; inverse sampling-intensity weighted accuracy metrics

## Distinctive Features
- **Pseudo-labeling threshold (0.9 confidence)** ensures only high-certainty mixed-plot pixels are added — guards against label noise propagation
- **Only evergreen-deciduous mixed units** used for pseudo-labeling — largest phenological contrast between classes → most reliable scores
- **Ablation on time series length**: tests systematically from 2 months to 24 months — documents the accuracy plateau after a full growing cycle
- **Multi-dimensional interpretability**: self-attention weight matrices, t-SNE hidden feature visualisation, separability index (SI-global), monthly PCA contributions
- **Inverse sampling-intensity weighting** corrects for spatial clustering of reference polygons

## Experimental Setup and Results

**Dataset (Table 1):**
- Total samples: 65,868 (pure + pseudo-labeled)
- Pseudo-labeled proportions per species: 5–52% of total per class (highest for Quercus and Pinus tabuliformis)

**Accuracy (5-fold CV, 24-month S1+S2):**
- OA 0.847, Kappa 0.815, macro-F1 0.836
- With inverse sampling weighting: OA_w 0.834, macro-F1_w 0.813
- Per-species F1: PT (pine) 0.89, BA (birch) 0.86, PO 0.85, LP (larch) 0.84, OT 0.81, QW (oak) 0.80, PB 0.79, PS (poplar) 0.81

**Without pretraining (24-month):** OA 0.764, macro-F1 0.737 → **pretraining gain: +8.3pp macro-F1**

**Time series length effect (Figure 5):**
- 2 months: OA 0.496, macro-F1 0.384
- 7 months: OA 0.68 (April–September, growing season)
- 12 months (full year): OA ~0.795
- 24 months: OA 0.847 → second year adds meaningful gain for inter-annual features
- Beyond 24 months (adding 3rd year): marginal additional gain

**Key spectral-temporal drivers:**
- **Vegetation indices dominate PC1** (37.9% variance); optical bands dominate PC2 (19.8%)
- **Red-edge indices** (NDre1, NDre2, CIre, NDVIre1, MSRre, MSReN) most discriminative in separability index
- **January–April and October–December** (leafless period for deciduous) show highest separability between evergreen and deciduous; July–September also high
- Self-attention focuses on seasonal transitions; heads capture different aspects (leaf-on, leaf-off, cross-year)

## Advantages and Limitations
- **Advantages**: Addresses pure-stand bias systematically; pseudo-label threshold (0.9) is principled; pretraining gain quantified; full interpretability analysis; open code; directly applicable to any species with sufficient phenological contrast.
- **Limitations**: Pseudo-labeling only applied to evergreen-deciduous pairs — same-type mixed species (two conifers, two deciduous) not addressed; binary classifier assumption may introduce systematic bias toward dominant species; spatial autocorrelation between training polygons and test pixels not fully addressed (cf. [[spatial_proxies_random_forest]]); study area in China, single region — transferability needs validation.

## Conclusion
**SSL pretraining + pseudo-labeling for mixed-stand extension is a validated, published approach for DL tree species classification from SITS.** The pseudo-labeling mechanism — train binary classifier on pure stands → score mixed stands → accept labels above 0.9 confidence — directly supports the methodological justification for artificial label datasets generated from plot observations. The 24-month multi-year time series advantage is consistent with findings in [[grabska_2024_tree_species_map]] and the ls_mapping approach. The **red-edge + leaf-off periods** result provides empirical RS support for the spectral separability of evergreen vs deciduous species.

## Related pages
- [[tree_species_mapping]]
- [[transformer_sits]]
- [[transfer_learning_remote_sensing]]
- [[sentinel_2]]
- [[sentinel_1_sar]]
- [[yuan_2023_pretraining]]
- [[yuan_2022_sitsformer]]
- [[blickensdörfer_2024_tree_species]]
- [[klehr_2025_synthetic_data]]
- [[hemmerling_2021_forest_mapping_s2]]
- [[grabska_2024_tree_species_map]]
- [[manas_2021_seasonal_contrast]]
- [[deep_ensemble_uncertainty]]
- [[zangh_2017_generalization]]
- [[hiebl_2025_pretraining]]
