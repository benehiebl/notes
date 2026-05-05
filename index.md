# Wiki Index

Table of contents for the LLM Wiki knowledge base covering remote sensing, machine learning, deep learning, and forest ecology.

## Concept Pages (`02_concepts/`)

| Page | Description |
|------|-------------|
| [[landsat]] | Landsat satellite program: sensors, archive history, observation density, key limitations |
| [[ndvi]] | Normalised Difference Vegetation Index: computation, derived metrics, limitations |
| [[phenology]] | Vegetation phenology: seasonal timing, curve fitting, alpine context |
| [[sampling_bias_remote_sensing]] | Systematic bias from non-uniform observation frequency in long time series; false greening trends |
| [[vegetation_greenness_trends]] | Multi-decadal greening/browning trends from satellite data: methods, drivers, caveats |
| [[functional_diversity]] | Rao's QE, functional dissimilarity, distinction between taxonomic and functional diversity |
| [[plant_functional_traits]] | TRY database, major trait spectra (leaf economic, root economic, size, reproductive, woody) |
| [[topographic_microclimate]] | Topographic regulation of local climate via solar radiation, aspect, soil moisture |
| [[national_forest_inventory]] | NFI purpose, multi-phase sampling design, variables, role as ground truth for remote sensing |
| [[sentinel_2]] | Sentinel-2 bands, revisit time, STMs, red-edge advantage, comparison with Landsat |
| [[tree_species_mapping]] | Methods, classifiers, class imbalance, accuracy assessment for species mapping from satellite data |
| [[forest_disturbances]] | Wildfire, bark beetles, windthrow — climate sensitivity, interactions, vegetation feedbacks, remote sensing |
| [[species_distribution_models]] | SDMs — response/predictor variables, RS integration, NG-SDM framework, circularity caveats |
| [[transfer_learning_remote_sensing]] | Pretraining strategies, self-supervised MVP, epistemic/aleatoric uncertainty, spatial autocorrelation in CV |
| [[leaf_habit_latitudinal_gradient]] | Evergreen–deciduous latitudinal shift in forests; canopy buffering drives tree–shrub differentiation in leaf habit response to climate |
| [[neural_network_training]] | Backpropagation, SGD, input normalisation, weight initialisation, learning rates, activations — foundational training principles |
| [[spectral_diversity_biodiversity]] | Spectral Variability Hypothesis (SVH): predicting species diversity from spectral heterogeneity metrics (Rao's Q, GLCM texture); optimal resolution |

## Notes Pages (`01_notes/`)

| Page | Paper |
|------|-------|
| [[01_notes/albrich_2019_climate_change_mountain_forests]] | Albrich et al. 2019 — Climate change critical transitions in mountain forests (iLand simulation) |
| [[01_notes/amico_2025_nfi_italy]] | Amico et al. 2025 — National Forest Inventory Italy |
| [[01_notes/bayle_2024_landsat_greening_inflated]] | Bayle et al. 2024 — Landsat greening trends inflated by increasing observation density |
| [[01_notes/bell_2024_hindcasting_forest_structure]] | Bell et al. 2024 — Hindcasting forest structure with Landsat |
| [[01_notes/brown_2025_alphaearth]] | Brown et al. 2025 — AlphaEarth foundation model |
| [[01_notes/chabalala_2023_dl_s2_mediterranean_fruit_trees]] | Chabalala et al. 2023 — Deep learning + Sentinel-2 for Mediterranean fruit tree mapping |
| [[01_notes/chastain_2007_eve_landsat_understory]] | Chastain & Townsend 2007 — Landsat ETM+ evergreen understory mapping, Appalachian forests |
| [[01_notes/chen_2020_contrastive_framework]] | Chen et al. 2020 — SimCLR contrastive self-supervised learning framework |
| [[01_notes/deluca_2022_s1_s2_lulc_mapping]] | DeLuca et al. 2022 — Sentinel-1 + Sentinel-2 LULC mapping |
| [[01_notes/fady_2025_native_trees_mediterranean]] | Fady et al. 2025 — Native trees and climate in the Mediterranean |
| [[01_notes/fischer_2025_glocal_canopy_atlas]] | Fischer et al. 2025 — Global canopy height atlas |
| [[01_notes/francioni_2026_canopy_closure]] | Francioni et al. 2026 — Canopy closure estimation |
| [[01_notes/bricca_2026_topo_diversity]] | Bricca et al. 2026 — Topography and soil moisture regulate temperature-biodiversity in forests |
| [[01_notes/gasparini_2022_nfi_italy]] | Gasparini et al. 2022 — Italian NFI INFC2015: methods, results, 10.98 Mha forest area |
| [[01_notes/grabska_2024_tree_species_map]] | Grabska-Szwagrzyk et al. 2024 — National Sentinel-2 tree species map for Poland; seasonal STMs + RF |
| [[01_notes/grünig_2026_climate_change_disturbances_forest]] | Grünig et al. 2026 — Climate change doubles forest disturbances in Europe; SVD deep learning framework |
| [[01_notes/he_2015_remote_sensing_sdm]] | He et al. 2015 — Remote sensing for next-generation SDMs; RS response and predictor variables; NG-SDM vision |
| [[01_notes/herraiz_2025_phen_shifts_mediterranean]] | Herraiz et al. 2025 — 28-yr Landsat phenology of 10 Mediterranean species; aridity shifts SOS/LOS; general greening |
| [[01_notes/hiebl_2025_pretraining]] | Hiebl et al. 2025 — Pretraining + deep ensemble uncertainty for EVE cover mapping from Sentinel-2 time series |
| [[01_notes/jin_2023_drivers_differentiation_evergreen]] | Jin & Qian 2023 — Canopy trees shift leaf habit (evergreen→deciduous) faster than understory shrubs along latitudinal temperature gradient in eastern Asian subtropics |
| [[01_notes/lecun_1998_efficient_backprop]] | LeCun et al. 1998 — Efficient BackProp: foundational training tricks for neural networks — SGD, normalisation, initialisation, learning rates, Hessian theory |
| [[01_notes/liu_2023_spectral_spatial_resolution_effect]] | Liu et al. 2023 — Sentinel-2 at 10m best for TSD mapping; 10–15m optimal resolution; Rao's Q and texture best spectral heterogeneity metrics; SVH confirmed |
| [[01_notes/koch_2025_intraspecies_variation_s2]] | Koch et al. 2025 — Intraspecies spectral variation with Sentinel-2 |