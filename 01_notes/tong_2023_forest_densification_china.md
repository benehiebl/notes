---
title: "Reforestation policies around 2000 in southern China led to forest densification and expansion in the 2010s"
authors:
  - Tong, Xiaowei
  - Brandt, Martin
  - Yue, Yuemin
  - Fensholt, Rasmus
  - Ciais, Philippe
  - Wang, Kelin
year: 2023
source: tong_2023_forest_densification_china
tags:
  - remote-sensing
  - forest-ecology
status: read
---

# Tong et al. 2023 — Reforestation in Southern China: Forest Densification and Expansion via Landsat

## Title and Authors
**Reforestation policies around 2000 in southern China led to forest densification and expansion in the 2010s**
Xiaowei Tong, Martin Brandt, Yuemin Yue et al. — *Communications Earth & Environment*, 2023

## Quick Overview
- **Why is it relevant?** Demonstrates how 30-year Landsat archives can reveal spatiotemporal patterns of forest densification and expansion at landscape scale — directly relevant to large-scale vegetation change monitoring methodologies.
- **What was done?** Annual forest probability maps (1986–2018) were derived from Landsat time series via machine learning to quantify forest age, densification rates, and fragmentation patterns across southern China at 30 m resolution.
- **What is the main outcome?** Forest area increased from 9% (249,414 km²) to 35% (978,954 km²) of southern China 1986–2018; reforestation policies around 2000 produced a forest surge around 2010 as planted trees matured; old forests shifted from mountain tops downhill.

## Main Goal and Fundamental Concept
Southern China underwent one of the world's largest reforestation transitions from the 1980s, but coarse satellite data could not resolve spatial details of individual stand formation and succession. This study uses Landsat's fine spatial resolution (30 m) and multi-decadal archive to reconstruct the full spatiotemporal history of individual forest stands, quantifying densification, expansion, age structure, and fragmentation.

## Technical Approach
- **Data:** Annual Landsat time series, 1986–2018 (30 m)
- **Model:** Machine-learning trained annual forest probability (fp) maps as proxy for forest density
- **Forest definition:** Dense forest = fp ≥ 50% maintained continuously; emerging forest = fp > 20%
- **Metrics derived:** Forest age (years at fp ≥ 50%), densification rate (annual Δfp from 20% to 50%), forest fragmentation (core vs. non-core ratio)
- **Spatial scope:** Southern China (Guangdong, Guangxi, Guizhou provinces + surrounding region)

## Distinctive Features
- Reconstruction of individual forest stand age across an entire sub-continental region at 30 m — unprecedented detail for a plantation-dominated landscape
- Explicitly separates forest densification (existing stands growing denser) from forest expansion (new stands forming)
- Documents downhill migration of forest coverage from ridgetops to lower slopes over three decades
- Shows temporal lag between plantation policy (~2000) and area surge (~2010) as trees matured

## Experimental Setup and Results
- **Forest area increase:** 249,414 km² (1986) → 491,496 km² (2003) → 978,954 km² (2018)
- **Only 23% of 2018 forests are older** than the satellite record (pre-1986)
- **Peak forest addition:** mid-1990s and ~2010, matching plantation programme rollout + maturation timing
- **Spatial pattern:** Old forests in 1980s concentrated on mountain tops; expansion moved 729,540 km² downhill
- **Fragmentation:** Early forests fragmented; converging into larger closed canopies in the 2010s

## Advantages and Limitations
- **Advantages:** Full landscape coverage; fine spatial resolution; temporal depth enabling age estimation; policy-relevant insights
- **Limitations:** Forest probability threshold choice affects results; short-rotation plantations may be excluded by fp thresholds; species composition unknowable from Landsat reflectance alone

## Conclusion
Landsat time series at 30 m can reconstruct the history of individual forest stand formation and densification over three decades. Southern China's reforestation transition was driven by post-2000 policies producing dense forests by 2010. The spatial pattern reveals relief-controlled expansion and substantial fragmentation reduction. This demonstrates the potential of long-term Landsat archives for forest change attribution at large scales.

## Related pages
- [[landsat]]
- [[vegetation_greenness_trends]]
- [[forest_disturbances]]
- [[phenology]]
