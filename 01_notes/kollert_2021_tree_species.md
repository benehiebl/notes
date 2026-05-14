---
title: "Exploring the potential of land surface phenology and seasonal cloud free composites of one year of Sentinel-2 imagery for tree species mapping in a mountainous region"
authors:
  - Kollert, Andreas
  - Bremer, Magnus
  - Löw, Markus
  - Rutzinger, Martin
year: 2021
source: kollert_2021_tree_species
tags:
  - remote-sensing
  - machine-learning
keywords:
  - Sentinel-2
  - land surface phenology
  - tree species mapping
  - mountainous terrain
  - random forest
  - Tyrol
  - composite imagery
status: read
---

# Kollert et al. 2021 — Sentinel-2 LSP and Seasonal Composites for Tree Species Mapping in Tyrol

## Title and Authors
**Exploring the potential of land surface phenology and seasonal cloud free composites of one year of Sentinel-2 imagery for tree species mapping in a mountainous region**
Andreas Kollert, Magnus Bremer, Markus Löw, Martin Rutzinger — *Int J Appl Earth Obs Geoinformation* 94: 102208 (2021).

## Quick Overview
- **Why is it relevant?** Tests whether seasonal composites and land surface phenology metrics from a single year of S2 can substitute for cloud-free single-date imagery in mountainous terrain — directly relevant for Alpine forest mapping where cloud-free coverage is scarce.
- **What was done?** RF classification of 5 tree species classes in Tyrol (Austria, ~5,000 km² forest) across two S2 tiles; compared regular multitemporal (3 cloud-free scenes) vs three-monthly composites + LSP metrics.
- **What is the main outcome?** Three-monthly composites + LSP improve OA by 1–2 pp over the cloud-free reference (84.4% → 85–86%); multitemporal beats monotemporal by ~10 pp; composites + LSP recommended for large mountain regions.

## Main Goal and Fundamental Concept
For tree species mapping in mountainous terrain, single cloud-free dates are rarely available across an entire study area covering multiple S2 orbits. Phenological differences are key for distinguishing conifers, broadleaves, and larch. Kollert et al. test whether temporally aggregated features (median composites + LSP metrics) can produce equal or better accuracy than the classical "pick a few cloud-free dates" approach.

## Technical Approach
- Study area: most of Tyrol (Austria), ~5,000 km² forest, two S2 tiles (32TPT, 32TQT), three orbits, elevation 450–3,800 m.
- 5 classes: Broadleaved, Larch (*Larix decidua*), Pine (*Pinus sylvestris*), Spruce/Fir (*Picea abies* / *Abies alba* merged), Dwarf Pine (*Pinus mugo*).
- Reference: 340 patches digitised from airborne LiDAR DSM/DTM + manual interpretation; ~47,000 S2 pixels (≈0.088% of forest).
- S2 preprocessing: Sen2Cor v2.05.05, 10 m DEM topographic correction, 20-m bands resampled to 10 m.
- Features tested:
  1. Mono-temporal (single cloud-free scene)
  2. Multi-temporal (3 cloud-free + 1 synthetic July median)
  3. Monthly + three-monthly median composites per band
  4. NDVI smoothed (Chen 2004) → LSP: SOS/EOS at 10/20/50% of annual amplitude + integral NDVI
- Classifier: Random Forest, patch-stratified k-fold CV (avoids using pixels from same patch in train/test).

## Distinctive Features
- Explicit comparison of LSP/composite features against the conventional cloud-free-date approach.
- Patch-stratified CV avoids spatial autocorrelation between training and test pixels (cf. [[spatial_proxies_random_forest]], [[transfer_learning_remote_sensing]]).
- Mountain context: handles topography + multi-orbit coverage rigorously.
- Quantifies the gain from temporal aggregation when single cloud-free scenes are scarce.

## Experimental Setup and Results

**Overall Accuracy by feature set**
- Monotemporal (single scene): ~74%
- Multitemporal (3 cloud-free + synthetic median): **84.4%**
- Three-monthly composites: ~85%
- Three-monthly composites + LSP metrics: ~86% (best)
- Monthly composites: noisier, marginally worse than three-monthly

**Feature importance (RF)**
- NDVI integral and SOS/EOS metrics rank high
- Red-edge bands consistently informative
- Spring + autumn composites distinguish larch (deciduous conifer) most strongly

**Species-level patterns**
- Larch easily separated (distinct deciduous-conifer phenology)
- Broadleaved well separated from conifers
- Spruce vs Fir merged due to indistinguishability + lack of pure Fir reference
- Dwarf pine: small sample → high variance

## Advantages and Limitations
- **Advantages**: Resource-efficient (one year of S2 only); shows that composites + LSP rival multi-date classical workflow; patch-stratified CV honest about accuracy.
- **Limitations**: Reference includes only pure stands (mixed forests untested — cf. [[blickensdörfer_2024_tree_species]] critique); five-class taxonomy is coarse; small dwarf-pine sample; single-year analysis cannot capture inter-annual variability.

## Conclusion
**Three-monthly seasonal composites + LSP metrics from a single year of S2 outperform classical multitemporal classification in mountainous terrain** where cloud-free imagery is scarce. The approach is recommended for large-scale operational mapping in Alpine regions, with the caveat that mixed-stand performance was not assessed. Strong precedent for the methodological choices in [[hiebl_2025_pretraining]] / Italian forest mapping.

## Related pages
- [[tree_species_mapping]]
- [[sentinel_2]]
- [[phenology]]
- [[hemmerling_2021_forest_mapping_s2]]
- [[grabska_2024_tree_species_map]]
- [[blickensdörfer_2024_tree_species]]
- [[pflugmacher_2019_lulc_landsat]]
- [[hiebl_2025_pretraining]]
