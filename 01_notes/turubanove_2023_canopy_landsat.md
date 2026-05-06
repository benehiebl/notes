---
title: "Tree canopy extent and height change in Europe, 2001–2021, quantified using Landsat data archive"
authors:
  - Turubanova, Svetlana
  - Potapov, Peter
  - Hansen, Matthew C.
  - Li, Xinyuan
  - Tyukavina, Alexandra
year: 2023
source: turubanove_2023_canopy_landsat
tags:
  - remote-sensing
  - forest-ecology
status: read
---

# Turubanova et al. 2023 — Tree Canopy Extent and Height Change in Europe 2001–2021 via Landsat

## Title and Authors
**Tree canopy extent and height change in Europe, 2001–2021, quantified using Landsat data archive**
Svetlana Turubanova, Peter Potapov, Matthew C. Hansen et al. — *Remote Sensing of Environment*, 2023

## Quick Overview
- **Why is it relevant?** Produces the first annual 30 m tree canopy height time series for all of Europe over 21 years, directly relevant for forest monitoring, disturbance detection, and carbon stock estimation studies.
- **What was done?** Integrated Landsat phenological metrics with ALS (Northern Europe) and GEDI (Central/Southern Europe) lidar calibration data via regression tree ensembles to model annual tree canopy height; combined with annual canopy removal maps for a consistent 21-year continental product.
- **What is the main outcome?** European tree canopy extent increased ~1% overall 2001–2021 but declined after 2016; tall canopy forests (≥15 m) decreased 3%; Fennoscandia lost 3.5% net; increasing disturbances and harvest intensification are drivers.

## Main Goal and Fundamental Concept
NFI data are inconsistent across European countries and cannot provide continuous annual tree canopy height change at continental scale. The Landsat archive provides 20+ years of consistent spectral observations. This study creates annual tree canopy height maps by calibrating Landsat phenological metrics against airborne and spaceborne lidar measurements, enabling direct quantification of canopy dynamics.

## Technical Approach
- **Landsat processing:** Annual phenological metrics from full archive (2001–2021, ~30 m); cloud masking, normalization
- **Calibration lidar data:**
  - ALS (Airborne Laser Scanning) for Northern Europe
  - GEDI (Global Ecosystem Dynamics Investigation, spaceborne lidar) for Central/Southern Europe
- **Model:** Regression tree ensemble; locally calibrated per region
- **Integration:** Annual height maps + separately produced tree canopy removal detection maps → harmonized 21-year time series
- **Tree canopy extent:** Derived from ≥5 m height threshold
- **Validation:** Set-aside ALS data + visually interpreted reference sample following Olofsson et al.

## Distinctive Features
- Combines two lidar sources (ALS + GEDI) to calibrate at continental scale where ALS coverage is incomplete
- Annual maps at 30 m — enables tracking individual disturbance events and recovery
- Product publicly accessible: `glad.earthengine.app/view/europe-tree-dynamics`
- Validates at two levels: continuous height (RMSE ≤ 4 m) and binary canopy extent (UA/PA ≥ 94%)

## Experimental Setup and Results
- **RMSE:** ≤4 m for both ALS- and GEDI-calibrated height maps
- **Canopy extent accuracy:** User's and Producer's ≥94%; canopy removal accuracy ≥80%
- **Net change (2001–2021):** +1% overall Europe tree canopy extent, but declining after 2016
- **Regional patterns:** Largest increase: Eastern Europe, Southern Europe, British Isles; Fennoscandia: −3.5% net
- **Tall canopy forests (≥15 m):** −3% continental — indicating reduction in carbon storage capacity
- **Post-2016 decline:** Consistent with timber harvest intensification (FAO statistics) and increasing disturbances

## Advantages and Limitations
- **Advantages:** Annual temporal resolution; continental coverage; GEDI extends to regions without ALS; publicly accessible product
- **Limitations:** RMSE ≤ 4 m limits precision for precise carbon accounting; 30 m resolution misses individual tree structure; model transferability between regions depends on lidar coverage

## Conclusion
Annual 30 m tree canopy height maps reveal that European forests transitioned from a net carbon sink (expanding canopy 2001–2016) toward a reduced sink after 2016 due to increasing disturbances and harvest intensification. The combination of Landsat + lidar calibration is a scalable approach for long-term continental forest structural monitoring.

## Related pages
- [[landsat]]
- [[forest_disturbances]]
- [[vegetation_greenness_trends]]
- [[national_forest_inventory]]
