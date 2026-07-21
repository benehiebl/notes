---
title: "Climate effects on vegetation vitality at the treeline of boreal forests of Mongolia"
authors:
  - Michael Klinge
  - Choimaa Dulamsuren
  - Stefan Erasmi
  - Dirk Nikolaus Karger
  - Markus Hauck
year: 2018
tags:
  - forest-ecology
  - remote-sensing
  - climate-change
  - mountain-forests
keywords:
  - treeline
  - NDVI
  - Mongolia
  - boreal forest
  - forest-steppe
  - precipitation
  - temperature limitation
  - Larix sibirica
  - permafrost
  - climate envelope
status: unread
---

## Title and Authors of the Paper
"Climate effects on vegetation vitality at the treeline of boreal forests of Mongolia" — Michael Klinge, Choimaa Dulamsuren, Stefan Erasmi, Dirk Nikolaus Karger, Markus Hauck. Published in Biogeosciences, 15, 1319–1333, 2018.

## Quick Overview
- **Why is it relevant?** Provides an empirical, remote-sensing-based analysis of which climate variables limit upper vs. lower treeline position in a semiarid boreal system, directly informative for treeline/climate-limitation concept pages.
- **What was done?** Landsat-derived forest maps, SRTM-derived treeline surfaces, and 15-year (1999–2013) averages of SPOT VGT NDVI and CHELSA/ERA-Interim climate data were combined to statistically relate vegetation vitality (NDVI) to precipitation, temperature and solar radiation at the upper and lower treelines of three Mongolian boreal forest types (taiga, subtaiga, forest–steppe).
- **What is the main outcome?** The upper treeline is primarily thermally limited (mean growing-season temperature, MGST, of 7.9–8.9 °C, minimum ~6 °C), while the lower treeline is primarily moisture-limited (mean annual precipitation, MAP, minimum of 230–290 mm yr⁻¹); the relative importance of humidity vs. snow cover as secondary limiting factors differs between forest–steppe and taiga.

## Main Goal and Fundamental Concept
- Characterize the climatic envelope of three types of Mongolian boreal forest (taiga, subtaiga, forest–steppe) and their treelines using satellite-derived vegetation vitality (NDVI) and gridded climate data.
- Test three hypotheses:
  - Each boreal forest type is delimited by a specific climatic envelope, reflected in NDVI–climate correlations.
  - Different forest types show different spatial gradients of climate-induced vitality change, especially at treelines.
  - Forest and grassland within the same ecological zone show different spatial gradients/relations to climate.
- Underlying concept: treelines represent visually obvious, climatically controlled ecotone boundaries; NDVI is used as a proxy for tree/vegetation vitality rather than direct field measurement.

## Technical Approach
- **Forest mapping**: supervised maximum-likelihood classification of 50 Landsat 8 images (30 m resolution; some gap-filled with Landsat 5), followed by manual correction and majority filtering.
- **Treeline delineation**: kernel-window analysis on the classified forest raster to detect points meeting slope, forest-in-surroundings and no-forest-beyond criteria; separate search parameters for upper treeline (UT) and lower treeline (LT). Points interpolated into continuous treeline surfaces via natural-neighbor interpolation; a 1 km buffer around each surface defines the treeline boundary zone (1 km chosen to match the ~1 km resolution of SPOT VGT NDVI/CHELSA climate grids).
- **Climate/vegetation data**: SPOT VGT NDVI (1999–2013, 1 km) aggregated to mean growing-season NDVI (MGS-NDVI, May–Sept); CHELSA gridded climate data (30 arcsec, ~1 km, terrain/wind-corrected) used for mean annual precipitation (MAP) and mean growing-season temperature (MGST); solar radiation (MGSR) computed via GIS-based approach from SRTM DEM.
- **Statistical analysis**: up to 3000 random points per class (forest/grassland × forest type × TE/LT/UT subunit = 18 ecological subunits); Duncan's multiple range test for group-mean comparisons; Pearson and multiple correlation coefficients between MGS-NDVI, MAP, MGST and MGSR.
- All variables are 15-year means, explicitly a simplification that discards interannual and phenological variability.

## Distinctive Features
- Combines high-resolution Landsat/SRTM structural mapping with coarser but terrain-corrected climate grids (CHELSA) to bridge spatial scales between forest structure and climate.
- Explicit separation of forest vs. grassland fractions and of upper vs. lower treeline subunits (18 total ecological subunits), rather than treating each forest biome as a single unit.
- Distinguishes the "subtaiga" as an ecological transition zone characterized by an approximately constant ~300 mm yr⁻¹ precipitation threshold that is largely independent of temperature.
- Identifies a temperature/precipitation correlation sign-flip between forest–steppe (positive MAP–MGST correlation) and taiga (negative correlation), interpreted as evidence of different secondary limiting factors (relative humidity in forest–steppe vs. snow cover distribution in taiga).
- Explicitly acknowledges that with up to 3000 random points per subunit, classical significance (t-test / p-value) testing becomes uninformative because p is essentially always < 0.05; the authors instead rely on correlation-coefficient magnitude for interpretation — a methodologically self-aware point worth noting.

## Experimental Setup and Results
- Study covers the full forested extent of southern Mongolia's boreal belt (73,818 km² total forest area out of 182,036 km² total ecological unit area across all three forest types).
- Upper treeline generally rises from ~1800 m a.s.l. (northeast) to ~2700 m a.s.l. (south); lower treeline rises from ~1000 m a.s.l. (northern taiga) to ~2500 m a.s.l. (south), with a longitudinal (not just latitudinal) gradient in places.
- MGST at the UT: 7.9–8.9 °C mean, minimum ~6 °C, narrow/uniform frequency distribution across all forest types — interpreted as MGST being the dominant limiting factor at the upper treeline.
- MAP at the LT: minimum 230–290 mm yr⁻¹, also limiting at the UT of forest–steppe.
- MGS-NDVI is generally lower in grassland than forest, and lower at treelines than at the forest-type-average (TE); one exception is the alpine/mountain-meadow vegetation at the UT of subtaiga and taiga, where grassland NDVI can exceed forest NDVI.
- Correlations (Table 2) between MGS-NDVI and MAP+MGST combined are generally the strongest predictors (r up to ~0.71–0.75 in some subunits); adding MGSR gives only marginal improvement.
- No trend analysis or future projection is generated by the study itself; it only compares its findings against other authors' climate-change projections for Mongolia (up to +5 °C warming by end of century; regionally divergent precipitation trends).

## Advantages and Limitations
- **Correlative, not causal or mechanistic**: the entire analysis rests on statistical correlation between 15-year mean NDVI and climate grids; no field validation of NDVI-vitality linkage, no experimental or physiological confirmation of the proposed limiting mechanisms.
- **NDVI as a vitality proxy has known caveats** (saturation in denser canopies, sensitivity to understory/mixed pixels) that are not deeply interrogated in the paper beyond a general caution.
- **Spatial-resolution mismatch**: 30 m Landsat forest classification vs. 1 km NDVI/climate grids necessarily mixes signal from heterogeneous ecological subunits; authors acknowledge this "spatial overlap producing mixed NDVI values cannot be totally avoided."
- **Averaging over 15 years discards interannual variability and extreme events** (droughts, fire years), which the authors themselves flag as a simplification, even though extreme events are likely important drivers of the dead-tree margins they describe.
- **Confounding factors omitted from the regression models**: permafrost distribution, soil hydrology, and human impacts (grazing, logging, fire) are all discussed qualitatively as important but are not included as covariates, so the reported MAP/MGST correlations may partly be capturing correlated but unmodeled drivers.
- **Statistical power inflation**: up to 3000 random points per subunit make conventional significance testing meaningless (p always < 0.05); the authors correctly pivot to correlation-coefficient interpretation, but readers should not over-read the "significant" language elsewhere in the paper.
- **Climate data quality**: CHELSA/ERA-Interim are reanalysis/modeled products, not direct mountain station measurements, in a region with sparse instrumental coverage — a source of uncertainty the authors themselves note.
- The authors explicitly caution against extrapolating future treeline/forest shifts directly from current NDVI–climate correlations, since this ignores tree rejuvenation dynamics, adaptation lag, and permafrost loss — a good example of appropriate self-restraint in interpretation.
- **Strength**: large spatial coverage (all of southern Mongolia's boreal forest), systematic separation of upper/lower treeline and forest/grassland subunits, and transparent workflow (Fig. 2) make the approach reproducible and extendable to other semiarid treeline systems.

## Conclusion
- Upper treeline position in Mongolia's boreal forests is mainly thermally controlled (MGST minimum ~6 °C), lower treeline position is mainly moisture controlled (MAP minimum 230–290 mm yr⁻¹), with subtaiga acting as a precipitation-defined (~300 mm yr⁻¹) transition zone relatively independent of temperature.
- Secondary limiting factors differ by forest type: relative humidity in the forest–steppe, snow cover distribution in the taiga.
- Rapid climate change in inner Asia is expected to relocate treelines, tree communities and boreal forest type boundaries, but the authors stress that directly deducing future forest/vitality trends from current NDVI–climate relationships is problematic due to human impact, tree rejuvenation dynamics, climate-adaptation lag and disappearing permafrost.

## Related pages
- [[babst_2019_redistribution]]
- [[noce_2023_altitude_shift_tree_italy]]
- [[chelli_2017_climate]]
- [[schuldt_2020_drought_forest]]
- [[topographic_microclimate]]
- [[drought_mortality]]
- [[forest_disturbances]]
- [[treeline_ecotone_theory]]
- [[snow_cover_treeline]]
