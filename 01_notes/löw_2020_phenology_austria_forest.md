---
title: "Phenology Modelling and Forest Disturbance Mapping with Sentinel-2 Time Series in Austria"
authors:
  - Markus Löw
  - Tatjana Koukal
year: 2020
tags:
  - remote-sensing
  - forest-ecology
keywords:
  - phenology modelling
  - Sentinel-2
  - Savitzky-Golay filter
  - forest disturbance
  - bark beetle
  - time series analysis
  - Austrian national forest inventory
status: read
---

## Title and Authors of the Paper

- "Phenology Modelling and Forest Disturbance Mapping with Sentinel-2 Time Series in Austria"
- Markus Löw, Tatjana Koukal (Austrian Research Centre for Forests, BFW)
- *Remote Sensing* 12(24): 4191 (2020); doi: 10.3390/rs12244191

## Quick Overview

- **Why is it relevant?** Authorities need area-wide, timely maps of forest disturbances in topographically complex terrain, and Sentinel-2 (S2) offers 10 m and few-day revisits but needs a robust time-series method.
- **What was done?** A time series analysis framework was developed that fits per-pixel phenology models with a dynamic Savitzky–Golay filter to dense S2 data (2017–2019), derives phenology metrics and flags disturbances as deviations from the modelled phenology.
- **What is the main outcome?** Nationwide phenology models and metrics for Austrian forests were produced, and in a bark-beetle case study in northern Austria 83.4 % of field-recorded disturbances were detected, with 95.2 % agreement on "no disturbance" points.

## Main Goal and Fundamental Concept

- Goal: build an operational, forest-monitoring workflow that locates disturbances and estimates the date they occurred.
- Concept: the expected seasonal course of a vegetation index at each pixel is estimated from a multi-year model period; persistent negative deviations from that baseline in a detection period indicate disturbance.
- Harmonic models are robust but smooth away intra-annual detail; a locally adapted Savitzky–Golay filter keeps more detail.

## Technical Approach

- **Data**: S2A/S2B Level-1C top-of-atmosphere data from 20 granules covering Austria, January 2017 to December 2019, using the 10 m bands B02, B03, B04, B08 and images with <80 % cloud cover. Sen2Cor bottom-of-atmosphere data were judged too error-prone for operational use without visual checks, so only the quality masks are used.
- **Masking**: combination of a NIR threshold, cloud probability and scene classification, plus outlier detection; restriction to the national forest map of the NFI definition.
- **Indices**: NDVI, GNDVI, RGVI (red–green vegetation index) and scaled NIR.
- **Phenology model**: dynamic Savitzky–Golay filtering with an adaptive window width; yearly snippets summarised by percentile courses (PC10, PC50, PC90); mean of PC10 and PC90 used as main phenology course (MPC). Metrics: start and end of vegetation period (SVP, EVP), maximum MPC and date of maximum.
- **Anomaly detection**: baseline offset from the MPC; cumulative deviation compared to a threshold (forest disturbance level, FDL; medium sensitivity FDL = 7); outputs the Cumulative Deviation Date and a backward-reconstructed Forest Disturbance Date (FDD). Model period 2017–2018, detection period 2018–2019.
- **Validation**: about 1500 in situ disturbance observations (≥3 affected trees; mostly bark beetle, also wind throw, snow breakage, fungi) from Lower Austria, plus 271 random "no disturbance" points sized following Olofsson et al. 2014.

## Distinctive Features

- First nationwide operational S2 forest phenology and disturbance system for Austria, as claimed by the authors.
- Dynamic window width in the Savitzky–Golay filter adapts to local data density, which varies strongly across Austria.
- Works on TOA data with own masking and outlier filtering.
- Outputs an estimated disturbance date, not only a binary map.

## Experimental Setup and Results

- About 40,000 km² of forest and about 400 million unique models per index were computed.
- RGVI proved the best index for negative-deviation detection (lowest noise, especially in coniferous forest); NDVI values around 0.65 indicate spruce-dominated forest.
- Disturbed forest in the case study region 2018–2019: 23,400 ha, on average 2.8 % of forest area, above 4 % in some municipalities.
- 83.4 % of field-recorded disturbances were detected (249 cases missed); 95.2 % of "no disturbance" points verified as undisturbed.
- Timing: in the vegetation period (May–September) 51 % of FDDs deviated by less than ±30 days from the field date and 76 % of FDDs lay before the field date; outside the vegetation period the FDD is about 130 days earlier than the recorded date for most cases (the reconstruction is anchored on a theoretical intersection date).

## Advantages and Limitations

**Advantages**
- Full-resolution (10 m), operational and scalable; flexible parameters (sensitivity, smoothing).
- Retains intra-annual dynamics and gives disturbance timing.
- National coverage allows phenology metrics (SVP, EVP) as ancillary NFI layers.

**Limitations**
- TOA reflectance without atmospheric correction; masks are imperfect and rely on outlier filtering.
- The validation covers one region and mostly bark beetle; the in situ dataset has low spatial coverage and date inaccuracies, which the authors cite to explain part of the 16 % omission error.
- Only three years (two for the model); only a short baseline for natural year-to-year variability (drought, snow, frost) and heavy dependence on S2B availability from 2018.
- No separation of disturbance type (harvest, bark beetle, storm); no accuracy in terms of area-adjusted estimates; no forest-type stratification.
- Topographic shadow and snow in the Alps remain challenging, not specifically evaluated in alpine ecotones.

## Conclusion

- Dense S2 time series with a locally adapted smoother yield nationwide phenology metrics and disturbance maps with good detection of field-recorded events.
- Relevance for forest-type and species-cover modelling: phenology metrics derived from S2 are plausible input features, but the paper does not use them for species or forest-type classification. Related: [[soto_2025_disturbance]], [[senf_2021_disturbance]], [[senf_2021_impacts_2018_forests]], [[wegler_2026_canopy_cover_loss]].
