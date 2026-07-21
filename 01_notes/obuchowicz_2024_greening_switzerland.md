---
title: "Change in observed long-term greening across Switzerland – evidence from a three decades NDVI time-series and its relationship with climate and land cover factors"
authors:
  - Claire Obuchowicz
  - Charlotte Poussin
  - Gregory Giuliani
year: 2024
tags:
  - remote-sensing
  - vegetation-trends
keywords:
  - NDVI
  - Landsat
  - Switzerland
  - greening trend
  - Swiss Data Cube
  - land cover
  - temperature correlation
  - precipitation correlation
  - Mann-Kendall
  - anomaly detection
status: unread
---

## Title and Authors of the Paper
- "Change in observed long-term greening across Switzerland – evidence from a three decades NDVI time-series and its relationship with climate and land cover factors"
- Claire Obuchowicz, Charlotte Poussin, Gregory Giuliani
- Institute for Environmental Sciences, EnviroSPACE lab, University of Geneva, Switzerland
- Published in *Big Earth Data*, 2024, Vol. 8, No. 1, pp. 1–32 (published online 20 Oct 2023), DOI: 10.1080/20964471.2023.2268322
- Open access

## Quick Overview
- **Why is it relevant?** It is a national-scale, Landsat-derived (30 m) NDVI greening-trend study for Switzerland spanning 1984–2018, directly comparable to other Landsat greening-trend papers such as [[bayle_2024_landsat_greening_inflated]] and [[herraiz_2025_phen_shifts_mediterranean]].
- **What was done?** The authors built annual and seasonal NDVI time-series from Landsat-5/-8 imagery (via the Swiss Data Cube) for all of Switzerland (1984–2018), analyzed trends at national, biogeographical-region, land-cover-class and pixel levels, computed z-score anomalies, and correlated NDVI with temperature and precipitation.
- **What is the main outcome?** A statistically significant national greening trend is found (61% of pixels significant, 97% of those positive; national annual mean slope ≈ 1.11×10⁻⁵/year, i.e. ~0.6%/year cited in the abstract), with a marked acceleration/break around 2010, greening driven more strongly by temperature than by precipitation, and forested classes (closed forest, open forest) among the most responsive land cover types.

## Main Goal and Fundamental Concept
- Assess long-term (35-year) vegetation greenness dynamics across Switzerland at higher spatial resolution than prior MODIS/AVHRR-based European/global greening studies, which the authors argue are too coarse for a small, topographically heterogeneous country like Switzerland.
- Three stated objectives: (1) characterize spatiotemporal NDVI patterns at national, biogeographical-region and pixel level; (2) identify which land cover classes are most responsive to NDVI change; (3) evaluate relationships between NDVI and temperature/precipitation.
- Framed as contributing "ready-to-use" ecological-state-of-vegetation monitoring information for national environmental reporting and SDG-related land degradation tracking, not as a mechanistic/causal study.

## Technical Approach
- **Satellite data / sensor**: Landsat-5 and Landsat-8 (Level-2/Collection 1), accessed and processed through the Swiss Data Cube (SDC). Landsat-7 explicitly excluded due to the post-2003 Scan Line Corrector failure (so 2012 has no data at all).
- **Time period**: 1984–2018 (35 years of archive coverage, though the usable annual time series spans 34 years of transitions; abstract calls it a "35-year" and "three decades" NDVI time-series).
- **Spatial resolution**: 30 m (native Landsat), later resampled to 1 km to match climate grids for correlation analysis.
- **NDVI computation**: standard (NIR−RED)/(NIR+RED); multi-date compositing (annual mean + 4 seasonal means: DJF, MAM, JJA, SON) to cope with cloud cover and sparse temporal sampling.
- **Cloud/quality filtering**: Landsat Collection 1 QA band; only "clear", "water", "snow" pixels retained; pixels with <10% clear observations over the whole record excluded (23% of all pixels excluded nationally, concentrated in the Alps — up to 22% of pixels excluded in summer, 10–17% in other seasons).
- **Land cover**: national Land Use Statistics (Federal Office for Statistics, NOLC04 nomenclature, 100 m resolution aerial-photo survey, static 2013/18 snapshot used) — 27 classes grouped into "Artificial areas", "Grass and herb vegetation", "Brush vegetation", "Tree vegetation" domains, including several forest sub-classes (closed forest, forest edges, forest strips, open forest, brush forest, linear woods, cluster of trees).
- **Trend statistics**: linear regression (R², p-value) and Mann-Kendall trend test (tau, p-value) at national, biogeographical-region (6 regions: Jura, Central Plateau, Northern Alps, Southern Alps, Western Central Alps, Eastern Central Alps), seasonal and land-cover levels; ACF/PACF checked for autocorrelation.
- **Anomalies**: NDVI z-scores (relative to the 1984–2018 mean/std) classified into 7 WMO-style classes (extremely bad → extremely good), computed annually, seasonally and by decade.
- **Climate correlation**: Pearson correlation (annual/seasonal NDVI vs. MeteoSwiss 1-km gridded temperature 1984–2018 and precipitation 2005–2018 only), plus pixel-wise Spearman correlation.

## Distinctive Features
- Analysis is **all-land-cover**, not forest-specific: it covers all of Switzerland's NOLC04 land cover classes (artificial areas, grasslands, shrubs, orchards, vines, and multiple forest categories), with forest classes analyzed as a subset among many.
- National-scale, high-resolution (30 m/Landsat) framing is explicitly positioned against prior European/global greening studies that used coarse MODIS (250 m–1 km) or AVHRR data — the authors argue Switzerland's small size and mountainous heterogeneity require finer resolution.
- Use of an operational Earth Observation Data Cube (Swiss Data Cube) for full-archive, analysis-ready processing.
- Identification of an apparent breakpoint/acceleration around 2010 in the greening trend across seasons and regions, with anomaly maps showing consistently "very good/extremely good" greening scores from 2011–2018.
- Correlates NDVI not just with temperature but explicitly separates winter/spring/summer/autumn responses, finding winter NDVI–temperature correlation strongest at the national scale (r=0.70).

## Experimental Setup and Results
- **National annual trend**: significant slope on ~61% of pixels (77,761,233 total pixels analyzed); of those significant pixels, >97% positive. National linear regression: R²=0.43, p<0.05, slope=1.11×10⁻⁵/year; Mann-Kendall tau=0.49, p<0.05. Mean annual NDVI 1984–2018 = 0.47, ranging from 0.34 (2002, drought year) to 0.57 (2013).
- **Seasonal trends**: significant increases in all seasons; strongest in summer (R²=0.31, p<0.05) and winter (R²=0.29, p<0.05); weaker in spring (R²=0.23) and autumn (R²=0.18). Highest seasonal NDVI values consistently recorded post-2010, especially 2016/2017.
- **Regional (biogeographic) trends**: significant positive trend in all 6 regions; strongest correlations in low-elevation Jura (R²=0.50) and Central Plateau (R²=0.40); weakest/least consistent in Eastern Central Alps (R²=0.19) and Western Central Alps (R²=0.22). Three elevation-based behavior clusters identified: low-elevation (Jura/Plateau, higher NDVI), Northern/Southern Alps, and Eastern/Western Central Alps (lowest NDVI).
- **Land cover classes**: nearly all classes show significant positive trends except "brush meadows" (class 32, R²=0.16, weak). Strongest responses: closed forest (R²=0.57), vines (R²=0.56), open forest (R²=0.49) — all p<0.05.
- **Anomalies**: lowest NDVI z-scores nationally in 1984, 1992, 2002 (z=−1.19), 2005; highest in 2013 (z=1.85). Clear shift to consistently positive anomalies (mostly "very good"/"extremely good") from 2011–2018 across all regions and decades.
- **Climate correlations**: national annual NDVI–temperature r=0.52 (p<0.05, moderate positive); strongest at regional scale in Jura (r=0.71) and Central Plateau (r=0.57); weak/non-significant in Western Central Alps (r=0.19) and Eastern Central Alps (r=0.00). Precipitation correlations mostly negative and non-significant at national/regional scale (national annual r=−0.41, not flagged significant in the results table for Switzerland column at annual level per Table 8, though seasonal spring precipitation shows a significant moderate negative correlation, r=−0.61 nationally, p<0.05; winter/spring low-elevation regions show the strongest negative precipitation correlations).
- Data (NDVI time-series) and code openly published (Zenodo/Yareta links + Jupyter notebooks referenced).

## Advantages and Limitations
- **Strengths**: full national coverage at 30 m resolution over a genuinely long (35-year) archive; multiple independent trend tests (linear regression + Mann-Kendall) improve robustness against non-normality; explicit seasonal decomposition; open data/code; combines land cover, climate and NDVI in one national framework — useful as a Switzerland-specific comparison point.
- **No sampling-bias / observation-density correction discussed anywhere in the paper.** The authors filter pixels by minimum clear-observation count (≥10% of the record) but do not test or discuss whether increasing Landsat observation density over time (more usable clear scenes in later years due to added sensors/improved processing) could itself inflate late-period NDVI or NDVI-max values — this is exactly the artifact mechanism demonstrated by [[bayle_2024_landsat_greening_inflated]] for Landsat-based Alpine greening trends above 2400 m. Given that (a) this study also uses Landsat over the Alps, (b) cloud-free observation density is explicitly shown to be spatially very uneven (Figure 3, with large excluded zones in the Alps), and (c) the paper's own reported "break point" and acceleration around 2010–2011 coincides with the kind of archive-density changes (additional sensors, improved processing) that Bayle et al. flag as a bias driver — this study appears vulnerable to the same artifact and does not test for or rule it out. This is a significant unaddressed caveat.
- **Correlative, not causal**: temperature/precipitation relationships are simple Pearson/pixel-wise correlations; no attribution modeling, no separation of CO2 fertilization, land management (afforestation/land abandonment), or snowmelt-timing effects, which the discussion itself acknowledges are confounded (e.g. forest area increased due to land abandonment in some regions, complicating a pure "climate greening" interpretation).
- **Precipitation data only covers 2005–2018** (13 years) versus temperature's full 1984–2018, so precipitation trend/correlation conclusions rest on a much shorter, more recent-biased window — the authors note this limits interpretability but the truncation is a real methodological asymmetry.
- **Static land cover dataset**: land cover survey used is essentially a single snapshot (2013/18 campaign) applied across the full 1984–2018 NDVI series, so land-cover-class NDVI trends do not account for actual land cover change during the study period — acknowledged by the authors as a limitation.
- **Landsat-7 fully excluded** (SLC-off issue), and 2012 has no data at all; several other years/seasons were dropped for cloud cover (e.g. winter 2003/2008/2013, spring 2003, autumn 1986/2002) — creates real gaps in an already coarse annual/seasonal composite.
- 23% of pixels nationally (concentrated in the Alps, the area most relevant to forest/alpine ecology questions) were excluded for insufficient clear observations — the areas most affected by cloud (and by the Bayle et al. bias mechanism) are exactly the areas least represented in this analysis.
- The abstract's headline "0.6%/year" greening figure and the body text's "slope=1.11×10⁻⁵/year" appear to use different framings/units — worth checking against the original PDF equations if citing a precise growth rate, as the two do not obviously match without knowing the exact percentage-normalization used.
- No forest-species or forest-type distinction is made (softwood vs hardwood) — flagged explicitly by the authors themselves as future work.
- Small, early-career authorship (MSc/PhD students plus a senior lead); single national case study — findings are not warranted to generalize beyond Switzerland/the Alps without independent replication.

## Conclusion
- Switzerland shows a statistically significant, moderate greening trend in NDVI at national, regional and seasonal scales over 1984–2018, with an apparent acceleration from around 2010–2011.
- Below the treeline, NDVI is more strongly controlled by temperature than precipitation; forested land cover classes (closed forest, open forest) and vines are among the most NDVI-responsive classes.
- The authors frame the work as an exploratory, policy-relevant national monitoring contribution (SDG-15 relevant) rather than a mechanistic attribution study, and explicitly call for future work incorporating land cover change dynamics, forest-type distinctions, and additional explanatory variables (soil, CO2, evapotranspiration).

## Related pages
- [[vegetation_greenness_trends]]
- [[sampling_bias_remote_sensing]]
- [[bayle_2024_landsat_greening_inflated]]
- [[kempf_2023_greening]]
- [[herraiz_2025_phen_shifts_mediterranean]]
- [[landsat]]
- [[ndvi]]
- [[phenology]]
