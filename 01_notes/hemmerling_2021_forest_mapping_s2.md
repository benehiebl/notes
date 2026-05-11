---
title: "Mapping temperate forest tree species using dense Sentinel-2 time series"
authors:
  - Hemmerling, Jan
  - Pflugmacher, Dirk
  - Hostert, Patrick
year: 2021
source: hemmerling_2021_forest_mapping_s2
tags:
  - remote-sensing
  - machine-learning
  - forest-ecology
  - sentinel-2
status: read
---

# Hemmerling et al. 2021 — Mapping Temperate Forest Tree Species with Dense Sentinel-2 Time Series

## Title and Authors
**Mapping temperate forest tree species using dense Sentinel-2 time series**
Jan Hemmerling, Dirk Pflugmacher, Patrick Hostert — *Remote Sensing of Environment*, 2021

## Quick Overview
- **Why is it relevant?** Demonstrates the power of dense Sentinel-2 time series for large-area tree species mapping, extending from single-image to full-phenology spectral-temporal characterisation.
- **What was done?** Applied Sentinel-2A/B time series (2017–2018) with a radial basis convolution filter ensemble to produce gap-free 5-day composites, then classified 17 tree species in Brandenburg, Germany using Random Forest.
- **What is the main outcome?** Nine main species (>0.5% area) were mapped with accuracies ranging from 98.9% to 66.8%; adding environmental and texture features only marginally improved minor species; spectral time series is the primary explanatory source.

## Main Goal and Fundamental Concept
The study tests whether dense Sentinel-2 time series — exploiting the full phenological cycle — can map a diverse portfolio of temperate tree species at regional scale, and whether adding environmental covariates and texture metrics improves accuracy beyond the spectral signal alone.

## Technical Approach
- **Time series construction:** All available S-2A/B observations, gap-filled via radial basis convolution filter ensemble → 5-day gap-free time series per spectral band
- **Features:** Spectral time series features + environmental data (climate, soil) + image texture metrics (GLCM)
- **Classifier:** Random Forest
- **Reference data:** Stand-wise forest inventory data for single-species stands, Brandenburg federal state
- **Classes:** 17 tree species (9 main with >0.5% area, 8 minor)

## Distinctive Features
- Uses all available cloud-free Sentinel-2 observations (not just composites) for maximum temporal density
- Explicit comparison of three feature sets: spectral-only, spectral + environmental, spectral + texture
- Addresses class imbalance and minority species mapping challenges explicitly
- Study area spans the full federal state of Brandenburg (~30,000 km²)

## Experimental Setup and Results
- **Main species accuracy:** 98.9% (best, likely pine) to 66.8% (most challenging species)
- **Minor species (<0.5% area):** Strongly affected by classification errors; absolute area correlates with reference but relative errors are high
- **Environmental features:** Only marginal improvement for few minor species
- **Texture metrics:** No consistent improvement when added to dense spectral time series
- **Conclusion:** Spectral time series is dominant source; contextual/environmental features provide diminishing returns when temporal density is high

## Advantages and Limitations
- **Advantages:** Regional scale mapping; dense time series captures full phenology; rigorous feature comparison; open data (Sentinel-2)
- **Limitations:** Class imbalance for rare species; single-year mapping may not generalise across years; stand-level inventory reference limits pixel-level accuracy assessment; vegetation shadow and mixed pixels are not addressed

## Conclusion
Dense Sentinel-2 time series is the primary and dominant explanatory source for temperate tree species mapping. Environmental variables and texture metrics offer only marginal gains. Minor species (< 0.5% area) remain challenging due to statistical limitations (sample size, class variance, imbalance). This confirms that maximising temporal resolution and coverage is the most impactful lever for species classification improvement.

## Related pages
- [[sentinel_2]]
- [[tree_species_mapping]]
- [[phenology]]
- [[spectral_diversity_biodiversity]]
