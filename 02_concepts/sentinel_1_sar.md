---
name: sentinel_1_sar
description: Sentinel-1 SAR sensor — C-band, dual polarisation, 6–12 day revisit, all-weather imaging; complementary to optical Sentinel-2 for forest, agriculture, and disturbance mapping
type: reference
tags:
  - remote-sensing
---

# Sentinel-1 SAR

**Summary**: Sentinel-1 is a twin-satellite ESA C-band synthetic-aperture radar (SAR) mission providing dual-polarisation (VV/VH) imagery at 5×20 m resolution with 6–12 day revisit. Because SAR is cloud- and illumination-independent, S-1 fills the gaps left by Sentinel-2 and complements optical data with sensitivity to vegetation structure, biomass, and surface moisture — particularly valuable in cloudy regions and for monthly-cadence change detection.

**Sources**: [[deluca_2022_s1_s2_lulc_mapping]], [[blickensdörfer_2024_tree_species]], [[zhao_2022_forest_harvesting]], [[qin_2026_forest_cover]], [[lang_2024_canopy_height]], [[tseng_2024_presto]], [[wang_2026_foundation]], [[hiebl_2026_alphaearth]], [[brown_2025_alphaearth]]

**Last updated**: 2026-05-14

---

## Sensor Properties

- **Sentinel-1A** launched April 2014; **Sentinel-1B** launched April 2016 (lost 2022); **Sentinel-1C** launched 2024.
- **C-band** (5.405 GHz) radar — penetrates light vegetation, sensitive to canopy structure.
- **Polarisations**: VV (co-polarised) and VH (cross-polarised) in IW mode.
- **Spatial resolution**: 5 × 20 m (single look), resampled to 10 m for standard products.
- **Revisit time**: 6 days at the equator (when both satellites operational); 12 days with one satellite.
- **Cloud + illumination independent**: provides observations in winter and during persistent cloud cover.

## Why SAR Complements Optical

Optical sensors (S-2, Landsat) measure surface **reflectance** — biochemistry, chlorophyll, water content. SAR measures **backscatter** — structure, geometry, dielectric properties.

| Property | Optical S-2 | SAR S-1 |
|---|---|---|
| Cloud-affected | Yes | No |
| Illumination-dependent | Yes (day only) | No |
| Sensitivity | Chlorophyll, biochemistry | Structure, biomass, moisture |
| Resolution | 10–60 m | 5×20 m (resampled to 10 m) |
| Revisit | 5 days | 6 days |
| Speckle noise | Low | Significant |

The two are routinely combined for land-cover and forest mapping (source: [[deluca_2022_s1_s2_lulc_mapping]], [[blickensdörfer_2024_tree_species]], [[hiebl_2026_alphaearth]]).

## Common Derived Variables

- **VV**, **VH**: raw backscatter coefficients (gamma-naught)
- **Cross-Ratio (CR) = VH/VV**: sensitive to biomass, vegetation water content, phenology
- **Radar Vegetation Index (RVI) = 4·VH / (VH+VV)**: vegetation cover and biomass
- **Polarimetric decompositions** (where dual-pol allows): scattering type information
- **Multi-temporal speckle filtering**: reduces speckle while preserving boundaries

## Use in Forest and Disturbance Mapping

**Tree species mapping**: S-1 winter composites add structural information complementary to S-2 phenology; particularly useful in cloudy regions. Including S-1 with S-2 raises F1 by a few percentage points for dominant species (source: [[blickensdörfer_2024_tree_species]]).

**Forest harvesting / change detection**: S-1 monthly composites with U-Net deep learning achieve mean F1 0.74–0.78 for monthly harvest mapping in California and Rondônia — exploiting the **landscape pattern** of harvested patches that SAR captures despite speckle noise. Cloud-independent, transferable with sparse local fine-tuning (source: [[zhao_2022_forest_harvesting]]).

**Cloud-prone forest cover**: combined with DL multi-sensor fusion + S-2 + MODIS, enables annual 30 m forest cover mapping across 2.04 million km² of southern China where < 3 cloud-free observations are available per year (source: [[qin_2026_forest_cover]]).

**Canopy height**: S-1 added to S-2 + AlphaEarth + GEDI improves CHM estimation accuracy (source: [[lang_2024_canopy_height]], [[wang_2026_foundation]]).

## Use in Foundation Models

S-1 is a standard ingredient in geospatial foundation models:
- **AlphaEarth Foundations** ingests S-1 alongside S-2, ALOS PALSAR-2, DEM, GEDI, ERA5, etc. as one of 10 data sources (source: [[brown_2025_alphaearth]])
- **PRESTO** uses S-1 VV/VH as one of 7 dynamic-in-time data products in its lightweight pixel-time-series transformer (source: [[tseng_2024_presto]])
- **Hiebl et al. 2026** evaluates S-1 inputs to TST for forest type and EVE cover mapping (source: [[hiebl_2026_alphaearth]])

## Limitations

- **Speckle noise** is a fundamental SAR artefact; reduced by multi-temporal filtering or DL methods that learn landscape patterns
- **Topographic distortion** (foreshortening, layover, shadow) in steep terrain
- **Penetration depth** in C-band limited compared to L-band (ALOS) or P-band (BIOMASS)
- **Interpretation complexity**: backscatter depends on a combination of moisture, geometry, and biomass — disentangling is non-trivial
- **Sentinel-1B failure (2022)** temporarily halved revisit; addressed by S-1C launch in 2024

## Related concepts
- [[sentinel_2]]
- [[landsat]]
- [[cloud_detection]]
- [[tree_species_mapping]]
- [[forest_disturbances]]
- [[geospatial_foundation_models]]
