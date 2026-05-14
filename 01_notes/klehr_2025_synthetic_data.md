---
title: "Mapping tree species fractions in temperate mixed forests using Sentinel-2 time series and synthetically mixed training data"
authors:
  - Klehr, David
  - Stoffels, Johannes
  - Hill, Andreas
  - Pham, Vu-Dong
  - van der Linden, Sebastian
  - Frantz, David
year: 2025
source: klehr_2025_synthetic_data
tags:
  - deep-learning
  - remote-sensing
  - machine-learning
keywords:
  - tree species fractions
  - Sentinel-2 time series
  - synthetic training data
  - regression-based unmixing
  - artificial neural network
  - mixed forests
  - data augmentation
  - rare species
status: read
---

# Klehr et al. 2025 — Tree Species Fractions in Mixed Forests with Synthetically Mixed Training Data

## Title and Authors
**Mapping tree species fractions in temperate mixed forests using Sentinel-2 time series and synthetically mixed training data**
David Klehr, Johannes Stoffels, Andreas Hill, Vu-Dong Pham, Sebastian van der Linden, David Frantz — *Remote Sensing of Environment* 323: 114740 (2025).

## Quick Overview
- **Why is it relevant?** Tackles the dual problem of **mixed forests** and **rare species** with a single methodological idea — synthetic linear-mixing data augmentation + ANN regression — that needs as few as 30 pure pixels per class. Directly relevant to Italian forest mapping where INFC plots are sparse and mixed.
- **What was done?** S2 time series + synthetic spectral library built by randomised linear mixing of pure-pixel endmembers; ensemble of ANN regressors predicts per-pixel tree species fractions; validated against forest planning data in Rhineland-Palatinate (8,080 km² forest).
- **What is the main outcome?** MAE 2.76–16.05% per species, R² up to 0.92; sufficient discrimination among nine tree species + an "other" class with just 30 pure pixels per class; viable operational deployment when reference data are limited.

## Main Goal and Fundamental Concept
Tree species mapping at 10 m S2 resolution fights two problems: (1) most forest pixels are *mixed* — even a single tree's canopy may span multiple pixels; (2) rare species are under-represented in standard inventories, biasing classifiers. Klehr et al. treat the task as **regression rather than classification** and synthetically generate large training sets by linearly mixing pure-pixel endmembers — letting an ANN learn the spectral-temporal signatures of *any* species mixture.

## Technical Approach
- Study area: Rhineland-Palatinate, Germany, 19,850 km² (41% forest); 14 forest ecoregions.
- Reference: statewide forest planning data + NFI; pure pixel endmembers per species.
- Sensor: dense Sentinel-2 time series (gap-filled, 2019–2023 for time series reconstruction; 2022 for prediction).
- **Synthetic mixing**: for each species, take its pure-pixel spectral-temporal profiles and randomly linearly combine them with profiles from other species in random proportions → synthetic library with controlled mixture fractions as labels.
- **Model**: artificial neural network for multi-target regression on per-pixel fractions, with optimised multi-target loss (Pham et al. 2024).
- **Ensemble**: multiple ANN realisations from different synthetic libraries → mean prediction + uncertainty.
- 9 tree species + 1 "other species" class: Beech, Sessile/Pedunculate Oak, Spruce, Scots Pine, Douglas Fir, Silver Fir, European Larch, Sycamore Maple, Black Alder, Birch.

## Distinctive Features
- **Synthetic linear-mixing data augmentation**: extends Okujeni et al. (2013) regression-based unmixing to gap-filled multi-temporal S2.
- **Pure pixel sample size as low as 30 per class** — operationally feasible for rare species.
- **Regression instead of classification** of mixtures — outputs continuous proportions rather than discrete labels.
- **Ensemble** for both stability and uncertainty quantification.
- Allows rare species inclusion without the usual class-imbalance / under-representation penalty.

## Experimental Setup and Results

**Per-species MAE (against forest planning data)**
- Most dominant species (Beech, Oak, Spruce, Pine): MAE 2.76–6%
- Less common species (Douglas Fir, Larch, Sycamore Maple): 5–11%
- Rare species (Silver Fir, Birch, Alder): up to 16.05%
- R² up to 0.92 overall

**Sample-size sensitivity**
- 30 pure pixels per class sufficient to distinguish 9 species + "other"
- More samples improve marginal accuracy but saturate quickly

**Ecoregion stratification**
- Performance varies across the 14 ecoregions
- Most accurate in regions with clearer phenological contrast

## Advantages and Limitations
- **Advantages**: Solves dual mixed-stand + rare-species problem with a single mechanism; very low pure-sample requirements; explicit uncertainty via ensembles; regression framework yields information-rich fractional maps.
- **Limitations**: Linear-mixing assumption simplifies real canopy mixing; "other species" class is heterogeneous; performance for Birch/Alder still has wider MAE; reliant on forest planning data quality for validation; gap-filling errors propagate.

## Conclusion
**Synthetic linear-mixing data augmentation + ensemble ANN regression unlocks tree species fraction mapping in mixed forests with very limited reference data.** Allows inclusion of rare species without distorting classifier training and produces fractional maps rather than dominant-class labels — much more useful for forest management and ecological reporting. Methodologically the most data-efficient precedent for Italian INFC-based species fraction mapping in the wiki context.

## Related pages
- [[tree_species_mapping]]
- [[transfer_learning_remote_sensing]]
- [[sentinel_2]]
- [[national_forest_inventory]]
- [[blickensdörfer_2024_tree_species]]
- [[hemmerling_2021_forest_mapping_s2]]
- [[bolyn_2022_tree_species_mapping]]
- [[hiebl_2025_pretraining]]
- [[hiebl_2026_alphaearth]]
- [[yang_2020_modis_evergreen]]
- [[deep_ensemble_uncertainty]]
- [[safonova_2023_small_data]]
- [[yuan_2025_sits_augmentation]]
