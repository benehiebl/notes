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
| [[vegetation_community_change]] | Long-term European plant community change: EIV bioindication, nitrogen eutrophication, vegetation densification, thermophilisation; links to RS greening |
| [[transformers_time_series]] | Transformer architecture for time series: self-attention, SITS adaptations, pre-training, TST/InceptionTime for forest mapping |
| [[ebv_biodiversity_monitoring]] | Essential Biodiversity Variables (EBVs): standardised monitoring framework; RS contributions to ecosystem structure, phenology, community composition |

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
| [[01_notes/mattioli_2025_carta_forestale]] | Mattioli et al. 2025 — CFI2020: Italy's first 1:10,000 national forest map; >10 Mha (FAO def.); three simultaneous forest definitions; +11.47% vs INFC2015 |
| [[01_notes/midolo_2026_denser_vegetation]] | Midolo et al. 2026 — 60yr European plant community change: nitrogen enrichment dominant (+0.25 EIV), vegetation densification (light -0.12); thermophilisation weak except alpine |
| [[01_notes/miettinen_2025_forest_maps_europe]] | Miettinen et al. 2025 — Pan-European 10m AGB, volume, and deciduous-conifer maps from Sentinel-2 + 14 national NFIs; kNN; nearly unbiased at European level but regression-to-mean bias |
| [[01_notes/noce_2023_altitude_shift_tree_italy]] | Noce et al. 2023 — MaxEnt SDMs for 20 Italian forest tree species; silver fir most vulnerable; larch and Turkey oak gain; tree line shifts upward; Northern Apennines most impacted |
| [[01_notes/pflugmacher_2019_lulc_landsat]] | Pflugmacher et al. 2019 — Pan-European LULC from Landsat STMs + LUCAS; OA=75.1%; auxiliary features +4.7pp; CORINE overestimates cropland by 63%; 3yr pooling eliminates cloud gaps |
| [[01_notes/sylvain_2024_tree_species_uncertainty]] | Sylvain et al. 2024 — CNN super-ensemble (9 models) for 0.9m boreal tree species mapping; F1=0.90; CHM +5pp; inter-model agreement = validated uncertainty map |
| [[01_notes/koch_2025_intraspecies_variation_s2]] | Koch et al. 2025 — Intraspecies spectral variation with Sentinel-2 |
| [[01_notes/adagbasa_2022_deep_learning_s2]] | Adagbasa et al. 2022 — MLP deep learning for grass species discrimination with Sentinel-2; F1=92% |
| [[01_notes/alessi_2023_sampling_approaches]] | Alessi et al. 2023 — Probabilistic vs preferential sampling for Italian forest diversity; combined use recommended |
| [[01_notes/astola_2019_s2_l8_comparison]] | Astola et al. 2019 — Sentinel-2 outperforms Landsat 8 for boreal forest variable prediction; red-edge B05 is best predictor |
| [[01_notes/atzberger_2020_monitoring_forests_eu]] | Atzberger et al. 2020 — EU report on monitoring forests through RS; reviews 6 themes including phenology, pests, biodiversity, carbon |
| [[01_notes/bolyn_2022_tree_species_mapping]] | Bolyn et al. 2022 — UNet++ CNN predicts per-pixel tree species proportions in Wallonia; OA_maj=0.73 |
| [[01_notes/hemmerling_2021_forest_mapping_s2]] | Hemmerling et al. 2021 — Dense Sentinel-2 time series maps 17 tree species in Brandenburg; spectral TS dominates over texture/env features |
| [[01_notes/kang_2021_lai_landsat]] | Kang et al. 2021 — Data-driven 30 m LAI from Landsat using MODIS as training reference; RMSE=0.8, r²=0.88 for CONUS |
| [[01_notes/kattenborn_2021_review_cnn_vegetation_monitoring]] | Kattenborn et al. 2021 — Comprehensive review of CNNs in vegetation remote sensing; CNNs outperform shallow ML for spatial tasks |
| [[01_notes/li_2022_cloud_detection]] | Li et al. 2022 — Systematic review of cloud/shadow detection for optical satellite imagery; deep learning + temporal features are emerging best practice |
| [[01_notes/liu_2023_mapping_tree_species_diversity]] | Liu et al. 2023 — SVH-based TSD mapping in temperate montane forest with S1+S2+topography; texture metrics best; R²=0.628 |
| [[01_notes/nguyen_2022_forest_mapping_explainable]] | Nguyen et al. 2022 — Explainable CNN encodes forest definition rules; reveals annotator biases at Swiss Alps treeline |
| [[01_notes/pu_2021_tree_species_mapping_review]] | Pu 2021 — 40-year review of tree species mapping with advanced RS; "multiple method" trend; deep learning improving accuracy |
| [[01_notes/reichstein_2019_deep_learning_earth_sciences]] | Reichstein et al. 2019 — Perspective on hybrid DL + physical process models for Earth system science; foundational framing paper |
| [[01_notes/safonova_2023_small_data]] | Safonova et al. 2023 — Review of 10 DL techniques for small data problems in RS; decision flowchart for technique selection |
| [[01_notes/schloegl_2026_reproducibility]] | Schlögl et al. 2026 — Position paper on reproducibility in geoscientific data analysis; FAIR principles, version control, containerisation |
| [[01_notes/sze_2017_efficient_dnn_processing]] | Sze et al. 2017 — Tutorial and survey on efficient DNN processing; energy/bandwidth bottlenecks; compression and hardware co-design |
| [[01_notes/thom_2026_disturbance_suitability]] | Thom et al. 2026 — Suitability ranking of 53 tree species for post-disturbance regeneration in Central European forests |
| [[01_notes/tong_2023_forest_densification_china]] | Tong et al. 2023 — 30-year Landsat reveals forest tripling in southern China; reforestation policies ~2000 drove area surge ~2010 |
| [[01_notes/torres_2021_forest_health_remote_sensing]] | Torres et al. 2021 — PRISMA systematic review of RS for forest health (2015–2020); Landsat dominates; early warning is key gap |
| [[01_notes/turubanove_2023_canopy_landsat]] | Turubanova et al. 2023 — Annual 30 m tree canopy height change in Europe 2001–2021 from Landsat + lidar; decline after 2016 |
| [[01_notes/vaswani_2023_attention_is_all]] | Vaswani et al. 2017 — Original Transformer paper; self-attention mechanism; foundation for all modern sequence models |
| [[01_notes/vihervaara_2017_ebv_remote_sensing]] | Vihervaara et al. 2017 — RS contributions to EBV monitoring in Finland; 4 EBV classes strongly benefit from RS |
| [[01_notes/wang_2022_tree_species_mapping]] | Wang et al. 2022 — S2 outperforms L8 for plantation species mapping; temporal saturation after ~2 phenological images |
| [[01_notes/wegler_2025_tree_species_germany]] | Wegler et al. 2025 — National 10 m tree species map for Germany; S2+S1+DEM; F1=0.89 without restricted NFI data |
| [[01_notes/wegler_2026_canopy_cover_loss]] | Wegler et al. 2026 — Species-specific canopy cover loss in Germany 2018–2024; spruce 51.3% of loss; peak 2020–2021 |
| [[01_notes/wen_2023_transformers_time_series]] | Wen et al. 2023 — Survey of Transformer variants for time series; forecasting, anomaly detection, classification |
| [[01_notes/xu_2022_cloud_native_algorithms]] | Xu et al. 2022 — Cloud-native containerisation for deploying user-defined DL algorithms on RS Data Cubes at continental scale |
| [[01_notes/yuan_2025_sits_augmentation]] | Yuan et al. 2025 — Empirical study of 11 SITS augmentation techniques; interpolation resampling best for irregular SITS/cross-year adaptation || [[01_notes/traceve_pretraining]] | traceve_pretraining repo — InceptionTimeEnsemble + BetaNLL deep ensembles + MVP pretraining on Sentinel-2 SITS; codebase for [[hiebl_2025_pretraining]] |
| [[01_notes/ae_training]] | ae_training repo — TRACEVE + AlphaEarth fusion; MLPAlpha, TST, CrossAttentionAlpha models; codebase for Hiebl et al. 2026 (ISPRS Annals) |
| [[01_notes/ls_mapping]] | ls_mapping repo — TSTpad on multi-annual Landsat time series; forest type + multi-target cover regression (EVE/Dec/NL) for Italy |
| [[01_notes/hiebl_2026_alphaearth]] | Hiebl et al. 2026 — AEF + Sentinel-2 Cross-Attention fusion for Italian forest mapping; TST_AEF,S2 best (RMSE=0.161, Acc=0.757); AEF matches S2 accuracy 10-24× faster |
| [[lai_estimation]] | Leaf Area Index (LAI): definition, MODIS/Landsat data fusion, saturation problem, biome-specific retrieval |
| [[cloud_detection]] | Cloud and cloud shadow detection: feature types, algorithm taxonomy, impact on time series preprocessing |
| [[01_notes/sattstools]] | sattstools repo — shared preprocessing library for all TRACEVE experiments; cloud masking, outlier detection, Whittaker smoothing, TSRobustStandardize, modality-specific data augmentation |
