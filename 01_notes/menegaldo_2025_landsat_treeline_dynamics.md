---
title: "Tree line dynamics and forest densification in the European Alps revealed by Landsat images and machine learning: a case study in the Senales/Schnals Valley"
authors:
  - Irene Menegaldo
  - Victoria Mølbach Sforzini
  - Roberto Tognetti
  - Michele Torresani
year: 2025
tags:
  - remote-sensing
  - machine-learning
  - forest-ecology
keywords:
  - tree line dynamics
  - Landsat
  - Random Forest
  - orthophoto interpretation
  - growing season
  - South Tyrol
status: read
---

## Title and Authors of the Paper

- "Tree line dynamics and forest densification in the European Alps revealed by Landsat images and machine learning: a case study in the Senales/Schnals Valley"
- Irene Menegaldo, Victoria Mølbach Sforzini, Roberto Tognetti, Michele Torresani
- *Vegetation Ecology and Diversity* 62: e177152 (2025); doi: 10.3897/ved.177152

## Quick Overview

- **Why is it relevant?** It tests whether a cheap Landsat + Random Forest workflow reproduces treeline positions from manual orthophoto delineation and links the change to climate and topography in the Italian Alps.
- **What was done?** Landsat 5 (1985) and Landsat 8 (2022) images in 16 sample areas of the Senales valley were classified into forest/non-forest with Random Forest; treelines were compared with manual delineation on orthophotos (1982/85 vs 2023), and climate trends (1981–2023, single station) were analysed with linear models and GAMs.
- **What is the main outcome?** Forest cover increased in all 16 areas (on average +44 %); treeline elevation increased in 15 of 16 areas by +32 m (Landsat) and +45 m (orthophotos), most on west-facing slopes, with climate (warming, summer precipitation) discussed as enabling factors.

## Main Goal and Fundamental Concept

- Goal: evaluate how well Landsat time series with machine learning monitor treeline dynamics and identify climatic and topographic drivers.
- Idea: a binary forest/non-forest classification of 30 m pixels, converted to a treeline line, is a sufficient and low-cost proxy for treeline elevation change when validated against high-resolution orthophotos.

## Technical Approach

- **Study area**: Senales valley (about 210 km²), South Tyrol; treeline species mostly *Larix decidua*, with *Pinus cembra* on N and E slopes.
- **Sampling design**: 16 study areas chosen from combinations of aspect (N, E, S, W) and slope (<30° vs ≥30°), each combination represented twice, from a DTM.
- **Classification**: atmospherically corrected Landsat surface reflectance; Random Forest in QGIS Semi-Automatic Classification Plugin with the default of 10 trees, balanced class weights, and manually labelled training areas for Forest vs Non-forest (grassland, rock, urban); accuracy assessed with the plugin's accuracy tool.
- **Manual delineation**: treelines drawn in QGIS on orthophotos from 1982/85 and 2023; points every 30 m along the lines received DTM elevation; shift = elevation difference between the two years; comparison between RF-derived and manual lines.
- **Climate**: daily data from one meteorological station about 5 km from the sites (1981–2023); trends in temperature, precipitation, a simple SWE estimate from min/max temperature, and thermal growing season (start, end, length) with LM and GAM.

## Distinctive Features

- Direct comparison of ML-derived and manually delineated treelines, which the authors say was missing.
- Includes derived growing-season and snow-water-equivalent variables.
- Balanced sampling across aspects and slope classes.

## Experimental Setup and Results

- RF accuracy: overall accuracy 98.65 % (1985) and 98.11 % (2022); producer's and user's accuracies >97 % for both classes.
- Forest cover increased in all 16 areas, mean +44 %; W- and S-facing areas showed large increases, E areas about +18 to +25 %; gentler slopes (<30°) tended to have a higher percentage increase.
- Treeline elevation advanced in 15 of 16 areas: +32 m (Landsat) and +45 m (orthophotos) on average, with the mean for the four west-facing areas about +53 m over 37 years (Landsat).
- RF and manual lines agreed with deviations below one Landsat pixel (30 m) in most cases.
- Climate: temperature rose significantly from about 2000 (about +0.05 °C per year; a decrease occurred before), spring and autumn minimum temperatures increased, summer precipitation increased significantly; no significant trends in snow water equivalent, growing-season length or annual precipitation.
- The authors suggest N-NW wind and föhn limit expansion on S-SE slopes.

## Advantages and Limitations

**Advantages**
- Transparent, reproducible and cheap workflow with an independent high-resolution check.
- Long record (1985–2022) and aspect/slope stratification.

**Limitations**
- Very high class accuracies (about 98 %) refer to a binary forest/non-forest problem on training areas chosen by the authors; the accuracy assessment is internal to the plugin, and no independent, area-adjusted validation (e.g. Olofsson-type) is described, so they do not translate into a treeline-position error.
- 30 m Landsat cannot capture sparse treeline trees, tree height or shrubs (dwarf pine), and forest "presence" needs a minimum area, which delays detection; existing trees may be recorded as new ones (the authors cite Garbarino et al. 2023).
- Landsat shifts (+32 m) are smaller than the orthophoto shifts (+45 m), i.e. the method underestimates change, and the shift is about one Landsat pixel.
- Orthophotos from 1982/85 are a composite from different years and resolution (1 m vs 0.2 m), which adds uncertainty.
- Only 16 areas in one valley, a single climate station and a simple SWE estimate (not interpolated, "not absolute"), so the climate–treeline link is correlative; land-use abandonment is mentioned but not analysed.
- RF with 10 trees and little hyper-parameter tuning.

## Conclusion

- Landsat with RF reproduces orthophoto-derived treeline change within about one pixel but with systematic underestimation; forest densification and a modest treeline rise of tens of metres are found in this valley.
- It supports the use of Landsat for coarse treeline monitoring but not for tree-scale processes. See [[garbarino_2023_treeline_remote_sensing]], [[carrieri_2025_hr_imagery_treeline]], [[nguyen_2024_treeline_monitoring]], [[frei_2023_treeline_shift]].
