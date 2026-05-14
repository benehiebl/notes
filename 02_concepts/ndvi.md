---
name: ndvi
description: NDVI definition, computation, derived annual metrics, known limitations including saturation and sampling bias
type: reference
tags:
  - remote-sensing
  - vegetation-index
---

# NDVI

**Summary**: The Normalised Difference Vegetation Index (NDVI) is the most widely used spectral index for quantifying vegetation greenness from red and near-infrared reflectance, serving as a proxy for photosynthetic activity, vegetation density, and plant biomass.

**Sources**: [[bayle_2024_landsat_greening_inflated]], [[chastain_2007_eve_landsat_understory]], [[he_2015_remote_sensing_sdm]], [[yel_2026_deciduous_forests]], [[yang_2020_modis_evergreen]], [[kempf_2023_greening]], [[schuldt_2020_drought_forest]]

**Last updated**: 2026-05-14

---

NDVI = (NIR − RED) / (NIR + RED)

Values range from −1 to +1; healthy dense vegetation typically yields 0.4–0.9; bare soil and sparse vegetation yield lower values.

## Key Derived Metrics

- **NDVImax**: Annual maximum NDVI from all available growing-season observations — most common metric for long-term productivity trend studies; highly sensitive to observation density (see [[sampling_bias_remote_sensing]])
- **Integrated NDVI (iNDVI)**: Seasonal sum of NDVI; less sensitive to single-observation timing but requires gap-filled time series
- **Mean growing-season NDVI**: Average over the phenologically defined season

## Relationship to Plant Productivity

- Closely correlated with leaf area index (LAI) and fraction of absorbed photosynthetically active radiation (fAPAR) at low-to-moderate values
- Saturates at high vegetation density (LAI ≳ 3–4) — limits sensitivity in dense forests
- Affected by soil background, atmospheric conditions, viewing geometry, and canopy structure

## Limitations and Biases

- **Sampling bias in NDVImax**: In seasonally snow-covered environments, NDVImax underestimates true peak greenness when observations are sparse; as observation frequency increases over time, estimates increase even without real vegetation change → spurious greening trends (source: [[bayle_2024_landsat_greening_inflated]]) — see [[sampling_bias_remote_sensing]]
- **Saturation**: Insensitive to productivity variation in dense vegetation
- **Cross-sensor differences**: Landsat TM vs ETM+ vs OLI vs Sentinel-2 require careful radiometric normalisation
- **Atmospheric and geometric confounders**: Solar angle, aerosols, snow/cloud contamination

## Common Alternatives

- **EVI** (Enhanced Vegetation Index): corrects for soil background and atmospheric effects; less prone to saturation
- **kNDVI**: Kernel NDVI; more robust at high vegetation density (source: [[yel_2026_deciduous_forests]])
- **SAVI** (Soil-Adjusted Vegetation Index): reduces soil background influence; useful in sparse vegetation
- **NDWI / NDMI**: canopy liquid water content — better drought tracking than NDVI (source: [[yel_2026_deciduous_forests]], [[schuldt_2020_drought_forest]])
- **PRI**: photosynthetic efficiency / xanthophyll cycle — captures rapid physiological change (source: [[yel_2026_deciduous_forests]])
- **SIF** (Solar-Induced Fluorescence): true photosynthetic activity — catches greenness-vs-GPP decoupling under stress (source: [[yel_2026_deciduous_forests]])

See [[yel_2026_deciduous_forests]] for a full inventory of indices with use cases and caveats.

## NDVI Time-Series Statistics for Mapping

Two derived statistics from a year of NDVI carry strong signal:
- **Intra-annual NDVI minimum (NDVI_annmin)**: diagnostic for evergreen presence — at the minimum, only evergreen + soil remain photosynthetic (source: [[yang_2020_modis_evergreen]])
- **Coefficient of variation (CV)** of the annual NDVI series: low for evergreen (flat curve), high for deciduous (large amplitude); discriminates evergreen from continuous crops (source: [[yang_2020_modis_evergreen]])

Combined as **FEVC-CV** with a dimidiate pixel model, these yield sub-pixel fractional evergreen cover with OA > 90% from MODIS (source: [[yang_2020_modis_evergreen]]).

## NDVI Anomaly Analysis for Drought Detection

Stacking long-term NDVI series and ranking each year against the empirical distribution exposes drought severity (source: [[schuldt_2020_drought_forest]]):
- 2018 Central European drought: area of deciduous forest in lowest NDVI quantiles ~2× that of 2003
- Quantile-based ranking is robust to systematic biases in absolute NDVI
- See [[drought_mortality]] and [[vegetation_greenness_trends]] for full treatment

Pan-European pairing of MODIS NDVI 2001–2021 with GLDAS climate variables reveals **trends in mean** can coexist with **growing anomaly intensity**, both of which signal vegetation vulnerability (source: [[kempf_2023_greening]]).

## Use in Species Distribution Models

NDVI is among the most widely used biotic predictor variables in SDMs:
- Proxy for vegetation productivity, food availability, and habitat quality (source: [[he_2015_remote_sensing_sdm]])
- Multi-year NDVI and projected future NDVI used to forecast species range dynamics under climate change
- **Circularity risk**: if the SDM response variable (species occurrence) was itself mapped from RS imagery, using RS-derived NDVI as a predictor creates a circular model — results should be interpreted with caution (source: [[he_2015_remote_sensing_sdm]])
- LAI3g and fPAR3g are improved alternatives to NDVI with better post-processing algorithms for SDM applications

## Related pages

- [[landsat]]
- [[phenology]]
- [[sampling_bias_remote_sensing]]
- [[vegetation_greenness_trends]]
- [[species_distribution_models]]