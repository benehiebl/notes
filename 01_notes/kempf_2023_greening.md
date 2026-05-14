---
title: "Enhanced trends in spectral greening and climate anomalies across Europe"
authors:
  - Kempf, Michael
year: 2023
source: kempf_2023_greening
tags:
  - remote-sensing
  - forest-ecology
keywords:
  - NDVI
  - greening trend
  - climate anomaly
  - drought
  - landcover change
  - MODIS
  - GLDAS
  - Europe
status: read
---

# Kempf 2023 — Enhanced Trends in Spectral Greening and Climate Anomalies Across Europe

## Title and Authors
**Enhanced trends in spectral greening and climate anomalies across Europe**
Michael Kempf — *Environmental Monitoring and Assessment* 195: 260 (2023).

## Quick Overview
- **Why is it relevant?** Pairs 21 years of MODIS NDVI with 74 years of GLDAS reanalysis to disentangle background greening trends from climate-anomaly–driven vegetation response across Europe — directly relevant to interpreting Italian vegetation trends.
- **What was done?** Linear-model trend analysis and standard-deviation-based anomaly mapping on annual and seasonal MODIS NDVI (2001–2021) and GLDAS variables (temperature, rain, snow, soil moisture, surface temperature) over Europe.
- **What is the main outcome?** Positive NDVI trends concentrated in Northern Europe (longer GSL, rising T, more soil moisture in winter/early growing season); negative trends in Southern Europe; long-term trends mask increasing year-to-year *anomalies* that signal vulnerability to extreme events.

## Main Goal and Fundamental Concept
The classical narrative of "global greening" obscures regional heterogeneity. Kempf asks: where in Europe is NDVI rising, where is it falling, and how do these patterns map onto climate trends *and* anomalies — i.e. trends in *variability* on top of trends in *mean*?

## Technical Approach
- MODIS NDVI monthly composites (0.05° / ~5.6 km), 2001–2021/22.
- GLDAS Noah Land Surface Model L4 monthly 0.25°, 1948–2021: surface temperature, snow precipitation rate, rain precipitation rate, snow depth, soil moisture 0–10 cm and 10–40 cm, soil temperature, air temperature.
- Annual + seasonal aggregation (MAM, JJA, SON, DJF) for both data sources.
- Trend analysis: pixelwise linear regression, slopes retained at p < 0.05.
- Anomaly analysis: deviations beyond mean ± 1 SD per pixel, year, and season.
- Spatial stratification into "northern" (below mean annual air T) and "southern" (above) zones using the 7.05 °C threshold computed for 1948–2021.

## Distinctive Features
- Long GLDAS climatology (74 yr) anchors short-term NDVI signals.
- Parallel treatment of trends and anomalies — a key conceptual point: trend stability can coexist with anomaly intensification, both of which matter for vegetation vulnerability.
- Seasonal stratification reveals strong winter/spring contributions to greening, often missed in growing-season-only analyses.
- All code and data publicly available (repository linked).

## Experimental Setup and Results

**Surface reflectance trends (2001–2021)**
- Strong positive greening in Northern Europe — Scandinavia, Baltics, parts of Russia, UK
- Mixed-to-negative trends in Mediterranean (Iberia, parts of southern Italy, Greece)
- Central Europe: locally heterogeneous; locally negative trends where heat/drought events repeat

**Seasonal contributions**
- Winter (DJF) + spring (MAM) NDVI rises strongly in northern latitudes — earlier/longer growing season
- Summer (JJA) trends regionally divergent: positive in north, negative in dry-Mediterranean
- Autumn (SON) generally positive

**Climate anomalies (1948–2021)**
- Temperature anomalies sharply increasing since the 1980s; positive deviations dominate
- Soil moisture anomalies: increasing variability with strong negative deviations in Southern Europe
- Rainfall anomalies: variable, with more negative excursions in Mediterranean
- Surface temperature anomalies: strong upward trend, especially over the past two decades

**Trend–anomaly relationship**
- Long-term trends in mean climate appear smooth but mask increasingly *intense* anomalies
- Vegetation response anomalies (NDVI deviations) growing alongside climate anomalies
- High-frequency variability → vegetation stress, even where mean trends are positive

## Advantages and Limitations
- **Advantages**: Combines short NDVI record with long climate baseline; explicit trend × anomaly framing; seasonal decomposition; open code.
- **Limitations**: Coarse NDVI resolution (~5.6 km) hides fine-scale events; pixelwise linear trends ignore non-linearity and breakpoints; no causal attribution between specific climate drivers and NDVI; landcover heterogeneity may inflate or dampen apparent trends (the classic [[sampling_bias_remote_sensing]] caution applies in interpretation).

## Conclusion
European greening is **regionally polarised** (N positive, S mixed-negative). Both **mean trends and anomaly intensity** are increasing across most variables, with anomalies the better indicator of vegetation vulnerability to climate extremes. Long-term trends should be interpreted alongside year-to-year variability, particularly in regions undergoing intensified heat or drought. Useful baseline for regional analyses of vegetation–climate coupling and for distinguishing Italian patterns from pan-European averages.

## Related pages
- [[ndvi]]
- [[vegetation_greenness_trends]]
- [[sampling_bias_remote_sensing]]
- [[phenology]]
- [[bayle_2024_landsat_greening_inflated]]
- [[herraiz_2025_phen_shifts_mediterranean]]
- [[chelli_2017_climate]]
- [[schuldt_2020_drought_forest]]
- [[babst_2019_redistribution]]
- [[yel_2026_deciduous_forests]]
