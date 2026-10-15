# WP3 gap candidates for the Tyrolean treeline / forest-line proposal

Scope: choose a third work package that complements WP1 (forest-line change, 40-yr Landsat; treeline volume change, WorldView stereo 2005-2025) and WP2 (stressors via Sentinel-2, dendrochronology, etc.). Study area: central Alps of Tyrol; 3 years, 1-2 PhD positions; PI background is deep learning on EO time series.

Evidence conventions: `[[note]]` = wiki note already in the repo; markdown links = new web evidence from this session. IMPORTANT caveat: all new web evidence below comes from search-result snippets or abstracts, not full texts; nothing here was verified against Crossref, so DOIs are omitted ("[verify]") unless they appeared in the wiki. Searches were limited (about 13 queries), so "no study found" means "not found in this session", not "does not exist". Confidence is stated per gap.

---

## 1. Which candidate WP3 option is best, and why?

### Takeaway
Best: **Option A, reframed as a spatially explicit, uncertainty-aware attribution of forest-line/treeline change** (land-use legacy vs browsing vs geomorphic/avalanche disturbance vs climate/snow), built on WP1 change maps and WP2 stress layers, using Tyrolean administrative data. It is the only option that (i) closes a gap the existing reports call open and unseparated, (ii) uses almost only data the team can obtain without new fieldwork, and (iii) plays to the PI's strengths (spatial CV, AOA, uncertainty). Runner-up: **Option B restricted to the Sentinel-2/AlphaEarth era** (species-resolved change *P. cembra* vs *Larix* vs *Picea*, with seed-source/nutcracker and microsite covariates). Novelty of A is real but must NOT be oversold: the "land use vs climate" question is classic (Gehrig-Fasel 2007, Cudlín 2017, Frei 2023), so the new part is the Tyrol-wide, multi-driver, quantitative, uncertainty-propagated decomposition, not the question itself. Causal language must be toned down: this is observational.

### Scoring (1 = poor, 5 = excellent; my judgement, not literature-derived)

| Option | Gap verified (conf.) | Novelty | Feasibility 3 yr | Fit PI skills | Link to WP1/WP2 | Risk (5 = low) | Sum /25 |
|---|---|---|---|---|---|---|---|
| A Drivers attribution | Partly (medium) | 4 | 4 | 4 | 5 | 3 | **20** |
| B Species-resolved change/regeneration | Partly (medium-low) | 4 | 3 | 5 | 4 | 3 | **19** |
| D Microclimate/snow explanatory layer | Partly (low-medium) | 3 | 3 | 3 | 4 | 3 | 16 |
| F Cross-sensor harmonisation/uncertainty | Yes for Tyrol (medium) | 3 | 5 | 5 | 5 | 4 | 22 raw, but see note |
| E Ecosystem consequences (protection, carbon, shrubs) | Partly (medium-low) | 3 | 3 | 3 | 4 | 3 | 16 |
| C iLand projection constrained by data | Yes (medium) | 4 | 2 | 1 | 3 | 2 | 12 |
| G Holocene / subfossil context | No new gap (high) | 2 | 2 | 1 | 2 | 3 | 10 |

Note on F: it scores highest on convenience, but it is a methods contribution that is mostly already embedded in WP1 (Landsat series + VHR validation). Treat it as a cross-cutting work task (validation and uncertainty layer inside WP1/WP3-A) rather than a stand-alone WP; a funder panel will likely read it as "WP1 methodology", not as a third scientific gap. Hence A is ranked first despite a lower raw sum.

---

## 2. Candidate-by-candidate evaluation

### Option A. Drivers attribution (land-use legacy, browsing, avalanche/rockfall, climate)

#### Takeaway
Gap is real at the Tyrol scale and in separating drivers quantitatively, but the underlying question is not new, and the key drivers (historic grazing, browsing) have coarse or incomplete data in Tyrol. Feasible and well matched to WP1/WP2 outputs.

#### Cited Findings
- Land-use legacy dominates Swiss forest-line ingrowth: above 1650 m only 10% of new forest was true upward shift, 90% ingrowth, 4% above the potential treeline (Gehrig-Fasel et al. 2007; via [[01_notes/frei_2023_treeline_shift]] context and the existing report). Wiki: [[treeline_land_use_legacy]].
- Pan-European comparison of 15 mountain units: temperature alone does not explain shift; land-use history, geomorphology and soils dominate, but the method is expert-based RDA ([[cudlin_2017_drivers_treeline_shift]]).
- Dischma 40-yr resurvey: ~10 m/decade, 79% of new cells infilling; microsite and 1900 land use control advance ([[frei_2023_treeline_shift]]).
- iLand projection for the Eastern Alps: expansion mainly through abandonment, climate shapes composition; no empirical validation ([[marzini_2025_expansion_forest]]). Counter-case: French Alps larch wave ~2003 tied to a climate window with 19th-century abandonment as precondition ([[nicoud_2025_landuse_larch_expansion]]); one region, 628 trees.
- The existing report states that no study separates historic land-use depression from demographic (dispersal/generation) lag, and that no peer-reviewed lag estimate exists (Alpine treeline literature review, section on lag, and Section 7 table).
- Austria-wide ungulate browsing monitoring (Wildeinflussmonitoring, WEM) exists since 2004, 3-year cycles, district and federal-state level; Tyrol surveys regeneration dynamics at least every 3 years; 2019-2021: strong game influence on 41.8% of Tyrol survey points; a Schutzwald-specific result is available for Tyrol, unlike several other states ([waldwissen WEM 2019-2021](https://www.waldwissen.net/de/waldwirtschaft/schadensmanagement/wildschaeden/wildeinflussmonitoring-2019-2021)). Caveat: the WEM sampling is point/district-level and monitors the regeneration areas under forest management, not primarily the ecotone above the forest line [inference; verify against BFW method documents].
- Browsing evidence near the Alpine treeline: in the Swiss National Park browsing probability on larch saplings peaked at 10-40 cm height and increased with elevation, yet sapling numbers rose over 30 years ([Fluri et al. 2023, Forests](https://camargue.unibas.ch/fileadmin/user_upload/camargue/Fluri_et_al_2023_Forests.pdf)); in Paneveggio (Italy) 20 years of browsing favoured unpalatable spruce ([D'Aprile et al. 2020, Forests](https://iris.unito.it/retrieve/handle/2318/1765505/689631/2020_daprileetal_Forests.pdf)); Swiss seedling densities collapse above ~5-10% annual leader browsing (Kupferschmid et al. 2019, via the same search snippet; [verify]). Wieser et al. 2019 attribute seedling re-establishment at the Central Austrian treeline to reduced grazing ([[wieser_2019_effects_climate_treeline]]).
- Tyrol-adjacent precedent for modelling land-use-driven regeneration: Wallentin, Tappeiner, Strobl & Tasser 2008, *Ecological Modelling*, natural forest regeneration on a summer pasture, Austrian Central Alps, 1954-2006 (from search snippet only; [verify details]). Plus Tasser & Tappeiner 2002 (land-use change, South Tyrol/Tyrol) in the existing proposal.
- Data in Tyrol: second airborne laser scan of the state 2017-2023 (>=8 ground points/m2), DTM/DSM free at 50 cm GeoTIFF; first full scan 2006-2010; orthophoto WMS includes historical images; 20 cm orthophotos orderable ([Land Tirol Laserscandaten](https://tirol.gv.at/sicherheit/geoinformation/geodaten-tiris/laserscandaten); [Land Tirol Orthofotos](https://tirol.gv.at/sicherheit/geoinformation/geodaten-tiris/orthofotos)). Note: two ALS epochs (2006-10 and 2017-23) provide an independent canopy-height change product that complements WorldView stereo (2005-2025) and could cross-validate it.
- Agrargemeinschaften hold much of the alpine pasture and forest (community forests 37% of ownership per a Landtag motion text; [NEOS Klimafitter Wald](https://www.neos.eu/_Resources/Persistent/69e184af12f2aac3a14770560a3f1aba9a223d46/Klimafitter%20Wald.pdf), political source, use cautiously); the legal reforestation duty also falls on the Agrargemeinschaft as use-right holder ([VwGH decision, jusline](https://www.jusline.at/entscheidung/78978.pdf)). I found no digitised Tyrol-wide alm-abandonment time series in this session.
- Large-scale attribution is acknowledged as an open challenge in EPFL/Swiss deep-learning treeline work (EGU24 abstract; [EGU24-9480](https://meetingorganizer.copernicus.org/EGU24/EGU24-9480.html)), conference-level evidence only. The Senales study says machine-learning vs manual treeline comparison including climate variables had not been done before ([Menegaldo et al. 2025, VED](https://ved.arphahub.com/article_preview.php?id=177152); [[menegaldo_2025_landsat_treeline_dynamics]]).
- Avalanche influence on treeline in the Alps: no remote-sensing study of treeline position vs avalanche disturbance found; closest hits were Montana (Allen & Walsh 1994) and Swiss protection-forest mapping chapters (search snippets only).

#### Inferences
- A defensible, novel contribution is a *probabilistic decomposition*: for each pixel/cell of the WP1 change maps, how much of the change is explained by climate/snow (WP2 layers), by land-use legacy (alm/pasture class, distance to alm hut, old orthophoto/Franciscean cadastre if digitised), by browsing (WEM district rates, game-management units), and by geomorphic constraints (slope, avalanche tracks from the Austrian avalanche/hazard zone plans, debris), with AOA masking where the model extrapolates.
- Risk: confounding (abandonment is correlated with remoteness/elevation/slope), ecological fallacy for district-level browsing, and survivorship in the historical record. Therefore frame as "attribution with bounds" (partial dependence, SHAP, spatial block CV with kNNDM, AOA, counterfactual scenarios), not as causal proof. Wiki support: [[spatial_proxies_random_forest]], [[area_of_applicability]], [[deep_ensemble_uncertainty]], [[mila_2024_spatial_proxies]].
- Overlap check: the existing draft already contains H3 ("forest-line change explained better by land-use legacy than by climate indices alone", in `04_projects/02_tree_line_stress.md` O3). If A becomes WP3 it should be upgraded from a single hypothesis to a full WP with its own data acquisition (digitising Alm cadastre/ownership, requesting WEM at point level from Land Tirol/BFW).

#### Gaps
- Tyrol-wide historic grazing intensity and alm-abandonment dates: not found; may require archive work (Franziszeischer/Katasterdaten, Agrarbehörde, alm-cadastre) [verify availability and licence].
- Whether WEM point-level coordinates can be released: unknown.
- Avalanche/rockfall disturbance layers at the ecotone: available as hazard-zone plans (WLV) but not checked.

**Gap verdict:** verified in part. Confidence: medium (searches limited to snippets; no Austrian-wide attribution study found). **Novelty verdict:** medium-high if framed as quantitative multi-driver decomposition with uncertainty at Tyrol scale; low if framed as "land use matters more than climate".

**One-line RQ:** How much of the 1984-2025 forest-line and 2005-2025 treeline volume change in Tyrol is attributable to land-use legacy, ungulate browsing, geomorphic disturbance and climate/snow, and where are these attributions unreliable (outside the area of applicability)?

**Method outline (A):**
1. Unit: 30 m cells (Landsat series) and 1 km transect/catchment aggregates (volume change); respect support differences ([[support_intensive_extensive]]).
2. Response: forest-line shift/infilling class (WP1), canopy volume change (WP1 WorldView; cross-check with ALS 2006-10 vs 2017-23), WP2 stress anomaly indices.
3. Predictors: SPARTACUS/SNOWGRID/ERA5-Land climate and snow, alm/pasture legacy, distance to seed source (from tree species map / NFI), browsing (WEM, game-management units), slope/aspect/microtopography from ALS, avalanche paths, soil/geology.
4. Models: gradient boosting/RF plus a simple interpretable baseline (GAM with spatial term); ensembles for uncertainty; SHAP; spatial CV (kNNDM); AOA; sensitivity to forest-line definition.
5. Validation of attribution: Dischma-type paired hindcast logic is not possible; instead use leave-one-valley-out CV and compare with expert/plot data (own WP2 plots, NFI).
6. Output: attribution maps with uncertainty + a Tyrol-wide table of driver shares by valley/elevation band.

**Data needs:** WP1/WP2 outputs; Land Tirol ALS/orthophotos (open); WEM at fine resolution (request); alm cadastre/ownership (request); hazard zone plans (request); BFW forest inventory (request).

**Feasibility:** high for the modelling; medium for data access (time-consuming negotiations, Year 1).

---

### Option B. Species-resolved change and regeneration (*P. cembra* vs *Larix* vs *Picea*)

#### Takeaway
Ecologically attractive (species respond differently to snow loss and dispersal) and well suited to the PI's expertise, but the long Landsat record cannot resolve species at the ecotone, so species-resolved change is realistic only for the Sentinel-2 / foundation-model era, and recruitment needs fieldwork already in WP2.

#### Cited Findings
- Snow-removal experiment: *Picea* resisted, *Sorbus/Acer* resprouted, *Larix* had high mortality without recovery ([[charra_2025_snow_treeline]]); *P. cembra* not tested. Frost and spring deacclimation risks differ by species ([[neuner_2014_frost_resistance]]). Larch/conifer water vs temperature limitation along elevation gradients ([[obojes_2018_water_stress_growth_larch]], [[obojes_2024_growth_limits_elevational]]).
- *P. cembra* recruitment at its upper range edge was found to be limited by seed deposition/biotic interactions rather than abiotic factors in a Dryad data record (title: "Biotic interactions and seed deposition rather than abiotic factors determine recruitment at elevational range limits of an alpine tree"; snippet only, [Dryad record](https://datadryad.org/dataset/doi:10.5061/dryad.8t2q2)); seed deposition fell 90% from lower to upper range margin but was offset by higher germination/survival (Merges et al. 2020, *Sci Rep*, via [PMC7331732](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7331732/)); GPS-tracked nutcracker caches averaged 5.3 km from harvest site, many at low elevations in spruce forest (Graf et al. 2024 [verify]). Existing report: seed-source distance and cache-like microsites must be recorded.
- Italian OLYMPUS project: UAV-SfM seedling mapping at 10 treelines; preliminary: ground cover (grass, deadwood) and heat load/eastness relate to establishment, neighbouring trees reduce it (conference abstracts only, [IMC 2025 abstract](https://imc2025.info/?p=40500)). Carrieri et al. 2025 UAV Mask R-CNN: 70% detection of conifers >50 cm, leave-one-site-out recall 0.56 ([[carrieri_2025_hr_imagery_treeline]]).
- Species mapping in Tyrol/Austria: [[kollert_2021_tree_species]] (Tyrol, S2 LSP + composites); BFW Austria-wide S2 CNN tree species map ([MDPI Remote Sens 2024, 16(16):2887](https://www.mdpi.com/2072-4292/16/16/2887/xml), snippet; DOI [verify]; I did not confirm whether *P. cembra* is a separate class). Foundation models: [[ball_2026_foundation_models]] (Trentino, 18 species, AlphaEarth/Tessera), [[feng_2026_tessera]], [[brown_2025_alphaearth]], [[tan_2025_deep_tree_species]]. Mixed stands reduce accuracy by 4-14 pp ([[blickensdörfer_2024_tree_species]]).
- Intraspecific/treeline-specific limits: WorldView-3 multi-class species accuracy 44-47% in the Rocky Mountains (Sindewald et al. 2025, in existing proposal; not Alpine).

#### Inferences
- AlphaEarth/Tessera embeddings only exist from about 2017 (Sentinel-era) [[brown_2025_alphaearth]]; so a *species-resolved forest-line change* would cover about 2017-2025: a short window, in which line displacement (>=1 m/yr) is below pixel size. Species composition shifts of the *ecotone belt* (share of larch vs cembra vs spruce in 1 ha cells) is more plausible than line displacement.
- Larch is deciduous, and the leaf-off/larch yellowing signal makes larch-vs-cembra separation easier than in evergreen mixtures; this is an advantage the PI can exploit with S2 time series ([[tree_species_mapping]], [[transformer_sits]]).
- Regeneration at sapling scale is not visible from satellites; it requires UAV/VHR (sub-5 cm) or ALS 2017-23 microtopography. A regeneration module overlaps with WP2's recruitment census and the Innsbruck group's work (Oberhuber, Gruber, Wieser, Mayr).

#### Gaps
- No Alpine-validated species map at the treeline ecotone found; labels for pre-2017 species composition: none. NFI plots at treeline are sparse and access-restricted.

**Gap verdict:** partly verified, confidence medium-low (I could not confirm what the BFW national map does at the forest line; there may be an existing product). **Novelty verdict:** medium; "first species-level treeline map for Tyrol" is overclaimable and should be checked.

**One-line RQ:** Does the species composition of the Tyrolean upper-forest belt (*P. cembra*, *Larix*, *Picea*) shift differently from total cover change, and is this shift explained by seed-source distance, microtopography and snow-cover duration?

**Method outline (B):** (1) build training labels from NFI/own plots/UAV-interpreted samples at the ecotone; (2) S2 annual time series + AlphaEarth/Tessera embeddings, deep-ensemble soft-label regression of species fractions ([[01_notes/hiebl_2025_pretraining]], [[01_notes/ball_2026_foundation_models]]); (3) AOA mask; (4) apply 2017-2025; (5) relate to seed-source distance (from the species map), ALS microtopography and snow metrics; (6) UAV validation at WP2 sites.

**Feasibility:** medium (labels are the bottleneck). **Risk:** mixed pixels at 10 m, small sample of reliable ecotone labels, short temporal window.

---

### Option C. Process-based modelling (iLand) projections 2050-2100

#### Cited Findings
- iLand in the Stubai Valley: tipping point >~+2 degC to small broadleaved forest, hysteresis ([[albrich_2020_transitions_mountain_forests]], [[albrich_2019_climate_change_mountain_forests]]); ecotone expansion via abandonment ([[marzini_2025_expansion_forest]]); EGU26-9249 abstract on treeline under land use and climate ([EGU26-9249](https://meetingorganizer.copernicus.org/EGU26/EGU26-9249.html)).
- I found no published iLand (or other process-model) hindcast of observed Alpine treeline change (search result; also stated in existing report: "no model has been validated against an observed Alpine treeline shift").

#### Inferences
- The gap (validation against WP1 observations) is genuine and attractive, but the model is run by a separate group (BOKU/Eurac/Marzini et al.); PI skills are not in process modelling, and calibrating iLand realistically takes more than 3 years of a PhD for a non-modeller. Viable only as a collaboration with a small hindcast-comparison task (compare iLand output for historic land-use scenarios with WP1 maps), which could be a subtask of A rather than a WP.

**Gap verdict:** verified (confidence medium). **Novelty:** medium-high but gated by collaboration. **RQ:** Can iLand, forced with historic land-use and climate, reproduce the observed 1984-2025 forest-line pattern in Tyrol? **Feasibility:** low-medium. **Risk:** high.

---

### Option D. Topographic microclimate and snow modelling as explanatory layer

#### Cited Findings
- Topographic regulation of temperature/biodiversity ([[bricca_2026_topo_diversity]], [[topographic_microclimate]], [[francioni_2026_canopy_closure]]); snow as protective cover ([[snow_cover_treeline]]); observational snow products: SNOWGRID-CL 1 km, -0.15 m depth, -42 days snow cover, significant below ~2000 m ([[olefs_2020_snow_depth_changes]]); Alpine station snow trends -8.4%/decade, few stations above 2000 m ([[matiu_2021_snow_depth_trends]]).
- Fine-scale microclimate improves distribution models (Lembrechts 2019, Scherrer & Körner 2011; in existing report; plants/not conifers).
- OLYMPUS: heat load/eastness related to seedling presence (conference abstract only).

#### Inferences
- Gap: no sub-100 m snow-duration/melt-out product at treeline elevations tied to recruitment; 1 km SNOWGRID is too coarse for treeline microsites. A DL-friendly route is pixel-level snow-cover fraction from Landsat/S2 time series (melt-out day, snow duration per year) at 10-30 m, calibrated on loggers/webcams from WP2.
- Probably already covered by WP2 (loggers, webcams). Making it WP3 risks being a sub-task, and the explanatory power of snow metrics for *recruitment* (not growth) is unproven (Charra-Vaskou experiment concerns saplings at 1700 m).

**Gap verdict:** partly verified (confidence low-medium; the snippets I got did not directly address snow duration and seedlings in the Alps). **Novelty:** medium. **RQ:** Does melt-out timing and snow-duration (10-30 m, S2/Landsat-derived) explain spatial variation in treeline ecotone infilling better than 1 km gridded snow? **Feasibility:** medium. **Risk:** medium (cloud/shadow, Landsat revisit in alpine terrain; sampling bias [[sampling_bias_remote_sensing]]).
Recommended use: integrate into A as a predictor-engineering task, not a separate WP.

---

### Option E. Ecosystem consequences: protection forest, carbon, biodiversity, shrubs

#### Cited Findings
- WP1's volume change enables biomass/carbon translation; pan-European volume/AGB maps from S2 + NFI show regression-to-mean bias ([[miettinen_2025_forest_maps_europe]]); canopy height products: [[lang_2024_canopy_height]], [[fischer_2025_glocal_canopy_atlas]]; Landsat canopy height change in Europe ([[turubanove_2023_canopy_landsat]]).
- Repeat stereo/aerial-based AGB: relation between CHM and AGB stable over time but performance dropped for time differences >2 years (Swiss aerial study, search snippet; [verify]). No WorldView treeline volume-change study found.
- Protection forest mapping in Switzerland combines LiDAR/RS with avalanche models, and uncertainty is highest where protective effect is high (Bebi et al. and Stritih chapters, [IntechOpen chapter](https://www.intechopen.com/chapters/78340); snippets only). No study found tracking the Alpine upper forest limit as protective boundary with satellite time series.
- Shrub encroachment: green alder (*Alnus viridis*) is described as the most expanding shrub in the Alps, with an FWF project (P34706) running 2021-2026 on its growth at the treeline ([FWF P34706](https://www.fwf.ac.at/en/research-radar/10.55776/P34706)); WSL/SLF are mapping alder and dwarf mountain pine by RS ([WSL project](https://www.wsl.ch/en/projects/nationwide-shrub-forest-distribution-maps-based-on-remote-sensing/)); Braunisch et al. 2016 (PLoS ONE, [PMC5058552](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5058552/)) classified treeline vegetation incl. *Alnus viridis*. Alder alters water balance of the Patscherkofel ecotone (IMC 2025 abstract; preliminary). *Pinus mugo* spread: [[dullinger_2004_climate_treeline_shifts]].
- Spectral diversity/biodiversity framing: [[spectral_diversity_biodiversity]], [[ebv_biodiversity_monitoring]]; GLORIA does not record tree density (existing proposal).

#### Inferences
- The carbon/volume translation is low-risk "added value" but mostly arithmetic (allometry/CHM-to-AGB) and unlikely to carry a WP alone; the interesting scientific point would be whether volume gain is concentrated in infilling (carbon gain in existing forest) vs upward expansion.
- Shrub encroachment is a genuine competing land-cover trajectory that tree-focused change detection (WP1) could misclassify; ongoing FWF/WSL work means novelty claims are risky, and collaboration is preferable.
- Protection-forest consequences need avalanche-model (e.g. RAMMS) expertise outside the team.

**Gap verdict:** partly verified, confidence medium-low. **Novelty:** medium (overlapping projects). **RQ:** How much of the 2005-2025 treeline volume gain is infilling vs upward expansion, vs. shrub (alder/mugo) expansion, and what does this mean for carbon and protective function? **Feasibility:** medium. **Risk:** medium-high (alder/mugo vs tree separation in WorldView and Landsat).
Recommendation: use as a "so-what" deliverable within A (volume/carbon translation, shrub class as competing trajectory), not as a WP.

---

### Option F. Cross-sensor harmonisation, uncertainty quantification, reproducibility

#### Cited Findings
- Landsat/orthophoto treeline discrepancies: +32 m (Landsat) vs +45 m (orthophoto) in one valley, 16 areas ([[menegaldo_2025_landsat_treeline_dynamics]]); Landsat greening inflation by observation density ([[bayle_2024_landsat_greening_inflated]], [[sampling_bias_remote_sensing]]); Garbarino et al. 2023 review of 372 papers argues for multiscale approaches ([[garbarino_2023_treeline_remote_sensing]]); nguyen_2022/2024 rule-informed CNN and temporal-consistency loss ([[nguyen_2022_forest_mapping_explainable]], [[nguyen_2024_treeline_monitoring]]); forest definition affects boundaries ([[treeline_remote_sensing_monitoring]]).
- Uncertainty tooling in wiki: [[deep_ensemble_uncertainty]], [[sylvain_2021_ensemble]], [[sylvain_2024_tree_species_uncertainty]], [[transfer_learning_remote_sensing]], [[schloegl_2026_reproducibility]].
- Conference-level: Swiss treeline mapping from aerial archives 1946-2020 with DL; attempt at Alps-wide treeline pattern mapping (EGU24 abstracts; [EGU24-9480](https://meetingorganizer.copernicus.org/EGU24/EGU24-9480.html)). So a competing group is working in the neighbourhood.

#### Inferences
- Genuine need: no Tyrolean (Austrian side) validated cross-sensor forest-line product with propagated uncertainty was found. But novelty is mostly methodological, and the competition (Tuia/EPFL, Garbarino) is strong; contribution as WP3 would look like an extension of WP1.

**Gap verdict:** verified for Tyrol, confidence medium. **Novelty:** low-medium. **RQ:** How large is the sensor/definition-induced uncertainty in forest-line change estimates (Landsat vs Sentinel-2 vs orthophoto/ALS), and does a deep-ensemble product propagate it faithfully? **Feasibility:** high. **Risk:** low.
Recommendation: include as a cross-cutting validation/uncertainty task inside WP1 and as the uncertainty layer feeding A.

---

### Option G. Paleo / long-term context

#### Cited Findings
- Kauner Valley dendro record: 20th-century treeline rise ~65 m; treeline above its 1980 level for most of 7100-2100 b.c. ([[nicolussi_2005_holocene_treeline_variability]]). Existing report: Holocene records agree on higher past limit but not on how much of the current gap is anthropogenic (Tinner & Theurillat, Colombaroli).
- I found nothing new in this session indicating an unsolved Tyrol-specific paleo gap addressable with RS skills.

#### Inferences
- Valuable as framing for the potential-line/lag discussion (what is the "potential" treeline), but producing new subfossil data needs specialised dendro/14C expertise, fieldwork at glacier forefields, and a long lead time. Use the existing record to bound the "potential treeline" in A (explicitly as a prior), rather than a WP.

**Gap verdict:** no new gap for this team (high confidence). **Novelty:** low. **Feasibility:** low for this team. **Risk:** medium.

---

### Additional candidate found (H): Ecotone structure-from-time: "infilling vs advance" decomposition from volume change
- Idea: WP1 provides both line shift (30 m resolution) and volume change (WorldView, 2005-2025). The wiki and existing literature show 79% of new cells in Dischma were infilling ([[frei_2023_treeline_shift]]) and 90% ingrowth in Gehrig-Fasel 2007. For Tyrol, a joint line-vs-volume decomposition (densification inside vs expansion above) has not been found in the Austrian Alps. This is basically a core WP1 result and the response variable for A; do not separate.

---

## 3. Recommended WP3: details

**Title (suggestion):** "Attributing and bounding the drivers of Tyrolean forest-line and treeline change."

**Why not the others:** C is not the team's skill set; D, E, F are best folded into A as tasks; G is context; B is the runner-up but depends on labels and a short time window.

**Work plan (3 years, 1 PhD part-time):**
- Y1: data acquisition and legal requests (WEM point-level data, alm cadastre/ownership, hazard-zone plans, ALS epochs); baseline model with WP1 preliminary maps; define forest-line definition and sensitivity.
- Y2: full attribution models with spatial CV, AOA, ensembles; integrate WP2 stress layers; ALS-vs-WorldView volume cross-validation.
- Y3: scenario/counterfactual analysis (e.g. "no browsing", "alp still grazed"), hindcast comparison with iLand outputs if collaborators agree; synthesis paper.

**Deliverables:** attribution maps with uncertainty; Tyrol-wide driver-share table; open data/code; 1-2 papers (e.g. *Global Change Biology*, *Remote Sensing of Environment*, *Journal of Ecology*; targets are suggestions).

**Runner-up B (S2/foundation model era species-resolved ecotone):** can be pursued as a second PhD's paper or a methods-heavy subtask if a species label source is secured.

**Overall risks to state in the proposal:** observational confounding; coarse browsing/grazing data; forest-line definition sensitivity; competing groups (EPFL/WSL, Italian OLYMPUS, FWF alder project, Innsbruck physiology group).

---

## 4. Candidate overarching research questions (5-8)

1. How have forest line (30 m, 1984-2025) and treeline canopy volume (2005-2025) changed in the central Tyrolean Alps, and how much of the change is infilling versus upward expansion? (WP1; Gehrig-Fasel 2007, Frei 2023 give Swiss analogues)
2. Do drought, winter snow deficit and soil frost act as additional constraints (versus thermal limitation) on *P. cembra*/*Larix* at the ecotone, and in which canopy positions? (WP2; the existing proposal's O1/O2)
3. How much of the observed change is attributable to land-use legacy, browsing, geomorphic disturbance and climate/snow, with what uncertainty? (WP3-A)
4. Is change speed/direction consistent across sensors and forest-line definitions (Landsat, Sentinel-2, orthophoto/ALS, WorldView)? (cross-cutting F)
5. Do species (*P. cembra*, *Larix*, *Picea*, shrubs) respond differently, and does this alter ecotone composition? (B)
6. Where in the landscape is the forest line most likely to advance, stall or retreat under climate scenarios, once land use is held constant or abandoned, and where are such inferences outside the area of applicability? (A/C bridge)
7. Is the stress signal (S2 anomaly, ring width) in the ecotone linked to the spatial pattern of 40-year change (stress as a predictor of stagnation)? (WP1+WP2 link; H3 in the draft)
8. What does treeline densification mean for carbon stock and avalanche protection functions? (E)

---

## 5. The 8-12 most important research gaps (whole topic)

Format: gap; evidence; confidence. Builds on the table in Section 7 of the existing report.

1. **Separation of land-use legacy, dispersal/demographic lag and warming.** Existing report: "no study separates them"; Marzini 2025 is a model with no validation; counter-evidence from French Alps (Nicoud 2025). Search this session found no Alps-wide formal separation (EGU24 abstract says attribution at range scale "remains challenging"). Confidence: medium.
2. **Quantified forest-line change for Austrian Tyrol.** Existing report: none peer-reviewed; nearest is Senales Valley, South Tyrol (+32/+45 m; [[menegaldo_2025_landsat_treeline_dynamics]]); Swiss DL aerial work is conference-level. Confidence: medium-high (searches echoed it).
3. **Cross-sensor consistency and uncertainty of forest-line products** (Landsat vs orthophoto 32 vs 45 m; definition effects; observation-density bias). [[menegaldo_2025_landsat_treeline_dynamics]], [[bayle_2024_landsat_greening_inflated]], [[garbarino_2023_treeline_remote_sensing]]. Confidence: medium.
4. **Treeline volume/biomass change from VHR stereo.** No WorldView treeline-volume study found; repeat-stereo AGB precedents are aerial (Swiss) and degrade at >2-year offsets (snippet; [verify]). Confidence: medium-low (limited search).
5. **Drought as co-limitation at the upper treeline for adult *P. cembra*/*Larix*.** Existing: only lower-elevation evidence and non-responding saplings; Märker 2025 shows emerging drought sensitivity in spruce at the High Tatras treeline ([[maerker_2025_drought_spruce]]); Obojes 2024 weak temperature signal at the forest line ([[obojes_2024_growth_limits_elevational]]). Confidence: high that it is open.
6. **Winter/snow-deficit effects on *P. cembra* (not sapling of other species) and the link to recruitment and landscape change.** [[charra_2025_snow_treeline]] (five species, 1700 m, no *P. cembra*); snow-fungus mortality at the other end (Barbeito 2013, existing proposal). Confidence: high.
7. **Recruitment limitation (nutcracker, seed source, microsite, browsing) at Tyrolean treelines.** Existing: Swiss data only; nutcracker/seed deposition evidence from Germany/Switzerland (Neuschulz group, snippets); Italian OLYMPUS UAV-SfM mapping preliminary. Confidence: medium-high.
8. **Browsing effect at the ecotone.** WEM exists at federal-state/district level but evidence for the ecotone is from Swiss National Park and Italian Paneveggio, with conflicting outcomes (sapling numbers rising vs diversity bottleneck; Fluri 2023 vs D'Aprile 2020). Confidence: medium.
9. **Species-resolved ecotone change with RS.** No Alpine-validated treeline species map found; WorldView species accuracy 44-47% (Rockies); mixed-stand accuracy drop ([[blickensdörfer_2024_tree_species]]). Confidence: medium-low.
10. **Small-tree detection limits** (<1-2 m): Carrieri 2025 70% (>50 cm), 86% (>2 m), leave-one-site-out recall 0.56 ([[carrieri_2025_hr_imagery_treeline]]); sets the observable lower bound of regeneration from imagery. Confidence: high.
11. **Validation of any treeline model against observed shift** (iLand, SDMs). Existing report and this session: none found. Confidence: medium.
12. **Shrub encroachment (alder, mugo) as competing trajectory.** Alder called the most expanding Alpine shrub (FWF project P34706); WSL mapping underway; no satellite time-series quantification across the Alps found. Confidence: medium-low (actively researched; may be being filled).

---

## 6. Items to verify / open flags

- Exact citations behind snippets: Kupferschmid 2019, Merges 2020 (*Sci Rep*), Graf et al. 2024, Neuschulz et al. 2018 title/journal, Wallentin et al. 2008, Braunisch et al. 2016, BFW 2024 species-map paper (MDPI 16(16):2887), Montesano (NASA NTRS), Swiss AGB repeat-stereo study. DOIs not checked.
- Whether BFW/Austrian species maps treat *P. cembra* separately and whether they cover the ecotone.
- Release terms and spatial resolution of WEM data; availability of historic alm/grazing data.
- Conference abstracts (EGU24-9480, EGU24-10296, EGU26-9249, IMC 2025 OLYMPUS) are not peer-reviewed; use as context, not evidence.
- Existing contradiction to keep: Gehrig-Fasel 2007/Cudlín 2017/Frei 2023 (land-use dominant) vs Nicoud 2025 (climate acceleration after 2003): flag in any proposal text.
- The 0.4 m/yr claim in `04_projects/project_ideas.md` motivation remains unsupported (already flagged removed in the revised proposal).
