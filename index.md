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
| [[spatial_proxies_random_forest]] | When coordinates/EDF/RFsp help random forests; decision rules; kNNDM CV vs random CV; RF–GLS as alternative |
| [[area_of_applicability]] | Predictor-space distance metric flagging per-pixel feature extrapolation; AOA in R package CAST |
| [[support_intensive_extensive]] | Variable support (point vs block) and intensive/extensive properties; split/merge policies for spatial aggregation |
| [[evergreen_broadleaved_expansion]] | Drivers (climate + propagule + land-use), distribution, and RS detection of evergreen broad-leaved species spread into deciduous European forests |
| [[deep_ensemble_uncertainty]] | Deep ensembles + proper scoring rules + β-NLL for epistemic + aleatoric uncertainty in NN regression |
| [[transformer_sits]] | Pretrained Transformer architectures for SITS — TST, SITS-BERT, SITS-Former, PRESTO; masked-value prediction; pixel vs patch |
| [[drought_mortality]] | Hotter droughts, xylem hydraulic failure, 20th-century redistribution of climatic drivers, drought-legacy effects |
| [[sentinel_1_sar]] | Sentinel-1 C-band SAR; dual polarisation VV/VH; cloud-independent companion to Sentinel-2 for forest mapping and disturbance detection |
| [[geospatial_foundation_models]] | AlphaEarth, PRESTO, Prithvi paradigm; pretrained Earth-observation embeddings for downstream mapping tasks with minimal labels |
| [[european_ground_truth_databases]] | EU-Forest, sPlotOpen, ICP Forest, NFIs — pan-European tree occurrence and vegetation plot databases for SDMs and RS calibration |
| [[treeline_ecotone_theory]] | Climatic/hormonal controls on treeline position: thermal vs moisture limitation, carbon-limitation hypothesis, emerging drought sensitivity, regeneration bottlenecks |
| [[snow_cover_treeline]] | Snow cover as protective winter microclimate at treeline: sapling freeze-thaw insulation, seed-bank cold stratification, boreal treeline snow control |
| [[treeline_remote_sensing_monitoring]] | DL/RS methods for treeline mapping: rule-informed CNNs, knowledge-guided multi-temporal segmentation (tCA loss), freeze/thaw RS, SHAP-explained SDMs |

## Paper Pages (`03_papers/`)

| Page | Description |
|------|-------------|
| [[03_papers/03_tree_species_cover_landsat]] | Mapping 40 years of dominant tree species and leaf type cover for Italy — ecological change detection paper (EVE expansion, climate drivers, latitudinal/altitudinal shifts) |
| [[03_papers/03_landsat_data_publication]] | Data publication: 40-year annual 30 m Landsat forest type and leaf type cover time series for Italy — methodology, validation, and dataset description |
| [[03_papers/06_spatial_autocorrelation]] | GEDI canopy height + alpine S2 tile — predictor SA range controls CV inflation; variogram → kNNDM buffer distance framework for spectral/topo/climate combinations |

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
| [[01_notes/mila_2024_spatial_proxies]] | Milà et al. 2024 — RFs with spatial proxies (coords/EDF/RFsp): help only for interpolation + residual autocorrelation + regular/random samples; never for transfer; kNNDM CV recommended; RF–GLS benchmark |
| [[01_notes/pebesma_2025_spatial_data]] | Pebesma et al. 2025 — SDSL workshop synthesis on R/Python/Julia spatial ecosystems; variable support, spherical geometry, data cubes, GeoParquet/GeoArrow, cross-language infrastructure |
| [[01_notes/berger_2006_distribution_eve]] | Berger & Walther 2006 — Insubrian EVE distribution along precipitation × bedrock gradients; W siliceous-humid vs E calcareous-dry partitioning |
| [[01_notes/chelli_2017_climate]] | Chelli et al. 2017 — Climate-vegetation response review across Italy's four climatic zones; drought overrides warming benefits beyond Mediterranean |
| [[01_notes/conedera_2018_drivers_evergreen]] | Conedera et al. 2018 — Propagule pressure (distance to garden) > climate for EVE invasion in Lago Maggiore; tobit regression on 200 plots |
| [[01_notes/yel_2026_deciduous_forests]] | Yel et al. 2026 — RS systematic review of climate-change impacts on deciduous forests; 70 papers; index inventory + analytical taxonomy |
| [[01_notes/schuldt_2020_drought_forest]] | Schuldt et al. 2020 — 2018 Central European drought first assessment; MGT +3.3°C vs baseline; widespread mortality; legacy effects |
| [[01_notes/dyderski_2025_species_shift]] | Dyderski et al. 2025 — SDMs for 20 European tree species under CMIP6 SSPs; boreal conifers most threatened by 2041–2060; trait-based generalisation |
| [[01_notes/kempf_2023_greening]] | Kempf 2023 — MODIS NDVI 2001–21 + GLDAS 1948–21 pan-European greening trends; regional polarisation; intensifying anomalies |
| [[01_notes/babst_2019_redistribution]] | Babst et al. 2019 — 20th-century redistribution from energy- to water-limited tree growth; T-limited area shrank by 10.8% from 2710 tree-ring sites |
| [[01_notes/blickensdörfer_2024_tree_species]] | Blickensdörfer et al. 2024 — National German tree species map with S1/S2 + NFI + mixed-stand pseudo-labelling; mixed-stand accuracy drops 4–14 pp |
| [[01_notes/kollert_2021_tree_species]] | Kollert et al. 2021 — Sentinel-2 LSP + three-monthly composites for tree species mapping in Tyrol; composites + LSP > 3 cloud-free scenes |
| [[01_notes/hamedianfar_2022_deep_learning]] | Hamedianfar et al. 2022 — Critical review of DL for forest inventory and planning; data, architecture, generalisation challenges |
| [[01_notes/lang_2024_canopy_height]] | Lang et al. 2024 — Global 10 m canopy height model fusing GEDI + S2 via CNN ensemble; aRMSE 7.3 m; only 5% of land has trees > 30 m |
| [[01_notes/qin_2026_forest_cover]] | Qin et al. 2026 — DL reconstruction + RF for annual 30 m forest cover in cloud-prone southern China 2000–20; OA 0.904 |
| [[01_notes/zhao_2022_forest_harvesting]] | Zhao et al. 2022 — Monthly forest harvesting mapping with Sentinel-1 SAR + U-Net; California + Rondônia; transferable model |
| [[01_notes/yang_2020_modis_evergreen]] | Yang et al. 2020 — FEVC-CV fractional evergreen cover from MODIS NDVI minimum + coefficient of variation; OA > 90%, RMSE ≈ 10% |
| [[01_notes/yan_2025_population]] | Yan et al. 2025 — Transformer + CNN hybrid for high-precision population estimation; SHAP-interpreted comparison with RF/ResNet |
| [[01_notes/bernico_2019_domain_similarity]] | Bernico et al. 2019 — Empirical scaling law: log-linear accuracy in data volume × source-target similarity for transfer learning |
| [[01_notes/klehr_2025_synthetic_data]] | Klehr et al. 2025 — Synthetic mixed training data + ANN regression for tree species fractions; 30 pure pixels per class suffice |
| [[01_notes/sylvain_2021_ensemble]] | Sylvain et al. 2021 — Bias correction + triple-resampling ensemble for predictive mapping uncertainty; conditional bias −25–50% |
| [[01_notes/tseng_2024_presto]] | Tseng et al. 2024 — PRESTO lightweight pretrained Transformer for RS pixel-time-series; 1000× smaller than ViT foundation models |
| [[01_notes/yuan_2022_sitsformer]] | Yuan et al. 2022 — SITS-Former patch-based Transformer with 3D-CNN embedding + SSL pretraining; +2.64–3.30% OA on crop classification |
| [[01_notes/yuan_2023_pretraining]] | Yuan & Lin 2022 — SITS-BERT: first BERT-style SSL pretraining for SITS; pixel-based, sinusoidal DOY encoding; +1.91–6.69% accuracy |
| [[01_notes/zerveas_2020_framework_transformer]] | Zerveas et al. 2020 — TST Transformer encoder for MTS representation learning; first unsupervised method to beat supervised SOTA |
| [[01_notes/zangh_2017_generalization]] | Zhang et al. 2017 — Deep nets fit random labels; classical complexity bounds cannot explain DL generalisation; reframed the field |
| [[01_notes/tan_2021_tser]] | Tan et al. 2021 — TSER benchmark: time series extrinsic regression; Rocket best overall; significant headroom for new methods |
| [[01_notes/wang_2026_foundation]] | Wang et al. 2026 — AlphaEarth + S1/S2 + GEDI for 10 m annual CHM + VHR Siamese change detection → annual forest carbon stock loss |
| [[01_notes/lakshminarayan_2017_uncertainty]] | Lakshminarayanan et al. 2017 — Deep ensembles: M independent networks + proper scoring rule; matches/exceeds Bayesian NNs; scales to ImageNet |
| [[01_notes/seitzer_2022_uncertainty]] | Seitzer et al. 2022 — β-NLL fixes the heteroscedastic NLL pitfall; one-line code change with large empirical improvement |
| [[01_notes/skidmore_2021_biodiversity]] | Skidmore et al. 2021 — Priority list of satellite-observable EBVs; ecosystem structure + function highest priority; genetic composition not feasible |
| [[01_notes/grantham_2020_anthropogenic_modification]] | Grantham et al. 2020 — Forest Landscape Integrity Index; only 40.5% of remaining forest has high integrity; 27% of which is protected |
| [[01_notes/manas_2021_seasonal_contrast]] | Mañas et al. 2021 — SeCo: temporal positive pairs (same location, different seasons) for contrastive RS pre-training; canonical source for ecological stability assumption enabling temporal contrastive learning |
| [[01_notes/alessi_2019_refugia]] | Alessi et al. 2019 — 11 native Italian laurophylls occupy <50% of potential range; central Apennines as Quaternary refugia; dispersal + land use > climate change; high EVE expansion potential |
| [[01_notes/fang_2016_eve_mosaics]] | Fang et al. 2016 — Soil P (>0.27 g/kg) drives evergreen-deciduous mosaic in 20-ha subtropical EBLF; habitat heterogeneity explains mosaic at all scales via hierarchical edaphic-topographic controls |
| [[01_notes/tan_2025_deep_tree_species]] | Tan et al. 2025 — Transformer + SSL pretraining + pseudo-labeling for S1/S2 SITS tree species mapping; OA 0.847; pseudo-labels from pure-stand DL model for mixed plots; red-edge + leaf-off most diagnostic |
| [[01_notes/feng_2026_tessera]] | Feng et al. 2026 — TESSERA: pixel-wise S1/S2 foundation model with Barlow Twins + temporal sampling invariance; 45.7M params; open weights + global 10m int8 embeddings; SOTA on tree species, crop segmentation, CHM regression |
| [[01_notes/ball_2026_foundation_models]] | Ball et al. 2026 — GFMs (AlphaEarth + Tessera) vs S1/S2 composites for 18-class tree species mapping in Trentino; WF1=0.83; near-asymptotic at 5% training data; soft labels outperform hard labels |
| [[01_notes/soto_2025_disturbance]] | Viana-Soto & Senf 2025 — European Forest Disturbance Atlas (EFDA): annual Landsat-based disturbance maps for 35 countries 1985–2023; F1=0.89; 439,000 km² disturbed; harvest dominates (79%) |
| [[01_notes/calvia_2022_pines]] | Calvia et al. 2022 — Diachronic aerial photo analysis of native Sardinian pine formations (Pinus halepensis, P. pinaster, P. pinea); +235/+1043/+27% expansion 1954–2019 |
| [[01_notes/mauri_2017_EU_tree_data]] | Mauri et al. 2017 — EU-Forest dataset: 249,410 plots, 242 tree species, 1 km INSPIRE grid, 21 NFIs; open-access pan-European tree occurrence database |
| [[01_notes/sabatini_2021_splot]] | Sabatini et al. 2021 — sPlotOpen: 95,104 open-access vegetation plots, 42,677 taxa, TRY trait integration; environmentally balanced global plant community dataset |
| [[01_notes/wessely_2023_tree_species_bottleneck]] | Wessely et al. 2024 — Tree species bottleneck for European forest management; −33–49% continuously suitable species under climate change; 3.18 timber/3.53 carbon/2.56 biodiversity sp/km² |
| [[01_notes/kang_2025_contrastive_vs_mae]] | Kang et al. 2026 — CL teachers outperform MAE teachers in SSKD despite MAE superiority in SSL; attention collapse diagnosed; I-SSKD (CL + MAE attention matching) achieves SOTA |
| [[01_notes/scheibenreif_2022_contrastive]] | Scheibenreif et al. 2022 — D-SimCLR: S1/S2 co-location as augmentation-free contrastive positives; 10% labels beats supervised 100%; linear probe on par with fully supervised |
| [[01_notes/stival_2025_contrastive_msi]] | Stival et al. 2025 — SACo+: spectral band group semantics + LBP texture + temporal as contrastive anchors for MSRSI; 94.72% EuroSAT (ResNet-18), +4.7pp over SeCo |
| [[01_notes/stival_2026_pixel_contrastive]] | Stival et al. 2026 — PIMC: recurrence plots of pixel VI time series as contrastive modality with RSI; 2D beats 1D for forecasting; pixel-wise SSL for SITS (preprint) |
| [[01_notes/li_2026_contrastive]] | Li et al. 2026 — HSSCL: hierarchical multi-level contrastive + GNN geometric consistency for SAR-optical matching; F1 85.8% claimed (+20% vs prior); treat with caution |
| [[01_notes/li_2023_land_cover_map]] | Li et al. 2023 — SinoLC-1: first 1 m national land-cover map of China via weakly+self-supervised L2HNet; OA=73.6%; no manual annotation; resolution mismatch resolved via L2H loss |
| [[01_notes/zhang_2026_statespacemodel]] | Zhang et al. 2026 — TSSMamba: dual-branch state space model (Mamba) for multi-temporal Sentinel-2 cloud removal; SOTA PSNR/SSIM/CC/SAM on 3 benchmarks with <1M params |
| [[01_notes/senf_2021_disturbance]] | Senf & Seidl 2021 — First continental map of Europe's forest disturbance regimes (1986–2016, 35 countries); frequency ↑ in 74%, severity ↓ in 88% of forest area; predecessor to EFDA |
| [[01_notes/maerker_2025_drought_spruce]] | Märker et al. 2025 — Norway spruce at High Tatras treeline show emerging, size-dependent drought sensitivity (largest trees) despite nominal temperature limitation |
| [[01_notes/vazques_2023_drought_treeline]] | Vázquez-Ramírez & Venn 2023 — Factorial snow/fire/drought experiment: drought most strongly suppresses alpine and treeline soil seed bank germination, Australian Alps |
| [[01_notes/klinge_2018_climate_treeline]] | Klinge et al. 2018 — Mongolian boreal treelines: upper treeline thermally limited (~6–9°C MGST), lower treeline moisture limited (230–290 mm yr⁻¹ MAP) |
| [[01_notes/charra_2025_snow_treeline]] | Charra-Vaskou et al. 2026 — Snow-removal experiment: reduced snow cover increases hydraulic/cell damage and mortality in alpine treeline saplings; species-specific resistance vs recovery |
| [[01_notes/dietrich_2026_treeline_della]] | Dietrich & Zeidler 2026 — Viewpoint proposing cold-induced GA/DELLA hormonal signalling (not carbon limitation) as a mechanistic driver of treeline formation; untested in trees |
| [[01_notes/li_2026_climate_treeline]] | Li et al. 2026 — Ensemble SDM + SHAP projects aspect-dependent (south gains, north loses) treeline shifts for Larix chinensis under CMIP6, Qinling Mountains |
| [[01_notes/nguyen_2024_treeline_monitoring]] | Nguyen et al. 2024 — U-Net + IrregConvGRU with knowledge-guided temporal loss (tCA) monitors 1946–2020 Swiss Alps treeline forest cover from a single labelled year |
| [[01_notes/melser_2024_freeze_constraints]] | Melser et al. 2024 — SMAP/SMOS L-band freeze-thaw clustering maps growing-season constraints on boreal productivity, Canada-wide |
| [[01_notes/stewart_2022_torchgeo]] | Stewart et al. 2022 — TorchGeo: PyTorch library for geospatial deep learning; on-the-fly reprojection/resampling, geospatial samplers, multispectral pretrained models; ImageNet pretraining boosts spatial generalization |
| [[01_notes/obuchowicz_2024_greening_switzerland]] | Obuchowicz, Poussin & Giuliani 2024 — National-scale 35-yr Landsat NDVI greening trend for Switzerland (all land cover types); significant acceleration post-2010, temperature-driven; sampling-bias risk unaudited |
