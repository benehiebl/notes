---
name: sentinel_2
description: Sentinel-2 satellite program — bands, temporal resolution, use in vegetation and tree species mapping, comparison with Landsat
type: reference
tags:
  - remote-sensing
  - sentinel-2
  - machine-learning
---

# Sentinel-2

**Summary**: Sentinel-2 is a twin-satellite ESA mission providing multispectral imagery at 10–20 m resolution with ~5-day revisit time, enabling high-resolution vegetation monitoring at spatial and temporal scales not achievable with Landsat alone.

**Sources**: [[grabska_2024_tree_species_map]], [[chabalala_2023_dl_s2_mediterranean_fruit_trees]], [[deluca_2022_s1_s2_lulc_mapping]], [[koch_2025_intraspecies_variation_s2]], [[liu_2023_spectral_spatial_resolution_effect]], [[miettinen_2025_forest_maps_europe]], [[fischer_2025_glocal_canopy_atlas]]

**Last updated**: 2026-05-05

---

## Satellites and Revisit

- **Sentinel-2A**: launched June 2015
- **Sentinel-2B**: launched March 2017
- Combined revisit time (A+B): ~5 days at the equator; higher frequency at higher latitudes
- 16-day repeat per satellite — much shorter gaps than Landsat (16 days per satellite)

## Spectral Bands

| Band | Name | Wavelength (nm) | Resolution |
|------|------|----------------|-----------|
| B2 | Blue | 490 | 10 m |
| B3 | Green | 560 | 10 m |
| B4 | Red | 665 | 10 m |
| B5 | Red Edge 1 (RE1) | 705 | 20 m |
| B6 | Red Edge 2 (RE2) | 740 | 20 m |
| B7 | Red Edge 3 (RE3) | 783 | 20 m |
| B8 | NIR1 (broad) | 842 | 10 m |
| B8A | NIR2 (narrow) | 865 | 20 m |
| B11 | SWIR1 | 1610 | 20 m |
| B12 | SWIR2 | 2190 | 20 m |

The **red-edge bands (RE1–RE3)** are Sentinel-2's key advantage over Landsat for vegetation applications — they are highly sensitive to chlorophyll content, leaf structure, and canopy stress, enabling finer discrimination of vegetation types and species.

## Data Levels in GEE

- **L1C** (top-of-atmosphere): `COPERNICUS/S2`
- **L2A** (surface reflectance, atmospherically corrected): `COPERNICUS/S2_SR` or `COPERNICUS/S2_SR_HARMONIZED`
- Harmonized collection normalises inter-sensor differences between S2A and S2B

## Spectral-Temporal Metrics (STMs)

A key strategy for managing cloud cover and capturing phenological signals in Sentinel-2 time series:
- Compute summary statistics (mean, median, percentiles) over a short seasonal window (15–30 days) using multi-annual observations
- STMs from multiple seasons (early spring, late spring, summer, autumn) capture species-specific phenological dynamics
- Multi-annual aggregation reduces inter-annual variability and cloud contamination
- Used in national-scale tree species mapping in Poland (source: [[grabska_2024_tree_species_map]]) and other large-area vegetation studies

## Use in Tree Species Mapping

Sentinel-2 is the primary sensor for fine-resolution tree species mapping:
- 10 m resolution resolves individual forest stands
- Red-edge bands distinguish between broadleaved and coniferous species and within those groups
- Multi-temporal approach (seasonal STMs or dense time series) captures phenological differences among species
- Key discriminating periods: autumn (leaf senescence) and early spring (green-up) — both show strong inter-species variation (source: [[grabska_2024_tree_species_map]])

## Sentinel-2 for Forest Structure Mapping (AGB, Volume, Composition)

Pan-European application combining Sentinel-2 with NFI data (Miettinen et al. 2025):
- 7 S2 bands (B2, B3, B4, B5, B8, B11, B12) as primary spectral features in kNN feature space alongside Copernicus FTY and TCD layers
- 10m resolution AGB, timber volume, and deciduous-coniferous proportion maps for 40 European countries (reference year 2020)
- RMSE 53–73% relative for AGB; nearly unbiased at continental scale; systematic regression-to-mean at pixel level
- S2 spectral bands capture canopy structure and composition signals that correlate with biomass density — combined with NFI plot calibration (source: [[miettinen_2025_forest_maps_europe]])

## Sentinel-2 for Tree Species Diversity Mapping

Direct sensor comparison in the Black Forest, Germany (130 one-ha plots, October senescence imagery):
- **Sentinel-2 at 10m** outperforms all other sensors for Shannon-Wiener TSD prediction: R²=0.477, RMSE=0.274 (source: [[liu_2023_spectral_spatial_resolution_effect]])
- RapidEye (10m): R²=0.346; PlanetScope (15m): R²=0.337; Landsat-8 (30m): R²=0.316
- **10m is the optimal spatial resolution**: sub-10m resolution introduces intra-crown spectral noise (sunlit vs shaded foliage, understory) that inflates spectral heterogeneity without reflecting inter-species diversity; 10–15m matches stand-level spectral variation
- Sentinel-2's advantage comes from both its three red-edge bands AND its broader NIR / narrower visible bands — even the 4-band Sentinel-2 subset outperforms PlanetScope and Landsat-8 4-band datasets at most resolutions
- Most important bands for TSD: NIR >> Red-edge > SWIR > Red, Green, Blue
- Best spectral heterogeneity metrics: Rao's Q and texture (GLCM) — see [[spectral_diversity_biodiversity]]

## Comparison with Landsat

| Feature | Sentinel-2 | Landsat 8/9 |
|---------|-----------|-----------|
| Resolution | 10–20 m | 30 m |
| Revisit | ~5 days (A+B) | 8 days (8+9), 16 days single |
| Red-edge bands | Yes (3 bands) | No |
| SWIR bands | Yes (2 bands) | Yes (2 bands) |
| Archive depth | 2015– | 1972– |
| Cloud sensitivity | Same | Same |

## Sentinel-2-Derived Canopy Height and Structure

Satellite canopy height models derived from Sentinel-2 (combined with GEDI or alone) show significant limitations at native resolution when validated against airborne laser scanning (ALS) reference data (source: [[fischer_2025_glocal_canopy_atlas]]):
- Lang et al. 2023 (Sentinel-2 + GEDI, 10m): R² = 0.28–0.38 vs ALS at native resolution; predicts maximum height better than mean height; relative RMSE 95–189%
- At 250m aggregation, performance improves substantially (R² = 0.56, RMSE = 170%) — coarser resolution averages out sub-pixel variability
- ALS remains the gold standard for canopy height and structure mapping; satellite CHMs are most useful for large-area relative patterns, not absolute height values (source: [[fischer_2025_glocal_canopy_atlas]])
- These limitations are directly relevant when using Sentinel-2-derived structural features as auxiliary predictors in NFI-based forest attribute mapping

## Observation Density Effects

Like Landsat, the number of cloud-free Sentinel-2 observations varies spatially:
- Non-overlapping orbit areas have fewer observations per season than overlapping areas
- In Poland, overlapping orbit areas achieved 90.1% classification OA vs 86.7% for non-overlapping areas (source: [[grabska_2024_tree_species_map]])
- Parallels the [[sampling_bias_remote_sensing]] issue identified for Landsat in alpine environments

## Related pages

- [[landsat]]
- [[ndvi]]
- [[phenology]]
- [[tree_species_mapping]]
- [[sampling_bias_remote_sensing]]
- [[spectral_diversity_biodiversity]]
