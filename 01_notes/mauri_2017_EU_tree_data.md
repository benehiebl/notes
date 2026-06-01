---
title: "EU-Forest, a high-resolution tree occurrence dataset for Europe"
authors:
  - Achille Mauri
  - Giovanni Strona
  - Jesús San-Miguel-Ayanz
year: 2017
tags:
  - forest-ecology
  - remote-sensing
keywords:
  - EU-Forest
  - tree occurrence
  - National Forest Inventories
  - European forest data
  - species distribution
  - INSPIRE grid
  - 1 km resolution
  - biodiversity
  - ground truth
status: read
---

## 1. Title and Authors

**EU-Forest, a high-resolution tree occurrence dataset for Europe**
Mauri et al. (2017), *Scientific Data* 4:160123. DOI: 10.1038/sdata.2016.123

## 2. Quick Overview

- **Why is it relevant?** EU-Forest is the primary European-scale ground truth dataset for tree species distribution, used directly in multiple SDM and RS studies (including [[wessely_2023_tree_species_bottleneck]] and [[miettinen_2025_forest_maps_europe]]).
- **What was done?** Harmonised tree occurrence data from 21 European NFIs + Forest Focus + Biosoil into a single 1 km × 1 km INSPIRE-compliant grid, covering 249,410 plots and 242 species.
- **What is the main outcome?** The dataset (EU-Forest) contains 588,983 species-level occurrences at 1 km² resolution across 30 European countries — the largest open European tree occurrence database at the time of publication.

## 3. Main Goal and Fundamental Concept

The JRC (Joint Research Centre) sought to make NFI-based tree occurrence data publicly available and interoperable across European countries. The core idea is that national monitoring programmes individually contain invaluable high-quality data, but their restricted access, heterogeneous protocols, and different spatial resolutions prevent continental-scale science. Harmonising to a 1 km INSPIRE grid provides a common currency while satisfying national privacy rules.

## 4. Technical Approach

- **Source integration**: Three inputs merged:
  1. **NFI dataset**: 21 countries, framework contract with JRC; ~96% of records (249,410 plots, 242 species)
  2. **Forest Focus**: EU monitoring network (23 genera, 47 species); fills geographic gaps
  3. **Biosoil**: Biodiversity sub-project (57 genera, 187 species)
- **Harmonisation**: Common species nomenclature (~200 species); TNRS v4.0 for taxonomic validation
- **Spatial aggregation**: All records attributed to INSPIRE 1km² grid centroids; upscaling necessary for legal privacy reasons (plot locations cannot be published exactly)
- **Validation**: Biogeographical consistency checked via network analysis (Infomap Bioregions); alpha-shape EOOs computed per species to flag outliers
- **Output**: Two CSV datasets (species and genus level), plus 242 individual species shapefiles and 203 EOO polygon shapefiles; published on figshare

## 5. Distinctive Features

- **Scale**: First dataset to integrate NFIs from 21 countries at 1 km resolution — an order of magnitude more occurrence records than previously available public datasets (Atlas Florae Europeae at ~50 km resolution)
- **DBH class field**: Provides diameter-at-breast-height class (≥120 mm threshold) allowing rough size/age stratification
- **Open access**: Critical for enabling downstream SDMs, RS validation, pest modelling
- **Biogeographical validation**: Identified three distinct Mediterranean biogeographical regions (Iberia, Italy, Cyprus) consistent with independent analyses

## 6. Experimental Setup and Results

| Dataset | Countries | Plots | Species |
|---------|-----------|-------|---------|
| NFI dataset | 21 | 248,776 | 242 |
| Forest Focus | EU-wide | 8,564 | 47 |
| Biosoil | EU-wide | 3,367 | 187 |
| **EU-Forest total** | **30** | **249,410** | **242** |

- Spain alone contributes 74,411 plots and 130 species — by far the largest national contribution
- Finland (24,649 plots), France (31,925), Germany (18,903) are major contributors
- Italy contributes 6,810 plots and 128 species

## 7. Advantages and Limitations

**Strengths**
- Largest open-access European tree occurrence dataset; de facto standard for continental SDMs
- 1 km resolution is compatible with most climate and RS data products
- Taxonomically comprehensive (242 species)

**Critical Limitations**
- **1 km aggregation hides within-cell variability**: Multiple species at sub-km scales are collapsed; irreversible information loss
- **Privacy-forced upscaling**: Original plot locations not shared; EOO alpha-shapes are approximate
- **Non-uniform sampling density**: Spain (74k plots) vs Bulgaria (220 plots) — strong national imbalance persists
- **No quantitative abundance**: Only presence/absence (DBH class, not basal area or volume)
- **Mixed planted/natural occurrences**: No flag distinguishing natural from planted stands; relevant for climate niche interpretation
- **Static snapshot**: Surveys collected at different dates (no standardised survey year); climate-matching is approximate
- **Geographic gaps**: Poland, Croatia, Slovenia, Greece, Bulgaria, Cyprus, Belarus, Moldova have partial/no NFI contribution

## 8. Conclusion

EU-Forest is the foundational European tree occurrence dataset and a critical dependency for continental-scale SDMs and RS validation studies. Its 1 km INSPIRE grid, 242 species, and open CC4.0 license make it widely used. However, the dataset is a static, presence-only, non-abundance snapshot with substantial national imbalances and privacy-mandated spatial imprecision. Users building SDMs (e.g., [[wessely_2023_tree_species_bottleneck]]) or calibrating RS maps should be aware that "occurrence" does not equal "dominant" or "natural", and that the 1 km resolution conceals species co-occurrence patterns at sub-km scales.

## Related Pages

- [[national_forest_inventory]]
- [[species_distribution_models]]
- [[tree_species_mapping]]
- [[wessely_2023_tree_species_bottleneck]]
- [[miettinen_2025_forest_maps_europe]]
- [[european_ground_truth_databases]]
