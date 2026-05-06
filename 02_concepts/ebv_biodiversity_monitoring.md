---
name: ebv_biodiversity_monitoring
description: Essential Biodiversity Variables (EBVs) — standardised monitoring framework; RS contributions to ecosystem structure, phenology, and community composition
type: reference
tags:
  - forest-ecology
  - remote-sensing
---

# Essential Biodiversity Variables and Remote Sensing

**Summary**: Essential Biodiversity Variables (EBVs) are a standardised framework for harmonising global biodiversity monitoring — remote sensing contributes substantially to 4+ EBV classes, particularly ecosystem structure, phenology, and community composition.

**Sources**: [[vihervaara_2017_ebv_remote_sensing]], [[spectral_diversity_biodiversity]], [[liu_2023_mapping_tree_species_diversity]]

**Last updated**: 2026-05-06

---

## EBV Framework

GEO BON (Group on Earth Observations Biodiversity Observation Network) proposed 22 candidate EBVs to harmonise global biodiversity monitoring (source: [[vihervaara_2017_ebv_remote_sensing]]):

**Six top-level EBV classes:**
1. Genetic composition
2. Species populations
3. Species traits
4. Community composition
5. Ecosystem structure
6. Ecosystem function

EBVs aim to provide a small but comprehensive set of monitoring variables balancing information content with measurement feasibility across scales.

## EBVs Measurable via Remote Sensing

Four EBV classes where RS can contribute substantially (source: [[vihervaara_2017_ebv_remote_sensing]]):

| EBV class | RS contribution | Data sources |
|-----------|----------------|--------------|
| **Ecosystem extent/distribution** | Land cover change detection, forest mapping | Sentinel-2, Landsat, SAR |
| **Ecosystem structure** | Canopy height, cover, LAI, biomass | LiDAR (GEDI, ALS), Sentinel-2, SAR |
| **Phenology** | Seasonal timing of green-up/senescence, SOS, EOS | NDVI/EVI time series, Sentinel-2 |
| **Community composition** | Species diversity indices via SVH; forest type mapping | Sentinel-2 spectral heterogeneity |

## Spectral Diversity as Proxy for Community Composition EBV

The Spectral Variability Hypothesis (SVH) links RS-measurable spectral heterogeneity to species diversity:
- Spectral heterogeneity metrics (Rao's Q, texture) predict species richness and Shannon diversity
- Best results at ~10 m resolution with multi-temporal Sentinel-2 data (source: [[liu_2023_mapping_tree_species_diversity]])
- This approach enables EBV monitoring without species-level classification labels
- See [[spectral_diversity_biodiversity]] for detailed treatment

## National Monitoring Integration

Finland case study — one of the most advanced biodiversity monitoring systems globally (source: [[vihervaara_2017_ebv_remote_sensing]]):
- 44 existing national indicators assessed against 22 EBV candidates
- Gaps identified in community composition, ecosystem function EBVs
- Existing RS applications (shore habitat mapping, water quality) already contribute to some EBVs
- Budget constraints in national monitoring make RS expansion the most feasible path to gap-filling
- New EBV candidates proposed: ecosystem functional types, primary productivity, spectral diversity

## EBVs and Forest Monitoring

Forest RS contributes to multiple EBV classes simultaneously:
- **Forest extent + structure** (Ecosystem structure): Sentinel-2 + lidar canopy height, cover fraction, biomass — see [[turubanove_2023_canopy_landsat]]
- **Phenology** (Species traits): Vegetation index time series for green-up/senescence timing
- **Species composition** (Community composition): Tree species mapping via classification or SVH-based approaches
- **Disturbance dynamics** (Ecosystem function): Disturbance frequency, severity, recovery rate from RS time series

## Policy Context

EBVs connect to:
- **Convention on Biological Diversity (CBD):** Aichi Biodiversity Targets (2010–2020); Kunming-Montreal Global Biodiversity Framework (post-2020)
- **EU Green Deal + Biodiversity Strategy 2030:** Restoration targets requiring monitoring
- **LULUCF carbon accounting:** Forest area + biomass monitoring
- **Copernicus Land Monitoring Service:** Provides operational RS products contributing to EBV monitoring

## Related pages

- [[spectral_diversity_biodiversity]]
- [[functional_diversity]]
- [[national_forest_inventory]]
- [[phenology]]
- [[tree_species_mapping]]
- [[sentinel_2]]
