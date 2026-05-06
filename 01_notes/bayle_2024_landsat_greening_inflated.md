---
title: Landsat-based greening trends in alpine ecosystems are inflated by multidecadal increases in summer observations
authors:
  - Bayle, Arthur
  - Gascoin, Simon
  - Berner, Logan T.
  - Choler, Philippe
year: 2024
source: bayle_2024_landsat_greening_inflated
tags:
  - remote-sensing
  - vegetation-greenness
  - landsat
  - ndvi
  - sampling-bias
  - alpine-ecosystems
  - phenology
keywords:
  - NDVImax
  - greening-trend
  - observation-density
  - false-trend
  - growing-season-length
  - snowmelt
  - European-Alps
  - MODIS
  - phenological-sampling-bias
  - Theil-Sen
status: summarized
---

## Title and Authors of the Paper

*Landsat-based greening trends in alpine ecosystems are inflated by multidecadal increases in summer observations* — Arthur Bayle, Simon Gascoin, Logan T. Berner, and Philippe Choler (2024), Ecography, e07394. Affiliations: Univ. Grenoble Alpes / Univ. Savoie Mont Blanc / CNRS / LECA, Grenoble; Univ. Toulouse / CESBIO / CNES / CNRS / IRD / INRAE / UT3 Paul Sabatier; School of Informatics, Northern Arizona University.

## Quick Overview

- **Why is it relevant?** Landsat-derived annual maximum NDVI (NDVImax) is widely used to study multi-decadal vegetation greening, but the reliability of this metric depends on consistent observation frequency — a condition not met across the Landsat archive.
- **What was done?** The study quantified a systematic sampling bias in Landsat-based greening trends caused by the increasing number of usable observations over time, focusing on the European Alps as a case study with global implications for cold ecosystems.
- **What is the main outcome?** In high-elevation alpine zones (>2400 m a.s.l.), up to 50% of observed Landsat-based greening can be explained solely by this observational sampling bias, with late-snowmelt sites being most affected.

## Main Goal and Fundamental Concept

The paper investigates how the inconsistent temporal sampling frequency of the Landsat archive — which has dramatically increased the number of cloud-free, snow-free growing-season observations over four decades — biases estimates of annual maximum NDVI and the greening trends derived from them.

The core concept: if you sample a vegetation phenology curve more often, you are more likely to capture its true peak. In early Landsat years (1980s), sparse observations caused NDVImax to be systematically underestimated; in recent years, denser observations allow the true peak to be captured more reliably. This creates a spurious positive trend (apparent "greening") even when vegetation productivity is unchanged. The bias is strongest where growing seasons are shortest — high-elevation, late-snowmelt alpine habitats.

## Technical Approach

The study is structured around three linked analyses:

1. **Quantifying false greening trends** — MODIS daily NDVI (250 m, MOD09QA/Terra Collection 6, 2000–2021) was used to model true vegetation phenological curves using BISE + Savitzky-Golay smoothing and seven-parameter double-logistic curve fitting. Actual Landsat growing-season observation counts (OBS_GS; cloud-free, snow-free) were extracted from Landsat 5 TM, 7 ETM+, and 8 OLI Collection 2 via Google Earth Engine for 1984–2021. MODIS phenology curves were then sub-sampled using actual Landsat OBS_GS to generate annual NDVImax estimates mimicking what Landsat would observe. Any trend in these sub-sampled values — absent in the true phenology — constitutes an absolute "false trend" (αβF), estimated via Theil-Sen slope.

2. **Drivers of false trend magnitude** — Growing season length (GSL) and cumulative growing season observation count (ΣOBS_GS) were used as predictors in a random forest model to explain spatial variability in αβF across the Alps (R² = 0.963, RMSE = 9.24 × 10⁻⁵).

3. **Spatial distribution and relative importance** — False trends were mapped across the European Alps (1500–2800 m a.s.l.) and compared to actual Landsat-based greening trends (βNDVImax) to compute the relative importance of false trends (RIβF). Floristic plot data (n = 11,114) from the French National Alpine Botanical Conservatory were used to characterise bias across plant community types.

## Distinctive Features

- **MODIS as phenological ground truth**: rather than correcting the bias statistically, the authors simulate the full Landsat sampling process using high-frequency MODIS data, making the false trend directly computable and spatially mappable.
- **Random forest explanation of spatial variability**: R² = 0.963 provides near-complete mechanistic explanation of where and why the bias is large.
- **Floristic community context**: linking the bias to vegetation plot data grounds the methodological finding in concrete ecological consequences — snowbed communities are shown to be most severely misrepresented.
- **Global scope**: supplementary analyses extend findings to Arctic tundra and Asian mountain ranges, confirming the bias is not Alps-specific.

## Experimental Setup and Results

- **Study area**: European Alps (Alpine Convention boundary); analysis restricted to non-forested pixels >1500 m a.s.l., tree cover <5%, NDVImax >0.1.
- **Observation trends**: OBS_GS increased from ~2–3 per season in the 1980s to ~8–12 by 2021, driven by overlapping tiles, new satellite launches, and improved acquisition planning. The increase was non-linear, with step changes around 1999 (Landsat 7) and 2013 (Landsat 8).
- **False trend magnitude**: αβF ranged from near 0 in low-elevation, long-growing-season sites to ~0.002 NDVI year⁻¹ at high elevations with short growing seasons and few observations.
- **Relative importance**: RIβF = 10–20% at 1500–2400 m, accelerating to 20–50% above 2400 m. North-exposed alpine screes had RIβF up to 30% (median); forest ecotone had only 8%.
- **Key drivers**: ΣOBS_GS was the slightly stronger predictor; its interaction with GSL (short season + few observations) produced the largest false trends.
- **Actual vs false trends**: Observed trends (βNDVImax) are systematically larger than false trends — real greening is occurring, but its magnitude is inflated, especially at high elevation.

## Advantages and Limitations

**Advantages:**
- Rigorous, spatially explicit quantification of a widely acknowledged but rarely measured bias.
- MODIS as reference avoids dependence on field data and is globally available.
- Findings are actionable: concrete avoidance and correction strategies are proposed.
- Results generalise to any cold, seasonally snow-covered ecosystem worldwide.

**Limitations:**
- Assumes stationary phenology; long-term shifts in growing season length (themselves climate-driven) could partially counteract the bias by providing more observations at the tail of the time series — this interaction is not modelled.
- Linear trend analysis (Theil-Sen) does not capture non-linear greening dynamics or phase shifts.
- Cloud mask errors at high elevations (cold surfaces misclassified as clouds by CFmask) introduce additional noise not fully quantified.
- Correction methods discussed (temporal reconstruction, data fusion) carry their own assumptions and uncertainties.

## Conclusion

Bayle et al. (2024) demonstrate that the increasing temporal sampling density of the Landsat archive systematically inflates vegetation greening trend estimates in seasonally snow-covered ecosystems. In the European Alps, up to half of the measured greening signal above 2400 m can be attributed to this sampling bias alone. The bias is strongest precisely in the ecosystems most sensitive to climate change — high-elevation, late-snowmelt habitats. The practical recommendation is simple: always report the number of observations per year alongside trend estimates, and apply corrections when the study area includes zones with short growing seasons and historically low observation density.

## Related Work & Obsidian Links

- [[landsat]]
- [[ndvi]]
- [[phenology]]
- [[sampling_bias_remote_sensing]]
- [[vegetation_greenness_trends]]

- [[chastain_2007_eve_landsat_understory]] — also uses Landsat in seasonally variable environments; complements Bayle et al. by showing how leaf-off phenology can be exploited constructively, while Bayle et al. warn against naive maximum compositing
- [[bell_2024_hindcasting_forest_structure]] — uses Landsat time series for long-term forest monitoring; the sampling bias described here is relevant to any Landsat annual composite analysis

## Related pages

- [[landsat]]
- [[ndvi]]
- [[sampling_bias_remote_sensing]]
- [[vegetation_greenness_trends]]
- [[phenology]]
- [[chastain_2007_eve_landsat_understory]]
- [[bell_2024_hindcasting_forest_structure]]
