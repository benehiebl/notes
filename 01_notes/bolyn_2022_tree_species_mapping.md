---
title: "Mapping tree species proportions from satellite imagery using spectral–spatial deep learning"
authors:
  - Bolyn, Corentin
  - Lejeune, Philippe
  - Michez, Adrien
  - Latte, Nicolas
year: 2022
source: bolyn_2022_tree_species_mapping
tags:
  - deep-learning
  - remote-sensing
  - forest-ecology
  - sentinel-2
status: read
---

# Bolyn et al. 2022 — Spectral-Spatial Deep Learning for Tree Species Proportion Mapping

## Title and Authors
**Mapping tree species proportions from satellite imagery using spectral–spatial deep learning**
Corentin Bolyn, Philippe Lejeune, Adrien Michez, Nicolas Latte — *Remote Sensing of Environment*, 2022

## Quick Overview
- **Why is it relevant?** Addresses the mixed-pixel problem in satellite-based tree species mapping by directly predicting species proportions (not discrete classes), enabling mapping of mixed forest stands at landscape scale.
- **What was done?** A nested UNet++ CNN was trained on forest parcel polygon data to predict per-pixel basal area proportions of 9 tree species/genera in Wallonia (Belgium) from Sentinel-2 imagery at 2.5 m resolution.
- **What is the main outcome?** OA_maj = 0.73 for majority species; the model can detect species composition (presence/absence) with MS indicator of 0.89, and estimate proportions with R²_adj = 0.50.

## Main Goal and Fundamental Concept
Most tree species mapping methods treat each pixel as belonging to a single species, failing in mixed forest stands where pixels contain multiple species. This study proposes a soft classification approach where the output is a vector of species proportions (summing to 1) rather than a hard label, fundamentally changing the mapping problem from classification to regression.

## Technical Approach
- **Architecture:** UNet++ (nested U-shaped CNN) applied to Sentinel-2 imagery super-resolved to 2.5 m
- **Input features:** 10 Sentinel-2 bands (4 at 10 m, 6 at 20 m) + time-weighted summer mosaic (13 dates, May–Aug 2018)
- **Target:** Per-pixel basal area proportion vector for 9 species: Spruce, Oak, Beech, Douglas fir, Pine, Poplar, Larch, Birch, other
- **Training data:** Forest parcel polygons from Wallonia forest administration geodatabase (includes mixed stands)
- **Validation:** Regional forest inventory plots (independent assessment)
- **Accuracy metrics:** OA_maj (majority species), MS (species composition), MPS (partial species), MUS (understory species), R²_adj (proportions)

## Distinctive Features
- First study to use CNN for direct quantification of per-pixel tree species proportions (soft classification)
- Explicitly includes mixed stands in training, using all pixels from pure to highly mixed
- Robust independent evaluation using regional forest inventory (not same data as training)
- Super-resolution applied to match 2.5 m forest parcel mask geometry

## Experimental Setup and Results
- **Study area:** Wallonia region, southern Belgium; 16,901 km², 33% forested, diverse species composition
- **OA_maj = 0.73** (majority species correctly identified)
- **MS = 0.89** (species composition correctly detected in most cases)
- **MPS = 0.72, MUS = 0.83** (partial and understory species detection)
- **Best species:** Spruce, Oak, Beech, Douglas fir (PA and UA > 0.70)
- **R²_adj = 0.50** for predicted proportions — moderate but useful for landscape-level analysis

## Advantages and Limitations
- **Advantages:** Handles mixed stands; uses freely available Sentinel-2; transferable to other regions with similar forest inventories; spatially explicit proportion maps
- **Limitations:** R² = 0.50 indicates substantial proportion estimation error; dependent on quality of training polygon database; 2018 single-year imagery limits temporal robustness

## Conclusion
Spectral-spatial deep learning (UNet++) can map tree species proportions across a heterogeneous mixed-forest landscape using Sentinel-2, overcoming the binary classification limitation of previous approaches. The method is particularly suited to regions with georeferenced forest parcel databases and achieves promising accuracy for majority species. Moderate proportion-level accuracy suggests refinement is needed for precise quantitative estimates.

## Related pages
- [[sentinel_2]]
- [[tree_species_mapping]]
- [[transfer_learning_remote_sensing]]
- [[neural_network_training]]
