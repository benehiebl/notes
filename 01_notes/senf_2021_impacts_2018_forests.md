---
title: "Persistent impacts of the 2018 drought on forest disturbance regimes in Europe"
authors:
  - Cornelius Senf
  - Rupert Seidl
year: 2021
tags:
  - remote-sensing
  - forest-ecology
  - climate-change
keywords:
  - 2018 drought
  - forest disturbance
  - Landsat disturbance map
  - vapor pressure deficit
  - soil moisture
  - disturbance regime
  - bark beetle
status: read
---

## Title and Authors of the Paper

- "Persistent impacts of the 2018 drought on forest disturbance regimes in Europe"
- Cornelius Senf, Rupert Seidl
- *Biogeosciences* 18: 5223–5230 (2021); doi: 10.5194/bg-18-5223-2021

## Quick Overview

- **Why is it relevant?** The 2018 drought and heat wave are a benchmark event for climate-driven forest disturbance in Europe, and satellite-based maps of canopy loss are directly relevant for forest mapping and for how long maps stay valid.
- **What was done?** An existing 30 m Landsat-based map of European canopy disturbance (updated to 2020) was aggregated to 0.1° cells, expressed as anomalies relative to 1986–2015, and related to summer soil-moisture and vapour-pressure-deficit anomalies with a log-linear model; disturbance regime characteristics (frequency, patch size, aggregation) were tracked over 1986–2020.
- **What is the main outcome?** Forest disturbance in 2018–2020 reached unprecedented levels, mainly in central and eastern Europe, and the elevated rates persisted for up to two years after the drought, associated with low 2018 soil moisture and high VPD in 2018–2020.

## Main Goal and Fundamental Concept

- Goal: provide a first continental assessment of how the 2018 compounding drought–heat event affected forest disturbance regimes in Europe.
- Hypothesis: low soil moisture in 2018 and high atmospheric water demand in 2018–2020 caused persistent increases in disturbance, partly through indirect effects such as bark beetle outbreaks.
- Disturbance is defined as any abrupt decline of the dominant forest canopy, whatever its cause (including harvest and salvage logging).

## Technical Approach

- **Disturbance data**: 30 m annual Landsat-based map of canopy disturbance in Europe (1986–2020; the existing product was updated with the same workflow); the initial map had an overall accuracy of 87.6 ± 0.5 %, a commission error of 17.1 ± 1.6 % and an omission error of 36.9 %, so it is conservative; Norway data excluded due to cloud artefacts.
- **Aggregation**: annual disturbed area per 0.1° (about 9 km) grid cell; disturbance anomaly A = D / D_ref × 100 relative to the 1986–2015 mean (cells with <1 ha/yr average disturbance removed).
- **Climate**: summer (June–August) soil moisture and VPD from ERA5-Land at 0.1°, converted to z-scores against 1986–2015.
- **Model**: log-linear Gaussian model of disturbance anomalies in 2018–2020 as a function of soil moisture 2018, VPD of the respective year, their interaction and year; compared by AIC.
- **Regime metrics**: frequency (disturbances per forest area and year), size (95th percentile of patch size), and spatiotemporal aggregation (proportion of patches within a 5 km kernel in the same year).

## Distinctive Features

- Continental scale with a consistent 35-year satellite record, allowing comparison with the past range of variation.
- Goes beyond area disturbed by characterising frequency, size and aggregation of disturbance.
- Open code and data.

## Experimental Setup and Results

- About 4.74 million ha were disturbed in 2018–2020, an average annual surplus of about 360,000 ha over the reference mean.
- Strongest increase in central Europe (mostly Germany, Czechia, Austria) and eastern Europe; western and southern Europe, less affected by the drought, showed smaller changes.
- Disturbance in 2019 and 2020 correlated significantly with the soil-moisture anomaly in 2018; VPD effects were weaker but a significant interaction indicated the highest anomalies where low soil moisture in 2018 coincided with high VPD in 2019–2020; soil moisture and VPD alone explained 11.5 % of the continental-scale variance.
- Frequency, size and aggregation of disturbances increased beyond historical levels, which the authors take as pushing the system outside its past basin of attraction.
- Disturbance in 2020 was 1.42 times higher than in 2000 (Storm Lothar year); fire explained only about 3 % of disturbed area in 2018 in the affected regions.

## Advantages and Limitations

**Advantages**
- Wall-to-wall, consistent measurement over decades.
- Transparent, simple statistical link to the drought drivers.

**Limitations**
- The disturbance map detects canopy loss regardless of cause (harvest, salvage logging, bark beetle, wind), so attribution to drought is indirect and salvage logging inflates mortality; only 11.5 % of variance is explained by the two climate variables.
- Map accuracy: omission error about 37 %, so absolute disturbed areas are underestimates; no area-adjusted uncertainty is propagated into the regional anomalies; 30 m Landsat misses partial disturbance.
- Only three years post-drought, so "persistent" and "loss of resilience" claims are extrapolations; the future development of the regime was unknown.
- 0.1° aggregation and ERA5-Land climate do not capture topography or local conditions (which the authors state).

## Conclusion

- The 2018 drought had unprecedented impacts on European forest disturbance with persistence over multiple years.
- For mapping: recent drought/disturbance dynamics mean that older forest maps may include mortality-affected areas, and training labels from 2018–2020 may be contaminated. Related: [[senf_2021_disturbance]], [[schuldt_2020_drought_forest]], [[soto_2025_disturbance]], [[löw_2020_phenology_austria_forest]], [[wegler_2026_canopy_cover_loss]].
