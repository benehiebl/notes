---
title: "Tree species from space: a new product for Germany based on Sentinel-1 and -2 time series"
authors:
  - Wegler, Marco
  - Kacic, Patrick
  - Thonfeld, Frank
  - Holzwarth, Stefanie
  - Jaggy, Niklas
  - Gessner, Ursula
  - Kuenzer, Claudia
year: 2025
source: wegler_2025_tree_species_germany
tags:
  - remote-sensing
  - machine-learning
  - forest-ecology
  - sentinel-2
status: read
---

# Wegler et al. 2025 — National Tree Species Map for Germany from Sentinel-1 and -2

## Title and Authors
**Tree species from space: a new product for Germany based on Sentinel-1 and -2 time series**
Marco Wegler, Patrick Kacic, Frank Thonfeld et al. — *International Journal of Remote Sensing*, 2025

## Quick Overview
- **Why is it relevant?** Produces the first national-scale 10 m tree species classification for Germany without relying on restricted NFI data, using an independently collected reference database — directly relevant as a benchmark for the wiki's national-scale species mapping context.
- **What was done?** Collected >80,000 reference samples from city tree registers, Google Earth Pro/Street View, and field observations; used spatio-temporal S2+S1+DEM composites to classify 10 dominant tree species groups across Germany at 10 m in 2022.
- **What is the main outcome?** S2+S1+DEM combination achieves highest F1=0.89; S2 alone gives nearly equivalent F1=0.86; primary species (pine, spruce, beech, oak) achieve F1=0.76–0.98.

## Main Goal and Fundamental Concept
Germany's current national tree species products rely on restricted NFI data (10-year update cycle, privacy protections). This study develops a reproducible, publicly accessible approach using alternative reference data sources and operational Sentinel data, enabling annual updates and temporal transferability — essential for monitoring climate-induced forest changes post-2018.

## Technical Approach
- **Reference data:** >80,000 dominant species samples from city tree registers, Google Earth Pro interpretation, Google Street View, field observations — no restricted NFI data
- **Features:** Spatio-temporal composites from Sentinel-2 + Sentinel-1 time series + Digital Elevation Model (DEM)
- **Species classes:** 10 dominant species groups (pine, spruce, beech, oak, birch, alder, larch, Douglas fir, fir, + other broadleaf)
- **Classifiers:** Multiple ML algorithms compared (Random Forest, XGBoost, SVM, kNN)
- **Scale:** National (all of Germany, ~350,000 km²), 10 m resolution, 2022
- **Accuracy:** F1-score per class; macro/weighted averages

## Distinctive Features
- Open, reproducible reference database not dependent on restricted governmental NFI data
- Tests both S2 alone and S2+S1+DEM combinations at national scale
- First German national product updating the prior 2011/2012 NFI-based classifications
- Explicitly designed for temporal transferability to enable multi-year mapping

## Experimental Setup and Results
- **Best model (S2+S1+DEM):** Weighted average F1 = 0.89
- **S2 alone:** F1 = 0.86 — minimal loss without SAR/DEM
- **Primary species F1:** Pine 0.94–0.98, Spruce 0.90–0.96, Beech 0.82–0.90, Oak 0.76–0.89
- **Other species:** Birch, alder, larch, Douglas fir, fir: F1 = 0.88–0.96
- S1 and DEM provide marginal but consistent improvements, especially for species with distinct structural signatures

## Advantages and Limitations
- **Advantages:** No restricted NFI data; 10 m resolution; national coverage; transferable across years; open reference approach
- **Limitations:** Reference data from multiple heterogeneous sources may introduce label noise; validation design and spatial autocorrelation need careful handling; training data quality varies by species

## Conclusion
National-scale tree species classification at 10 m for Germany is achievable without restricted NFI data using S2+S1+DEM composites and diverse open reference sources. S2 alone provides nearly equivalent accuracy, confirming optical multitemporal data as the primary driver. The approach is reproducible and temporally transferable, enabling monitoring of climate-induced species composition changes.

## Related pages
- [[sentinel_2]]
- [[tree_species_mapping]]
- [[national_forest_inventory]]
- [[forest_disturbances]]
- [[wegler_2026_canopy_cover_loss]]
