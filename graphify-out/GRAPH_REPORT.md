# Graph Report - 01_notes + 02_concepts  (2026-05-08)

## Corpus Check
- 84 files · ~78,612 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 181 nodes · 236 edges · 20 communities (14 shown, 6 thin omitted)
- Extraction: 74% EXTRACTED · 26% INFERRED · 0% AMBIGUOUS · INFERRED: 62 edges (avg confidence: 0.82)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- [[_COMMUNITY_Landsat Long-Term Forest Monitoring|Landsat Long-Term Forest Monitoring]]
- [[_COMMUNITY_Foundation Models & Transfer Learning|Foundation Models & Transfer Learning]]
- [[_COMMUNITY_Pan-European Forest Mapping|Pan-European Forest Mapping]]
- [[_COMMUNITY_Sentinel-2 Vegetation Classification|Sentinel-2 Vegetation Classification]]
- [[_COMMUNITY_Ecological Indicators & Forest Variables|Ecological Indicators & Forest Variables]]
- [[_COMMUNITY_Deep Learning for Earth Observation|Deep Learning for Earth Observation]]
- [[_COMMUNITY_Mediterranean Climate & Vegetation Change|Mediterranean Climate & Vegetation Change]]
- [[_COMMUNITY_Biodiversity & Spectral Diversity|Biodiversity & Spectral Diversity]]
- [[_COMMUNITY_Italian Forest Ecology & Disturbances|Italian Forest Ecology & Disturbances]]
- [[_COMMUNITY_Forest Inventory & Disturbance Recovery|Forest Inventory & Disturbance Recovery]]
- [[_COMMUNITY_Self-Supervised Pretraining|Self-Supervised Pretraining]]
- [[_COMMUNITY_Canopy-Understory Dynamics|Canopy-Understory Dynamics]]
- [[_COMMUNITY_Explainable Forest Mapping|Explainable Forest Mapping]]
- [[_COMMUNITY_Neural Network Fundamentals|Neural Network Fundamentals]]
- [[_COMMUNITY_Cloud-Native RS Processing|Cloud-Native RS Processing]]
- [[_COMMUNITY_Italian Forest Inventory|Italian Forest Inventory]]
- [[_COMMUNITY_Reproducible Geoscience|Reproducible Geoscience]]
- [[_COMMUNITY_Efficient DNN Processing|Efficient DNN Processing]]
- [[_COMMUNITY_CNN Vegetation Monitoring|CNN Vegetation Monitoring]]
- [[_COMMUNITY_LAI Estimation|LAI Estimation]]

## God Nodes (most connected - your core abstractions)
1. `Hiebl et al. 2025 - Pretraining Strategies and Deep-Ensemble Uncertainty for EVE Cover Mapping` - 11 edges
2. `NDVI` - 9 edges
3. `Phenology` - 9 edges
4. `Species Distribution Models` - 8 edges
5. `Landsat` - 7 edges
6. `Vegetation Community Change` - 7 edges
7. `Leaf Habit and Latitudinal Gradient` - 7 edges
8. `Tree Species Mapping - Methods, Challenges, and Best Practices` - 7 edges
9. `Sentinel-2` - 6 edges
10. `Sampling Bias in Remote Sensing` - 6 edges

## Surprising Connections (you probably didn't know these)
- `Enhanced NFI - Annual Estimates, Remote Sensing Integration, Stakeholder Co-Design` --conceptually_related_to--> `Forest Disturbances - Wildfire, Bark Beetles, Windthrow, Climate Sensitivity`  [INFERRED]
  01_notes/amico_2025_nfi_italy.md → 02_concepts/forest_disturbances.md
- `Dense Sentinel-2 time series is the dominant explanatory source for tree species mapping` --conceptually_related_to--> `TRACEVE Pretraining - InceptionTime Deep Ensemble Framework for Sentinel-2 Time Series`  [INFERRED]
  01_notes/hemmerling_2021_forest_mapping_s2.md → 01_notes/traceve_pretraining.md
- `Functional and Taxonomic Diversity of Italian Forests - Temperature, Solar Radiation, and Soil Moisture Effects` --conceptually_related_to--> `Rao's Quadratic Entropy as Remote Sensing Biodiversity Metric`  [INFERRED]
  01_notes/bricca_2026_topo_diversity.md → 02_concepts/spectral_diversity_biodiversity.md
- `Forest Disturbances - Wildfire, Bark Beetles, Windthrow, Climate Sensitivity` --references--> `Wegler et al. 2025 - National Tree Species Map for Germany from Sentinel-1 and -2`  [EXTRACTED]
  02_concepts/forest_disturbances.md → 01_notes/wegler_2025_tree_species_germany.md
- `Wegler et al. 2025 - National Tree Species Map for Germany from Sentinel-1 and -2` --conceptually_related_to--> `National-Scale Tree Species Mapping with Sentinel-2 Time Series`  [INFERRED]
  01_notes/wegler_2025_tree_species_germany.md → 02_concepts/tree_species_mapping.md

## Hyperedges (group relationships)
- **Sentinel-2 time series for forest and land cover mapping at national/continental scale** — grabska_2024_tree_species_map_paper, miettinen_2025_forest_maps_europe_paper, astola_2019_s2_l8_comparison_paper, pflugmacher_2019_lulc_landsat_paper, ae_training_paper [INFERRED 0.95]
- **Deep learning under limited labelled data in remote sensing** — safonova_2023_small_data_paper, yuan_2025_sits_augmentation_paper, reichstein_2019_deep_learning_earth_sciences_paper, ae_training_paper, sattstools_paper [INFERRED 0.90]
- **Mediterranean forest species responses to climate change and aridity** — fady_2025_native_trees_mediterranean_paper, herraiz_2025_phen_shifts_mediterranean_paper, albrich_2019_climate_change_mountain_forests_paper, midolo_2026_denser_vegetation_paper [INFERRED 0.90]
- **Long-term Landsat archive for continental forest monitoring and change detection** — turubanove_2023_canopy_landsat_paper, tong_2023_forest_densification_china_paper, bell_2024_hindcasting_forest_structure_paper, bayle_2024_landsat_greening_inflated_paper, ls_mapping_document [INFERRED 0.95]
- **Deep learning and Sentinel-2 time series for tree species classification and proportion mapping** — pu_2021_tree_species_mapping_review_paper, bolyn_2022_tree_species_mapping_paper, wang_2022_tree_species_mapping_paper, hiebl_2026_alphaearth_paper, wegler_2026_canopy_cover_loss_paper [INFERRED 0.90]
- **Long-term forest ecological monitoring linking canopy structure, biodiversity and climate change** — francioni_2026_canopy_closure_paper, jin_2023_drivers_differentiation_evergreen_paper, vihervaara_2017_ebv_remote_sensing_paper, mattioli_2025_carta_forestale_paper [INFERRED 0.85]
- **Sentinel-2 time series for vegetation and tree species mapping** — hemmerling_2021_forest_mapping_s2_paper, chabalala_2023_dl_s2_mediterranean_fruit_trees_paper, koch_2025_intraspecies_variation_s2_paper, adagbasa_2022_deep_learning_s2_paper, traceve_pretraining_document, liu_2023_spectral_spatial_resolution_effect_paper, liu_2023_mapping_tree_species_diversity_paper [INFERRED 0.95]
- **Climate change impacts on Italian forest ecology and species distribution** — noce_2023_altitude_shift_tree_italy_paper, gasparini_2022_nfi_italy_paper, grunig_2026_climate_change_disturbances_forest_paper [INFERRED 0.90]
- **Self-supervised and transfer pretraining for deep learning in remote sensing** — chen_2020_contrastive_framework_paper, traceve_pretraining_document, traceve_mvp_pretraining_rationale, chen_2020_simclr_contrastive_rationale, kattenborn_2021_review_cnn_vegetation_monitoring_paper [INFERRED 0.85]
- **Deep Ensemble Uncertainty Quantification for Forest Species Mapping** — hiebl_2025_pretraining_paper, sylvain_2024_tree_species_uncertainty_paper, transfer_learning_rs_doc, hiebl_2025_epistemic_aleatoric, sylvain_2024_super_ensemble [INFERRED 0.95]
- **National-Scale Tree Species Mapping from Sentinel-2 Time Series Without Restricted NFI Data** — wegler_2025_tree_species_germany_paper, amico_2025_nfi_italy_paper, tree_species_mapping_doc, tree_species_mapping_national_scale [INFERRED 0.90]
- **Spectral Diversity as Scalable EBV Proxy for Forest Biodiversity Monitoring** — spectral_diversity_biodiversity_doc, ebv_biodiversity_doc, bricca_2026_topo_diversity_paper, tree_species_mapping_svh_approach, ebv_spectral_diversity_proxy, spectral_diversity_raos_q [INFERRED 0.85]

## Communities (20 total, 6 thin omitted)

### Community 0 - "Landsat Long-Term Forest Monitoring"
Cohesion: 0.1
Nodes (25): Bayle et al. 2024 - Landsat Greening Trends in Alpine Ecosystems Inflated by Sampling Bias, Increasing Landsat observation density over time spuriously inflates NDVImax greening trends, Gradient Nearest Neighbor temporal transferability for hindcast and updated forest structure maps, Bell et al. 2024 - Hindcasting and Updating Landsat-based Forest Structure Mapping, UNet++ soft classification predicting per-pixel basal area species proportions instead of hard labels, Bolyn et al. 2022 - Spectral-Spatial Deep Learning for Tree Species Proportion Mapping, De Luca et al. 2022 - Integrated Sentinel-1 and Sentinel-2 for LULC Mapping in Mediterranean Region, SAR backscatter, InSAR coherence and optical time series provide complementary structural and biochemical discriminative features (+17 more)

### Community 1 - "Foundation Models & Transfer Learning"
Cohesion: 0.17
Nodes (18): Brown et al. 2025 - AlphaEarth Foundations: Embedding Field Model for Global Mapping, Continuous-Time Modeling with Sinusoidal Timecodes for Arbitrary Date Range Queries, 64-Dimensional Embedding Fields at 10m Resolution - Universal Geospatial Feature Space, Space Time Precision (STP) Encoder - Parallel Spatial, Temporal, and Convolutional Branches, Cloud and Cloud Shadow Detection for Optical Satellite Imagery, Cloud Masking Impact on Satellite Image Time Series Irregularity, Disentangled Epistemic and Aleatoric Uncertainty for OOD Detection in Forest Mapping, Probabilistic InceptionTime CNN with 15-Head Deep Ensemble for EVE Cover Regression (+10 more)

### Community 2 - "Pan-European Forest Mapping"
Cohesion: 0.15
Nodes (15): Probabilistic and preferential sampling are complementary for forest biodiversity monitoring, Probabilistic and preferential sampling approaches offer integrated perspectives of Italian forest diversity, Comparison of Sentinel-2 and Landsat 8 imagery for forest variable prediction in boreal region, Red-edge band (B05) is the most predictive Sentinel-2 feature for forest inventory variables, Dense multi-sensor time series (S1+S2+Landsat) on cloud platforms is the recommended operational approach for EU forest monitoring, Monitoring of Forests through Remote Sensing - EU Final Report, Map of forest tree species for Poland based on Sentinel-2 data, Short-period multi-annual Spectral-Temporal Metrics from Sentinel-2 for robust national-scale tree species classification (+7 more)

### Community 3 - "Sentinel-2 Vegetation Classification"
Cohesion: 0.16
Nodes (15): Adagbasa et al. 2022 - Deep Learning with Stratified K-Fold for Vegetation Species Discrimination using Sentinel-2, MLP combining Sentinel-2, Sentinel-1 SAR, vegetation indices, and DEM for vegetation species classification, Temporal optimisation - restricting imagery to cloud-free phenological windows, Chabalala et al. 2023 - Mapping fruit tree dynamics using phenological metrics from optimal Sentinel-2 data and Deep Neural Network, Phenological metrics as dimensionality reduction for time-series classification, Dense Sentinel-2 time series is the dominant explanatory source for tree species mapping, Hemmerling et al. 2021 - Mapping temperate forest tree species using dense Sentinel-2 time series, Koch et al. 2025 - Assessing Intraspecific Variation of Tree Species Based on Sentinel-2 Vegetation Indices (+7 more)

### Community 4 - "Ecological Indicators & Forest Variables"
Cohesion: 0.47
Nodes (14): Functional Diversity, Landsat, Leaf Habit and Latitudinal Gradient, National Forest Inventory, NDVI, Neural Network Training, Phenology, Plant Functional Traits (+6 more)

### Community 5 - "Deep Learning for Earth Observation"
Cohesion: 0.2
Nodes (14): Cross-attention fusion: AlphaEarth embedding as query attending over Sentinel-2 time steps, ae_training - TRACEVE + AlphaEarth Cross-Attention Fusion Framework, Hybrid models coupling physics and deep learning for reliable Earth system prediction, Deep learning and process understanding for data-driven Earth system science, Ten deep learning techniques to address small data problems with remote sensing, Spatial k-fold cross-validation is essential for honest accuracy assessment in spatially autocorrelated RS data, Transfer learning is the most accessible and broadly effective technique for small-data RS problems, NaN-safe PyTorch normalization classes for cloud-gap satellite time series ML pipelines (+6 more)

### Community 6 - "Mediterranean Climate & Vegetation Change"
Cohesion: 0.17
Nodes (13): Climate change causes critical transitions and irreversible alterations of mountain forests, Tipping point at +2C warming triggers irreversible forest state shift in Eastern Alps, Topographic complexity buffers but cannot prevent critical transitions under climate change, Mediterranean as a biodiversity hotspot with high endemism and knowledge gaps, Habitat heterogeneity drives tree species richness in Mediterranean botanical territories, Native Trees of the Mediterranean Region: Distribution, Diversity and Conservation Challenges, The Global Canopy Atlas: analysis-ready maps of 3D structure for the worlds woody ecosystems, Current global satellite canopy height models perform poorly at native resolution (R2 < 0.38 at 1-30 m) (+5 more)

### Community 7 - "Biodiversity & Spectral Diversity"
Cohesion: 0.22
Nodes (13): Functional and Taxonomic Diversity of Italian Forests - Temperature, Solar Radiation, and Soil Moisture Effects, Space-for-Time Substitution for Climate Change Projections, Bricca et al. 2026 - Topography and Soil Moisture Regulate Temperature-Biodiversity Relationship, Essential Biodiversity Variables and Remote Sensing, Spectral Diversity as Proxy for Community Composition EBV, Spectral Diversity and Biodiversity - SVH, Rao's Q, Optimal Resolution, Optimal Spatial Resolution 10-15m for SVH-Based Forest Diversity Mapping, Rao's Quadratic Entropy as Remote Sensing Biodiversity Metric (+5 more)

### Community 8 - "Italian Forest Ecology & Disturbances"
Cohesion: 0.18
Nodes (11): Gasparini et al. 2022 - Italian National Forest Inventory: Methods and Results of the Third Survey (INFC2015), Three-phase national forest inventory design on 1km systematic grid for Italy, Grunig et al. 2026 - Climate change will increase forest disturbances in Europe throughout the 21st century, SVD deep learning metamodel for continental-scale forest dynamics from 135M simulation years, Next-generation SDM framework integrating RS as both response and predictor variables, He et al. 2015 - Will remote sensing shape the next generation of species distribution models?, RS-derived SDM predictor catalogue: NDVI, phenology, LAI, LST, canopy structure, Kang et al. 2021 - Data-driven LAI estimation from Landsat for the contiguous US (+3 more)

### Community 9 - "Forest Inventory & Disturbance Recovery"
Cohesion: 0.22
Nodes (10): Enhanced NFI - Annual Estimates, Remote Sensing Integration, Stakeholder Co-Design, D'Amico et al. 2025 - National Forest Inventory in Italy: New Perspectives for Forest Monitoring, Tessellation Stratified Sampling for National Forest Inventory, Chastain and Townsend 2007 - Landsat ETM and Topographic Data for Evergreen Understory Mapping, Spring Leaf-Off Timing for Evergreen Understory Detection Beneath Deciduous Canopy, Topoedaphic Niche Differentiation for Understory Species Discrimination, Disturbance Cascade Interactions - Wind, Bark Beetle, Fire, Forest Disturbances - Wildfire, Bark Beetles, Windthrow, Climate Sensitivity (+2 more)

### Community 10 - "Self-Supervised Pretraining"
Cohesion: 0.25
Nodes (9): Chen et al. 2020 - SimCLR: A Simple Framework for Contrastive Learning of Visual Representations, Nonlinear projection head absorbs augmentation artifacts to preserve semantic encoder representations, SimCLR contrastive self-supervised pretraining with data augmentation and NT-Xent loss, Per-head bootstrapped deep ensemble with BetaNLL uncertainty decomposition for EVE cover mapping, Masked Value Prediction (MVP) self-supervised pretraining on Sentinel-2 time series without labels, TRACEVE Pretraining - InceptionTime Deep Ensemble Framework for Sentinel-2 Time Series, Vaswani et al. 2017 - Attention Is All You Need (Transformer architecture), Multi-head attention with positional encoding as modular sequence representation (+1 more)

### Community 11 - "Canopy-Understory Dynamics"
Cohesion: 0.33
Nodes (6): Beta diversity partitioning into turnover and nestedness distinguishes directional change from interannual fluctuation, Francioni et al. 2026 - Canopy Closure and Climate Extremes Drive Understory Species Loss, Canopy buffering of understory microclimate mediates leaf habit shift differences between trees and shrubs, Jin and Qian 2023 - Drivers of Tree vs Shrub Leaf Habit Differentiation in Subtropical Eastern Asia, Vihervaara et al. 2017 - Essential Biodiversity Variables and Remote Sensing for National Monitoring, EBV framework linking RS capabilities to standardised biodiversity monitoring

### Community 12 - "Explainable Forest Mapping"
Cohesion: 0.67
Nodes (3): Correction pathway for quantifying annotator label inconsistency, Nguyen et al. 2022 - Explainable Deep Learning for Forest Mapping at Alpine Treeline, Rule-informed CNN encoding forest definition criteria as differentiable graph

### Community 13 - "Neural Network Fundamentals"
Cohesion: 0.67
Nodes (3): LeCun et al. 1998 - Efficient BackProp, Input normalization and decorrelation minimise Hessian condition number for fastest gradient descent convergence, Weight initialisation with sigma=fan-in^(-1/2) keeps activations in the active sigmoid regime

## Knowledge Gaps
- **65 isolated node(s):** `Neural Network Training`, `Mediterranean as a biodiversity hotspot with high endemism and knowledge gaps`, `Habitat heterogeneity drives tree species richness in Mediterranean botanical territories`, `Tipping point at +2C warming triggers irreversible forest state shift in Eastern Alps`, `Topographic complexity buffers but cannot prevent critical transitions under climate change` (+60 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **6 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `Hiebl et al. 2025 - Pretraining Strategies and Deep-Ensemble Uncertainty for EVE Cover Mapping` connect `Foundation Models & Transfer Learning` to `Forest Inventory & Disturbance Recovery`, `Biodiversity & Spectral Diversity`?**
  _High betweenness centrality (0.028) - this node is a cross-community bridge._
- **Why does `Koch et al. 2025 - Assessing Intraspecific Variation of Tree Species Based on Sentinel-2 Vegetation Indices` connect `Sentinel-2 Vegetation Classification` to `Italian Forest Ecology & Disturbances`?**
  _High betweenness centrality (0.018) - this node is a cross-community bridge._
- **What connects `Neural Network Training`, `Mediterranean as a biodiversity hotspot with high endemism and knowledge gaps`, `Habitat heterogeneity drives tree species richness in Mediterranean botanical territories` to the rest of the system?**
  _65 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `Landsat Long-Term Forest Monitoring` be split into smaller, more focused modules?**
  _Cohesion score 0.1 - nodes in this community are weakly interconnected._