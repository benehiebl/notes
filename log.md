# Operations Log

Append-only record of all wiki operations.

---

## 2026-07-20

**Updated** `04_projects/project_ideas.md`
- Filled in Motivation, Research gap, and Research questions/Hypotheses callouts for "Alpine forest tree line under stress" entry
- Dual-stressor framework: summer drought (VPD stress differential between open ecotone and closed forest) + winter snow cover deficit (soil frost → seedling recruitment failure)
- Focus species: *Pinus cembra* in the Tyrolean Alps; methods include drone-SIF, juvenile dendrochronology, phenocam, satellite SITS, individual crown segmentation
- Incorporated 6 new web sources (Charra-Vaskou 2026 New Phytologist, Baglioni 2025 Biogeosciences, Camarero 2025 Nature Reviews Earth & Env., Grünig 2023, Bringing SAM to New Heights 2025, VHR aerial treeline 2025)

**Updated** `04_projects/02_tree_line_stress.md`
- Filled in full project description: Motivation, Zielsetzung, Work packages (WP1: SIF/dendro, WP2: satellite RS), Outcome (5 planned papers), Zeitrahmen (3-year timeline 2026–2029)
- Key references section with 15+ scientifically verified publications

---

## 2026-06-01

**Revised** `03_papers/06_spatial_autocorrelation.md`
- Replaced NFI-based Italian design with a fully public, general-purpose design: GEDI canopy height as Y, single alpine S2 tile (32TNT, Tyrol) as study area
- Predictor sets unchanged (S / S+T / S+C / S+T+C) but now use SRTM, CHELSA, S2 seasonal composites — no restricted data
- Added tile-extent limitation note: climate SA range may approach or exceed 140 km tile diagonal; optional multi-tile extension (32TNS, 32TPT) recommended for reliable climate variogram estimation
- Study framed as general methodological contribution, replicable in any S2 tile with GEDI coverage

**Created** `03_papers/06_spatial_autocorrelation.md`
- New paper study: "How predictor choice shapes spatial autocorrelation and CV bias in satellite-based vegetation cover models"
- Three-part design: (1) variogram analysis of SA ranges per predictor group; (2) CV inflation experiment (random vs kNNDM for S / S+T / S+C / S+T+C); (3) residual variogram to separate genuine ecological signal from spatial memorisation
- Key output: empirically grounded rule for kNNDM separation distance as a function of max predictor SA range
- Study area: Italy (TRACEVE/NFI plots + S2/Landsat predictors)

**Updated** `index.md` — added paper entry

---

## 2026-05-31 (4)

**Ingested** 4 new sources from `00_literature/` (all contrastive SSL for RS cluster)

**Created** `01_notes/scheibenreif_2022_contrastive.md`
- Scheibenreif et al. (ISPRS Annals 2022): D-SimCLR + MMA — augmentation-free contrastive SSL via S1/S2 co-location as natural positive pairs; 10% labels beats supervised 100%; linear probe on par with fully supervised; cross-dataset transfer to EuroSAT

**Created** `01_notes/stival_2025_contrastive_msi.md`
- Stival et al. (ISPRS J. PRS 2025): SACo+ — semantic band groups (vegetation/urban/water) + LBP texture + temporal positives for MSRSI SSL; 94.72% EuroSAT (ResNet-18) vs SeCo 90.05%; +4.67pp via semantic module; validated on classification, change detection, segmentation

**Created** `01_notes/stival_2026_pixel_contrastive.md`
- Stival et al. (arXiv preprint Jan 2026): PIMC — recurrence plots (2D) of pixel NDVI/EVI/SAVI time series as one contrastive modality vs RSI patches; 2D consistently beats 1D for forecasting; pixel-level SSL directly relevant to per-pixel forest cover regression. Caution: unreviewed preprint, no comparison to TST/PRESTO/SITS-BERT

**Created** `01_notes/li_2026_contrastive.md`
- Li et al. (Sci. Reports 2026): HSSCL — hierarchical multi-level contrastive + GNN geometric consistency for SAR-optical image matching; claimed +20% gains across all metrics are not credible without ablation/error bars; task (image registration) is tangential to forest classification focus

**Updated** `02_concepts/transfer_learning_remote_sensing.md`
- Added "Contrastive SSL Variants for Multispectral RS" section covering D-SimCLR (cross-modal), SACo+ (semantic band groups), PIMC (recurrence plot pixel-wise)
- Added comparison table of contrastive paradigms (SimCLR, SeCo, D-SimCLR, SACo+, PIMC, I-SSKD) by positive pair source, augmentation need, task scale, key strength
- Updated sources list

**Updated** `index.md` — added 4 note entries

---

## 2026-05-31 (3)

**Updated** `02_concepts/national_forest_inventory.md`
- Added section on EU-Forest (mauri_2017) and sPlotOpen (sabatini_2021) as pan-European harmonised products derived from / complementary to NFIs
- Cross-references [[european_ground_truth_databases]]

**Updated** `02_concepts/functional_diversity.md`
- Added section on sPlotOpen as global source of community-weighted trait means (18 traits, 95k plots); notes gap between CWMs and Rao's QE computation

**Updated** `02_concepts/forest_disturbances.md`
- Added "Tree Species Bottleneck" subsection in Management Responses: climate change shrinks replacement species pool by −38% (RCP 4.5), curtailing mixed-forest strategy; cites [[wessely_2023_tree_species_bottleneck]]

**Updated** `02_concepts/transfer_learning_remote_sensing.md`
- Added "Knowledge Distillation for Compact Model Deployment" section: CL teacher > MAE teacher in SSKD despite MAE SSL superiority; I-SSKD combines CL features + MAE attention matching; RS deployment implications re: SeCo vs MAE-style pretraining; cites [[kang_2025_contrastive_vs_mae]]

---

## 2026-05-31 (2)

**Ingested** `kang_2025_contrastive_vs_mae.pdf`

**Created** `01_notes/kang_2025_contrastive_vs_mae.md`
- Kang, Bae, Zhang (IEEE Access 2026): SSKD comparison of CL (MoCo-V3, DINO) vs MAE/SimMIM teachers for ViT-Tiny/Small distillation
- Key finding: CL teachers outperform MAE teachers in SSKD despite MAE being stronger standalone SSL — CL representations are semantically denser
- Weakness diagnosed: attention collapse in CL-distilled students (low NMI, low inter-head KL)
- I-SSKD fix: L_SSKD (CL features) + λ·L_attn (MAE attention scores); λ=0.1; SOTA on ImageNet, ADE20K, COCO
- RS relevance: CL-style pretraining (SeCo-type) may be preferable as teacher for lightweight SITS model distillation

**Updated** `index.md` — added 1 note entry

---

## 2026-05-31

**Ingested** 4 new sources from `00_literature/`

**Created** `01_notes/calvia_2022_pines.md`
- Calvia et al. 2022 (Rendiconti Lincei): Diachronic aerial photo analysis of native Sardinian pine formations 1954–2019
- P. halepensis +235%, P. pinaster +1043%, P. pinea +27%; land abandonment driver; 90% of formations in protected areas
- Methodological note: manual interpretation only, no accuracy assessment, absolute areas remain small

**Created** `01_notes/mauri_2017_EU_tree_data.md`
- Mauri et al. 2017 (Scientific Data): EU-Forest dataset — 249,410 plots, 242 tree species, 1 km INSPIRE grid, 21 NFIs
- Key inputs: NFIs (96%) + Forest Focus + Biosoil; open-access figshare CC4.0
- Critical for wiki: standard ground truth for European tree SDMs; used in wessely_2023 and miettinen_2025

**Created** `01_notes/sabatini_2021_splot.md`
- Sabatini et al. 2021 (GEB): sPlotOpen — 95,104 open-access global vegetation plots, 42,677 taxa, 18 TRY trait CWMs
- Environmentally balanced via global climatic/soil PCA; three replicate subsets; 114 countries
- Relevant as RS ground truth for functional diversity; presence+absence unlike EU-Forest

**Created** `01_notes/wessely_2023_tree_species_bottleneck.md`
- Wessely et al. 2024 (Nature E&E): SDMs for 69 European tree species; bottleneck concept = continuous suitability over 2020–2100
- Average -38% species pool under RCP 4.5; Northern Europe most affected (-52%); mountain ranges buffered
- Only 3.18/3.53/2.56 high-potential sp/km² for timber/carbon/biodiversity remain plantable today

**Created** `02_concepts/european_ground_truth_databases.md`
- New concept covering EU-Forest, sPlotOpen, ICP Forest, and NFIs as pan-European reference datasets
- Includes comparison table and caveats for RS applications (planted vs natural, 1 km aggregation, temporal mismatch)

**Updated** `02_concepts/species_distribution_models.md`
- Added section on key ground truth databases (EU-Forest, sPlotOpen, ICP Forest)
- Added section on tree species bottleneck concept (Wessely et al. 2024): temporal continuity requirement; -33–49% species pool under RCP 2.6–8.5

**Updated** `index.md`
- Added 4 new note entries and 1 new concept entry

---

## 2026-05-28

**Created** `03_papers/03_landsat_data_publication.md`
- Split off from `03_papers/03_tree_species_cover_landsat.md` — new file is a standalone data publication focusing on the methodology and dataset
- Covers: Landsat time series assembly, TSTpad model, three-stage contrastive training workflow, mapping scheme, validation scheme, technical validation (temporal consistency, sensor consistency, observation density effects), data records, and limitations specific to dataset quality
- Ecological analysis sections (EVE expansion trends, latitudinal/altitudinal gradients, climate driver attribution, winter greening) remain in `03_tree_species_cover_landsat.md`
- Updated `index.md` with new `03_papers/` section listing both paper files

---

## 2026-05-25

**Revised** `04_projects/project_ideas.md`
- Reformulated both project ideas ("Forests under pressure", "Dying trees in Tyrolean forests") with precise scientific language
- Grounded motivation in specific mechanisms (hotter droughts, VPD, xylem hydraulic failure, *Ips typographus* dynamics) backed by wiki sources
- Added quantitative context from [[wegler_2026_canopy_cover_loss]], [[soto_2025_disturbance]], [[babst_2019_redistribution]], [[drought_mortality]], [[forest_disturbances]]
- Sharpened research gaps to distinguish what is truly missing vs. what existing products (EFDA, Sentinel-2) already address
- Reformulated research questions to be testable and species-specific

---

## 2026-05-22

**Ingested** `feng_2026_tessera.pdf` → `01_notes/feng_2026_tessera.md`
- Feng et al. 2026 (arXiv): TESSERA — pixel-wise multi-modal (S1+S2) foundation model; Barlow Twins + temporal sampling invariance + global shuffling + mix-based regulation; 45.7M params; open weights + global 10m int8 embeddings; SOTA on TreeSatAI-TS (F1=79.23), Austrian Crop segmentation (mIoU=53.12), Borneo CHM (RMSE=13.1m), Biomassters (RMSE=27.43 t/ha)
- Updated `02_concepts/geospatial_foundation_models.md` — added TESSERA section and expanded comparison table

**Ingested** `ball_2026_foundation_models.pdf` → `01_notes/ball_2026_foundation_models.md`
- Ball et al. 2026 (bioRxiv): GFM embeddings (AlphaEarth + Tessera) for 18-class tree species mapping in Trentino; WF1=0.83 vs 0.80 baseline; 5% training data near-asymptotic; soft labels from species proportions outperform hard labels; temporal transfer drops 9–15%
- Updated `02_concepts/geospatial_foundation_models.md` — added "Tree Species Mapping with GFMs" section
- Updated `02_concepts/tree_species_mapping.md` — added [[ball_2026_foundation_models]] to sources

**Ingested** `soto_2025_disturbance.pdf` → `01_notes/soto_2025_disturbance.md`
- Viana-Soto & Senf 2025 (ESSD): European Forest Disturbance Atlas (EFDA); annual Landsat-based disturbance detection for 35 European countries 1985–2023; F1=0.89; 439,000 km² total disturbed area; harvest 79.2%; first product with multiple events per pixel
- Updated `02_concepts/forest_disturbances.md` — added "European Forest Disturbance Atlas (EFDA)" section

**Ingested** `li_2023_land_cover_map.pdf` → `01_notes/li_2023_land_cover_map.md`
- Li et al. 2023 (ESSD): SinoLC-1 — first 1 m national land-cover map of China; weakly + self-supervised L2HNet; OA=73.6%; no manual annotation; note is peripheral to European forest focus but methodology (L2H resolution mismatch resolution) is relevant

## 2026-05-15

**Refactored**: `adagbasa_2022_deep_learning_s2.md` — added inline SVG/HTML diagrams for the multi-source data pipeline, stratified K-fold scheme, and classifier F1 score comparison bar chart.

---

## 2026-05-05

**Ingested**: `bayle_2024_landsat_greening_inflated.pdf`

**Created**:
- `01_notes/bayle_2024_landsat_greening_inflated.md` — full summary of Bayle et al. 2024 (Ecography)
- `02_concepts/landsat.md` — Landsat program, sensors, observation density patterns, limitations
- `02_concepts/ndvi.md` — NDVI definition, NDVImax, limitations, alternatives
- `02_concepts/phenology.md` — Vegetation phenology, double-logistic fitting, PAM clustering, alpine context
- `02_concepts/sampling_bias_remote_sensing.md` — Core methodological concept: false greening trends from non-uniform observation frequency
- `02_concepts/vegetation_greenness_trends.md` — Greening/browning trends: detection methods, drivers, caveats

**Updated**: `index.md` — initialised index with all concept and note pages (note: index.md and log.md moved to root by user)

---

## 2026-05-05 (2)

**Ingested**: `bricca_2026_topo_diversity.pdf`

**Created**:
- `01_notes/bricca_2026_topo_diversity.md` — full summary of Bricca et al. 2026 (Global Ecology and Biogeography)
- `02_concepts/functional_diversity.md` — Rao's QE, multi-FD, taxonomic vs functional diversity, functional redundancy
- `02_concepts/plant_functional_traits.md` — TRY database, major trait spectra, ITV, remote sensing links
- `02_concepts/topographic_microclimate.md` — Solar radiation, aspect, soil moisture, topographic buffering

**Updated**: `index.md` — added 3 new concept pages and bricca_2026 note

---

## 2026-05-05 (3)

**Ingested**: `gasparini_2022_nfi_italy.pdf`

**Note**: This is a reference book (580+ pages), not a journal article. Summary covers methods framework and headline results from forewords and Chapter 1; Chapters 7–13 contain detailed results.

**Created**:
- `01_notes/gasparini_2022_nfi_italy.md` — summary of INFC2015 book (Gasparini et al. 2022, Springer)
- `02_concepts/national_forest_inventory.md` — NFI purpose, multi-phase sampling design, Italian NFI history, role as remote sensing ground truth

**Updated**: `index.md` — added national_forest_inventory concept and gasparini_2022 note

---

## 2026-05-05 (4)

**Ingested**: `grabska_2024_tree_species_map.pdf`

**Created**:
- `01_notes/grabska_2024_tree_species_map.md` — summary of Grabska-Szwagrzyk et al. 2024 (ESSD)
- `02_concepts/sentinel_2.md` — Sentinel-2 bands, revisit, STMs, red-edge advantage, comparison with Landsat
- `02_concepts/tree_species_mapping.md` — species mapping methods, class imbalance, accuracy assessment, scale-dependent strategies

**Updated**: `index.md` — added 2 concept pages and grabska_2024 note

---

## 2026-05-05 (5)

**Ingested**: `grünig_2026_climate_change_disturbances_forest.pdf`

**Created**:
- `01_notes/grünig_2026_climate_change_disturbances_forest.md` — summary of Grünig et al. 2026 (Science)
- `02_concepts/forest_disturbances.md` — wildfire, bark beetles, windthrow, disturbance interactions, vegetation feedbacks, remote sensing detection

**Updated**: `index.md` — added forest_disturbances concept and grünig_2026 note

---

## 2026-05-05 (6)

**Ingested**: `he_2015_remote_sensing_sdm.pdf`

**Created**:
- `01_notes/he_2015_remote_sensing_sdm.md` — summary of He et al. 2015 (Remote Sensing in Ecology and Conservation)
- `02_concepts/species_distribution_models.md` — SDMs, response/predictor variables, correlative-process continuum, NG-SDM framework, circularity warning

**Updated**:
- `02_concepts/ndvi.md` — added SDM use section (NDVI as biotic predictor, circularity risk); added he_2015 to sources
- `02_concepts/phenology.md` — added phenology as SDM predictor section (growing season length, tree species discrimination); added grabska_2024 and he_2015 to sources

**Updated**: `index.md` — added species_distribution_models concept and he_2015 note

---

## 2026-05-05 (7)

**Ingested**: `herraiz_2025_phen_shifts_mediterranean.pdf`

**Created**: `01_notes/herraiz_2025_phen_shifts_mediterranean.md` — summary of Herraiz et al. 2025 (Ecological Indicators)

**Updated**:
- `02_concepts/phenology.md` — added Mediterranean inverted phenological cycle section (NDVI peak in winter, aridity effects on SOS/LOS, timing vs magnitude trend distinction)
- `02_concepts/vegetation_greenness_trends.md` — added species-level greening variation section from Mediterranean Landsat study; added herraiz_2025 to sources

**Updated**: `index.md` — added herraiz_2025 note

---

## 2026-05-05 (8)

**Ingested**: `hiebl_2025_pretraining.pdf`

**Created**:
- `01_notes/hiebl_2025_pretraining.md` — summary of Hiebl et al. 2025 (JAG); user's own paper on pretraining for EVE cover mapping
- `02_concepts/transfer_learning_remote_sensing.md` — pretraining strategies, MVP self-supervised learning, epistemic/aleatoric uncertainty, spatial autocorrelation in CV

**Updated**: `index.md` — added transfer_learning_remote_sensing concept and hiebl_2025 note

---

## 2026-05-04 (9)

**Ingested**: `jin_2023_drivers_differentiation_evergreen.pdf`

**Created**:
- `01_notes/jin_2023_drivers_differentiation_evergreen.md` — summary of Jin & Qian 2023 (Plant Diversity); canopy trees shift leaf habit faster than understory shrubs along latitudinal temperature gradient; canopy buffering mechanism
- `02_concepts/leaf_habit_latitudinal_gradient.md` — evergreen–deciduous latitudinal gradient; canopy vs. understory differentiation; species range as climatic niche proxy; climate change implications

**Updated**:
- `02_concepts/plant_functional_traits.md` — added leaf habit economics section (evergreen vs. deciduous resource strategy, phylogenetic conservatism); added jin_2023 to sources
- `02_concepts/topographic_microclimate.md` — added canopy microclimate buffering section (biotic analog of topographic buffering; strata-specific effective climate); added jin_2023 to sources

**Updated**: `index.md` — added leaf_habit_latitudinal_gradient concept and jin_2023 note

---

## 2026-05-05 (10)

**Ingested**: `lecun_1998_efficient_backprop.pdf`

**Note**: Chapter from "Neural Networks: Tricks of the Trade" (Springer, 1998), not a journal article. Foundational reference for neural network training methodology.

**Created**:
- `01_notes/lecun_1998_efficient_backprop.md` — summary of LeCun et al. 1998 practical backprop tricks (SGD, normalisation, sigmoid, initialisation, learning rates, Hessian theory)
- `02_concepts/neural_network_training.md` — backprop algorithm, stochastic vs batch learning, input normalisation, activations, weight initialisation, Hessian/learning rate theory, modern optimizers, regularisation

**Updated**: `index.md` — added neural_network_training concept and lecun_1998 note

---

## 2026-05-05 (11)

**Ingested**: `liu_2023_spectral_spatial_resolution_effect.pdf`

**Created**:
- `01_notes/liu_2023_spectral_spatial_resolution_effect.md` — summary of Liu et al. 2023 (RSEC); Sentinel-2 at 10m best for tree species diversity mapping; optimal spatial resolution 10–15m; Rao's Q and GLCM texture best metrics; SVH confirmed
- `02_concepts/spectral_diversity_biodiversity.md` — Spectral Variability Hypothesis, spectral heterogeneity metrics (Rao's Q, GLCM, CV, CHA, CHV, SAM, SSD), optimal spatial resolution, best spectral bands, phenological timing

**Updated**:
- `02_concepts/sentinel_2.md` — added TSD mapping section: 10m optimal resolution, red-edge + NIR advantage, sensor comparison results; added liu_2023 to sources
- `02_concepts/functional_diversity.md` — added spectral Rao's Q link to functional Rao's QE; added RS-diversity monitoring context; added liu_2023 to sources
- `02_concepts/tree_species_mapping.md` — added SVH-based spectral diversity approach section; added liu_2023 to sources

**Updated**: `index.md` — added spectral_diversity_biodiversity concept and liu_2023 note

---

## 2026-05-05 (12)

**Ingested**: `mattioli_2025_carta_forestale.pdf`

**Note**: Short paper in Italian (6 pages) with English abstract. Presents CFI2020, Italy's first national forest map at 1:10,000 scale.

**Created**: `01_notes/mattioli_2025_carta_forestale.md` — summary of Mattioli et al. 2025 (Forest@); CFI2020 cartographic forest map; three simultaneous forest definitions; >10 Mha Italian forest area; distinction from INFC statistical survey

**Updated**: `02_concepts/national_forest_inventory.md` — added CFI2020 section (cartographic vs statistical NFI distinction; three forest definitions; headline area; comparison table with INFC2015; SINFor portal)

**Updated**: `index.md` — added mattioli_2025 note

---

## 2026-05-05 (13)

**Ingested**: `midolo_2026_denser_vegetation.pdf`

**Created**:
- `01_notes/midolo_2026_denser_vegetation.md` — summary of Midolo et al. 2026 (Science Advances); 60yr European vegetation community change; nitrogen dominant driver (+0.25 CM_EIV); light decline (-0.12); thermophilisation weak except alpine; 644,524 plots, random forest spatiotemporal interpolation
- `02_concepts/vegetation_community_change.md` — EIV bioindication system, nitrogen eutrophication, vegetation densification, habitat-specific moisture changes, acid rain recovery, thermophilisation pattern; RS links to NDVI greening

**Updated**: `02_concepts/vegetation_greenness_trends.md` — added eutrophication/densification section (nitrogen-driven greening as major non-climatic RS signal; management cessation); added midolo_2026 to sources

**Updated**: `index.md` — added vegetation_community_change concept and midolo_2026 note

---

## 2026-05-05 (14)

**Ingested**: `miettinen_2025_forest_maps_europe.pdf`

**Note**: Data in Brief paper describing a publicly available dataset (Zenodo: doi.org/10.5281/zenodo.13143235). Part of EU PathFinder project.

**Created**: `01_notes/miettinen_2025_forest_maps_europe.md` — summary of Miettinen et al. 2025 (Data in Brief); pan-European 10m AGB/volume/DCP maps; kNN with 14-country NFI + Sentinel-2; regression-to-mean bias pattern; NFI plot density as quality driver

**Updated**:
- `02_concepts/national_forest_inventory.md` — added model-assisted estimation/wall-to-wall mapping section (kNN, regression-to-mean, plot density effect, PathFinder framework); added miettinen_2025 to sources
- `02_concepts/sentinel_2.md` — added forest structure mapping section (AGB, volume, DCP from S2+NFI kNN); added miettinen_2025 to sources

**Updated**: `index.md` — added miettinen_2025 note

---

## 2026-05-05 (15)

**Ingested**: `noce_2023_altitude_shift_tree_italy.pdf`

**Created**: `01_notes/noce_2023_altitude_shift_tree_italy.md` — summary of Noce et al. 2023 (Front. For. Glob. Change); MaxEnt SDMs for 20 Italian tree species; VHR-REA_IT 2.2km climate; 5 mountain sections; silver fir = most vulnerable; larch + turkey oak = winners; tree line upward shift; Northern Apennines most impacted

**Updated**:
- `02_concepts/species_distribution_models.md` — added MaxEnt altitudinal shift section (NFI-based occurrence data, high-res climate, altitudinal band analysis, Italian results); added noce_2023 to sources

**Updated**: `index.md` — added noce_2023 note

---

## 2026-05-05 (16)

**Ingested**: `pflugmacher_2019_lulc_landsat.pdf`

**Created**: `01_notes/pflugmacher_2019_lulc_landsat.md` — summary of Pflugmacher et al. 2019 (RSE); pan-European LULC mapping with Landsat STMs + LUCAS; OA=75.1%; auxiliary environmental features most impactful (+4.7pp); 3yr multi-year pooling eliminates cloud gaps; CORINE comparison

**Updated**: `02_concepts/landsat.md` — added STMs for land cover mapping section (seasonal medians, annual variance statistics, multi-year pooling, LUCAS-based map results, CORINE comparison); added pflugmacher_2019 to sources

**Updated**: `index.md` — added pflugmacher_2019 note

---

## 2026-05-05 (17)

**Ingested**: `sylvain_2024_tree_species_uncertainty.pdf`

**Created**: `01_notes/sylvain_2024_tree_species_uncertainty.md` — summary of Sylvain et al. 2024 (JAG); 9-model CNN super-ensemble for 0.9m boreal tree species mapping in Quebec; F1=0.90; CHM adds +5pp; inter-model agreement as validated spatially explicit uncertainty map

**Updated**:
- `02_concepts/tree_species_mapping.md` — added CNN/deep learning approach section (super-ensemble, CHM integration, agreement uncertainty); added sylvain_2024 to sources
- `02_concepts/transfer_learning_remote_sensing.md` — added CNN ensemble agreement uncertainty section; comparison with hiebl_2025 deep ensemble; added sylvain_2024 to sources

**Updated**: `index.md` — added sylvain_2024 note

---

## 2026-05-05 (18) — Concept page cleanup

**Task**: Replace PDF references with wiki backlinks and add tags to all concept pages.

**Updated all 18 concept pages in `02_concepts/`**:
- Replaced all `filename.pdf` references with `[[filename]]` wiki backlinks (both in Sources lines and inline body citations)
- Added YAML `tags:` fields to every concept page; pages without frontmatter received full frontmatter blocks

**Tag assignments:**
- `landsat.md`: remote-sensing, landsat, time-series, land-cover
- `ndvi.md`: remote-sensing, vegetation-index
- `phenology.md`: remote-sensing, forest-ecology, vegetation
- `sampling_bias_remote_sensing.md`: remote-sensing, methodology, time-series
- `vegetation_greenness_trends.md`: remote-sensing, forest-ecology, vegetation
- `functional_diversity.md`: forest-ecology, biodiversity, remote-sensing
- `plant_functional_traits.md`: forest-ecology, biodiversity
- `topographic_microclimate.md`: forest-ecology, remote-sensing
- `national_forest_inventory.md`: forest-ecology, remote-sensing, methodology
- `sentinel_2.md`: remote-sensing, sentinel-2, machine-learning
- `tree_species_mapping.md`: remote-sensing, forest-ecology, machine-learning, deep-learning
- `forest_disturbances.md`: forest-ecology, remote-sensing
- `species_distribution_models.md`: forest-ecology, machine-learning, remote-sensing
- `transfer_learning_remote_sensing.md`: deep-learning, machine-learning, remote-sensing
- `leaf_habit_latitudinal_gradient.md`: forest-ecology, biodiversity
- `neural_network_training.md`: deep-learning, machine-learning
- `spectral_diversity_biodiversity.md`: remote-sensing, forest-ecology, biodiversity
- `vegetation_community_change.md`: forest-ecology, biodiversity, remote-sensing

---

## 2026-05-05 (19) — Source completeness and un-integrated notes

**Task**: (1) Add sources to every paragraph/section in concept pages; (2) integrate 7 pre-existing but un-referenced notes into concept pages.

**Un-integrated notes now integrated:**
- `amico_2025_nfi_italy` → `national_forest_inventory.md` (tessellation sampling, annual rolling-panel IFNI, RS integration, participatory design)
- `bell_2024_hindcasting_forest_structure` → `national_forest_inventory.md` + `landsat.md` (GNN temporal transferability, hindcasting/updating Landsat forest maps)
- `brown_2025_alphaearth` → `transfer_learning_remote_sensing.md` (geospatial foundation models, AEF, multi-modal pretraining, few-shot mapping)
- `chen_2020_contrastive_framework` → `transfer_learning_remote_sensing.md` (SimCLR contrastive learning, NT-Xent loss, augmentation policy)
- `fady_2025_native_trees_mediterranean` → `species_distribution_models.md` (Mediterranean tree diversity baseline, 496 spp, endemism hotspots, data gaps)
- `fischer_2025_glocal_canopy_atlas` → `sentinel_2.md` (satellite CHM validation against ALS, R²<0.38 at native resolution, Lang et al.)
- `francioni_2026_canopy_closure` → `forest_disturbances.md` + `vegetation_community_change.md` + `functional_diversity.md` (25yr understory diversity decline, canopy closure drivers, ICP Forests)

**Sourcing fixes across all concept pages:**
- `forest_disturbances.md`: added [[grünig_2026_climate_change_disturbances_forest]] to all unsourced bullets; added [[albrich_2019_climate_change_mountain_forests]] to disturbance interactions and management responses; added [[francioni_2026_canopy_closure]] to vegetation feedbacks
- `national_forest_inventory.md`: added per-bullet sources for kNN section; added temporal transferability section (bell_2024); added enhanced NFI section (amico_2025)
- `transfer_learning_remote_sensing.md`: added SimCLR section (chen_2020); added geospatial foundation models section (brown_2025)
- `vegetation_community_change.md`: added per-paragraph sources; added 25yr understory decline section (francioni_2026)
- `species_distribution_models.md`: added paragraph-level sources to predictor section; added Mediterranean tree diversity section (fady_2025)
- `sentinel_2.md`: added satellite CHM validation section (fischer_2025)
- `landsat.md`: added temporal transferability section (bell_2024); added sources to Key Limitations section
- `functional_diversity.md`: added francioni_2026 as long-term monitoring application
---

## 2026-05-06

**Batch ingest**: 28 research papers from `00_literature/` — batch converted with `markitdown`, then summarized.

**Created (01_notes/)**:
- `adagbasa_2022_deep_learning_s2.md` — MLP + Sentinel-2 grass species discrimination; F1=92%
- `alessi_2023_sampling_approaches.md` — Probabilistic vs preferential sampling for Italian forest diversity
- `astola_2019_s2_l8_comparison.md` — Sentinel-2 outperforms Landsat 8 for boreal forest variables; red-edge B05 best predictor
- `atzberger_2020_monitoring_forests_eu.md` — EU report on RS monitoring of forests; 6 themes reviewed
- `bolyn_2022_tree_species_mapping.md` — UNet++ CNN for tree species proportions in Wallonia; OA_maj=0.73
- `hemmerling_2021_forest_mapping_s2.md` — Dense Sentinel-2 TS maps 17 species in Brandenburg; spectral TS dominates
- `kang_2021_lai_landsat.md` — Data-driven 30 m LAI from Landsat via MODIS; RMSE=0.8, r²=0.88 CONUS
- `kattenborn_2021_review_cnn_vegetation_monitoring.md` — Review of CNNs in vegetation RS; CNNs outperform shallow ML
- `li_2022_cloud_detection.md` — Systematic review of cloud/shadow detection; deep learning + temporal features emerging best
- `liu_2023_mapping_tree_species_diversity.md` — SVH-based TSD mapping with S1+S2+topography; R²=0.628 best
- `nguyen_2022_forest_mapping_explainable.md` — Explainable CNN for forest mapping at Swiss Alps treeline
- `pu_2021_tree_species_mapping_review.md` — 40-year review of tree species mapping; "multiple method" trend
- `reichstein_2019_deep_learning_earth_sciences.md` — DL + process understanding for Earth system science; hybrid models
- `safonova_2023_small_data.md` — 10 DL techniques for small data in RS; decision flowchart
- `schloegl_2026_reproducibility.md` — Reproducibility in geoscientific data analysis; FAIR, version control
- `sze_2017_efficient_dnn_processing.md` — Tutorial on efficient DNN processing; energy/bandwidth bottlenecks
- `thom_2026_disturbance_suitability.md` — Suitability of 53 species for post-disturbance regeneration in Central Europe
- `tong_2023_forest_densification_china.md` — 30-year Landsat shows forest tripling in southern China
- `torres_2021_forest_health_remote_sensing.md` — PRISMA review RS for forest health; early warning is key gap
- `turubanove_2023_canopy_landsat.md` — Annual 30 m canopy height Europe 2001–2021; decline after 2016
- `vaswani_2023_attention_is_all.md` — Original Transformer paper (Attention is All You Need)
- `vihervaara_2017_ebv_remote_sensing.md` — EBVs and RS for national biodiversity monitoring (Finland)
- `wang_2022_tree_species_mapping.md` — S2 vs L8 for plantation species mapping; temporal saturation ~2 images
- `wegler_2025_tree_species_germany.md` — National 10 m tree species map Germany; S2+S1+DEM; F1=0.89
- `wegler_2026_canopy_cover_loss.md` — Species-specific canopy loss Germany 2018–2024; spruce 51.3% of loss
- `wen_2023_transformers_time_series.md` — Survey of Transformers for time series; forecasting, anomaly detection, classification
- `xu_2022_cloud_native_algorithms.md` — Cloud-native containerisation for user-defined DL on RS Data Cubes
- `yuan_2025_sits_augmentation.md` — 11 SITS augmentation techniques; interpolation resampling best for cross-year

**Created (02_concepts/)**:
- `transformers_time_series.md` — Transformer architecture for time series; SITS adaptations; TST, InceptionTime, pre-training
- `ebv_biodiversity_monitoring.md` — Essential Biodiversity Variables framework; RS contributions to 4 EBV classes

**Updated (02_concepts/)**:
- `transfer_learning_remote_sensing.md` — Added 7 new sources; new sections on small data techniques (safonova), hybrid DL (reichstein), Transformer architecture (vaswani, wen), CNN efficiency (kattenborn, sze)
- `tree_species_mapping.md` — Added 13 new sources; new sections on national-scale mapping, soft classification, sensor comparison, dense TS approach, explainable DL
- `forest_disturbances.md` — Added 5 new sources; new sections on RS forest health review (torres), canopy height change Europe (turubanova), species-specific loss Germany (wegler_2026), post-disturbance regeneration (thom), forest expansion China (tong)

**Updated**: `index.md` — added 28 notes + 2 concept pages

---

## 2026-05-06 (2)

**Ingested**: Code repositories in `00_literature/`

**Created (01_notes/)**:
- `traceve_pretraining.md` — TRACEVE pretraining codebase; InceptionTimeEnsemble + BetaNLL + MVP pretraining on Sentinel-2 SITS; codebase for hiebl_2025_pretraining
- `ae_training.md` — TRACEVE + AlphaEarth fusion repo; MLPAlpha, TST, CrossAttentionAlpha architectures; codebase for Hiebl et al. 2026 (ISPRS Annals)
- `ls_mapping.md` — TSTpad on multi-annual Landsat time series for forest type + multi-target EVE/Dec/NL cover regression for Italy

**Updated**: `index.md` — added 3 repository notes

---

## 2026-05-06 (3)

**Revised**: Repository notes using proper /summarize-codebase skill template

**Updated (01_notes/)**:
- `traceve_pretraining.md` — rewritten with full codebase template; added BetaNLLLoss forward pass detail, MVP callback mechanics, bootstrap training per-head optimizer detail
- `ae_training.md` — rewritten; added CrossAttentionAlpha forward pass (query=AE embd, KV=S2 time steps), skip-connection design rationale, TST time_encoding implementation detail
- `ls_mapping.md` — rewritten; added TSTpad architecture detail (timestamp encoding, padding mask, multi-target head), Optuna HPO mechanics, progressive fine-tuning hierarchy table

---

## 2026-05-06 (4)

**Ingested**: `hiebl_2026_alphaearth.pdf`

**Created**:
- `01_notes/hiebl_2026_alphaearth.md` — Hiebl et al. 2026 (ISPRS Annals); Cross-Attention fusion of AEF + Sentinel-2/CHELSA for Italian forest type and EVE cover mapping; TST_AEF,S2 outperforms stand-alone models; AEF matches S2 accuracy 10–24× faster with no preprocessing

**Updated**: `index.md`

---

## 2026-05-06 (5)

**Lint and fix pass** — resolved all 7 issues identified in lint report:

1. ✅ **Stale 00_literature_md links** — removed from 12 early notes (albrich_2019, amico_2025, bell_2024, brown_2025, chabalala_2023, chastain_2007, chen_2020, deluca_2022, fady_2025, fischer_2025, francioni_2026, koch_2025)
2. ✅ **Title-case broken links** — removed from same 12 notes; replaced with proper lowercase wikilinks
3. ✅ **Missing Related pages sections** — added to all 29 notes that were missing it (12 old notes reformatted + 17 batch notes normalised); capitalisation `## Related Pages` → `## Related pages` normalised across all 32 remaining notes
4. ✅ **safonova year** — confirmed already correct (safonova_2023)
5. ✅ **Missing concept pages** — created `02_concepts/lai_estimation.md` and `02_concepts/cloud_detection.md`; added to index.md
6. ✅ **hiebl_2025 missing 2026 link** — added `[[hiebl_2026_alphaearth]]` to hiebl_2025_pretraining Related pages
7. ✅ **liu_2023_mapping not in spectral_diversity sources** — added to spectral_diversity_biodiversity.md Sources line

**Final state:** 0 broken links, 0 orphan pages, 0 missing Related pages, 22 concept pages, 60 notes, all indexed.

---

## 2026-05-06 (6)

**YAML frontmatter** — added headers to all notes missing them per /summarize-paper skill spec.

- Added YAML frontmatter (`title`, `authors`, `year`, `source`, `tags`, `status: read`) to 32 notes that were missing it
- Fixed 2 pre-existing headers that lacked a required tag (`midolo_2026`, `miettinen_2025`)
- All 61 notes now have valid frontmatter with at least one of: `deep-learning`, `machine-learning`, `remote-sensing`, `forest-ecology`

---

## 2026-05-07

**Ingested**: `00_literature/sattstools/` (new git submodule)

**Created**:
- `01_notes/sattstools.md` — sattstools preprocessing library; rsutils (cloud masking S2/Landsat), outlier.py (IQR/z-score/IsoForest), smooth.py (Whittaker+FFT+RBF), TSpreprocess.py (TSRobustStandardize, modality-specific augmentation for optical/climate/AEF); shared backbone for traceve_pretraining, ae_training, ls_mapping

**Updated**: `index.md`

---

## 2026-05-13

**Ingested**: `mila_2024_spatial_proxies.pdf`, `pebesma_2025_spatial_data.pdf`

**Created**:
- `01_notes/mila_2024_spatial_proxies.md` — Milà et al. 2024 (GMD); simulation + Spain case studies on when coordinates/EDF/RFsp help random forests; kNNDM CV vs random CV; RF–GLS benchmark
- `01_notes/pebesma_2025_spatial_data.md` — Pebesma et al. 2025 (arXiv); SDSL workshop synthesis comparing R/Python/Julia spatial ecosystems; variable support, spherical geometry, data cubes, cross-language tooling
- `02_concepts/spatial_proxies_random_forest.md` — decision rules for adding spatial proxies to RF predictors; AOA-based diagnostics; RF–GLS alternative
- `02_concepts/area_of_applicability.md` — Meyer & Pebesma's predictor-space distance metric; flags feature extrapolation per pixel
- `02_concepts/support_intensive_extensive.md` — variable support (point vs block) and intensive/extensive properties; split/merge policies; software status across sf, GeoPandas, Julia

**Updated**:
- `02_concepts/transfer_learning_remote_sensing.md` — Spatial Autocorrelation in Validation section extended with random CV mis-ranking + kNNDM CV; added Mila 2024 to Sources
- `02_concepts/sampling_bias_remote_sensing.md` — added cross-link to spatial-clustered-sampling overfitting via Mila 2024
- `index.md` — added 2 new notes and 3 new concepts

---

## 2026-05-14

**Ingested batch of 30 sources** across forest ecology, RS forest mapping, DL methodology, uncertainty, and biodiversity.

**Created (30 notes in `01_notes/`)**:

*Forest ecology (8)*
- `berger_2006_distribution_eve.md` — Insubrian EVE distribution along precipitation × bedrock gradients
- `chelli_2017_climate.md` — Italy climate-vegetation review across four climatic zones
- `conedera_2018_drivers_evergreen.md` — Lago Maggiore EVE drivers; propagule pressure > climate
- `yel_2026_deciduous_forests.md` — RS review of climate-change impacts on deciduous forests
- `schuldt_2020_drought_forest.md` — 2018 Central European drought first assessment
- `dyderski_2025_species_shift.md` — SDMs for 20 European tree species under CMIP6 SSPs
- `kempf_2023_greening.md` — Pan-European NDVI greening + climate anomalies
- `babst_2019_redistribution.md` — 20th-century redistribution of climatic drivers of tree growth

*RS mapping (8)*
- `blickensdörfer_2024_tree_species.md` — National German tree species map with S1/S2 + NFI
- `kollert_2021_tree_species.md` — Sentinel-2 LSP + composites for Tyrol tree species
- `hamedianfar_2022_deep_learning.md` — Critical review of DL for forest inventory
- `lang_2024_canopy_height.md` — Global 10 m canopy height from GEDI + S2
- `qin_2026_forest_cover.md` — Annual 30 m forest cover in cloud-prone southern China
- `zhao_2022_forest_harvesting.md` — Monthly forest harvesting with Sentinel-1 + U-Net
- `yang_2020_modis_evergreen.md` — FEVC-CV fractional evergreen cover from MODIS NDVI
- `yan_2025_population.md` — Transformer + CNN hybrid for population estimation

*DL methodology (10)*
- `bernico_2019_domain_similarity.md` — Log-linear scaling of transfer learning with data × similarity
- `klehr_2025_synthetic_data.md` — Synthetic mixed training data for tree species fractions
- `sylvain_2021_ensemble.md` — Bias correction + ensemble for predictive mapping uncertainty
- `tseng_2024_presto.md` — PRESTO lightweight pretrained RS transformer
- `yuan_2022_sitsformer.md` — SITS-Former patch-based Transformer with SSL pretraining
- `yuan_2023_pretraining.md` — SITS-BERT: first BERT-style SSL pretraining for SITS
- `zerveas_2020_framework_transformer.md` — TST Transformer for multivariate time series
- `zangh_2017_generalization.md` — Random label memorisation challenges classical learning theory
- `tan_2021_tser.md` — TSER benchmark for time series extrinsic regression
- `wang_2026_foundation.md` — AlphaEarth + GEDI + VHR for annual forest carbon stock loss

*Uncertainty + biodiversity (4)*
- `lakshminarayan_2017_uncertainty.md` — Deep ensembles for predictive uncertainty
- `seitzer_2022_uncertainty.md` — β-NLL fix for heteroscedastic NLL pitfall
- `skidmore_2021_biodiversity.md` — Priority list of satellite-observable EBVs
- `grantham_2020_anthropogenic_modification.md` — Forest Landscape Integrity Index globally

**Created (4 new concept pages in `02_concepts/`)**:
- `evergreen_broadleaved_expansion.md` — Drivers and RS of EVE spread; climate × propagule × land-use hierarchy
- `deep_ensemble_uncertainty.md` — Recipe, β-NLL fix, epistemic + aleatoric components, wiki applications
- `transformer_sits.md` — Pretrained Transformer architectures for SITS — TST/SITS-BERT/SITS-Former/PRESTO lineage
- `drought_mortality.md` — Hotter droughts, hydraulic failure, 20th-c. climate-driver redistribution

**Updated (concept pages)**:
- `forest_disturbances.md` — added drought_mortality, monthly harvest detection, forest integrity sections; new sources
- `tree_species_mapping.md` — added mixed-stand validation, synthetic data, mountain forests, foundation model sections
- `transfer_learning_remote_sensing.md` — added Bernico scaling law, SITS Transformer lineage, synthetic data, uncertainty integration
- `transformers_time_series.md` — added cross-link to transformer_sits concept; new sources
- `ebv_biodiversity_monitoring.md` — added Skidmore prioritisation + Grantham FLII sections
- `vegetation_greenness_trends.md` — added Kempf pan-European anomalies, Babst 20th-c. redistribution, Yel RS methods
- `species_distribution_models.md` — added Dyderski trait-based generalisation section
- `neural_network_training.md` — added Zhang generalisation, deep ensemble uncertainty references

**Updated**: `index.md` — added 30 notes + 4 new concepts

---

## 2026-05-14 (lint pass)

**Lint findings** (all 7 categories audited):
1. ✅ Format compliance — all 94 notes + 29 concepts have valid frontmatter, required tags, Related pages, and (for concepts) Summary/Sources/Last updated
2. ✅ Broken wiki-links — 0
3. ✅ Orphan files — 0 truly orphan; 3 weakly linked (alessi_2023, sattstools, yan_2025) only via index.md
4. 🔧 Missing concept pages — created 2: `sentinel_1_sar` and `geospatial_foundation_models`
5. 🔧 Stale concept pages — updated 7 with new sources and integrative sections: `sentinel_2`, `phenology`, `ndvi`, `national_forest_inventory`, `cloud_detection`, `landsat`, `lai_estimation`, `plant_functional_traits`
6. 🔧 Missing cross-links — added in `brown_2025_alphaearth`, `fischer_2025_glocal_canopy_atlas`, `hiebl_2025_pretraining`, `hiebl_2026_alphaearth`, `wegler_2026_canopy_cover_loss`, `mila_2024_spatial_proxies`, `lang_2024_canopy_height` (linking to new methodological ancestors and companion foundation-model papers)

**Created**:
- `02_concepts/sentinel_1_sar.md` — Sentinel-1 C-band SAR; complementary to optical S-2 for cloud-prone regions and structure-sensitive forest mapping
- `02_concepts/geospatial_foundation_models.md` — AlphaEarth + PRESTO paradigm; comparison; use patterns for forest mapping

**Updated** (concept pages with new sources + sections):
- `sentinel_2.md` — added Companion Sensors, Foundation Models, SITS Pretraining sections; +9 new sources
- `phenology.md` — added Evergreen FEVC, Climate Stress, LSP Mountain Mapping sections; +6 new sources
- `ndvi.md` — added alternatives table, time-series statistics, drought-anomaly sections; +4 new sources
- `national_forest_inventory.md` — added NFI–pixel linking and synthetic mixing sections; +3 new sources
- `cloud_detection.md` — added cloud-prone regions, SAR alternatives, mountain forest strategies; +4 new sources
- `landsat.md` — +5 new sources
- `lai_estimation.md` — +1 new source (yel_2026)
- `plant_functional_traits.md` — +1 new source (dyderski_2025)

**Updated** (cross-links between notes):
- `brown_2025_alphaearth.md` ↔ `wang_2026_foundation`, `lang_2024_canopy_height`, `tseng_2024_presto`
- `fischer_2025_glocal_canopy_atlas.md` ↔ `lang_2024_canopy_height`, `wang_2026_foundation`
- `hiebl_2025_pretraining.md` → methodological ancestors (zerveas_2020, yuan_2022/2023, lakshminarayan_2017, seitzer_2022) + new concepts
- `hiebl_2026_alphaearth.md` → wang_2026, tseng_2024, lang_2024, zerveas_2020 + new concepts
- `wegler_2026_canopy_cover_loss.md` → schuldt_2020 (causal drought driver), drought_mortality concept, blickensdörfer_2024, zhao_2022, turubanove_2023
- `mila_2024_spatial_proxies.md` → kollert_2021, blickensdörfer_2024 (both apply spatial validation), zangh_2017
- `lang_2024_canopy_height.md` → fischer_2025, wang_2026, sentinel_1_sar, geospatial_foundation_models

**Updated**: `index.md` — added 2 new concepts

---

## 2026-05-14 (SeCo ingest)

**Ingested**: `manas_2021_seasonal_contrast.pdf`

**Triggered by**: knowledge gap identified in `03_papers/03_tree_species_cover_landsat.md` line 49 — no wiki source for the assumption that ecological/spectral stability over time enables temporal contrastive learning.

**Created**:
- `01_notes/manas_2021_seasonal_contrast.md` — SeCo; temporal positive pairs (same location, different seasons); multi-head architecture Z₀/Z₁/Z₂; beats ImageNet on BigEarthNet, EuroSAT, OSCD; canonical source for temporal stability assumption; includes scope caveat (3-month vs multi-year windows)

**Updated**:
- `02_concepts/transfer_learning_remote_sensing.md` — added "Temporal contrastive learning — SeCo" subsection with key inductive-bias quote, multi-year scope caveat, and forest-ecology corroboration
- `02_concepts/geospatial_foundation_models.md` — added SeCo as methodological precursor section; added to Sources
- `index.md` — added manas_2021 entry

---

## 2026-05-16

**Ingested**: `alessi_2019_refugia.pdf`, `fang_2016_eve_mosaics.pdf`, `tan_2025_deep_tree_species.pdf`

**Created**:
- `01_notes/alessi_2019_refugia.md` — Alessi et al. 2019 (JVS); 17,087 Italian vegetation plots; 11 native laurophylls identified; 9/11 occupy <50% potential range → non-equilibrium; central Apennines as Quaternary refugia; high EVE expansion potential throughout Apennines + southern Alps
- `01_notes/fang_2016_eve_mosaics.md` — Fang et al. 2016 (JVS); 20-ha stem-mapped EBLF, 94,605 trees; habitat heterogeneity explains EVE-deciduous mosaic; soil P (>0.27 g/kg) is dominant driver at all scales; hierarchical edaphic-topographic control
- `01_notes/tan_2025_deep_tree_species.md` — Tan et al. 2025 (Front. For.); Transformer + SSL pretraining + pseudo-labeling for S1/S2 SITS tree species (OA 0.847, macro-F1 0.836); pseudo-labels from pure-stand binary DL model for mixed stands (confidence >0.9); red-edge most discriminative; leaf-off periods most diagnostic

**Updated**:
- `02_concepts/evergreen_broadleaved_expansion.md` — added "Native Laurophylls in Italy: non-equilibrium + expansion potential" (Alessi 2019) and "Within-Stand EVE Mosaic Drivers" (Fang 2016) sections; added both to Sources
- `02_concepts/transfer_learning_remote_sensing.md` — added "Pseudo-labeling for Mixed-Stand Extension" section (Tan 2025); added to Sources
- `02_concepts/tree_species_mapping.md` — expanded Mixed Forest section with DL pseudo-labeling paragraph (Tan 2025); added to Sources
- `index.md` — added 3 new notes

## 2026-06-12 — Ingest: zhang_2026_statespacemodel, senf_2021_disturbance

**Created**:
- `01_notes/zhang_2026_statespacemodel.md` — Zhang et al. 2026 (Int. J. Appl. Earth Obs. Geoinf.); TSSMamba, a dual-branch state space model (Mamba) for multi-temporal Sentinel-2 cloud removal; SATM (temporal-spectral) + SPTM (temporal-spatial) branches + TSSF fusion; SOTA PSNR/SSIM/CC/SAM on STGAN, Sen2_MTC, SEN12MS-CR-TS with <1M params
- `01_notes/senf_2021_disturbance.md` — Senf & Seidl 2021 (Nat. Sustain.); first continental, 30-yr (1986-2016), 30m forest disturbance regime map for Europe (35 countries, LandTrendr + RF, OA 92.5%); 17% forest area disturbed; disturbance rate increase driven by frequency (74% of area, 71% of variance) not size; severity decreased in 88% of area

**Updated**:
- `02_concepts/cloud_detection.md` — added "Multi-Temporal Cloud Removal (Image Reconstruction)" subsection (TSSMamba)
- `02_concepts/transformers_time_series.md` — added "State Space Models (Mamba) as an Alternative to Attention" section; added to Sources
- `02_concepts/forest_disturbances.md` — added "Senf & Seidl 2021" subsection as predecessor to EFDA; linked from EFDA section; added to Sources
- `index.md` — added 2 new notes

## 2026-07-21 — Ingest: 9 treeline ecotone sources (batch)

**Ingested**: `maerker_2025_drought_spruce.pdf`, `vazques_2023_drought_treeline.pdf`, `klinge_2018_climate_treeline.pdf`, `charra_2025_snow_treeline.pdf`, `dietrich_2026_treeline_della.pdf`, `li_2026_climate_treeline.pdf`, `nguyen_2022_treeline_mapping.pdf`, `nguyen_2024_treeline_monitoring.pdf`, `melser_2024_freeze_constraints.pdf`

**Note**: `nguyen_2022_treeline_mapping.pdf` was identified as a duplicate of the already-ingested `nguyen_2022_forest_mapping_explainable.pdf` (identical title/authors/DOI: Nguyen, Kellenberger & Tuia 2022, RSE, doi:10.1016/j.rse.2022.113217) — no new note was written for it; no changes made to `00_literature/`.

**Created**:
- `01_notes/maerker_2025_drought_spruce.md` — Märker et al. 2025 (Trees); Norway spruce at High Tatras treeline: emerging, size-dependent drought sensitivity (largest trees) despite nominal temperature limitation; size-class isolation (SCI) method
- `01_notes/vazques_2023_drought_treeline.md` — Vázquez-Ramírez & Venn 2023 (Ann. Bot.); factorial snow/fire/drought greenhouse experiment on alpine/treeline soil seed banks (Kosciuszko NP); drought dominant stressor (44–72% germinant reduction)
- `01_notes/klinge_2018_climate_treeline.md` — Klinge et al. 2018 (Biogeosciences); Landsat + CHELSA analysis of Mongolian boreal treelines; upper treeline thermally limited (~6–9°C MGST), lower treeline moisture limited (230–290 mm yr⁻¹ MAP)
- `01_notes/charra_2025_snow_treeline.md` — Charra-Vaskou et al. 2026 (New Phytol.); two-winter snow-removal experiment, Tyrolean Alps; reduced snow cover increases hydraulic/cell damage and mortality in saplings; species-specific resistance vs recovery strategies
- `01_notes/dietrich_2026_treeline_della.md` — Dietrich & Zeidler 2026 (New Phytol., Viewpoint); proposes cold-induced GA/DELLA hormonal signalling as alternative to carbon-limitation hypothesis for treeline formation; conceptual, untested in trees
- `01_notes/li_2026_climate_treeline.md` — Li et al. 2026 (J. Environ. Manage.); ensemble SDM + SHAP for *Larix chinensis* treeline (Qinling Mountains); aspect-dependent (south gains, north loses) projected shifts under CMIP6
- `01_notes/nguyen_2024_treeline_monitoring.md` — Nguyen et al. 2024 (RSE); U-Net + IrregConvGRU with knowledge-guided temporal loss (tCA) monitors 1946–2020 Swiss Alps treeline forest cover from a single labelled year (F1c 66.7%→80.9%)
- `01_notes/melser_2024_freeze_constraints.md` — Melser et al. 2024 (RSE); SMAP/SMOS L-band freeze-thaw clustering maps growing-season constraints on boreal productivity (Canada); GSL-GPP sensitivity ~5.3–5.6 gC m⁻² yr⁻¹/day
- `02_concepts/treeline_ecotone_theory.md` — new hub concept: thermal vs moisture limitation, carbon-limitation hypothesis vs DELLA hormonal hypothesis, emerging drought sensitivity, aspect-dependent shifts, regeneration bottlenecks
- `02_concepts/snow_cover_treeline.md` — new concept: snow as winter protection for saplings, seed-bank cold stratification, secondary control on boreal treeline
- `02_concepts/treeline_remote_sensing_monitoring.md` — new concept: rule-informed CNN mapping, knowledge-guided multi-temporal segmentation, freeze/thaw RS, SHAP-explained SDMs for treeline

**Updated**:
- `02_concepts/drought_mortality.md` — added "Emerging Drought Sensitivity at Treeline (Size-Dependent)" (Märker 2025) and "Regeneration-Stage Drought Impacts (Seed Banks)" (Vázquez-Ramírez 2023) sections; added both to Sources
- `02_concepts/topographic_microclimate.md` — added "Aspect-Dependent Treeline Response" (Li 2026) and "Snow Cover Duration as Topographic Microclimate at Treeline" sections; added Li 2026 to Sources
- `02_concepts/species_distribution_models.md` — added "SHAP Explainability for Ensemble SDMs" section (Li 2026); added to Sources
- `01_notes/nguyen_2022_forest_mapping_explainable.md` — added links to nguyen_2024_treeline_monitoring and the two new treeline concepts
- `index.md` — added 8 new notes, 3 new concept pages

## 2026-07-21 — Ingest: stewart_2022_torchgeo

**Ingested**: `stewart_2022_torchgeo.pdf`

**Created**:
- `01_notes/stewart_2022_torchgeo.md` — Stewart et al. 2022 (arXiv:2111.08872); TorchGeo: PyTorch library for geospatial deep learning; spatiotemporal-coordinate-indexed GeoDatasets with on-the-fly reprojection/resampling, composable union/intersection datasets, geospatial samplers (Random/RandomBatch/Grid), multispectral transforms, pretrained Sentinel-2 models; close-to-SOTA results on 8 benchmark datasets; ImageNet pretraining improves out-of-domain spatial generalization (Chesapeake Land Cover cross-state splits) without improving in-domain accuracy

**Updated**:
- `01_notes/sattstools.md` — added cross-reference link to stewart_2022_torchgeo (tool-adjacent infrastructure literature, not a direct dependency)
- `index.md` — added 1 new note

## 2026-07-21 — Revised 04_projects/02_tree_line_stress.md with treeline batch findings

**Updated**:
- `04_projects/02_tree_line_stress.md` — integrated the 8 newly-ingested treeline papers throughout:
  - Motivation: added Klinge 2018 (upper-thermal/lower-moisture treeline dichotomy) as a caveat to the temperature-driven-advance framing; added Märker 2025 (emerging size-dependent drought sensitivity, High Tatras spruce) reinforcing the drought-stressor case; **corrected** a factual error in the snow-stressor paragraph — the draft previously claimed snow removal drives treeline seed-bank mortality, but Vázquez-Ramírez & Venn 2023 actually found the treeline seed bank was comparatively robust to snow loss (only the herbfield seed bank was harmed) and most sensitive to drought instead; rewrote the snow paragraph with Charra-Vaskou et al. 2026's actual mechanism (freeze-thaw cycling, not sustained freezing; species-specific resistance vs. recovery strategies) and correct seed-bank findings; added a new "open mechanistic question" paragraph on the carbon-limitation vs. DELLA-hormonal-signalling debate (Dietrich & Zeidler 2026)
  - WP1: added SCI method + moving-window correlation recommendation (Märker 2025) to the dendrochronology subsection; added freeze-thaw-cycle-frequency monitoring rationale and SMAP regional cross-check (Melser 2024) to microclimate instrumentation
  - WP2: added knowledge-guided multi-temporal DL (Nguyen 2024) and rule-informed CNN (Nguyen 2022) as methodological upgrades over the planned threshold/Mann-Kendall Landsat pipeline; added upper-vs-lower limiting-factor SDM split (Klinge 2018), SHAP explainability, aspect-resolved projection, and bootstrapped-CI shift detection (Li 2026) to the SDM subsection
  - Key references: added proper wikilinks for all 8 sources, replacing informal citations for Charra-Vaskou and the seed-bank paper; added new synthesis-page cross-references to [[treeline_ecotone_theory]], [[snow_cover_treeline]], [[treeline_remote_sensing_monitoring]]

## 2026-07-21 — Ingest: obuchowicz_2024_greening_switzerland

**Ingested**: `obuchowicz_2024_greening_switzerland.pdf`

**Created**:
- `01_notes/obuchowicz_2024_greening_switzerland.md` — Obuchowicz, Poussin & Giuliani 2024 (Big Earth Data); national-scale 35-year (1984–2018) 30m NDVI greening trend for Switzerland from Landsat-5/8 via the Swiss Data Cube, all NOLC04 land cover classes (not forest-specific); 61% of pixels significant (97% positive), national R²=0.43, acceleration ~2010–2011, temperature more influential than precipitation; closed/open forest among most responsive classes; **critically**, the paper never tests for observation-density sampling bias despite excluding 23% of pixels (concentrated in the Alps) for insufficient clear observations and reporting a trend break coinciding with likely archive-density changes — flagged as a plausible, unaudited vulnerability to the exact artifact [[bayle_2024_landsat_greening_inflated]] demonstrates

**Updated**:
- `02_concepts/vegetation_greenness_trends.md` — added "National-Scale High-Resolution Landsat Greening (Switzerland)" section with critical caveat; added to Sources
- `02_concepts/sampling_bias_remote_sensing.md` — added Obuchowicz et al. 2024 as a worked example of an at-risk, unaudited study; added to Sources
- `index.md` — added 1 new note
