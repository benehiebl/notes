---
title: "TRACEVE – Tracing the evergreen broad-leaved species and their spread (FWF International Cooperation Project proposal)"
authors:
  - Martin Rutzinger
  - Stefan Zerbe
year: 2023
tags:
  - remote-sensing
  - machine-learning
  - forest-ecology
keywords:
  - evergreen broad-leaved species
  - laurophyllisation
  - vegetation-plot observations
  - Landsat
  - Sentinel-2
  - space-for-time substitution
  - joint species distribution models
  - biome shift
status: read
---

## Title and Authors of the Paper

- "TRACEVE – Tracing the evergreen broad-leaved species and their spread"; FWF International Cooperation Project, Austria – South Tyrol/Alto Adige
- Applicant/PI: Priv.-Doz. Dr. Martin Rutzinger (Department of Geography, University of Innsbruck); Co-PI: Prof. Stefan Zerbe (Free University of Bozen-Bolzano)
- **This is a research proposal, not a publication**: not peer reviewed, no results, and the PDF is a scanned/printed file (created Feb 2023, 26 pages). The text was read from page images (no OCR available); pages 1–20 (cover to project management) were read, pages 21–26 (presumably references, annexes, letters of intent) were not inspected. Whether the project was funded is not stated in the document.

## Quick Overview

- **Why is it relevant?** It defines the intended chain from plot data to Landsat back-casting and transfer to Austria/South Tyrol, and thematically matches the wiki's evergreen-mapping work ([[hiebl_2025_pretraining]], [[hiebl_2026_alphaearth]]); a formal link between the proposal and those papers is not stated in the document.
- **What was done?** The proposal sets out seven work packages that combine large vegetation-plot databases, new field plots in six Italian protected areas, Sentinel-2/Landsat machine-learning models, historical change detection, and transfer of the models to a northern target region.
- **What is the main outcome?** None yet (planned outputs: drivers of EVE diversity, EVE cover/diversity maps for Italy, historical change since 1990, and maps of potential EVE spread in Austria and South Tyrol).

## Main Goal and Fundamental Concept

- Goal: track the distribution, diversity and drivers of woody evergreen broad-leaved species (EVEs) in broad-leaved (deciduous) forests across a 13° latitudinal gradient (36°40′N–49°N, Italy to Austria) and identify potential areas of spread at the northern edge of the evergreen biome.
- Background assumptions: EVE spread ("laurophyllisation", "mediterranization") is attributed to warmer winters, forest regrowth after land abandonment, and rising CO₂; it is treated as a paradigm for global-change effects on forest diversity.
- Core idea: evergreen species keep photosynthesising in winter, so leaf-life-span contrast against deciduous canopies makes them detectable in satellite time series; Italy (EVE-rich) serves as model system and Austria/South Tyrol (EVE-poor) as target system (space-for-time substitution).

## Technical Approach

- **WP1 (UNIBZ)**: harmonise archived vegetation-plot observations (VPOs; ~180,000 estimated for Austria and Italy, ~15,000–20,000 in broad-leaved forest after filtering), attach CHELSA bioclimate, EU-DEM topography and Global Human Influence Index; analyse EVE diversity with GLMs and joint species distribution models (jSDM).
- **WP2 (UNIBZ)**: new field survey in about six protected areas along a latitudinal gradient; ~80–100 sites per area (~500–600 sites in total); at each site four 10 × 10 m plots on neighbouring Sentinel-2 cells in the cardinal directions (~2,500 plots), recording woody species cover by vertical layer; sites stratified by a suitability map from WP1; single visit per site.
- **WP3 (UIBK)**: ML ensemble (Random Forest, SVM; also mixed models, jSDM) to map EVE cover and diversity from Sentinel-1/2 and Landsat-8 (2019–2022) vegetation indices (NDVI, EVI, LAI), phenology and spectral heterogeneity/texture metrics plus climate, topography, human influence and management (coppice, high forest, old-growth).
- **WP4 (UIBK)**: apply the best WP3 model to Landsat Collection 2 time windows (e.g. 1990–93, 2000–03, 2010–13, 2020–23) for change detection, validated against historical VPOs; relate change to climate change (CHELSA) and land use with GLMs (space-for-time).
- **WP5/WP6 (all)**: transfer the models to Austria and South Tyrol for current cover and for change; accuracy tested with archived VPOs.
- **WP7**: management, dissemination; three-year Gantt plan; computing via Google Earth Engine and the Innsbruck cluster.

## Distinctive Features

- First planned cross-regional study of evergreen expansion in southern European broad-leaved forests, combining VPO databases with multi-sensor EO.
- Uses phenological contrast (leaf life span) as the detection principle and includes growth forms (trees, shrubs, lianas) and vertical layers.
- Explicit model-system to target-system transfer, with Sentinel-2 used to quantify the uncertainty of back-projecting Landsat.
- Plot design nested to match Sentinel-2 and Landsat pixels and ICP Forests sampling (data from 2007 in Italy).

## Experimental Setup and Results

- No experiments or results are reported; Figure 2 only illustrates the planned design for six Italian protected areas (e.g. Foreste Casentinesi, Gran Sasso, Pollino, Cilento, Sibillini, Val Grande) with existing archived VPO counts (≈17,000 Italian plots in total) and bioclimatic zonation.
- Planned validation: stratified field data (WP2) and archived VPOs (WP1); metrics are not specified in detail.

## Advantages and Limitations

- **Advantages**: coherent chain from drivers to mapping to history to transfer; uses large standardised plot archives; open data and GEE; explicit handling of scale (10 m vs 30 m plots/pixels); partners with complementary expertise.
- **Limitations** (critical reading of a proposal):
  - Space-for-time substitution assumes that spatial gradients equal temporal change and equilibrium with climate; the proposal itself cites disequilibrium and dispersal lag ([[alessi_2019_refugia]]), which undermines this assumption.
  - Transfer from Italy to Austria/South Tyrol is a strong domain shift (EVEs rare, different canopy and phenology); no explicit applicability-domain or uncertainty step is mentioned (cf. [[area_of_applicability]], [[deep_ensemble_uncertainty]]).
  - Detecting understory EVEs (e.g. *Ruscus*, *Hedera*) beneath deciduous canopies with 10–30 m optical imagery is not shown to be feasible; sparse cover may be below detectability, and leaf-off winter imagery is not discussed in detail (Landsat/Sentinel-2 snow and cloud constraints are only noted).
  - Four plots on adjacent cells per site are spatially autocorrelated, and single-visit, woody-only plots limit independence and temporal representativeness; no spatial cross-validation is described.
  - Historical back-casting to 1990 depends on archived VPOs of varying geolocation accuracy and on sensor harmonisation; plot–pixel mismatch (10 m plots vs 30 m Landsat) is acknowledged but not quantified.
  - Planned "potential areas of spread" use current relationships; no future climate or land-use scenarios are described, and dates are partly inconsistent (e.g. imagery 2019–2022 vs 2020–2023 vs 2017–2021).
  - The proposal does not mention the opposite signal documented later for holm oak dieback ([[mediterranean_holm_oak_dieback]]).
  - Several claims in its state-of-the-art section (e.g. EVE spread as biome shift; CO₂ as a driver) lack evaluation here; it should not be cited as evidence.

## Conclusion

- TRACEVE is a well-structured proposal for tracking evergreen broad-leaved species with plot data and Landsat/Sentinel-2 time series, with a clear methodological chain but major untested assumptions (space-for-time, detectability, transfer).
- Use this note for project context and for linking the wiki's EVE material ([[evergreen_broadleaved_expansion]], [[03_papers/04_evergreen_distribution_change]]); do not use it as a citable source for ecological claims.
