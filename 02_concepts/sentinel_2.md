---
name: sentinel_2
description: Sentinel-2 satellite program — bands, temporal resolution, use in vegetation and tree species mapping, comparison with Landsat
type: reference
---

# Sentinel-2

**Summary**: Sentinel-2 is a twin-satellite ESA mission providing multispectral imagery at 10–20 m resolution with ~5-day revisit time, enabling high-resolution vegetation monitoring at spatial and temporal scales not achievable with Landsat alone.

**Sources**: grabska_2024_tree_species_map.pdf, chabalala_2023_dl_s2_mediterranean_fruit_trees.pdf, deluca_2022_s1_s2_lulc_mapping.pdf, koch_2025_intraspecies_variation_s2.pdf

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
- Used in national-scale tree species mapping in Poland (source: grabska_2024_tree_species_map.pdf) and other large-area vegetation studies

## Use in Tree Species Mapping

Sentinel-2 is the primary sensor for fine-resolution tree species mapping:
- 10 m resolution resolves individual forest stands
- Red-edge bands distinguish between broadleaved and coniferous species and within those groups
- Multi-temporal approach (seasonal STMs or dense time series) captures phenological differences among species
- Key discriminating periods: autumn (leaf senescence) and early spring (green-up) — both show strong inter-species variation (source: grabska_2024_tree_species_map.pdf)

## Comparison with Landsat

| Feature | Sentinel-2 | Landsat 8/9 |
|---------|-----------|-----------|
| Resolution | 10–20 m | 30 m |
| Revisit | ~5 days (A+B) | 8 days (8+9), 16 days single |
| Red-edge bands | Yes (3 bands) | No |
| SWIR bands | Yes (2 bands) | Yes (2 bands) |
| Archive depth | 2015– | 1972– |
| Cloud sensitivity | Same | Same |

## Observation Density Effects

Like Landsat, the number of cloud-free Sentinel-2 observations varies spatially:
- Non-overlapping orbit areas have fewer observations per season than overlapping areas
- In Poland, overlapping orbit areas achieved 90.1% classification OA vs 86.7% for non-overlapping areas (source: grabska_2024_tree_species_map.pdf)
- Parallels the [[sampling_bias_remote_sensing]] issue identified for Landsat in alpine environments

## Related pages

- [[landsat]]
- [[ndvi]]
- [[phenology]]
- [[tree_species_mapping]]
- [[sampling_bias_remote_sensing]]
