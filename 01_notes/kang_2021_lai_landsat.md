---
title: "A data-driven approach to estimate leaf area index for Landsat images over the contiguous US"
authors:
  - Kang, Yanghui
  - Ozdogan, Mutlu
  - Gao, Feng
  - Anderson, Martha C.
  - White, William A.
  - Yang, Yun
  - Erickson, Tyler A.
year: 2021
source: kang_2021_lai_landsat
tags:
  - remote-sensing
  - machine-learning
status: read
---

# Kang et al. 2021 — Data-Driven LAI Estimation from Landsat for the Contiguous US

## Title and Authors
**A data-driven approach to estimate leaf area index for Landsat images over the contiguous US**
Yanghui Kang, Mutlu Ozdogan, Feng Gao et al. — *Remote Sensing of Environment*, 2021

## Quick Overview
- **Why is it relevant?** Provides a validated, large-scale 30 m LAI product derived from Landsat, which is a key input for vegetation monitoring, carbon flux modelling, and phenology studies.
- **What was done?** Trained biome-specific Random Forest models using 1.6 million spatially homogeneous MODIS LAI/Landsat sample pairs (2006–2018) to estimate LAI at 30 m resolution for CONUS, implemented on Google Earth Engine.
- **What is the main outcome?** Overall RMSE = 0.8, r² = 0.88 across 19 NEON sites; the approach successfully extends MODIS LAI spatial detail to Landsat resolution while maintaining consistency with MODIS products.

## Main Goal and Fundamental Concept
Leaf Area Index (LAI) is fundamental for modelling vegetation-atmosphere interactions, but MODIS LAI products are limited to 250–1000 m resolution. The goal is to leverage MODIS LAI as a training source to produce 30 m LAI from Landsat, maintaining cross-scale consistency for multi-scale modelling applications (e.g., ET estimation via DisALEXI).

## Technical Approach
- **Training data:** 1.6 million spatially homogeneous MODIS LAI/Landsat sample pairs extracted using a homogeneity criterion (ensures MODIS pixel is not mixed at Landsat scale)
- **Model:** Biome-specific Random Forest (8 biomes from NLCD)
- **Sample balance:** Equal representation of saturated (LAI > 4) and unsaturated MODIS LAI to prevent underestimation in dense canopies
- **Noise detection:** Machine-learning-based technique to flag low-quality training samples
- **Platform:** Google Earth Engine for large-scale implementation
- **Validation:** 19 NEON sites + 8 independent sites spanning forests, grasslands, shrublands, croplands

## Distinctive Features
- Data fusion approach: uses MODIS LAI as reference rather than in-situ measurements, enabling CONUS-wide coverage
- Addresses MODIS LAI saturation explicitly via balanced sampling strategy
- Produces Landsat LAI back to the 1980s, creating long-term 30 m LAI records
- Open-source code on GitHub for reuse and extension

## Experimental Setup and Results
- **NEON sites RMSE:** 0.8; r² = 0.88
- **Independent site RMSE:** 0.52–0.91 across diverse biomes
- **Long-term record:** LAI from 1980s using historical Landsat archive
- **Biome variation:** Uncertainty varies by biome; croplands and shrublands show higher RMSE than forests

## Advantages and Limitations
- **Advantages:** No field LAI required for training; cross-scale consistency with MODIS; 30 m resolution resolves heterogeneity important for agriculture/hydrology; GEE implementation enables scalability
- **Limitations:** Inherited MODIS LAI uncertainty; saturation issues in very dense canopies not fully resolved; Random Forest may not extrapolate well to under-represented vegetation types

## Conclusion
A MODIS-consistent 30 m Landsat LAI product is achievable at continental scale using data-fusion-based Random Forest models. The approach succeeds in extending moderate-resolution LAI into fine-scale mapping while preserving consistency for multi-scale land surface modelling. Balanced sampling for MODIS saturation is critical for accurate high-LAI estimation.

## Related pages
- [[landsat]]
- [[sentinel_2]]
- [[ndvi]]
- [[phenology]]
