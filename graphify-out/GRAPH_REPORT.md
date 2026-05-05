# Graph Report - 02_concepts  (2026-05-05)

## Corpus Check
- Corpus is ~15,103 words - fits in a single context window. You may not need a graph.

## Summary
- 47 nodes · 128 edges · 11 communities
- Extraction: 94% EXTRACTED · 6% INFERRED · 0% AMBIGUOUS · INFERRED: 8 edges (avg confidence: 0.82)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- [[_COMMUNITY_Sentinel-2 Tree Mapping|Sentinel-2 Tree Mapping]]
- [[_COMMUNITY_Forest Inventory & Cartography|Forest Inventory & Cartography]]
- [[_COMMUNITY_Landsat Trends & Bias|Landsat Trends & Bias]]
- [[_COMMUNITY_Species Distribution Models|Species Distribution Models]]
- [[_COMMUNITY_Spectral & Functional Diversity|Spectral & Functional Diversity]]
- [[_COMMUNITY_Forest Disturbances|Forest Disturbances]]
- [[_COMMUNITY_Plant Traits & Microclimate|Plant Traits & Microclimate]]
- [[_COMMUNITY_Deep Learning & Transfer|Deep Learning & Transfer]]
- [[_COMMUNITY_Landsat Land Cover|Landsat Land Cover]]
- [[_COMMUNITY_Vegetation Community Change|Vegetation Community Change]]
- [[_COMMUNITY_Neural Network Foundations|Neural Network Foundations]]

## God Nodes (most connected - your core abstractions)
1. `Sentinel-2` - 16 edges
2. `Phenology` - 15 edges
3. `Tree Species Mapping` - 14 edges
4. `Species Distribution Models` - 13 edges
5. `Vegetation Community Change` - 13 edges
6. `NDVI` - 13 edges
7. `Landsat` - 12 edges
8. `Functional Diversity` - 12 edges
9. `Leaf Habit and Latitudinal Gradient` - 10 edges
10. `Transfer Learning in Remote Sensing` - 10 edges

## Surprising Connections (you probably didn't know these)
- `Vegetation Greenness Trends` --cites--> `midolo_2026_denser_vegetation`  [EXTRACTED]
  02_concepts/vegetation_greenness_trends.md → 01_notes/midolo_2026_denser_vegetation.md
- `Landsat` --cites--> `bell_2024_hindcasting_forest_structure`  [EXTRACTED]
  02_concepts/landsat.md → 01_notes/bell_2024_hindcasting_forest_structure.md
- `Tree Species Mapping` --cites--> `sylvain_2024_tree_species_uncertainty`  [EXTRACTED]
  02_concepts/tree_species_mapping.md → 01_notes/sylvain_2024_tree_species_uncertainty.md
- `NDVI` --cites--> `chastain_2007_eve_landsat_understory`  [EXTRACTED]
  02_concepts/ndvi.md → 01_notes/chastain_2007_eve_landsat_understory.md
- `Sentinel-2` --cites--> `miettinen_2025_forest_maps_europe`  [EXTRACTED]
  02_concepts/sentinel_2.md → 01_notes/miettinen_2025_forest_maps_europe.md

## Hyperedges (group relationships)
- **Landsat Trend Artefact Analysis** — landsat, ndvi, sampling_bias_remote_sensing, vegetation_greenness_trends, phenology [INFERRED 0.95]
- **Biodiversity Remote Sensing** — spectral_diversity_biodiversity, functional_diversity, plant_functional_traits, tree_species_mapping, leaf_habit_latitudinal_gradient [INFERRED 0.85]
- **Deep Learning for Remote Sensing** — transfer_learning_remote_sensing, neural_network_training, tree_species_mapping, sentinel_2, national_forest_inventory [INFERRED 0.85]
- **Forest Ecology and Vegetation Change** — vegetation_community_change, forest_disturbances, vegetation_greenness_trends, topographic_microclimate, species_distribution_models [INFERRED 0.85]
- **Species and Habitat Modelling** — species_distribution_models, tree_species_mapping, national_forest_inventory, leaf_habit_latitudinal_gradient, topographic_microclimate [INFERRED 0.75]

## Communities (11 total, 0 thin omitted)

### Community 0 - "Sentinel-2 Tree Mapping"
Cohesion: 0.43
Nodes (7): chabalala_2023_dl_s2_mediterranean_fruit_trees, deluca_2022_s1_s2_lulc_mapping, fischer_2025_glocal_canopy_atlas, grabska_2024_tree_species_map, koch_2025_intraspecies_variation_s2, Sentinel-2, Tree Species Mapping

### Community 1 - "Forest Inventory & Cartography"
Cohesion: 0.33
Nodes (6): amico_2025_nfi_italy, bell_2024_hindcasting_forest_structure, gasparini_2022_nfi_italy, mattioli_2025_carta_forestale, miettinen_2025_forest_maps_europe, National Forest Inventory

### Community 2 - "Landsat Trends & Bias"
Cohesion: 1.0
Nodes (5): bayle_2024_landsat_greening_inflated, NDVI, Phenology, Sampling Bias in Remote Sensing, Vegetation Greenness Trends

### Community 3 - "Species Distribution Models"
Cohesion: 0.5
Nodes (4): fady_2025_native_trees_mediterranean, he_2015_remote_sensing_sdm, noce_2023_altitude_shift_tree_italy, Species Distribution Models

### Community 4 - "Spectral & Functional Diversity"
Cohesion: 0.83
Nodes (4): bricca_2026_topo_diversity, Functional Diversity, liu_2023_spectral_spatial_resolution_effect, Spectral Diversity and Biodiversity

### Community 5 - "Forest Disturbances"
Cohesion: 0.5
Nodes (4): albrich_2019_climate_change_mountain_forests, Forest Disturbances, francioni_2026_canopy_closure, grünig_2026_climate_change_disturbances_forest

### Community 6 - "Plant Traits & Microclimate"
Cohesion: 0.83
Nodes (4): jin_2023_drivers_differentiation_evergreen, Leaf Habit and Latitudinal Gradient, Plant Functional Traits, Topographic Microclimate

### Community 7 - "Deep Learning & Transfer"
Cohesion: 0.5
Nodes (4): brown_2025_alphaearth, chen_2020_contrastive_framework, sylvain_2024_tree_species_uncertainty, Transfer Learning in Remote Sensing

### Community 8 - "Landsat Land Cover"
Cohesion: 0.67
Nodes (3): chastain_2007_eve_landsat_understory, Landsat, pflugmacher_2019_lulc_landsat

### Community 9 - "Vegetation Community Change"
Cohesion: 0.67
Nodes (3): herraiz_2025_phen_shifts_mediterranean, midolo_2026_denser_vegetation, Vegetation Community Change

### Community 10 - "Neural Network Foundations"
Cohesion: 0.67
Nodes (3): hiebl_2025_pretraining, lecun_1998_efficient_backprop, Neural Network Training

## Knowledge Gaps
- **13 isolated node(s):** `pflugmacher_2019_lulc_landsat`, `noce_2023_altitude_shift_tree_italy`, `fady_2025_native_trees_mediterranean`, `grünig_2026_climate_change_disturbances_forest`, `albrich_2019_climate_change_mountain_forests` (+8 more)
  These have ≤1 connection - possible missing edges or undocumented components.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `Sentinel-2` connect `Sentinel-2 Tree Mapping` to `Forest Inventory & Cartography`, `Landsat Trends & Bias`, `Species Distribution Models`, `Spectral & Functional Diversity`, `Deep Learning & Transfer`, `Landsat Land Cover`, `Neural Network Foundations`?**
  _High betweenness centrality (0.201) - this node is a cross-community bridge._
- **Why does `National Forest Inventory` connect `Forest Inventory & Cartography` to `Sentinel-2 Tree Mapping`, `Spectral & Functional Diversity`, `Plant Traits & Microclimate`, `Deep Learning & Transfer`, `Landsat Land Cover`?**
  _High betweenness centrality (0.164) - this node is a cross-community bridge._
- **Why does `Landsat` connect `Landsat Land Cover` to `Sentinel-2 Tree Mapping`, `Forest Inventory & Cartography`, `Landsat Trends & Bias`, `Species Distribution Models`, `Forest Disturbances`?**
  _High betweenness centrality (0.151) - this node is a cross-community bridge._
- **Are the 2 inferred relationships involving `Tree Species Mapping` (e.g. with `National Forest Inventory` and `Species Distribution Models`) actually correct?**
  _`Tree Species Mapping` has 2 INFERRED edges - model-reasoned connections that need verification._
- **Are the 2 inferred relationships involving `Species Distribution Models` (e.g. with `Topographic Microclimate` and `Tree Species Mapping`) actually correct?**
  _`Species Distribution Models` has 2 INFERRED edges - model-reasoned connections that need verification._
- **Are the 2 inferred relationships involving `Vegetation Community Change` (e.g. with `Vegetation Greenness Trends` and `Leaf Habit and Latitudinal Gradient`) actually correct?**
  _`Vegetation Community Change` has 2 INFERRED edges - model-reasoned connections that need verification._
- **What connects `pflugmacher_2019_lulc_landsat`, `noce_2023_altitude_shift_tree_italy`, `fady_2025_native_trees_mediterranean` to the rest of the system?**
  _13 weakly-connected nodes found - possible documentation gaps or missing edges._