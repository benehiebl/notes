---
title: "Mapping tree species diversity in temperate montane forests using Sentinel-1 and Sentinel-2 imagery and topography data"
authors:
  - Liu, Xiang
  - Frey, Julian
  - Munteanu, Catalina
  - Still, Nicole
  - Koch, Barbara
year: 2023
source: liu_2023_mapping_tree_species_diversity
tags:
  - remote-sensing
  - machine-learning
  - forest-ecology
  - sentinel-2
status: read
---

# Liu et al. 2023 — Mapping Tree Species Diversity in Temperate Montane Forests with S1+S2+Topography

## Title and Authors
**Mapping tree species diversity in temperate montane forests using Sentinel-1 and Sentinel-2 imagery and topography data**
Xiang Liu, Julian Frey, Catalina Munteanu, Nicole Still, Barbara Koch — *Remote Sensing of Environment*, 2023

## Quick Overview
- **Why is it relevant?** Extends SVH-based TSD mapping to large-scale (~4000 km²) temperate montane forests using freely available Sentinel data combined with SAR and topography, addressing a methodological gap at operational scales.
- **What was done?** Developed a large-scale TSD mapping workflow comparing 24 prediction scenarios combining S1, S2 (STM and multi-temporal), and topographic data with six image heterogeneity metrics against in-situ species richness (S) and Shannon diversity (H').
- **What is the main outcome?** Best accuracy achieved with S1+S2+topography: R²=0.562 (S) and R²=0.628 (H'); texture metrics outperform all other heterogeneity metrics; altitudinal gradient strongly reduces TSD.

## Main Goal and Fundamental Concept
The Spectral Variability Hypothesis (SVH) posits that spectral heterogeneity in satellite imagery correlates with species diversity. This study is the first to apply SVH-based TSD mapping at landscape scale (~4000 km²) in temperate montane forest using multi-sensor Sentinel data, systematically comparing heterogeneity metrics, phenological information, and sensor combinations.

## Technical Approach
- **Study area:** ~4000 km² temperate montane forest, Germany/Austria
- **Sensors:** Sentinel-2 (STM, multi-temporal), Sentinel-1 (SAR), topographic data
- **Heterogeneity metrics:** Coefficient of Variation (CV), texture (GLCM), Rao's Q, Convex Hull Volume, Spectral Angle Mapper, Convex Hull Area
- **Target variables:** Species richness (S) and Shannon-Wiener diversity (H')
- **Modelling:** 24 prediction scenarios with different feature combinations → Random Forest regression
- **Validation:** In-situ TSD measurements from field plots

## Distinctive Features
- Explicitly tests whether phenological information (via STM and multi-temporal S2) improves TSD prediction
- Tests SAR (S1) as additional heterogeneity source beyond optical
- Comprehensive comparison of 6 image heterogeneity metrics at large scale
- Identifies altitudinal pattern as dominant spatial driver of TSD variation

## Experimental Setup and Results
- **Best model (S+S1+S2+topo):** R²=0.562 for S; R²=0.628 for H'
- **Texture metrics outperform** all other heterogeneity metrics (CV, Rao's Q, CHV, SAM, CHA)
- **EVI-derived heterogeneity** most effective among vegetation index choices
- **S1 adds value** over S2 alone; topography further improves both
- **Altitudinal gradient:** r=−0.61 (S), −0.45 (H') — strong decrease in diversity with elevation
- Multi-temporal and STM data both capture phenology and outperform single-date imagery

## Advantages and Limitations
- **Advantages:** Large-scale operational mapping; free Sentinel data; systematic metric comparison; maps show clear ecological patterns
- **Limitations:** SVH indirect approach cannot identify species; accuracy still moderate (R²~0.56); spectral variation confounded by intraspecific variation and stand structure

## Conclusion
Combining S1+S2+topography via SVH-based methods produces the most accurate large-scale TSD maps in temperate montane forest, with texture metrics as the best heterogeneity predictor. Phenological information from multi-temporal Sentinel data is important, and topography adds independent ecological signal. The strong altitudinal TSD gradient confirms that elevation is a key driver of forest biodiversity in montane systems.

## Related pages
- [[spectral_diversity_biodiversity]]
- [[sentinel_2]]
- [[topographic_microclimate]]
- [[tree_species_mapping]]
- [[functional_diversity]]
