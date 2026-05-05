# Operations Log

Append-only record of all wiki operations.

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