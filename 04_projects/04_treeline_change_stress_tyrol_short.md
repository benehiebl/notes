# Forest-line change, stress and drivers in the central Alps of Tyrol — 2-page summary

> Condensed version of [[04_treeline_change_stress_tyrol]] (full evidence, DOIs and [verify] list there). Items marked **[verify]** are unconfirmed.

## Background and gaps

- Alpine forest lines are climate-sensitive boundaries, but reported shifts differ widely with site, definition and method: ~1 m/yr in a Swiss valley, mostly infilling [[frei_2023_treeline_shift]]; +32 m (Landsat) vs +45 m (orthophoto) over ~37 years in one South Tyrolean valley [[menegaldo_2025_landsat_treeline_dynamics]].
- Climate vs land use is unresolved. Land use and microsite dominate in [[cudlin_2017_drivers_treeline_shift]], [[frei_2023_treeline_shift]] and [[marzini_2025_expansion_forest]] (simulation, Stubai). A climate-favoured larch wave around 2003 is reported in the French Alps [[nicoud_2025_landuse_larch_expansion]]. No source reconciles the two views.
- Stress at the Tyrolean forest line is a hypothesis: growth is mainly temperature-limited [[obojes_2024_growth_limits_elevational]]; snow-removal damage was shown in saplings at 1700 m [[charra_2025_snow_treeline]]; snow loss at 1900–2300 m is assumed, not shown [[olefs_2020_snow_depth_changes]], [[matiu_2021_snow_depth_trends]].
- This proposal studies the **forest line** (closed canopy, ≥5 m, ≥30% cover; thresholds varied), not the thermal treeline (definition distinction from the literature; no wiki note yet, needs verification).

**Research gaps (limited search; confidence medium unless stated)**
1. No tested Landsat forest-line series for Austrian Tyrol, and the Landsat greening artefact (up to 50% of NDVImax greening above 2400 m) is not handled in treeline work [[bayle_2024_landsat_greening_inflated]], [[obuchowicz_2024_greening_switzerland]].
2. No 3D (canopy height/volume) forest-line change study for the Eastern Alps; no satellite-stereo treeline study found.
3. No quantitative, uncertainty-aware separation of climate, land-use legacy, browsing and disturbance for Tyrolean forest-line change.
4. No test whether Sentinel-2 anomalies at an Alpine forest line match tree-ring records; Austrian S2 validation is closed-canopy only [[löw_2020_phenology_austria_forest]].

## Research questions

- **RQ-A:** How far have position, density and canopy height of the Tyrolean forest line changed since 1984, and at what detection limit?
- **RQ-B:** Do heat/drought, frost and snow-cover change leave detectable signatures in Sentinel-2 series and tree rings?
- **RQ-C:** How much of the spatial variation in change is attributable, with bounds, to land-use legacy, browsing, avalanche/geomorphic disturbance and climate/snow?

## Work packages (study area: central Tyrol, forest-line belt ~1900–2300 m)

**WP1 — Forest-line change (Year 1–2)**
- *Landsat 1984–2025:* sub-pixel forest fraction plus a time-series model robust to observation density (do not trend NDVImax) [[landsat]], [[sampling_bias_remote_sensing]]. Over 40 years, 8–64 m of shift is at or below one 30 m pixel, so a minimum detectable shift is reported first. Validation with Land Tirol orthophotos and deep-learning delineation [[nguyen_2022_forest_mapping_explainable]].
- *3D canopy change:* WorldView stereo DSM differencing, as requested, with an empirical error model from stable terrain. Constraints: the ESA WorldView archive reportedly covers 2009–2020 only, so a 20-year record from 2005 is unsupported; DSM errors of ~1–4 m exceed sapling growth (detection limit ~2.8 m at 1 m error; own arithmetic). Both statements have no wiki note and need verification. The two Tyrol airborne laser epochs (2006–2010, 2017–2023) are therefore the core 3D source and benchmark; stereo is a bounded feasibility test where footprints allow. A negative detection limit counts as a result.
- *H1:* forest fraction rises near the forest line beyond bootstrapped noise (H0: greening artefact); Landsat underestimates orthophoto shifts by ≲13 m.

**WP2 — Stressors (Year 1–3)**
- *Sentinel-2 (2015/17–2025):* per-pixel seasonal baselines and anomalies for event years 2003 (Landsat), 2015, 2018, 2022 [[schuldt_2020_drought_forest]]; tree-cover purity thresholds varied; baselines stratified by larch share; snow melt-out from S2 snow products.
- *Dendrochronology:* fresh cores (existing public series reportedly end before 1976; needs verification) of *P. cembra* and *Larix* at several sites over ≥2 valleys; ring width, blue-intensity/density, frost rings, pointer years, moving-window climate response [[larch_growth_climate]], [[frank_2026_larch_growth_temperature_density]]; larch budmoth screened as confounder.
- *Climate/snow:* SPARTACUS, SNOWGRID, ERA5-Land, SPEI/VPD; optional loggers and phenocams [[snow_cover_treeline]].
- *Linking:* only ~10 overlapping seasons, so pooled mixed models and event-year contrasts, no per-site correlation claims. Null results (e.g. no 2018/2022 signal at altitude) are an acceptable outcome. Stressor interaction (snow × drought) is exploratory only.

**WP3 — Driver attribution (Year 2–3)**
- Response: WP1 forest-fraction trend and ALS height/gap change per cell. Predictors: land-use legacy (alm/pasture cadastre), browsing (WEM), avalanche/geomorphic layers, climate/snow and WP2 anomalies, topography [[topographic_microclimate]].
- Models: gradient boosting/random forest plus deep ensemble for uncertainty [[deep_ensemble_uncertainty]]; spatial block/kNNDM cross-validation [[mila_2024_spatial_proxies]]; area of applicability masks [[area_of_applicability]].
- Output: variance shares per driver family with intervals and counterfactual scenarios; observational attribution, not causal proof. H3.1 (land use) and H3.2 (climate wave) are tested against a topography-only baseline.
- Optional extension: species-resolved ecotone composition (2017–2025) with foundation-model embeddings [[brown_2025_alphaearth]].

## Dependencies, outputs and timeline

| | Year 1 | Year 2 | Year 3 |
|---|---|---|---|
| WP1 | data requests, Landsat pipeline, definition sensitivity | ALS differencing, stereo feasibility, validation | final products, Papers 1–2 |
| WP2 | sites, first coring, S2 baselines | ring processing, event contrasts | integration, Paper 3 |
| WP3 | driver data requests | model set-up, spatial CV | attribution, Paper 4, data paper |

- WP1 feeds WP3 (response); WP2 feeds WP3 (stress/snow predictors) and WP1 interpretation. WP2 degrades gracefully if null.
- Papers: Landsat forest-line detection limits; ALS/stereo canopy change; stress signatures (nulls accepted); attribution with bounds; open data paper.

## Main risks

- Shift below Landsat detection limit → trend product plus orthophoto validation.
- WorldView coverage/noise → ALS core, published error model.
- No S2 stress signal at altitude, short overlap → pre-accepted null, pooled models.
- Missing driver data (browsing, abandonment, avalanches) → Year-1 requests, proxies, report non-separable drivers.
- Funding: FWF Stand-Alone is the realistic fit **[verify]**; no partner letters exist.

## Open items to verify

- WorldView footprints over Tyrol; first-epoch ALS surface model and tile dates; earliest orthophoto year.
- Landsat 5 geolocation in mountains; artefact size at 1900–2200 m.
- WEM point-level release; "Larix decemlineata" in the brief matches no organism found (which pest was meant?).
- A documented Scopus/Web of Science search before any "first study" claim.
