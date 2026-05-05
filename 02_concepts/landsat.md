---
name: landsat
description: Landsat satellite program overview — sensors, archive history, observation density patterns, and key limitations for time series analysis
type: reference
tags:
  - remote-sensing
  - landsat
  - time-series
  - land-cover
---

# Landsat

**Summary**: The Landsat program is a multi-decade series of Earth observation satellites operated by NASA and USGS, providing the longest continuous global land surface record in remote sensing history at 30 m spatial resolution.

**Sources**: [[bayle_2024_landsat_greening_inflated]], [[chastain_2007_eve_landsat_understory]], [[pflugmacher_2019_lulc_landsat]], [[bell_2024_hindcasting_forest_structure]]

**Last updated**: 2026-05-05

---

## Satellite Generations

| Satellite | Years Active | Sensor | Key Notes |
|-----------|-------------|--------|-----------|
| Landsat 1–3 | 1972–1983 | MSS | 80 m resolution |
| Landsat 4–5 | 1982–2013 | TM | 30 m, 7 bands; workhorse of the archive |
| Landsat 7 | 1999–present | ETM+ | SLC failure 2003 → ~22% data gaps |
| Landsat 8 | 2013–present | OLI + TIRS | Improved radiometry, SNR |
| Landsat 9 | 2021–present | OLI-2 + TIRS-2 | First concurrent pair without technical failure |

## Temporal Resolution and Observation Density

- Nominal revisit time: 16 days per satellite
- Overlapping path tiles double effective revisit frequency in those areas
- Usable (cloud-free, snow-free) observations vary dramatically by location and era:
  - 1980s: ~2–4 usable growing-season observations per year in the European Alps
  - 2013+: ~8–12 usable growing-season observations per year
- The non-uniform increase over time is a major source of bias in trend analyses (source: [[bayle_2024_landsat_greening_inflated]]) — see [[sampling_bias_remote_sensing]]

## Common Derived Products

- **NDVImax**: Annual maximum NDVI from all cloud-free observations within a season — see [[ndvi]] and [[sampling_bias_remote_sensing]]
- **Tasseled Cap**: Brightness, Greenness, Wetness indices
- **Annual composites**: Medoid or median composites for land cover mapping
- **LULC time series**: Long-term land use and land cover change products (e.g., Pflugmacher et al.)

## Spectral-Temporal Metrics (STMs) for Land Cover Mapping

STMs are per-pixel statistical summaries of all cloud-free observations within a time window — the operational approach for large-area Landsat-based land cover classification:
- **Seasonal medians**: median per spectral band/index for spring (Mar–May), summer (Jun–Aug), fall (Sep–Nov), and growing season (May–Sep) → captures phenological dynamics distinguishing land cover types
- **Annual statistics**: min, max, mean, std, 5th–95th percentile per band/index → captures within-year variability (useful for differentiating crops from grasslands)
- **Multi-year pooling**: pooling 3 years of observations rather than 1 reduces spring/fall cloud gaps from ~7% to <0.2%; improves accuracy especially for temporally dynamic classes (source: [[pflugmacher_2019_lulc_landsat]])
- **Auxiliary features**: geographic coordinates (latitude, longitude) and WorldClim bioclimatic variables contribute +4.7pp OA — larger than any single spectral feature group — by providing biogeographic context for geographically restricted classes (perennial cropland, shrubland, artificial)

**LUCAS-based pan-European LULC map (Pflugmacher et al. 2019)** (source: [[pflugmacher_2019_lulc_landsat]]):
- 12 land cover classes, 30m resolution, 2015 reference year; OA=75.1% (Random Forest + 178 features)
- Area proportions correlate with LUCAS at r=0.98 vs r=0.84 for CORINE
- CORINE overestimates seasonal cropland by 63%, underestimates grassland by 37% — STM-based approach substantially more accurate at area estimation
- Mixed forest (PA=50%) and Mediterranean grassland/shrubland remain the most challenging classes

## Temporal Transferability: Hindcasting and Updating

Landsat-based forest attribute models can be reliably applied outside their reference epoch (source: [[bell_2024_hindcasting_forest_structure]]):
- Gradient Nearest Neighbor (GNN) imputation linking USDA FIA plot data to Landsat imagery is robust for hindcast (applying a 2007–2016 model to 2001–2006) and update (applying a 2001–2010 model to 2011–2016) extrapolations
- At the plot and pixel level, full and extrapolation models are statistically indistinguishable (95% CI overlapping for R², mean error)
- At landscape scale (780 ha hexagons), small spatially structured errors emerge — associated with geographic areas where the pool of available FIA plots differed between model configurations
- Key assumption: stationarity of the spectral-forest structure relationship over time; Landsat sensor drift, shifting phenology, and canopy lichen changes can alter spectral signals independently of forest structure change
- Practical implication: long-term continuous forest map records can be generated from a temporally limited field inventory, enabling both retrospective analysis and forward-looking change detection

## Key Limitations for Time Series Analysis

- Observation frequency increased non-linearly over the archive → systematic bias in annual composites (see [[sampling_bias_remote_sensing]]; source: [[bayle_2024_landsat_greening_inflated]])
- SLC failure in Landsat 7 (post-2003) creates striped data gaps of ~22%
- Cloud and snow masking (CFmask/Fmask) can misclassify cold surfaces as clouds at high elevations (source: [[bayle_2024_landsat_greening_inflated]])
- Cross-sensor radiometric differences between TM, ETM+, and OLI require normalization; 3-year multi-sensor pooling reduces seasonal cloud gaps from ~7% to <0.2% (source: [[pflugmacher_2019_lulc_landsat]])

## Related pages

- [[ndvi]]
- [[sampling_bias_remote_sensing]]
- [[vegetation_greenness_trends]]
- [[phenology]]