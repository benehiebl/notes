---
title: "National tree species mapping using Sentinel-1/2 time series and German National Forest Inventory data"
authors:
  - Blickensdörfer, Lukas
  - Oehmichen, Katja
  - Pflugmacher, Dirk
  - Kleinschmit, Birgit
  - Hostert, Patrick
year: 2024
source: blickensdörfer_2024_tree_species
tags:
  - remote-sensing
  - machine-learning
keywords:
  - tree species mapping
  - Sentinel-2
  - Sentinel-1
  - National Forest Inventory
  - mixed forests
  - pseudo-labelling
  - Germany
status: read
---

# Blickensdörfer et al. 2024 — National Tree Species Mapping in Germany with Sentinel-1/2 + NFI

## Title and Authors
**National tree species mapping using Sentinel-1/2 time series and German National Forest Inventory data**
Lukas Blickensdörfer, Katja Oehmichen, Dirk Pflugmacher, Birgit Kleinschmit, Patrick Hostert — *Remote Sensing of Environment* 304: 114069 (2024).

## Quick Overview
- **Why is it relevant?** National-scale tree species mapping with NFI training data via pixel–plot linking and mixed-stand pseudo-labelling — directly informs the methodological choices for Italian forest mapping using INFC plots.
- **What was done?** Combined dense S2 (5-day RBF-interpolated) + monthly S1 backscatter + topography/meteorology covariates, with German NFI variable-radius plots as training/validation source; assessed pure vs mixed stand performance.
- **What is the main outcome?** Pure-stand F1 = 72–97% for five dominant species; including mixed stands reduces accuracy by 4–14 pp — mixed-stand validation is essential; pseudo-labelling extends NFI training data beyond pure plots.

## Main Goal and Fundamental Concept
NFI data are the gold-standard ground reference for tree species across Europe but have two problems for pixel-level RS: (1) plots are variable-radius rather than fixed-pixel, so linking to satellite pixels is non-trivial; (2) most plots are mixed-species, so excluding them biases training and assessing only pure stands overestimates accuracy. Blickensdörfer et al. solve both problems and produce the first national German tree species map from S1/S2 + NFI.

## Technical Approach
- Study area: Germany, 357,581 km², 32% forest.
- **S2 time series**: all bands (visual/red-edge/NIR/SWIR) + NDVI, March–November 2017 + 2018; FORCE preprocessing; 5-day RBF-interpolated time series with σ ∈ {5,7,10,20,30}.
- **S1 time series**: monthly VV/VH backscatter composites + Radar Vegetation Index + cross-ratio; 2017–2018; winter scenes included.
- **Environmental covariates**: topography (elevation, slope, aspect), climate (monthly T, P), continentality index.
- **NFI training**: variable-radius plots → pixel-plot linking by species count proportions; pseudo-labelling for mixed plots using neighbourhood matching.
- Classifier: random forest, 500 trees.
- Five dominant species classes: spruce, pine, beech, oak, Douglas fir; less frequent species grouped.
- Accuracy: pure-stand F1 + mixed-stand accuracy stratification.

## Distinctive Features
- **Mixed-stand pseudo-labelling**: uses NFI species occurrence per plot to constrain pseudo-label confidence; pixels with neighbourhood-consistent labels promoted to training.
- **Variable-radius plot handling**: links each pixel to NFI plot only if pixel proportion of dominant species exceeds threshold.
- **Pure vs mixed validation stratification**: explicit comparison shows how accuracy degrades from clean test cases to realistic mixed forests.
- National scale with explicit environmental gradient handling.

## Experimental Setup and Results

**Pure-stand classification accuracy (F1 score)**
- Spruce (Picea): 97%
- Pine (Pinus): 95%
- Beech (Fagus): 88%
- Oak (Quercus): 79%
- Douglas fir: 72%
- Less frequent species (larch, fir, other broadleaves): lower, more variable

**Mixed-stand validation**
- Accuracy decreased by 4–14 pp for dominant species when mixed plots included
- Boundary effects + canopy mixing degrade pixel-level performance
- Importance: pure-stand accuracy systematically overestimates real map accuracy

**Pseudo-labelling effect**
- Training set extended beyond pure-species plots → better coverage of environmental gradient
- Confidence-constrained pseudo-labels avoided propagating errors

**Sentinel-1 contribution**
- Winter composites add structural information; complementary to leaf-on phenology
- Particularly helpful in cloudy regions where S2 gaps are wide

## Advantages and Limitations
- **Advantages**: Full national coverage; rigorous NFI-pixel linking; mixed-stand validation; freely available code via FORCE.
- **Limitations**: Reliant on availability of geolocated NFI plot data (not always politically accessible — cf. [[wegler_2025_tree_species_germany]] using restricted data); 10 m resolution may still mix species at boundaries; less frequent species poorly mapped; 2017–2018 only.

## Conclusion
**S1/S2 time series + NFI plot data + pseudo-labelling produce nationally consistent tree species maps**, but only if mixed-stand validation is performed honestly — pure-stand accuracies overestimate real map quality by 4–14 pp. Method generalises to other European countries with plot-based NFIs and is the closest precedent for INFC-based Italian mapping in the wiki.

## Related pages
- [[tree_species_mapping]]
- [[sentinel_2]]
- [[national_forest_inventory]]
- [[hemmerling_2021_forest_mapping_s2]]
- [[grabska_2024_tree_species_map]]
- [[wegler_2025_tree_species_germany]]
- [[deluca_2022_s1_s2_lulc_mapping]]
- [[kollert_2021_tree_species]]
- [[pflugmacher_2019_lulc_landsat]]
