---
title: Map of forest tree species for Poland based on Sentinel-2 data
authors:
  - Grabska-Szwagrzyk, Ewa
  - Tiede, Dirk
  - Sudmanns, Martin
  - Kozak, Jacek
year: 2024
source: grabska_2024_tree_species_map
tags:
  - remote-sensing
  - tree-species-mapping
  - sentinel-2
  - random-forest
  - time-series
  - forest-ecology
  - Poland
keywords:
  - spectral-temporal-metrics
  - STM
  - seasonal-composites
  - Google-Earth-Engine
  - multi-annual
  - class-imbalance
  - forest-data-bank
  - phenology
  - national-scale-mapping
  - accuracy-assessment
status: summarized
---

## Title and Authors of the Paper

*Map of forest tree species for Poland based on Sentinel-2 data* — Ewa Grabska-Szwagrzyk, Dirk Tiede, Martin Sudmanns, and Jacek Kozak (2024), Earth System Science Data, 16, 2877–2891. Open Access. Data: https://doi.org/10.5281/zenodo.10180469

## Quick Overview

- **Why is it relevant?** National-scale tree species maps from satellite data are urgently needed for forest management, biodiversity monitoring, and carbon accounting, yet large-area mapping at species level remains challenging due to class imbalance, observation gaps, and environmental heterogeneity.
- **What was done?** Short-period seasonal Spectral-Temporal Metrics (STMs) from multi-annual Sentinel-2 observations (2018–2021) were combined with environmental variables and a Random Forest classifier in Google Earth Engine to map 16 tree species/genera across all of Poland.
- **What is the main outcome?** The first national-scale forest tree species map for Poland was produced, achieving overall accuracy >80%, with the best results for dominant species (pine F1 ≈ 95%) and poorer performance for rare or spectrally similar broadleaved species.

## Main Goal and Fundamental Concept

The paper aims to produce a wall-to-wall forest tree species map for Poland — a country with ~9.5 million hectares of forest (~30% of territory) — using freely available Sentinel-2 time series data. The key methodological advance is the use of **short-period multi-annual STMs** instead of single-year full-season composites. Computing seasonal averages over short, phenologically meaningful windows (15–30 days) from multiple years reduces cloud contamination and inter-annual variability, while retaining species-discriminating phenological signals (green-up, full leaf, senescence).

## Technical Approach

**Predictor construction:**
- Sentinel-2 L2A harmonized collection (GEE: `COPERNICUS/S2_SR_HARMONIZED`), cloud masked using Sentinel-2 cloud probability dataset (<40% cloud cover)
- 4 seasonal STMs (mean reflectance over multi-annual observations 2018–2021):
  1. Early spring (late April – early May): captures species-specific green-up differences
  2. Late spring (mid-May – early June): full leaf expansion
  3. Summer (June – July): stable phenological plateau; also used for NDVI threshold
  4. Autumn (October – November): leaf senescence/colouring
- 10 bands per STM: Blue, Green, Red, RE1, RE2, RE3, NIR1, NIR2, SWIR1, SWIR2 → 40 spectral features total
- Environmental variables: elevation (SRTM 30 m), WorldClim bioclimate (bio01 mean annual temp, bio12 precipitation, bio17 driest quarter precipitation), TerraClimate max temp 2018, soils (OpenLandMap)

**Forest mask:**
- Combined ESA WorldCover 2021 (tree cover only) + Dynamic World (tree probability >0.6, summer 2021 mean) + NDVI >0.6 (from summer STM)
- Two datasets used together because WorldCover overestimates forest in some areas; Dynamic World can be noisy

**Reference data:**
- Polish Forest Data Bank (FDB): management units with species share values (1–10 scale)
- Pure stands ≥90% species share selected; 60–80% threshold for rare species
- Automated and visual validation against very-high-resolution orthoimagery
- 4500 final polygons → 2999 training + 1501 test; ~400,000 training pixels

**Classification:**
- Image segmentation using SNIC algorithm in GEE before intersecting with FDB stands
- Random Forest (200 trees), 10-fold cross-validation
- Two sampling strategies to address class imbalance (pine dominates at ~59%):
  1. **Proportional**: sample size proportional to species area estimate
  2. **Disproportional**: oversample rare species, undersample pine; total ~20,000 pixels per class

**Accuracy assessment:**
- Area-adjusted confusion matrices (producer's accuracy, user's accuracy, F1, OA)
- Stratified random sampling following Olofsson et al. (2014) recommendations
- Separate analysis for overlapping vs non-overlapping Sentinel-2 orbit areas

## Distinctive Features

- **Short-period multi-annual STMs**: using 15–30 day seasonal windows computed across 4 years rather than single-year composites substantially reduces missing data from cloud cover and captures phenological timing more precisely
- **National scale in GEE**: the first national-scale species map for Poland; demonstrates feasibility of country-wide Sentinel-2 species mapping on cloud infrastructure
- **Dual sampling strategy**: explicit comparison of proportional vs disproportional sample allocation quantifies the trade-off between overall accuracy and minority-class performance
- **Open data**: map and training/test data freely available; can be explored online

## Experimental Setup and Results

**Target classes** (16 species/genera):
Pine (*Pinus* spp.), Oak (*Quercus* spp.), Beech, Alder, Birch, Larch, Spruce, Fir, Hornbeam, Poplar, Ash, Maple, Lime, Douglas fir, Black locust, Dwarf mountain pine

**Accuracy results:**
- 10-fold CV OA: 83.3% average (range 79.3–84.9%)
- Test set OA: 89.6% (proportional); 84% (disproportional)
- Overlapping orbits: 90.1% OA; non-overlapping: 86.7%
- High F1 species (>80%): Pine (~95%), Dwarf mountain pine, Beech, Spruce, Alder, Fir, Oak, Larch, Birch, Black locust
- Low F1 species (<60%): Poplar, Douglas fir, Maple, Lime, Hornbeam, Ash
- Common confusions: ash/lime/hornbeam ↔ oak/beech; Douglas fir ↔ pine; young stands misclassified as other broadleaves

**Forest composition map results:**
- Pine: 47.5% (underestimated vs official 58.5% — partly due to confusion with spruce and disturbance)
- Birch: 11.7%, Alder: 9%, Beech: 8.1%, Oak: 7.2%, Spruce: 3.6%, Fir: 3.7%

**Variable importance:**
- Top predictors: maximum temperature (autumn), elevation, VISR and NIR autumn bands, bioclimate variables (bio01, bio12)
- Autumn bands ranked highest phenologically, followed by early spring
- Soil variables had notably lower importance than in some previous studies

## Advantages and Limitations

**Advantages:**
- Short-period multi-annual STMs are more robust to cloud gaps and inter-annual variability than single-year composites
- National coverage in a single seamless workflow using GEE
- Environmental variables (especially temperature and elevation) substantially improve accuracy beyond spectral features alone
- Freely accessible map and data enable replication and further research

**Limitations:**
- Severe class imbalance (pine ~59%) degrades performance for minority classes
- Rare species lack sufficient reference polygons in FDB; private forests not represented
- Observation frequency differs between overlapping/non-overlapping orbit areas → accuracy varies spatially
- Spectrally similar broadleaved species (ash, hornbeam, lime, maple) are mutually confused; more phenological detail (e.g., early/late autumn STMs) could help but is limited by cloud cover
- Optimal seasonal windows vary regionally and inter-annually due to phenological gradients
- Young stands have spectrally different signatures from mature stands of the same species

## Conclusion

Grabska-Szwagrzyk et al. (2024) demonstrate that short-period seasonal Spectral-Temporal Metrics from multi-annual Sentinel-2 data can achieve >80% accuracy for national-scale tree species mapping. The approach is computationally feasible in GEE, is transferable to other countries with forest inventory reference data, and explicitly addresses the twin challenges of cloud cover (through multi-annual aggregation) and class imbalance (through dual sampling strategies). The resulting open-access Poland tree species map is a benchmark for national-scale Sentinel-2 species mapping in temperate Europe and illustrates the remaining hard problems: rare species, spectrally similar broadleaves, and spatially variable observation density.

## Related Work & Obsidian Links

- [[sentinel_2]]
- [[tree_species_mapping]]
- [[phenology]]
- [[sampling_bias_remote_sensing]]

**Cross-paper links (same vault):**
- [[01_notes/koch_2025_intraspecies_variation_s2]] — both use Sentinel-2 for species-level forest discrimination; Koch et al. focus on intraspecific spectral variation which is a key source of confusion in Grabska et al.'s classification
- [[01_notes/chabalala_2023_dl_s2_mediterranean_fruit_trees]] — both perform species-level classification with Sentinel-2 time series; different classifiers (RF vs DNN) and ecosystem contexts
- [[01_notes/deluca_2022_s1_s2_lulc_mapping]] — both use Sentinel time series with GEE for vegetation classification; DeLuca et al. add Sentinel-1 SAR for LULC distinction
- [[01_notes/bayle_2024_landsat_greening_inflated]] — Grabska et al. also show that observation frequency (overlapping vs non-overlapping orbits) affects accuracy, paralleling Bayle et al.'s sampling bias argument for Landsat
