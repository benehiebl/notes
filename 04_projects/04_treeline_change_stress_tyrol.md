# Forest-line change, stress and drivers in the central Alps of Tyrol

> **Status (2026-10-15):** Draft proposal built on `reports/Tyrol treeline proposal gaps.md` and `research_notes/Tyrol treeline proposal gaps/`. Companion to (not a replacement of) [[02_tree_line_stress]], which remains the physiology-and-monitoring variant. Evidence conventions: claims with a wiki note are cited as [[note]]; claims taken only from the research notes (abstract- or search-summary-level, publisher full texts mostly not read) carry **[verify]** or are named as such. "Not found" means "not found in a limited search", not "does not exist". No "first study" claim is made without a documented Scopus/Web of Science search.

---

## Motivation

- Alpine forest lines are climate-sensitive biome boundaries, but observed shifts vary widely with site, definition and method.
  - Central Swiss valley (Dischma), 1972/73-2012: about 1 m/yr mean, up to 42 m per decade [[frei_2023_treeline_shift]]. 79% of new forest cells were infilling, not advance into new ground (same source, via the report).
  - South Tyrol (Schnals valley, 16 areas, Landsat 5 1985 vs Landsat 8 2022): +32 m (Landsat) vs +45 m (manual orthophoto delineation); forest cover +44% on average [[menegaldo_2025_landsat_treeline_dynamics]]. One valley, single climate station.
  - Holocene context in Tyrol: the Kauner Valley treeline rose about 65 m between ~1860 and 1980 (to ~2245 m), and stood above its 1980 position for much of ~7100-2100 BC [[nicolussi_2005_holocene_treeline_variability]]. The present edge is therefore not in equilibrium with climate in any simple sense.
- **Definition matters.** "Treeline" in the strict sense is a thermally limited, globally comparable forest edge; it must not be confused with the forest line (closed canopy) or timberline (Körner & Hoch 2023, doi:10.1111/jbi.14593; carried over from [[02_tree_line_stress]]).
  - This proposal studies the **forest line** (operational: closed canopy, tree height at least 5 m, cover at least 30%; thresholds are an assumption from the research notes and are varied in a sensitivity analysis). Boundary position depends strongly on such thresholds [[nguyen_2022_forest_mapping_explainable]].
  - Where the edge is set by land use, it is not a thermal "treeline" at all. Stubai simulations place the present edge near 2000 m, mainly land-use constrained, with expansion after abandonment regardless of warming [[marzini_2025_expansion_forest]] (iLand, not empirically validated).
- **Climate versus land use is unresolved (explicit contradiction).**
  - Land-use-dominated view: Swiss ingrowth was 90% into former pasture above 1650 m (Gehrig-Fasel et al. 2007, via [[02_tree_line_stress]]); a pan-European expert comparison finds temperature alone insufficient, with geomorphology, soil, microclimate and land-use history explaining most variability [[cudlin_2017_drivers_treeline_shift]]; Dischma advance is microsite- and land-use-controlled [[frei_2023_treeline_shift]]; see also [[treeline_land_use_legacy]].
  - Climate-wave view: a larch establishment wave around 2003 (95% interval 1995-2010) at about 2300 m in the southern French Alps coincided with a favourable climate window, not with changed pastoral pressure; 19th-century abandonment was only the precondition [[nicoud_2025_landuse_larch_expansion]] (628 trees, one region).
  - These two views are not reconciled by any source; WP3 treats them as competing hypotheses.
- **Stress at the Tyrolean forest line is a hypothesis, not a premise.**
  - Documented: *P. cembra* growth at the forest line is temperature-limited, with weaker-than-expected temperature response in a dry valley [[obojes_2024_growth_limits_elevational]]; larch is water-limited up to ~1715 m and temperature-limited above ~2000 m [[obojes_2018_water_stress_growth_larch]]; larch growth decoupled from warming after 2000, more strongly in dense abandoned stands (subalpine, mean 1723 m, so below the forest line) [[frank_2026_larch_growth_temperature_density]]; snow removal damaged saplings of five species at 1700 m (not *P. cembra*) [[charra_2025_snow_treeline]]; three years of top-soil rain exclusion hardly changed sap flow in treeline saplings [[wieser_2019_effects_climate_treeline]]; winter frost damage risk is low in alpine woody plants but premature deacclimation (notably *P. cembra*) and spring snow loss may become critical [[neuner_2014_frost_resistance]].
  - Not documented for adult trees at the Tyrolean forest line: climate-driven browning or mortality in 2003, 2015, 2018 or 2022, frost rings, stressor interactions (needs verification; limited search).
  - The snow premise is itself weak at treeline elevation: station snow depth fell 8.4% per decade, but stations are scarce above 2000 m [[matiu_2021_snow_depth_trends]]; the Austrian 1 km model finds a 42-day loss of snow-cover duration that is significant only below about 2000 m [[olefs_2020_snow_depth_changes]]. "Reduced snow" at 1900-2300 m is an exposure assumption.
  - The 2018 drought was exceptional at continental scale (Landsat canopy disturbance, central and eastern Europe, effects persisting up to two years) [[senf_2021_impacts_2018_forests]], but this says little about high-elevation Alpine canopies.

## Research gaps

Gap list from `reports/Tyrol treeline proposal gaps.md`; confidence is the report's judgement from limited searches, not a literature-derived score.

1. **No tested Landsat forest-line time series for Austrian Tyrol, and no treatment of the Landsat greening artefact in treeline work.**
   - Evidence: nearest study is one South Tyrolean valley [[menegaldo_2025_landsat_treeline_dynamics]]; Swiss national NDVI greening (1984-2018) was not corrected for observation density [[obuchowicz_2024_greening_switzerland]]; up to 50% of NDVImax greening above 2400 m can come from more usable summer scenes [[bayle_2024_landsat_greening_inflated]]; see [[sampling_bias_remote_sensing]].
   - Confidence: artefact part high, Tyrol part medium. Verified in wiki notes: Menegaldo, Bayle, Obuchowicz. [verify]: size of the artefact near 1900-2200 m (Bayle's result is for non-forest pixels above 2400 m); a follow-up on forest-stand dynamics behind greening (DOI 10.1002/rse2.430, journal unconfirmed).
2. **No 3D (canopy height/volume) forest-line change study for the Eastern Alps, and no satellite-stereo forest-line volume study found.**
   - Evidence: repeat-ALS treeline height change exists only for Norway/Sweden (Næsset et al. 2019, doi:10.3390/rs11151804; Næsset et al. 2021, doi:10.3390/rs13132469; both report-level only); five targeted searches found no WorldView/Pléiades/SPOT treeline change study. Only 19% of 372 treeline papers use multi-sensor designs [[garbarino_2023_treeline_remote_sensing]].
   - Confidence: medium. [verify]: whether Tyrol's first-epoch ALS surface model exists; WorldView stereo footprints over Tyrol.
3. **No quantitative separation of climate, land-use legacy, browsing and disturbance for Tyrolean forest-line change (and no uncertainty-aware spatial attribution).**
   - Evidence: sources disagree (see Motivation); iLand work is simulation only [[marzini_2025_expansion_forest]]; dispersal and invasibility can matter as much as 0-2 °C of warming in models [[dullinger_2004_climate_treeline_shifts]].
   - Confidence: medium-high that the question is open; low-medium that data suffice (see Risks).
4. **No test of whether Sentinel-2 anomalies at an Alpine forest line match tree-ring records.**
   - Evidence: Sentinel-2 disturbance mapping in Austria was validated in closed canopies only (83.4% of field disturbances detected with two baseline years) [[löw_2020_phenology_austria_forest]]; the Swiss 2018 study found fewer severe declines at high elevation and many NDWI increases (Sturm et al. 2022, doi:10.1111/gcb.16136; report-level); NDVI vs ring width was not correlated in lowland spruce (D'Andrea et al. 2022, doi:10.3390/f13091417; report-level).
   - Confidence: medium. No S2-plus-rings study at an Alpine treeline was found in a limited search.
5. **No density-based (blue intensity / maximum latewood density) ring series from Tyrolean *P. cembra* extending the Patscherkofel divergence through 2003, 2015, 2018, 2022.**
   - Evidence: divergence after the mid-1980s unexplained (Oberhuber 2004 and 2008, doi:10.1007/s00468-007-0166-7; only abstracts read); existing ITRDB Obergurgl/Stubai chronologies end before 1976 (report-level).
   - Confidence: medium. [verify]: ITRDB species label (AUST002), existing unpublished series at Innsbruck.
6. **Species-level change of the ecotone belt (*P. cembra*, *Larix*, *Picea*) is unmapped** - kept as an optional extension only (see WP3).
   - Evidence: no Alpine demonstration below 50 cm; WorldView-3 multiclass species accuracy 44-47% in the Rocky Mountains (Sindewald et al. 2025, non-Alpine); Carrieri 2025 does no species classification [[carrieri_2025_hr_imagery_treeline]]. Confidence: medium.

Gap deliberately not claimed: "no multi-decadal Landsat plus VHR fusion". French Alpine work already fuses Landsat, aerial photos, ALS and dendrochronology (Bayle et al. 2025, report-level [verify]); only satellite *stereo* is untested.

---

## Research questions and hypotheses

**Overarching questions**
- **RQ-A.** How much has the upper forest line in the central Tyrolean Alps changed in position, density and canopy height since 1984, and at what detection limit can this be stated?
- **RQ-B.** Do climate stressors (heat/drought, winter and spring frost, snow-cover change) leave detectable signatures in Sentinel-2 time series and tree rings at the forest line?
- **RQ-C.** How much of the spatial variation in forest-line change can be attributed, with stated bounds, to land-use legacy, browsing, avalanche/geomorphic disturbance and climate/snow?

**WP1 (change detection)**
- RQ1.1: Is the 1984-2025 Landsat trend in forest fraction near the forest line positive and larger than the detection limit (about one pixel plus geolocation error) after correcting for observation density?
  - H1.1: forest fraction rises in a belt around the 2020s forest line (increase beyond bootstrapped noise). H0: no trend after density correction (the greening is a sampling artefact).
- RQ1.2: Do Landsat-derived forest-line shifts agree with orthophoto-derived shifts?
  - H1.2: the Landsat method underestimates orthophoto shifts by about 13 m or less (the Schnals bias [[menegaldo_2025_landsat_treeline_dynamics]]). H0: bias is larger, so Landsat is reported as a trend product only.
- RQ1.3: Can WorldView stereo DSM differencing detect canopy height/volume change at the forest line?
  - H1.3: detectable change exists only in tall closed stands, gaps and krummholz/alder, not for saplings. H0: stereo noise (about 1-4 m per DSM, level of detection roughly 2.8 m at 1 m error; arithmetic from the research notes) exceeds the signal everywhere, giving a published negative detection limit.
- RQ1.4: Does ALS epoch differencing (2006-2010 vs 2017-2023) show canopy height gain at the forest line?
  - H1.4: positive mean height change in the forest-line belt, larger on formerly grazed (abandoned) sites. H0: no change beyond ALS vertical error.

**WP2 (stressors)**
- RQ2.1: Do event years (2003, 2015, 2018, 2022; Schuldt et al. 2020 [[schuldt_2020_drought_forest]]) leave a Sentinel-2/Landsat anomaly at the forest line?
  - H2.1: negative anomalies in dry inner-Alpine sites and larch-rich pixels. H0: no anomaly at the forest line (consistent with the Swiss 2018 picture). A null result is an acceptable outcome.
- RQ2.2: Do ring width and density respond to summer heat/drought, and does the response change over time (divergence)?
  - H2.2: July/summer temperature remains the main control, with density series recovering a signal lost in ring width. H0: no density-based climate signal beyond ring width.
- RQ2.3: Do frost rings or spring-frost/low-snow years appear in the record?
  - H2.3: frost rings co-occur with low-snow springs. H0: none (frost risk low, [[neuner_2014_frost_resistance]]).
- RQ2.4 (exploratory): does a snow-by-summer-drought carry-over in larch exceed the main effects? H0: no interaction.
- RQ2.5: Is the satellite-ring link detectable at all with about ten overlapping seasons?
  - H2.5: event-year contrasts in pooled mixed models reach a detectable effect. H0: not distinguishable from zero; the S2 layer is then reported as a failed predictor.

**WP3 (attribution)**
- RQ3.1: Which driver group explains most of the spatial variance of WP1 change?
  - H3.1 (land-use legacy): abandonment/grazing history and browsing explain more than climate/snow. H3.2 (climate wave, after [[nicoud_2025_landuse_larch_expansion]]): climate/snow metrics explain more, mainly at higher elevations and in larch-rich stands. H0: no driver group beats a topography-only baseline under spatial cross-validation.
- RQ3.2: Where is the attribution model reliable? H3.3: predictions outside the area of applicability have markedly larger error ([[area_of_applicability]]).

---

## Work packages

Study area: central Alps of Tyrol (Austria), forest-line belt roughly 1900-2300 m (assumption; exact elevation to be taken from the Tyrolean forest inventory [verify]). Three work packages, years relative to project start (earliest realistic 2027).

### WP1 - Forest-line change: Landsat 1984-2025 and 3D canopy change (Year 1-2)

**Objective:** produce a forest-line change product with an explicit minimum detectable shift, and a canopy height/volume change product with an empirical detection limit.

**WP1a. Landsat forest-line change (1984-2025)**
- Detection limit first: at 0.2-1.6 m/yr, 40 years gives 8-64 m, only the upper half of which exceeds one 30 m pixel (arithmetic from the research notes). Report a minimum detectable shift (about one pixel plus geolocation error) and do not claim sub-pixel displacement without validation.
- Method: classify forest fraction per year (sub-pixel / fraction approach rather than hard classes), then fit a time-series model robust to sampling density (e.g. harmonic/BFAST/LandTrendr-style fits; no treeline precedent found, so this is methodology transfer). Do not trend annual NDVImax: the greening artefact [[bayle_2024_landsat_greening_inflated]] and the Swiss uncorrected analysis [[obuchowicz_2024_greening_switzerland]] are the warning cases. Include observation-count diagnostics per pixel and year ([[sampling_bias_remote_sensing]], [[landsat]]).
- Sensor issues to design in: TM/ETM+/OLI harmonisation (HLS v2.0 starts April 2013 with no Landsat 5; transforms such as Roy et al. 2016 not checked [verify]); ETM+ scan-line gaps after 2003; topographic shadow gave the largest between-sensor differences in an HLS comparison (report-level); Landsat 4/5 geolocation in mountain terrain not found [verify]; cloud/shadow masking [[cloud_detection]].
- Validation: Land Tirol orthophoto archive (20 cm, updated every three to four years, earliest years unknown; request needed) and manual/deep-learning delineation ([[nguyen_2022_forest_mapping_explainable]], [[nguyen_2024_treeline_monitoring]]; DOI for 2024 unconfirmed [verify]). Benchmark: Schnals +32 m vs +45 m [[menegaldo_2025_landsat_treeline_dynamics]].
- Definition: forest line (see Motivation) with threshold sensitivity analysis. Continental canopy products do not substitute: 30 m European series RMSE up to 4 m [[turubanove_2023_canopy_landsat]]; 10 m GEDI-Sentinel-2 product aRMSE 7.3 m for 2020 only [[lang_2024_canopy_height]]; both comparable to the krummholz-to-tree height range.

**WP1b. 3D canopy change - tiered design**
- **Tier 1 (core): Land Tirol ALS epochs** (first 2006-2010; second 2017-2023, at least 8 pts/m2; DTM/DSM at 50 cm, mosaics of flights from different years, so per-tile flight dates are essential; tirol.gv.at laser data page, report-level). Change interval about 7-17 years per tile. Output: canopy height model difference, gap/loss/gain classes, canopy envelope volume (height integral, not stem volume or biomass). [verify]: availability of the first-epoch surface model, licence, dates.
- **Tier 2 (stated user aim): WorldView stereo over roughly the past 20 years.** Constraint stated honestly: the ESA WorldView archive covers 2009-02-07 to 2020-12-01 only (report-level), so a record from 2005 is unsupported, and no current Austrian national licence was found. Action: query catalogue footprints for Tyrol first; if enough tri/stereo pairs exist, process DSMs (Nuth and Kääb co-registration, doi:10.5194/tc-5-271-2011; report-level) and build an empirical error model from stable off-vegetation terrain (NMAD by slope/aspect, autocorrelation-corrected). Photogrammetry over mountain forest has per-pixel errors of about 1-4 m (Piermattei et al. 2018, doi:10.3390/RS10101542; sigma-MAD figures [verify]) and smooths small solitary trees (Næsset et al. 2021).
- Use of stereo: only where the error model supports it (tall closed stands, gaps, dense krummholz/alder), benchmarked against ALS in the overlap years. A published negative detection limit counts as a result.
- Fallback if footprints are insufficient: ALS epochs only plus historical aerial stereo for pre-2006 (availability for Tyrol unverified).

**Key uncertainties:** 30 m pixel vs shift rate; artefact size near the forest line unquantified; stereo noise larger than sapling growth; ALS epochs are year-mosaics.

**Expected outputs:** annual forest-fraction series and forest-line change map with detection limits (1984-2025); ALS change maps (2006-2023); WorldView feasibility report with error model; benchmark dataset (open).

### WP2 - Stressors at the forest line: Sentinel-2, tree rings, climate and snow (Year 1-3)

**Objective:** test, not assume, whether heat/drought, summer vs winter stress, frost and snow-cover change are detectable at the forest line and which are linked to growth.

**WP2a. Remote sensing (Sentinel-2 2015/17-2025, Landsat for the longer baseline)**
- Seasonal baseline model per pixel and anomaly detection in the style of Austrian S2 phenology/disturbance work [[löw_2020_phenology_austria_forest]] ([[sentinel_2]], [[phenology]]); red-edge/NDWI-type indices; use full season composites, not August only (the Swiss study used August only; report-level).
- Pixel purity: tree islands/krummholz at 10 m are mixed with grass, rock and shadow; tree coordinates in steep terrain carry errors of about a pixel. The earlier 50% tree-cover threshold has no literature basis; vary it (e.g. 20/35/50%).
- Stratify baselines by larch fraction (deciduous, strong phenology amplitude); no S2 study separating *Larix* from evergreens at the forest line was found.
- Snow: Sentinel-2 snow products (Gascoin et al. 2019, doi:10.5194/essd-11-493-2019; report-level) for melt-out dates, checked against stations; ERA5-Land snow not used raw (bias grows with elevation; report-level).

**WP2b. Dendrochronology**
- Fresh coring (existing ITRDB series end before 1976): 20-30 trees per site, *P. cembra* and *Larix decidua* (and *Picea abies* where present), several sites over at least two valleys/aspects incl. dry inner-Alpine and wetter settings. Sites co-located with WP1 change and, where possible, with Innsbruck long-term treeline sites (Patscherkofel; collaboration to be agreed [verify]).
- Variables: ring width, density proxies (blue intensity or maximum latewood density), frost rings, pointer years (event years 2003, 2015, 2018, 2022). Moving-window response functions because sensitivity can be non-stationary [[maerker_2025_drought_spruce]] (spruce, High Tatras, DOI [verify]); basal area increment and stand-density covariates [[frank_2026_larch_growth_temperature_density]]; see [[larch_growth_climate]], [[drought_mortality]].
- Larch budmoth outbreaks (about 9-year cycle) must be screened as a confounder of larch series [[frank_2026_larch_growth_temperature_density]]; no Tyrolean outbreak record 2015-2025 found [verify]. ("Larix decemlineata" from the brief matches no organism found; clarify which agent was meant.)

**WP2c. Climate and snow data**
- SPARTACUS (Hiebl & Frei 2016, doi:10.1007/s00704-015-1411-4), SNOWGRID (Olefs et al. 2020, [[olefs_2020_snow_depth_changes]]), ERA5-Land with station checks; SPEI/VPD. Optional: microclimate loggers and phenocams at a subset of sites ([[snow_cover_treeline]], [[topographic_microclimate]]).

**Linking satellite and rings (main methodological risk)**
- Only about ten overlapping seasons (2015-2025): a per-site correlation needs |r| above about 0.63 for p < 0.05 with 8 degrees of freedom (arithmetic from the research notes). Therefore: multi-site mixed models and event-year vs reference-year contrasts, plus Landsat anomalies from 2003. Satellites see canopy exposure and phenology; rings record stem carbon allocation, so a weak link is not a failed experiment. NDVI vs ring width was uncorrelated in lowland spruce (D'Andrea et al. 2022; report-level).

**Key uncertainties:** null signal in S2 at altitude (plausible); sparse tree-level coordinates; short overlap; stressor interactions untested (exploratory only).

**Expected outputs:** stress-anomaly layers (S2/Landsat) with uncertainty, ring-width/density/frost-ring chronologies, event-year contrast results (positive or null), snow-metric layers used by WP3.

### WP3 - Driver attribution of forest-line change (Year 2-3)

**Objective:** attribute the spatial pattern of WP1 change to land-use legacy, browsing, avalanche/geomorphic disturbance and climate/snow (using WP2 stress layers), with bounds, not causal proof.

- **Response:** per-cell (e.g. 100-250 m hexagons or elevation-belt cells along the forest line) forest-fraction trend (WP1a) and ALS canopy height/gap change (WP1b).
- **Predictors:** (i) land-use legacy: historical land cover, alm/pasture cadastre, ownership, distance to huts (datasets to be requested; no Tyrol-wide abandonment time series found); (ii) browsing: WEM (Wildeinflussmonitoring) district or point data (strong game influence at 41.8% of Tyrol survey points 2019-2021, waldwissen.net; samples regeneration areas, not the ecotone); (iii) avalanche/geomorphic disturbance: avalanche tracks, slope and curvature layers (layer not yet located); (iv) climate/snow: SPARTACUS, SNOWGRID, WP2 anomaly layers; (v) topography and microclimate ([[topographic_microclimate]]).
- **Model:** gradient boosting / random forest baseline plus a deep ensemble for predictive uncertainty ([[deep_ensemble_uncertainty]], [[lakshminarayan_2017_uncertainty]]); interpretation by partial dependence and SHAP (grouped by driver family).
- **Validation:** spatial block / kNNDM cross-validation, not random splits, because spatial autocorrelation inflates scores ([[spatial_proxies_random_forest]], [[mila_2024_spatial_proxies]], [[pebesma_2025_spatial_data]]); area of applicability to mask extrapolation ([[area_of_applicability]]); propagate WP1 detection-limit error into the response.
- **Attribution with bounds:** report variance shares per driver family with intervals, counterfactual scenario runs (e.g. "no browsing", "climate of 1984-1993"), and where the data cannot separate drivers (collinearity of elevation, abandonment and snow). Observational; cannot prove causation.
- **Explicit hypothesis contest:** land-use-dominated [[cudlin_2017_drivers_treeline_shift]], [[frei_2023_treeline_shift]], [[marzini_2025_expansion_forest]] vs climate wave [[nicoud_2025_landuse_larch_expansion]].
- **Optional extension / runner-up: species-resolved ecotone composition.** Shares of larch vs *P. cembra* vs spruce per cell, using Tyrolean S2 species work [[kollert_2021_tree_species]] and foundation-model embeddings [[brown_2025_alphaearth]], [[ball_2026_foundation_models]], [[geospatial_foundation_models]]. Embeddings exist only from about 2017, so this is a 2017-2025 composition change, not 40-year line shift; whether the BFW species map separates *P. cembra* at the forest line is unconfirmed [verify]. Competing groups (EPFL/WSL, OLYMPUS UAV project, FWF P34706 alder) noted in the research notes [verify].

**Key uncertainties:** driver datasets incomplete (browsing, abandonment); WP1 response noise; compound attribution limits.

**Expected outputs:** driver-attribution maps with uncertainty and applicability masks; variance-share table; optional species-composition layer.

---

## Work-package interdependencies

| From \ To | WP1 Change | WP2 Stressors | WP3 Attribution |
|---|---|---|---|
| **WP1** | - | change map and site selection (where trees changed or did not) | response variable (trend, height/gap change) and its detection-limit error |
| **WP2** | stress/snow layers inform interpretation of change; Landsat baseline shared | - | climate/stress predictors (anomaly, snow, ring-based sensitivity) |
| **WP3** | feeds back driver-based stratification for validation sites | suggests which drivers need field/ring follow-up | - |

Critical path: WP1 (Landsat product, ALS differencing) must deliver a first change layer by the end of Year 1 for WP3; WP2 can run in parallel and degrades gracefully (a null WP2 reduces WP3 to climate/snow from gridded data only).

---

## Data availability

| Data | Coverage | Access / status | Main limitation |
|---|---|---|---|
| Landsat 5/7/8/9 (Collection 2) | 1984-2025, 30 m | open (USGS) | pixel vs shift rate; observation-density artefact; TM harmonisation by project; TM mountain geolocation unknown [verify] |
| WorldView stereo | ESA archive 2009-02 to 2020-12 (report-level) | catalogue query needed; no national licence found | footprints over Tyrol unchecked; DSM error about 1-4 m |
| ALS (Land Tirol) | epoch 1: 2006-2010; epoch 2: 2017-2023 | DTM/DSM free at 50 cm; per-tile dates required | year mosaics; first-epoch DSM unconfirmed [verify] |
| Orthophotos (Land Tirol) | 20 cm, 3-4 year updates, some historical | request earliest years | earliest year unknown; validation only |
| WEM browsing (Wildeinflussmonitoring) | 2019-2021 reported at district/state level | request point-level release | samples regeneration areas, not the ecotone [verify] |
| SPARTACUS / SNOWGRID | daily climate and 1 km snow, Austria | via GeoSphere Austria (access terms [verify]) | 1 km; snow bias at altitude; few stations above 2000 m |
| ERA5-Land | hourly, 9 km | open (Copernicus) | snow bias increasing with elevation |
| Sentinel-2 | 2015/17-2025, 10 m | open | about ten seasons; mixed pixels; snow/shadow |
| Tree rings | new cores + ITRDB | fieldwork; permits | existing ITRDB series end before 1976 |
| Land-use history, avalanche layers, ownership | unknown | Year 1 requests (Land Tirol, forest service) | not found in a limited search |

---

## Expected outputs

| Paper | Focus | Target journal (suggestion) | Timing |
|---|---|---|---|
| Paper 1 | Detection limits and results of Landsat forest-line change with density-robust trends, validated against orthophotos | *Remote Sensing of Environment* / *Biogeosciences* | Year 2 |
| Paper 2 | Repeat-ALS (and WorldView feasibility) canopy change at the Tyrolean forest line | *Remote Sensing of Environment* / *Remote Sensing* | Year 2 |
| Paper 3 | Do heat, drought, frost and snow leave Sentinel-2 and tree-ring signatures at the forest line? (null results accepted) | *Agricultural and Forest Meteorology* / *Global Change Biology* | Year 3 |
| Paper 4 | Attribution with bounds of forest-line change to land use, browsing, disturbance and climate | *Global Change Biology* / *Ecography* | Year 3 |
| Data | Change maps, error models, chronologies (open) | *Earth System Science Data* | Year 3 |

Data outputs: forest-line change maps, error models, chronologies, driver layers. Policy relevance (Land Tirol, forest owners, Natura 2000 habitat 9420) is plausible but **no data agreements or support letters exist; roles unverified**.

---

## Risks and mitigation

| Risk | Likelihood | Mitigation |
|---|---|---|
| Landsat shift below detection limit | high | report minimum detectable shift; density/fraction trend as primary product; orthophoto validation |
| Greening artefact mimics change | medium | observation-density diagnostics, robust time-series model; do not trend NDVImax |
| WorldView archive does not cover 2005-2009 or Tyrol | high | ALS as 3D core; stereo as bounded feasibility test |
| Stereo noise exceeds signal | high | empirical error model; restrict to tall stands/gaps; publish negative limit |
| ALS first-epoch DSM or dates unavailable | medium | request early; use DTM+aerial photogrammetry fallback [verify] |
| No Sentinel-2 stress signal at altitude | medium-high | pre-registered acceptable null; event-year contrasts; Landsat baseline to 2003 |
| Only about 10 S2 seasons vs ring series | high | pooled mixed models, event contrasts, no per-site correlation claims |
| Driver data (browsing, abandonment, avalanches) missing | medium-high | Year 1 requests; proxy layers; report where drivers cannot be separated |
| Attribution mistaken for causation | medium | wording "attribution with bounds"; counterfactual scenarios; AOA masks |
| Competing groups (Innsbruck physiology, EPFL/WSL, Italian UAV) | medium | collaboration with Innsbruck; distinct scope (Tyrol-wide, multi-driver) |
| Funding | high | FWF Stand-Alone Project is the realistic fit [verify terms]; no budget or staffing plan yet |

---

## Timeline (3 years, relative to project start; earliest realistic 2027)

| Phase | Year 1 | Year 2 | Year 3 |
|---|---|---|---|
| **WP1** | data requests (ALS, orthophotos, WorldView footprints); Landsat pipeline; forest-line definition and sensitivity | ALS differencing; WorldView feasibility and error model; Landsat series and validation | final change products; Paper 1, Paper 2 |
| **WP2** | site selection; coring (first campaign); S2 baseline | ring processing (width, density, frost rings); event-year contrasts | integration; Paper 3 |
| **WP3** | driver data requests (WEM, land use, avalanches) | model set-up, spatial CV, AOA | attribution, uncertainty, optional species extension; Paper 4 |
| **Outputs** | datasets and design documents | Paper 1, Paper 2 | Paper 3, Paper 4, data paper |

---

## Open items to verify before submission

- ESA WorldView footprints over Tyrol 2009-2020 and any licence route; whether 20-year stereo coverage exists at all.
- Land Tirol: first-epoch ALS DSM, per-tile flight dates, licence; earliest orthophoto year.
- Landsat 4/5 TM geolocation error in mountain terrain; Roy et al. 2016 harmonisation transforms; HLS between-sensor DOI.
- Piermattei et al. 2018 sigma-MAD figures (report mentions Salzburg wrongly); Næsset 2019/2021 details.
- Size of the Landsat greening artefact at 1900-2200 m; Bayle follow-up DOI 10.1002/rse2.430 (journal unconfirmed).
- WEM point-level release; alm-abandonment time series; avalanche and ownership layers.
- Nguyen 2024 DOI; Märker 2025 DOI; Charra-Vaskou year (2025 vs 2026); ITRDB AUST002 species; "Larix decemlineata" meaning; Oberleitner site elevation.
- Documented Scopus/Web of Science search before any "first study" claim.
- Funding scheme terms and partner roles (no letters exist).

---

## Key references

DOIs only where verified in the wiki notes or in [[02_tree_line_stress]]; others marked [verify].

**Wiki notes (cited above)**
- [[menegaldo_2025_landsat_treeline_dynamics]] - doi:10.3897/ved.177152
- [[frei_2023_treeline_shift]] - doi:10.3390/f14020412 (from [[02_tree_line_stress]])
- [[garbarino_2023_treeline_remote_sensing]] - doi:10.1002/rse2.351
- [[carrieri_2025_hr_imagery_treeline]] - doi:10.5194/bg-22-6393-2025
- [[marzini_2025_expansion_forest]] - doi:10.1007/s10980-025-02070-8
- [[nicoud_2025_landuse_larch_expansion]] - doi:10.1016/j.scitotenv.2024.178326
- [[cudlin_2017_drivers_treeline_shift]] - doi:10.3354/cr01465
- [[dullinger_2004_climate_treeline_shifts]] - Dullinger, Dirnböck & Grabherr 2004, *J Ecol* 92:241-252
- [[albrich_2020_transitions_mountain_forests]] - doi:10.1111/gcb.15118
- [[obojes_2018_water_stress_growth_larch]] - doi:10.1111/nph.15348
- [[obojes_2024_growth_limits_elevational]] - doi:10.3389/ffgc.2024.1332941
- [[frank_2026_larch_growth_temperature_density]] - doi:10.1007/s10342-026-01912-7
- [[matiu_2021_snow_depth_trends]] - [verify DOI]
- [[olefs_2020_snow_depth_changes]] - doi:10.3390/atmos11121330
- [[senf_2021_impacts_2018_forests]] - doi:10.5194/bg-18-5223-2021
- [[löw_2020_phenology_austria_forest]] - doi:10.3390/rs12244191
- [[neuner_2014_frost_resistance]] - doi:10.3389/fpls.2014.00654
- [[nicolussi_2005_holocene_treeline_variability]] - doi:10.1007/s00334-005-0013-y
- [[bayle_2024_landsat_greening_inflated]] - *Ecography* e07394 [verify DOI]
- [[obuchowicz_2024_greening_switzerland]], [[turubanove_2023_canopy_landsat]], [[lang_2024_canopy_height]] - [verify DOIs]
- [[charra_2025_snow_treeline]] - doi:10.1111/nph.70926
- [[wieser_2019_effects_climate_treeline]], [[schuldt_2020_drought_forest]], [[maerker_2025_drought_spruce]], [[nguyen_2022_forest_mapping_explainable]] (doi:10.1016/j.rse.2022.113217), [[nguyen_2024_treeline_monitoring]] [verify], [[kollert_2021_tree_species]], [[brown_2025_alphaearth]], [[ball_2026_foundation_models]], [[lakshminarayan_2017_uncertainty]], [[mila_2024_spatial_proxies]], [[pebesma_2025_spatial_data]]
- Vitasse et al. 2021 [[vitasse_2021_shifts_plants_alps]]: measures species optimum shifts (+18-25 m/decade), not a treeline rate; context only.

**From the research notes (report-level, publisher full text not read)**
- Körner, C. & Hoch, G. (2023). *J Biogeogr* 50:838-845. doi:10.1111/jbi.14593
- Piermattei, L. et al. (2018). *Remote Sens* 10:1542. doi:10.3390/RS10101542
- Næsset, E. et al. (2019). *Remote Sens* 11:1804. doi:10.3390/rs11151804; (2021). *Remote Sens* 13:2469. doi:10.3390/rs13132469
- Nuth, C. & Kääb, A. (2011). *Cryosphere* 5:271. doi:10.5194/tc-5-271-2011
- Sturm, J. et al. (2022). *Glob Change Biol* 28:2956. doi:10.1111/gcb.16136
- D'Andrea, E. et al. (2022). *Forests* 13:1417. doi:10.3390/f13091417
- Gascoin, S. et al. (2019). *Earth Syst Sci Data* 11:493. doi:10.5194/essd-11-493-2019
- Oberhuber, W. et al. (2008). *Trees* 22:31. doi:10.1007/s00468-007-0166-7; Oberhuber 2004 doi:10.1093/treephys/24.3.291
- Hiebl, J. & Frei, C. (2016). *Theor Appl Climatol* 124:161-178. doi:10.1007/s00704-015-1411-4
- Gehrig-Fasel, J. et al. (2007). *J Veg Sci* 18:571-582. doi:10.1111/j.1654-1103.2007.tb02571.x
- Sindewald, L. et al. (2025). *Biogeosciences* 22:6509-6543. doi:10.5194/bg-22-6509-2025 (non-Alpine)
- Mayr et al. 2003 (doi:10.1104/pp.011452), Oberleitner et al. 2022 (doi:10.1111/pce.14369), browsing studies (Fluri et al. 2023; D'Aprile et al. 2020) - context only [verify]

**Related wiki pages:** [[treeline_ecotone_theory]] · [[treeline_land_use_legacy]] · [[treeline_remote_sensing_monitoring]] · [[snow_cover_treeline]] · [[larch_growth_climate]] · [[drought_mortality]] · [[forest_disturbances]] · [[forest_landscape_models_iland]] · [[02_tree_line_stress]]
