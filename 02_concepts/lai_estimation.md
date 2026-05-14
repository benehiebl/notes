---
name: lai_estimation
description: Leaf Area Index (LAI) — definition, satellite-based estimation methods, data fusion from MODIS to Landsat/Sentinel-2, biome-specific retrieval and saturation challenges
type: reference
tags:
  - remote-sensing
  - vegetation-biophysics
---

# Leaf Area Index Estimation from Satellite Data

**Summary**: Leaf Area Index (LAI) is a key vegetation structural variable quantifying canopy density; it is estimated from satellite reflectance via empirical, radiative transfer, or data-fusion methods, with a fundamental trade-off between spatial resolution and global coverage.

**Sources**: [[kang_2021_lai_landsat]], [[yel_2026_deciduous_forests]]

**Last updated**: 2026-05-14

---

## Definition and Ecological Importance

- LAI = one-sided leaf area per unit ground area (m²/m²); fundamental driver of photosynthesis, transpiration, and energy balance
- Controls water and carbon fluxes, net primary productivity, and energy exchanges in global ecosystems
- Essential input to land surface models, evapotranspiration estimation (e.g., ALEXI/DisALEXI), and phenology monitoring

## Estimation Approaches

### Empirical (vegetation index regression)
- Direct regression between satellite-derived VIs (NDVI, EVI, NIRv) and in-situ LAI measurements
- Accurate locally but does not generalise across biomes without recalibration
- Confounded by soil background, canopy structure, sun-sensor geometry

### Radiative transfer model (RT) inversion
- PROSAIL-based look-up tables (e.g., MODIS LAI algorithm, Sentinel-2 L2 LAI product)
- Physically consistent but ill-posed inversion — regularisation requires site-specific priors
- MODIS LAI flags retrievals as "saturated" for dense canopies (LAI > 4) where reflectance becomes insensitive to LAI

### Data fusion (MODIS → Landsat/Sentinel-2)
- Leverages spatially homogeneous MODIS pixels to train biome-specific Random Forest models predicting LAI from Landsat reflectance (source: [[kang_2021_lai_landsat]])
- Requires: homogeneity sampling (Landsat pixel variance < threshold within MODIS pixel); balanced sampling of saturated and unsaturated MODIS LAI
- Produces 30 m LAI consistent with MODIS scale for multi-scale modelling applications
- Implemented on Google Earth Engine → enables wall-to-wall LAI from 1980s Landsat archive (source: [[kang_2021_lai_landsat]])

## Saturation Problem

- MODIS LAI algorithm flags retrievals in "saturation domain" where reflectance cannot discriminate LAI > 4
- Excluding saturated samples from training → systematic underestimation in dense canopies
- Fix: balanced sampling design ensuring equal representation of saturated and unsaturated LAI values (source: [[kang_2021_lai_landsat]])

## Validation Results (30 m Landsat LAI for CONUS)

- NEON sites (19): RMSE = 0.8, r² = 0.88 (source: [[kang_2021_lai_landsat]])
- 8 independent sites: RMSE = 0.52–0.91 across biomes
- Uncertainty varies by biome — croplands and shrublands higher RMSE than forests

## Relationship to Other Variables

- LAI correlates with NDVI but saturates earlier (NDVI saturates around LAI 3–5)
- NIRv and kNDVI show better linearity with LAI at high values
- LAI is distinct from canopy cover (fractional cover) and canopy height but correlates with both in closed forests

## Related pages

- [[ndvi]]
- [[phenology]]
- [[sentinel_2]]
- [[landsat]]
- [[kang_2021_lai_landsat]]
