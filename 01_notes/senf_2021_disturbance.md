---
title: Mapping the forest disturbance regimes of Europe
authors:
  - Cornelius Senf
  - Rupert Seidl
year: 2021
tags:
  - remote-sensing
  - forest-ecology
keywords:
  - forest disturbance
  - LandTrendr
  - Landsat time series
  - disturbance regime
  - Europe
  - random forest
status: read
---

1. **Title and authors of the Paper:**
Mapping the forest disturbance regimes of Europe. Senf & Seidl (2021), Nature Sustainability.

2. **Quick Overview:**
- **Why is it relevant?** Prior to this study there was no spatially and temporally consistent, continental-scale dataset on Europe's forest disturbance regimes (size, frequency, severity) covering both natural and anthropogenic causes.
- **What was done?** The authors mapped annual forest disturbances across continental Europe (1986–2016, 35 countries, 210 million ha) at 30 m resolution using >30,000 Landsat images via LandTrendr + random forest classification, calibrated/validated with ~20,000 manually interpreted reference pixels.
- **What is the main outcome?** 17% of Europe's forest area (39 million ha, 36 million patches) was disturbed over the 30-year period; disturbance frequency increased significantly (in 74% of forest area) while disturbance severity decreased (in 88% of forest area), and frequency changes — not size changes — explain most (71%) of the increase in disturbance rates.

3. **Main Goal and Fundamental Concept:**
- Goal: produce the first continental-scale, spatially explicit characterization of Europe's forest disturbance regimes (size, frequency, severity) and quantify how these three dimensions changed 1986–2016.
- Concept: disturbance regimes are the cumulative effect of all disturbance events in an area/period, summarized by patch size, frequency (patches per km² forest area), and severity (probability of stand-replacing canopy loss). Disentangling whether rising disturbance *rates* are driven by more frequent events or larger events requires mapping all three dimensions jointly.

4. **Technical Approach:**
- **Reference data:** 19,996 manually interpreted Landsat forest pixels (visual interpretation of spectral trajectories + Google Earth imagery; from Senf et al. prior work), plus 46,461 country-stratified non-forest pixels (66,457 total; 61,457 for calibration, 5,000 for validation).
- **Mapping workflow (Google Earth Engine):**
  1. Screened all Tier 1 Landsat 4/5/7/8 surface reflectance images, spectrally cross-calibrated (Roy et al. coefficients), filtered to summer (1 Jun–30 Sep), built annual medoid composites.
  2. Ran **LandTrendr** time-series segmentation on two spectral bands (SWIR1, SWIR2) and two indices (Tasseled Cap Wetness, Normalized Burn Ratio), with maximally sensitive (no filtering) parameters.
  3. Extracted the greatest-change segment per pixel and derived magnitude, duration, rate-of-change, signal-to-noise, pre-change value, and post-change rate metrics.
  4. **Random forest classification** (using these LandTrendr metrics + 3-yr Tasseled Cap brightness/greenness/wetness composites centred on 1985 and 2018) classified each pixel as no-forest / undisturbed forest / disturbed forest — filtering LandTrendr commission errors (e.g., spectral changes in agricultural land).
  5. Disturbance year assigned via majority vote (median as tie-break) across the four spectral bands/indices.
  6. **Severity** (0–1, probability of stand-replacing disturbance) derived via logistic regression predicting stand-replacing vs. non-stand-replacing disturbance (from post-disturbance land cover in reference data) from the four spectral change magnitudes.
- **Regime characterization:** disturbance size and severity aggregated at patch level (rook-contiguity patches, 0.09 ha pixels) then averaged to 50×50 km hexagons (3,240 hexagons across Europe); frequency computed directly per hexagon (patches/km² forest/yr). Trends quantified via Theil–Sen estimator (robust to outliers).

5. **Distinctive Features:**
- First continental-scale (35 countries, 210M ha), 30-year, annually-resolved map combining natural **and** anthropogenic disturbances in a single consistent product.
- Joint quantification of three disturbance regime dimensions (size, frequency, severity) — enabling decomposition of disturbance *rate* trends into frequency vs. size contributions (71% vs. 24% of variance explained).
- Severity is derived as a continuous 0–1 proxy from spectral change magnitude via a logistic model trained against manually-interpreted post-disturbance land cover, rather than a binary disturbed/undisturbed classification.
- Hexagonal landscape grid (50 km, ~2,165 km²) chosen over square grid to better match Europe's complex coastlines/borders.

6. **Experimental Setup and Results:**
- Overall map accuracy: 92.5% ± 2.1%; commission error 14.6% ± 1.8%; omission error 32.8% ± 0.3% (mostly low-severity disturbances indistinguishable from noise).
- Disturbance year: mean absolute error 3 years vs. manual interpretation; 77% within 3 years.
- 36 million disturbance patches, 39 million ha disturbed (17% of European forest area), mean patch size 1.09 ha (median 0.45 ha; 78% < 1 ha; 99% < 10 ha); largest single patch = 16,617 ha (2012 southern Spain fire).
- Mean disturbance frequency 0.52 patches/km² forest/yr (median 0.37); mean severity 0.77 (median 0.83) — majority of disturbances were stand-replacing.
- Spatial patterns: larger patches in northern/southern and eastern Europe vs. central/western Europe; highest frequencies concentrated in Portugal; highest severities in Atlantic Ireland/UK, Iberia, Po Valley, Pannonian Basin; lowest severities along the Dinaric range and Italian Apennines.
- Trends 1986–2016: disturbance size trends spatially variable (increasing in Baltic states, UK, Ireland, Italy; decreasing in eastern Germany, western Poland, SE Europe); frequency increased in 74% of forest area (hot spots central/eastern Europe); severity decreased in 88% of forest area (strongest declines central and SE Europe).
- Countries with small-scale, continuous-cover management (e.g., Slovenia, Switzerland) showed substantially smaller patch size and lower severity than even-aged/plantation-dominated countries (e.g., Finland, Sweden, Denmark, Hungary, Ireland), suggesting management is a major driver of spatial variability beyond biophysical/forest-type differences.

7. **Advantages and Limitations:**
- **Advantages:** spatially and temporally consistent across the whole of continental Europe; open data and code (Zenodo/GitHub); robust validation against a large, independently-collected reference dataset; severity proxy enables differentiation of stand-replacing vs. partial disturbances at scale.
- **Limitations:** omission error concentrated in low-severity/partial disturbances (signal close to background noise); each pixel's disturbance history is reduced to its single "greatest change" segment, so multiple sequential disturbance events within the 30-yr window on the same pixel are not captured (explicitly addressed by the successor product [[soto_2025_disturbance]], which maps multiple events per pixel); severity is a spectral-change proxy, validated only indirectly (no pan-European canopy-loss ground truth); no disturbance-agent attribution (wind/bark beetle/fire/harvest not separated — also addressed in [[soto_2025_disturbance]]).

8. **Conclusion:**
This paper provides the first continental, 30-year, spatially explicit baseline of Europe's forest disturbance regimes, showing that the well-documented increase in European forest disturbance rates is driven primarily by an increase in disturbance *frequency* (more, generally smaller events) rather than disturbance *size*, while disturbance *severity* has broadly decreased — likely reflecting shifts toward smaller-scale forest management interacting with rising natural disturbance activity. It establishes the LandTrendr + random forest mapping framework and reference dataset later extended by [[soto_2025_disturbance]] (European Forest Disturbance Atlas) to multi-event, agent-attributed disturbance mapping, and is foundational evidence cited by [[grünig_2026_climate_change_disturbances_forest]] for disturbance trend baselines used in process-based forest models.

## Related pages
- [[forest_disturbances]]
- [[soto_2025_disturbance]]
- [[grünig_2026_climate_change_disturbances_forest]]
- [[landsat]]
