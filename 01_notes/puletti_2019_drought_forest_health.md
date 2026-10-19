---
title: "Monitoring the effects of extreme drought events on forest health by Sentinel-2 imagery"
authors:
  - Nicola Puletti
  - Walter Mattioli
  - Filippo Bussotti
  - Martina Pollastrini
year: 2019
tags:
  - remote-sensing
  - forest-ecology
  - climate-change
keywords:
  - Sentinel-2
  - crown dieback
  - 2017 drought
  - NDVI
  - Mediterranean forests
  - Fagus sylvatica
  - Quercus ilex
status: read
---

## Title and Authors of the Paper

- "Monitoring the effects of extreme drought events on forest health by Sentinel-2 imagery"
- Nicola Puletti, Walter Mattioli, Filippo Bussotti, Martina Pollastrini
- *Journal of Applied Remote Sensing* 13(2): 020501 (2019); doi: 10.1117/1.JRS.13.020501 (a short "JARS Letter", 7 pages)

## Quick Overview

- **Why is it relevant?** It is an early Sentinel-2 test of whether the 2017 Mediterranean drought can be seen in vegetation indices, and its photosynthetic-activity contrast between species is one of the few RS evidence points for evergreen (holm oak) vs deciduous drought response in Tuscany.
- **What was done?** 118 field plots in beech, downy oak and holm oak stands in Tuscany were labelled "healthy" or "unhealthy" (crown desiccation/defoliation), and NDVI, red-edge NDVI and simple ratio from 30 Sentinel-2 tile dates (2016–2018) were compared between the two groups.
- **What is the main outcome?** Healthy and unhealthy plots differed significantly in August 2017 (p < 0.01), mostly in the deciduous stands, and beech recovered in 2018 while unhealthy holm oak plots showed a lasting NDVI reduction.

## Main Goal and Fundamental Concept

- Goal: test whether multitemporal Sentinel-2 vegetation indices can detect crown dieback caused by an extreme drought, without field surveys.
- Idea: stressed crowns lose photosynthetic activity, which lowers visible/NIR indices; comparing the intra-annual trajectory of "healthy" vs "unhealthy" plots reveals both the event and species-specific response strategies.
- Species contrast is the conceptual core: deciduous beech (drought-sensitive but able to refoliate) vs evergreen holm oak (sclerophyllous, nominally drought-tolerant).

## Technical Approach

- **Plots**: 118 observational samples in three stand types along a coastal–inland gradient (beech ~72 km², downy oak ~125 km², holm oak ~125 km² regional area), with varying bedrock, soil depth, altitude, slope and aspect.
- **Plot labels**: binary "healthy"/"unhealthy" from drought-induced leaf/branch desiccation and crown defoliation; the labelling protocol is not described in detail, and the post-event visual check (2018) is also used as validation of the index trajectories.
- **Imagery**: 30 Sentinel-2 Level-1C tile dates (3 tiles; June–August 2016, 2017, 2018; April–May for 2018), corrected to surface reflectance with Sen2Cor via the `sen2r` package.
- **Indices** (10 m bands): NDVI, red-edge NDVI (RENDVI) and simple ratio (SRI).
- **Terrain layers**: elevation, slope, aspect from a 20 m DTM were collected, but the results focus on indices.
- **Analysis**: (i) indices for June–August 2017; (ii) monthly healthy vs unhealthy comparison with t-tests; (iii) beech and holm oak trajectories for 2016 and 2018 (before/after).

## Distinctive Features

- Very early Sentinel-2 application (2017 data, published 2019) on a sharply defined climatic extreme.
- Field-based health class per plot rather than pure image-based change detection.
- Species-level comparison inside one drought event, including recovery in the following year.

## Experimental Setup and Results

- Indices were highest in June and lowest in August 2017; healthy and unhealthy plots did not differ in June/July (p > 0.5) but did in August (p < 0.01), strongest for beech and downy oak.
- The three indices performed similarly and are considered interchangeable.
- Beech: unhealthy plots reached the same NDVI as healthy ones again in July/August 2018 (e.g. July: 0.79 ± 0.06 vs 0.79 ± 0.02 in 2018), interpreted as recovery through refoliation.
- Holm oak: eleven "unhealthy" plots showed a persistent NDVI reduction after 2017; downy oak behaved more like holm oak than like beech, despite being deciduous.
- The authors conclude that 10 m Sentinel-2 can serve as an early-warning tool and propose a Google Earth Engine implementation.

## Advantages and Limitations

- **Advantages**: simple, reproducible index workflow; free data; ground-referenced plots; shows recovery trajectories and species differences.
- **Limitations** (critical reading):
  - Only 118 plots, one event and one region; no spatial cross-validation or autocorrelation handling, and pixels/plots are tested with t-tests.
  - Healthy/unhealthy labels were assigned from the same drought event; the validation of trajectories by visual inspection is not independent.
  - The text gives inconsistent p-value statements for the beech comparison (similar values reported with "p < 0.01"), so the significance claims in the 2016/2018 comparison cannot be taken at face value without checking the figures.
  - Single scenes per month and tile (Table 1), no atmospheric/phenological normalisation and no compositing, so intra-month illumination and phenology differences are not controlled.
  - Mean NDVI of ~0.8 for beech suggests saturation; the "recovery" in NDVI does not prove physiological recovery (cf. drought legacy effects in [[drought_mortality]]).
  - Beech vs holm oak contrasts are explained by plausible physiology, but no mechanistic data are collected.
  - The authors themselves note that Sentinel-2's short archive limits historical analysis.

## Conclusion

- Sentinel-2 vegetation indices separate healthy from drought-damaged crowns in the peak of an extreme drought and show species-specific recovery.
- It is a useful, citable proof of concept for the Tuscany 2017 event, but methodologically light; later studies (e.g. [[seddaiu_2025_mediterranean_dieback]]) reuse its ΔIndex magnitude (−0.1) as a threshold, so its weaknesses propagate.
- Relevant for: [[sentinel_2]], [[ndvi]], [[drought_mortality]], [[mediterranean_holm_oak_dieback]].
