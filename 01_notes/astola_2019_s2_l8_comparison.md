---
title: "Comparison of Sentinel-2 and Landsat 8 imagery for forest variable prediction in boreal region"
authors:
  - Astola, Heikki
  - Häme, Tuomas
  - Sirro, Laura
  - Molinier, Matthieu
  - Kilpi, Jorma
year: 2019
source: astola_2019_s2_l8_comparison
tags:
  - remote-sensing
  - machine-learning
  - forest-ecology
status: read
---

# Astola et al. 2019 — Sentinel-2 vs Landsat 8 for Forest Variable Prediction in Boreal Forests

## Title and Authors
**Comparison of Sentinel-2 and Landsat 8 imagery for forest variable prediction in boreal region**
Heikki Astola, Tuomas Häme, Laura Sirro, Matthieu Molinier, Jorma Kilpi — *Remote Sensing of Environment*, 2019

## Quick Overview
- **Why is it relevant?** Provides a rigorous quantitative benchmark comparing the two dominant free multispectral satellite sensors for operational forest inventory applications, essential for choosing sensor for forest variable mapping workflows.
- **What was done?** Compared Sentinel-2 and Landsat 8 for predicting stem volume, diameter, height, and basal area in boreal Finland using 739 field plots, MLP and regression trees, 100-iteration validation.
- **What is the main outcome?** Sentinel-2 consistently outperforms Landsat 8 across all forest variables and spatial resolutions, with best predictor being the red-edge band (B05_RE1).

## Main Goal and Fundamental Concept
The study quantifies whether Sentinel-2's improved spatial resolution (10 m vs. 30 m) and additional spectral bands (especially red-edge) provide measurable gains for forest inventory variable prediction over Landsat 8, with implications for operational forest monitoring services.

## Technical Approach
- **Sensors:** Sentinel-2 MSI (10–20 m, 13 bands) and Landsat 8 OLI (30 m, 11 bands)
- **Models:** Multi-layer perceptron (MLP) and regression tree with brute-force forward band selection
- **Cross-validation:** 12 modelling setups, 100 iterations with equal-size train/validation/test splits
- **Reference data:** 739 circular field plots from the Finnish Forest Centre
- **Target variables:** Stem volume (V), stem diameter (D), tree height (H), basal area (G) + species-wise components (pine, spruce, broadleaf)

## Distinctive Features
- Tests Sentinel-2 at 10 m native and downsampled to 30 m to isolate spectral vs. spatial resolution effects
- Identifies best individual predictive bands, finding red-edge consistently most important for forest variables
- Concurrent acquisition of Sentinel-2 and Landsat 8 data for unbiased comparison

## Experimental Setup and Results
- **Sentinel-2 RMSE%:** Diameter 38.4%, Basal area 42.5%, Height 30.4%, Stem volume 59.3%
- **Landsat 8 RMSE%:** Diameter 44.6%, Basal area 50.2%, Height 36.6%, Stem volume 72.2%
- **Best Sentinel-2 bands:** Red-edge 1 (B05), SWIR1 (B11), SWIR2 (B12), Green (B03)
- **Sentinel-2 advantage persists** even when downsampled to 30 m — spectral resolution matters beyond spatial
- Bias differences between sensors were not statistically significant

## Advantages and Limitations
- **Advantages:** Rigorous 100-iteration validation; direct comparison under identical conditions; forest variable range is operationally relevant
- **Limitations:** Boreal Finland-specific; stem volume prediction remains high RMSE (~60%) suggesting limits of optical data alone; LiDAR not included as baseline

## Conclusion
Sentinel-2 is recommended as the principal Earth observation source for operational forest resource assessment, outperforming Landsat 8 in all tested variables. The red-edge band is the single most predictive feature. The advantage is partly attributable to spectral richness (red-edge, additional SWIR) beyond pure spatial resolution improvement.

## Related pages
- [[sentinel_2]]
- [[landsat]]
- [[national_forest_inventory]]
- [[tree_species_mapping]]
