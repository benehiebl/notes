---
title: "A high-resolution canopy height model of the Earth"
authors:
  - Lang, Nico
  - Jetz, Walter
  - Schindler, Konrad
  - Wegner, Jan Dirk
year: 2024
source: lang_2024_canopy_height
tags:
  - deep-learning
  - remote-sensing
  - forest-ecology
keywords:
  - canopy height
  - GEDI
  - Sentinel-2
  - CNN ensemble
  - probabilistic deep learning
  - global mapping
  - biomass
  - height saturation
status: read
---

# Lang et al. 2024 — A High-Resolution Canopy Height Model of the Earth

## Title and Authors
**A high-resolution canopy height model of the Earth**
Nico Lang, Walter Jetz, Konrad Schindler, Jan Dirk Wegner — *Nature Ecology & Evolution* 7: 1778–1789 (2023; published in this issue 2024).

## Quick Overview
- **Why is it relevant?** First global 10 m canopy height model fusing GEDI LiDAR with Sentinel-2 imagery via a deep ensemble — a benchmark for any canopy structure / biomass mapping work and a methodological reference for sparse-label deep learning.
- **What was done?** Trained a probabilistic CNN ensemble on 600 million GEDI–S2 patch pairs to retrieve canopy-top height anywhere on Earth at 10 m GSD for 2020, with per-pixel uncertainty.
- **What is the main outcome?** Global 10 m CHM with aRMSE=7.3 m and aME=−1.8 m balanced across 5 m height bins; only 5% of land has trees taller than 30 m; only 34% of those tall canopies are in protected areas.

## Main Goal and Fundamental Concept
The Global Ecosystem Dynamics Investigation (GEDI) LiDAR mission provides accurate canopy structure but covers only ~4% of the land surface, mostly between 51.6° N/S. Sentinel-2 provides global wall-to-wall optical coverage. Lang et al. fuse the two via deep learning to extrapolate sparse GEDI to a dense global CHM, with explicit uncertainty.

## Technical Approach
- **Reference**: 600 million GEDI footprints (RH98 — relative height containing 98% of returned energy), April–August 2019 + 2020; rasterised to S2 10 m grid as sparse supervision.
- **Predictor**: S2 image patches 15×15 px centred on each GEDI footprint; cyclic geographic-coordinate encoding as additional channels.
- **Model**: CNN ensemble (multiple independently trained CNNs).
- **Key techniques** to mitigate underestimation of tall canopies:
  1. Geographic priors via cyclic lat/lon encoding
  2. Inverse-frequency-weighted loss per 1 m height bin (counters long-tailed reference distribution)
  3. Ensemble + multi-date S2 aggregation
- **Split**: 80/20 by 100 km × 100 km S2 tile (spatial split → avoids spatial autocorrelation between train/test, cf. [[spatial_proxies_random_forest]]).
- **Uncertainty**: variance across ensemble + learned per-pixel variance.

## Distinctive Features
- **Sparse supervision** at scale: ~600 million labelled GEDI pixels, but loss computed only at footprint centres — enables wall-to-wall prediction without dense labels.
- **Spatial-feature exploitation**: 15 × 15 px input patches let the CNN use texture and context (vs pixel-wise mapping), which is critical for tall-canopy retrieval.
- **Long-tail-aware training**: inverse-frequency weighting + ensemble averaging targeted at the saturation problem of tall canopies.
- **Geographic priors**: cyclic lat/lon encoding lets the model learn region-specific biases.
- **Production scale**: global 10 m CHM publicly released; interactive viewer.

## Experimental Setup and Results

**Global accuracy (validation)**
- aRMSE (balanced across 5 m bins): 7.3 m
- aME (balanced bias): −1.8 m
- Overall RMSE: 6.0 m, ME: +1.3 m (slight low-canopy overestimation as price for tall-canopy improvement)

**Biome-level patterns**
- Deserts: zero canopy correctly identified
- Montane/temperate/tropical grasslands + Mediterranean + tropical dry broadleaf: low bias
- Mangroves, tundra, tropical coniferous: ~+2.5 m overestimation
- Tropical and temperate coniferous: highest residual spread
- Tundra under-represented (GEDI coverage stops at 51.6° N)

**Global statistics**
- Only ~5% of land has trees taller than 30 m
- Only 34% of those tall canopies fall within protected areas — conservation gap

## Advantages and Limitations
- **Advantages**: Global coverage; explicit uncertainty; tackles tall-canopy saturation via three complementary measures; spatial-context-aware via CNN; public release.
- **Limitations**: Reference (GEDI RH98) noisy — slope, beam geometry effects; tundra/high-latitude regions extrapolated beyond GEDI coverage; 2020 single year; canopy height ≠ biomass directly; persistent biome-specific biases (mangrove, tundra, tropical conifer).

## Conclusion
**Sparse-supervision deep learning fuses LiDAR + optical to produce the first 10 m global canopy height map with per-pixel uncertainty.** The combination of geographic priors, height-balanced loss, ensemble averaging, and CNN spatial features attacks the long-standing tall-canopy saturation problem. The product is a benchmark reference for any canopy structure / biomass mapping and directly relevant to forest type mapping in the wiki (structure complements species).

## Related pages
- [[transfer_learning_remote_sensing]]
- [[sentinel_2]]
- [[sentinel_1_sar]]
- [[tree_species_mapping]]
- [[brown_2025_alphaearth]]
- [[miettinen_2025_forest_maps_europe]]
- [[fischer_2025_glocal_canopy_atlas]]
- [[bell_2024_hindcasting_forest_structure]]
- [[turubanove_2023_canopy_landsat]]
- [[lakshminarayan_2017_uncertainty]]
- [[deep_ensemble_uncertainty]]
- [[wang_2026_foundation]]
- [[geospatial_foundation_models]]
- [[spatial_proxies_random_forest]]
