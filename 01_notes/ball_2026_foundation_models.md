---
title: "Geospatial foundation models enable data-efficient tree species mapping in temperate mountain forests"
authors:
  - James GC Ball
  - Jana Annika Wicklein
  - Zhengpeng Feng
  - Jovana Knezevic
  - Sadiq Jaffer
  - Anil Madhavapeddy
  - Clement Atzberger
  - Michele Dalponte
  - David Coomes
year: 2026
tags:
  - deep-learning
  - remote-sensing
  - forest-ecology
  - foundation-models
keywords:
  - geospatial foundation models
  - tree species classification
  - AlphaEarth
  - Tessera
  - Sentinel-1/2
  - label efficiency
  - soft labels
  - mountain forests
  - temporal transfer
status: read
---

## 1. Title and Authors

**Geospatial foundation models enable data-efficient tree species mapping in temperate mountain forests**
Ball et al. (2026), bioRxiv preprint. Cambridge, Edmund Mach Foundation, CYCLOPS MRV.

## 2. Quick Overview

- **Why is it relevant?** Tree species mapping in complex mountain terrain is a persistent challenge; geospatial foundation models (GFMs) offer a potential step change in data efficiency and representation quality.
- **What was done?** Two GFM embeddings (AlphaEarth and Tessera) were compared against conventional Sentinel-1+2 composites for 18-class tree species classification in Trentino (Italy), using parcel-level forest inventories as reference data.
- **What is the main outcome?** GFM embeddings consistently outperform conventional composites (weighted F1 = 0.83 vs. 0.80), reach near-asymptotic accuracy with 5% of training data, and shift the primary bottleneck from feature engineering to reference-data availability and temporal alignment.

## 3. Main Goal and Fundamental Concept

The study evaluates whether globally pre-trained GFMs can serve—without any fine-tuning—as data-efficient representations for regional-scale tree species mapping in heterogeneous mountain forests. The central hypothesis is that self-supervised learning on petabyte-scale satellite archives encodes species-discriminative spectral-temporal structure that downstream classifiers can exploit with far fewer labelled parcels than conventional feature engineering requires.

## 4. Technical Approach

- **Study area:** Trentino, northern Italy — steep elevational gradients, mixed stands, strong BRDF effects, 18 species/groups
- **Reference data:** ~83,000 forest management parcels from the Trentino Forest Inventory (2010–2021), each with species proportional cover
- **Representations compared:**
  - *AlphaEarth (AEF):* patch-level embeddings trained with multi-modal auxiliary targets (lidar, climate, topography) [[brown_2025_alphaearth]]
  - *Tessera:* pixel-level embeddings trained from S1/S2 time series via Barlow Twins self-supervised objective [[hiebl_2026_alphaearth]]
  - *Baseline:* Sentinel-1+2 seasonal spectral composites
- **Classifiers tested:** Logistic Regression, k-NN, Random Forest (RF), shallow MLP, deeper MLP — evaluated along a classifier capacity axis
- **Experimental axes:** (i) overall accuracy & ecological coherence; (ii) label efficiency (0–100% training data); (iii) label purity (30–90% dominant species threshold); (iv) ancillary terrain covariates (DEM, slope, aspect, TPI, curvature); (v) temporal transfer (train 2018, predict 2021)
- **Evaluation:** pixel-level weighted/macro F1 on pure parcels (≥80% dominant species); parcel-level Proportion L1 error for mixed stands

## 5. Distinctive Features

- First systematic evaluation of GFMs for *species-level* (18-class) tree mapping from 10 m satellite data in complex mountain terrain
- Soft-label training: species proportions from inventory used directly as supervision targets rather than hard per-pixel assignments — captures the compositional knowledge encoded in inventory data without fabricating spatial certainty
- Simultaneous comparison of five classifiers spanning linear to deep, disentangling representation quality from classifier capacity
- Ablation design: one factor varied at a time around a fixed reference configuration, enabling clean attribution of performance changes

## 6. Experimental Setup and Results

| Setting | Tessera (MLP) | AlphaEarth (MLP) | S1+2 Seasonal (MLP) |
|---|---|---|---|
| Weighted F1 (reference) | 0.824 | 0.833 | 0.797 |
| Macro F1 (reference) | 0.551 | 0.537 | 0.500 |
| PropL1 (parcel-level) | 0.349 | 0.384 | — |

Key findings:
- **Label efficiency:** Near-asymptotic performance reached with 5% of training parcels for GFMs; conventional composites require far more data to plateau [[hiebl_2025_pretraining]]
- **Classifier capacity:** Linear classifiers on GFM embeddings *underperform* an MLP on conventional composites — discriminative structure is non-linearly separable; shallow MLP captures most gains, deeper networks add nothing
- **Terrain covariates:** Adding DEM/slope/aspect/TPI provides no additional benefit — abiotic gradients are implicitly encoded in phenological signals (Tessera) or explicit auxiliary objectives (AlphaEarth)
- **Label purity:** Performance is flat from 30–80% dominant-species purity; aggressive filtering (≥90%) degrades results due to data scarcity; hard-label distillation within parcels does not help
- **Soft labels:** Using species proportions as supervision targets improves macro F1 and PropL1 for both models (Tessera macro F1: 0.551→0.586; AEF: 0.537→0.589) — particularly benefits minority species
- **Temporal transfer:** Weighted F1 declines 9% (Tessera) and 15% (AlphaEarth) when training on 2018 embeddings and predicting 2021; rare species suffer disproportionate losses
- **Ecological coherence:** Misclassification follows taxonomic/functional axes (Abies↔Picea; pine cluster; broadleaf groups) — representations encode biologically meaningful hierarchy

## 7. Advantages and Limitations

**Advantages:**
- Strong label efficiency — practical for regions with sparse inventories
- No fine-tuning required — zero-shot transfer of pre-trained embeddings
- Robust to moderate label impurity — mixed inventory parcels can be retained
- Soft-label supervision unlocks compositional information in inventory data
- Ecologically coherent error structure useful for forest management

**Limitations:**
- Temporal transfer degrades substantially, especially for rare species — temporal alignment of embeddings and reference data is critical
- Linear classifiers cannot exploit GFM embeddings — nonlinear head is required
- AlphaEarth's patch-level design may over-smooth fine-grained within-parcel spectral variation
- Terrain covariates tested only via feature concatenation — richer integration not evaluated
- Reference inventory spans 2010–2021, introducing temporal mismatch with satellite data
- Pre-print (bioRxiv), not peer-reviewed at time of note creation

## 8. Conclusion

Ball et al. (2026) demonstrate that globally pre-trained GFMs (AlphaEarth and Tessera) provide substantially more data-efficient and ecologically coherent representations for tree species mapping than conventional Sentinel-1+2 composites, achieving weighted F1 = 0.83 for 18 classes in complex mountain forest with only 5% of training parcels. The primary bottleneck shifts from feature engineering to reference-data quality, temporal alignment, and annotation strategy — soft labels from species-proportion inventories outperform hard per-pixel assignments. Temporal transfer remains an open challenge. The study directly validates the utility of [[brown_2025_alphaearth]] and [[hiebl_2026_alphaearth]] for species-level biodiversity monitoring.

## Related pages

- [[brown_2025_alphaearth]]
- [[hiebl_2026_alphaearth]]
- [[hiebl_2025_pretraining]]
- [[blickensdörfer_2024_tree_species]]
- [[bolyn_2022_tree_species_mapping]]
- [[klehr_2025_synthetic_data]]
- [[grabska_2024_tree_species_map]]
- [[gasparini_2022_nfi_italy]]
- [[geospatial_foundation_models]]
- [[tree_species_mapping]]
- [[label_efficiency]]
