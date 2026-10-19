# Theme C: Remote-sensing and modelling methods for forest-line change and driver attribution (Tyrol scoping review)

Method note. Searches 2026-10-17: WebSearch (about 20 queries), CrossRef API (metadata and abstracts), Semantic Scholar API (abstracts, forward citations), publisher/repository pages via WebFetch. OpenAlex was rate-limited (HTTP 429) for the whole session, so forward citations come from Semantic Scholar only (coverage incomplete). Google Scholar was not queried directly. Tags: [ABSTRACT-READ] = abstract text read in full or nearly so (CrossRef/Semantic Scholar/publisher); [ABSTRACT-VIA-SEARCH] = abstract known only through a search-engine or fetch-tool summary (paraphrase); [SNIPPET/TLDR-ONLY]; [METADATA-ONLY]; [FULLTEXT-PARTLY-READ] = web page text read (used for Land Tirol pages). No full-text PDFs of journal papers were read. Quotes are short fragments of abstracts. "Wiki" = note exists in 01_notes/ (not re-read here). Cross-references to shared methods (Olofsson, Pontius and Lippitt, LandTrendr) point to `03_papers/04_evergreen_distribution_change_litreview.md`.

## Q1. Landsat 1984-2025 forest-line change in mountain terrain: what is documented, and what are the detection limits?

### Takeaway
Landsat treeline studies exist (South Tyrol, Italian Alps, western North America, Tianshan) but none states a validated minimum detectable shift in metres, and none controls observation density; the only documented counter-finding to the greening-artefact worry comes from grasslands, not forest lines. Geolocation of Landsat TM in mountain terrain is still undocumented (only a generic Tier 1 tolerance of 12 m RMSE was found).

### Cited Findings
Charted studies (all Landsat or Landsat-plus-aerial treeline or forest-line studies found; wiki notes noted where they exist).

| Ref (full) | Tag | Region, period | Data / method | Finding (short quote) | Limits | Supports |
|---|---|---|---|---|---|---|
| Menegaldo et al. 2025, *Vegetation Ecology and Diversity*, [10.3897/ved.177152](https://doi.org/10.3897/ved.177152) (wiki: menegaldo_2025_landsat_treeline_dynamics; citation by S2 as "Tree line dynamics and forest densification in the European Alps revealed by Landsat images and machine learning") | wiki, abstract not re-read here | Schnals valley, South Tyrol, 1985 vs 2022 | Landsat 5/8, Random Forest, vs manual orthophoto delineation | +32 m (Landsat) vs +45 m (orthophoto); forest +44% (wiki, from proposal) | one valley, one climate station; 98% accuracy is plugin-internal, not a line-position error | Landsat underestimates by about 13 m; closest benchmark to Tyrol |
| Baglioni, Morresi, Garbarino, Urbinati 2025, *Biogeosciences* 22(17):4349-4366, [10.5194/bg-22-4349-2025](https://doi.org/10.5194/bg-22-4349-2025) | [ABSTRACT-READ] | Italian Alps and Apennines, 1984-2023 | Landsat vegetation-index trends (contextual Mann-Kendall) in buffers along an automatically mapped forestline | "general expansion of the forest cover mainly close to the forestline and at lower elevations" | trend significance on index values, no observation-density correction mentioned in the abstract; no shift in metres given in abstract; full text unread | Landsat trend products near the forest line are published for Italy; Tyrol not covered |
| Corimanya et al. 2025, *Biogeosciences* 22:5665, [10.5194/bg-22-5665-2025](https://doi.org/10.5194/bg-22-5665-2025) | [ABSTRACT-READ] plus fetch summary of page | 115 peaks, western North America, 1984-1988 vs 2013-2017 | Landsat NDVI along 100 m-spaced transect points; NDVI isoline matched between periods | mean 20.2 m upslope, range 165 m downslope to 127 m upslope (fetch summary of the paper) | authors name sensor changes ("may introduce noise") and short time span; Landsat pixel size not treated as limitation; sub-pixel shifts are inferred from NDVI isolines, unvalidated | an NDVI-isoline method yields sub-pixel mean shifts but with no stated detection limit |
| Luo & Dai 2013, *J Appl Remote Sens* 7(1):073520, [10.1117/1.JRS.7.073520](https://doi.org/10.1117/1.JRS.7.073520) | [ABSTRACT-READ] | Tianshan (Xinjiang), 1962/1981 aerial photos to 2006 QuickBird | object-based classification, post-classification comparison | tree line rose "2 to 3 m" (1962-2006) and "7 to 12 m" (1981-2006) | not Landsat; shows that VHR gives metre-scale shifts that Landsat could not resolve | order of magnitude of true shifts |
| Bayle et al. 2025, *Remote Sens Ecol Conserv*, [10.1002/rse2.430](https://doi.org/10.1002/rse2.430) | [ABSTRACT-READ] | SW French Alps, 1983/2018 images, Landsat 1984-2023 | orthorectified diachronic images, dendrochronology, LiDAR vs Landsat greening | "most of the alpine greening in this area can be attributed to forest dynamics, including forest ingrowth and treeline upward shift"; greening highest where trees established "in the mid-80s" | one region; closes the proposal's [verify] on journal (RSEC, 2025) | greening near forest lines reflects stand growth and infilling, not only line shift |
| Bayle et al. 2024, *Ecography* e07394, [10.1111/ecog.07394](https://doi.org/10.1111/ecog.07394) | wiki (also in evergreen review: "almost 50 %" of greening explained by observation density; bias "less pronounced" in lower forest zones) | Alps, non-forest above 1500 m | Landsat summer NDVI | observation-density artefact | measured above treeline; size at 1900-2200 m unquantified | artefact warning |
| Obuchowicz, Poussin & Giuliani 2024, *Big Earth Data* 8(1):1-32, [10.1080/20964471.2023.2268322](https://doi.org/10.1080/20964471.2023.2268322) | wiki; search summary confirms L5/L8 only, L7 excluded for scan-line gaps, 0.6%/yr slope for 61% significant pixels ([UNIGE record](https://archive-ouverte.unige.ch/unige:172538)) | Switzerland 1984-2018 | Swiss Data Cube NDVI | national greening | no observation-density correction found in sources read; no treeline analysis | "uncorrected" warning case |
| Lewińska et al. 2025, *Remote Sens Environ* 323:114736, [10.1016/j.rse.2025.114736](https://doi.org/10.1016/j.rse.2025.114736) | [ABSTRACT-VIA-SEARCH] (publisher abstract truncated in S2) | 13 European grassland sites, Landsat plus Sentinel-2 | spectral mixture analysis, three data-density scenarios | per search summary: "no significant effect of data density" on trends of cumulative endmember fractions; endmember definition mattered more | grasslands, fraction products, not NDVImax, not forest lines. Contradicts the generality of Bayle 2024 only partly (different metric) | endmember/definition sensitivity of sub-pixel trends; counter-evidence to treat the artefact as metric-specific |
| Senf, Laštovička, Okujeni, Heurich 2020, *Remote Sens Environ* 240:111691, [10.1016/j.rse.2020.111691](https://doi.org/10.1016/j.rse.2020.111691) | [ABSTRACT-READ] | Bavarian Forest/Sumava (central Europe), three decades of Landsat | regression-based unmixing (SVR/RFR trained on synthetic mixtures) | forest cover fraction "r2 = 0.74/RMSE = 0.18"; "highest map errors in mature stands, residential areas, and recently disturbed forests"; some variability in stable pixels explained by acquisition dates | fraction RMSE 0.18 is large relative to the thin forest-line fraction gradient; non-Alpine treeline | sub-pixel forest fraction approach is feasible; the RMSE sets a noise floor; observation-date effects are documented |
| Roy et al. 2016, *Remote Sens Environ* 185:57-70, [10.1016/j.rse.2015.12.024](https://doi.org/10.1016/j.rse.2015.12.024) | [ABSTRACT-READ] (partial) | ETM+ vs OLI overlap, 59 million 30 m pairs | per-band and NDVI transforms | ETM+ to OLI continuity transforms | covers ETM+ to OLI only, not TM; transform values not read | harmonisation reference (resolves the proposal's "Roy 2016 not checked" partly: it exists, TM not covered) |
| Storey, Choate & Lee 2014, *Remote Sens* 6:11127-11152, [10.3390/rs61111127](https://doi.org/10.3390/rs61111127) | [ABSTRACT-READ] | Landsat 8 OLI | on-orbit geometric calibration | all geometric requirements "meet or exceed" | OLI only; no mountain-terrain or TM statement | geolocation of OLI; TM remains a gap |
| Landsat 5 Collection 2 Tier 1 definition, Google Earth Engine catalogue [LT05 C02 T1](https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LT05_C02_T1) | [SNIPPET/TLDR-ONLY] | global | USGS tier criteria | Tier 1 requires georegistration "<=12 m root mean square error (RMSE)" | RMSE is a scene-level control-point statistic, not a statement about terrain displacement in relief; USGS primary page not read | partial answer to the proposal's open item (TM geolocation) |
| Kennedy et al. 2010, [10.1016/j.rse.2010.07.008](https://doi.org/10.1016/j.rse.2010.07.008); Cohen et al. 2010 (TimeSync), [10.1016/j.rse.2010.07.010](https://doi.org/10.1016/j.rse.2010.07.010) | [METADATA-ONLY] here (both known; evergreen review holds Kennedy at ABSTRACT-VIA-SEARCH level) | Pacific Northwest forests | LandTrendr segmentation; TimeSync image-interpretation validation | - | no treeline use found; the Tatra LandTrendr study (see Q7) is the nearest mountain use | methodology transfer; TimeSync-style plot interpretation is the standard validation design for Landsat trajectories |
| Sexton et al. 2015 (publ. 2016), *Nature Climate Change* 6:192-196, [10.1038/nclimate2816](https://doi.org/10.1038/nclimate2816) | [METADATA-ONLY] | global | tree-cover threshold sensitivity (title: "Conservation policy and the measurement of forests") | - | abstract not obtained; cited for the principle that forest area depends on the canopy-cover threshold | threshold sensitivity of forest definitions |

- Sub-pixel versus hard classes: published regression unmixing (Senf 2020) and the Italian 40-year fraction series (wiki notes 03_tree_species_cover_landsat, 03_landsat_data_publication) show fractions are practical; none was tested at a forest line.
- Topographic correction: only unrelated hits found (an EGU26 abstract on topographic correction efficacy for disturbance mapping, [10.5194/egusphere-egu26-16306](https://doi.org/10.5194/egusphere-egu26-16306), snippet-level); no Alpine treeline benchmark found.
- Austrian/Tyrolean Landsat forest-cover products: none found in two searches. Nearest items are a Lower Austrian district study (Mödling) and an Austrian biosphere-reserve Landsat project (BRMON report), neither at a forest line (search snippets only).

### Inferences
- A 30 m pixel plus a 12 m Tier 1 registration tolerance suggests a practical minimum detectable shift on the order of one pixel for a single date pair; sub-pixel means (as in Corimanya) are statistically estimable but not validated against ground truth. This is an inference, not a published detection limit.
- Because Bayle 2025 attributes greening mainly to infilling and growth of existing stands, a forest-fraction or NDVI trend near the line mixes line advance, densification and growth; the project must separate them (orthophotos, ALS).
- Lewińska 2025 suggests the density artefact may be metric-dependent; the Tyrol project should test it directly rather than assume either size.

### Gaps
- No documented geolocation accuracy of Landsat 4/5 TM Collection 2 over steep terrain (only the 12 m Tier 1 tolerance).
- No study found that bootstraps observation density at a forest line (not found in limited search; no Scopus/WoS search done).
- No Alpine topographic-correction benchmark for TM/ETM+ forest cover.
- Menegaldo 2025, Baglioni 2025, Corimanya 2025 full texts unread, so reported accuracies and uncertainty handling are unverified beyond abstracts.

## Q2. 3D canopy change: repeat ALS, satellite stereo, historical aerial photos; error models and detection limits

### Takeaway
Repeat-ALS treeline height change is documented for Norway only (plus Swiss non-treeline forest work); satellite stereo has documented 1-4 m-class canopy uncertainty and clear small-object height loss, and no stereo treeline-change paper was found. Historical aerial stereo now exists as a countrywide Swiss product (1979-2006), which makes an Austrian aerial-photo DSM fallback plausible but unverified. Land Tirol's ALS page confirms two epochs but not downloadable first-epoch DOM.

### Cited Findings
| Ref | Tag | Region, period | Data / method | Finding | Limits | Supports |
|---|---|---|---|---|---|---|
| Næsset, Gobakken & McRoberts 2019, *Remote Sens* 11(15):1804, [10.3390/rs11151804](https://doi.org/10.3390/rs11151804) | [ABSTRACT-READ] | boreal-alpine tree line, SE Norway, 2006/2012, 12 ha | bi-temporal ALS, model-dependent inference | 316 trees, 0.11-5.20 m; "Average growth in height was 0.19 m"; change estimated for "domains of size 1.5 ha or greater" | one 12 ha site; area-based, not individual trees | sapling growth over 6 years is about 0.2 m; ALS detects it only in aggregated domains |
| Næsset, Gobakken, Jutras-Perreault & Ramtvedt 2021, *Remote Sens* 13(13):2469, [10.3390/rs13132469](https://doi.org/10.3390/rs13132469) | [ABSTRACT-READ] | same ecotone | ALS vs UAS photogrammetry (DAP) | "smaller regression model residuals ... when using ALS data and ... small and solitary trees tended to be smoothed out in DAP data" | UAS DAP, not satellite stereo | DAP smooths small trees; subtle (<0.2 m over about 5 yr) change needs ALS |
| Noordermeer, Candelas-Bielza, Saarela & Gobakken 2023, *Int J Appl Earth Obs Geoinf* 117:103201, [10.1016/j.jag.2023.103201](https://doi.org/10.1016/j.jag.2023.103201) | [ABSTRACT-VIA-SEARCH] (publisher blocked; summary: three ALS campaigns 2008, 2012, 2018, 25 sites along the Scandinavian Mountain Range, compared with field data) | Norway, 60-69 N | time series of ALS | tree occupancy and height tracked | numbers not obtained | the best repeat-ALS treeline precedent; not Alps |
| Thapa et al. 2026, *J Appl Ecol*, [10.1111/1365-2664.70561](https://doi.org/10.1111/1365-2664.70561) | [ABSTRACT-READ] | Cairngorms, Scotland, 569 km2, ALS 22 pulses/m2 | segmentation of regenerating trees | clusters "detectable once they outgrow neighbouring shrubs (up to 1.1 m)"; detection 83% for 1.4-1.6 m, over 95% for over 1.8 m | single-epoch map; high pulse density; Scotland | empirical sapling detection limit with ALS at high density (compare Tyrol at about 8 ground points/m2 in epoch 2) |
| Yu, Qi, Zhao & Huang 2024, *Int J Digit Earth* 17(1):2345725, [10.1080/17538947.2024.2345725](https://doi.org/10.1080/17538947.2024.2345725) | [ABSTRACT-READ] | boreal forest, 2012-2016 | bi-temporal CHM, six height metrics, five resolutions | resolution below 2 m and low percentiles "consistently underestimated"; 95th percentile at 10 m gives RMSE 0.88-1.11 m for height | boreal, not alpine | CHM differencing needs coarse resolution and top-percentile metrics; supports an aggregated change design |
| Gretler, Kükenbrink, Marty, Ginzler & Morsdorf 2026, preprint egusphere-2026-1689 (listed on SSRN as "Robustness of forest metrics from multitemporal airborne laser scanning", [10.2139/ssrn.5473216](https://doi.org/10.2139/ssrn.5473216)) | [ABSTRACT-VIA-SEARCH] | northern Switzerland, ALS 2014, 2019, 2020 | operational ALS, different sensors | "Canopy height appears robust", complex traits (plant area index) are not | preprint under review; Swiss lowland-type forest, not treeline | canopy height difference is the most robust ALS change metric |
| Marty, Piermattei, Waser & Ginzler 2025, *Earth Syst Sci Data* 17(11):5811-5832, [10.5194/essd-17-5811-2025](https://doi.org/10.5194/essd-17-5811-2025) | [ABSTRACT-READ] (CrossRef abstract; numbers from fetch summary) | Switzerland, 1979-2006 | about 32,000 scanned stereo aerial images, four countrywide 1 m DSM epochs and vegetation height models | completeness "64 %" (glacial/snow) to "98 %" (sealed); closed forest 93% and NMAD about 0.8 m (fetch summary, publisher page) | Switzerland only; image-matching completeness above treeline lower; no Austria | historic aerial DSM differencing is operational for Switzerland; analogous Land Tirol aerial archive (photos since the 1940s) makes a fallback plausible |
| Piermattei, Marty, Karel & Ressl 2018, *Remote Sens* 10(10):1542, [10.3390/rs10101542](https://doi.org/10.3390/rs10101542) | [ABSTRACT-READ] (partial; results truncated) | Ticino (CH) and near Ljubljana (SI) | Pleiades stereo/tri-stereo CHMs vs aerial matching and ALS | tests tri-stereo vs pairs and viewing angle | sigma-MAD figures not read: proposal's [verify] remains; abstract names Ticino and Ljubljana, not Salzburg | stereo CHM feasibility in mountain forest |
| Piermattei, Marty, Ginzler & Pöchtrager 2019, *Int J Appl Earth Obs Geoinf* 80:240-256, [10.1016/j.jag.2019.04.008](https://doi.org/10.1016/j.jag.2019.04.008) | [ABSTRACT-READ] (partial) | four Swiss Alpine sites | Pleiades CHMs vs aerial image matching; errors vs shadow, aspect, slope | forest metrics (Hmax, Hp95, canopy gaps) derived; error relation to shadows, aspect and slope assessed | quantitative results truncated | error covariates for a stereo error model |
| Loghin, Otepka-Schremmer & Pfeifer 2020, *Sensors* 20(9):2695, [10.3390/s20092695](https://doi.org/10.3390/s20092695) | [ABSTRACT-READ] (numbers from fetch summary of PMC page) | Vienna-area test objects | Pleiades 0.7 m and WorldView-3 0.31 m tri-stereo DSMs | estimated height "strongly depends on its size"; fetch summary: small objects recovered under 20% of height (Pleiades) and under 50% (WorldView-3) | percentages come from a tool summary of the full text; check before citing; isolated objects, not forest | stereo smoothing hides saplings and solitary trees |
| Wang, Ginzler, Eben & Rehush 2022, *Remote Sens* 14(9):2135, [10.3390/rs14092135](https://doi.org/10.3390/rs14092135) | [ABSTRACT-READ] | Swiss treeline ecotones, 1980 vs 2010 B&W aerial images | CNN trained on ALS-derived structure classes | high agreement for "dense forest", lower for "group of trees" | two time points; classes from ALS | historical B&W photos plus ALS labels work for dense forest, are weak for sparse trees |
| Wang et al. 2026, *Biogeosciences* 23:623, [10.5194/bg-23-623-2026](https://doi.org/10.5194/bg-23-623-2026) | [ABSTRACT-READ] | Xue Mountain, Taiwan, about 400 ha, 2012 vs 2021 | WorldView-2 images, RF and U-Net | OA 0.838; upper forest limit "shifted upslope by 32.00 ± 4.00 m" | 2D classification, not stereo; small area | satellite VHR treeline change does exist (2D); stereo height still untested |
| Mishra & Singh 2026, *Remote Sens* 18(2):309, [10.3390/rs18020309](https://doi.org/10.3390/rs18020309) | [ABSTRACT-READ] | Manang Valley, Nepal | UAV LiDAR, single date | canopy height and cover collapse "within a narrow ~60-80 m vertical interval" | single epoch | structural definition of the line |
| Sindewald et al. 2025, *Biogeosciences* 22:6509, [10.5194/bg-22-6509-2025](https://doi.org/10.5194/bg-22-6509-2025) | [ABSTRACT-READ] | southern Rocky Mountains | WorldView-3 plus CNN, six species | authors state "To our knowledge, we are the first to attempt tree species identification at treeline using satellite imagery" | non-Alpine; the abstract part read gives no accuracy figure (proposal's 44-47% from earlier notes) | species mapping at the line is nascent |
| Mandl, Stritih, Seidl & Ginzler 2023, *Remote Sens Ecol Conserv* 9(5):599-614, [10.1002/rse2.330](https://doi.org/10.1002/rse2.330) | [ABSTRACT-READ] | two Alpine landscapes | GEDI vs ALS | "weak to moderate agreement ... (R2 from 0.03 to 0.61)" | not a treeline study | GEDI is not a substitute for ALS in rugged terrain |
| Maroschek, Seidl, Senf & Rammer 2024/25, EGU24-1844, [10.5194/egusphere-egu24-1844](https://doi.org/10.5194/egusphere-egu24-1844) | [ABSTRACT-READ] (conference abstract; fetch summary for findings) | Berchtesgaden NP, nine time steps 1953-2020 | instance segmentation of trees and shrubs on historic and recent orthophotos | fetch summary: no consistent upward shift of the treeline; montane-subalpine ecotone moved up to five times faster | conference abstract, no peer-reviewed version found; findings are tool-paraphrased | nearest Eastern-Alps-adjacent (Northern Calcareous Alps) multi-epoch aerial treeline study; 3D not used |

- Land Tirol ALS page ([tirol.gv.at laser data](https://www.tirol.gv.at/sicherheit/geoinformation/geodaten-tiris/laserscandaten/)) [FULLTEXT-PARTLY-READ via fetch summary]: first campaign 2006-2010 "with updates in 2010, 2012-2013, 2015, and 2016"; second campaign 2017-2023 with ground-point density "mindestens 8 Punkte / m2"; DGM and DOM mosaics free at 50 cm (GeoTIFF) and 1 m (XYZ); classified LAS/LAZ point clouds and historical terrain models orderable by email for a fee; historical DGM/DOM visible as hillshade in the "Laser- und Luftbildatlas", where individual strip flight times can be queried. The page did not state whether a first-epoch DOM is downloadable. This partly resolves the proposal's [verify]: epochs and the 8 points/m2 are confirmed; first-epoch DOM availability remains open (point clouds and "historical terrain models" are orderable; ask for the surface model or the LAS).
- Land Tirol orthophoto page ([tirol.gv.at orthophotos](https://www.tirol.gv.at/sicherheit/geoinformation/geodaten-tiris/orthofotos/)) [FULLTEXT-PARTLY-READ]: 20 cm resolution, updated every 3 to 4 years, "ausgewählte historische Orthofotostände" in the WCS service (years not stated); aerial photos "seit den 1940er Jahren ... archiviert"; example historical images shown are from 1972, 1982 and 1990. Earliest orthophoto year is still unknown.
- ESA WorldView archive page ([dragon3.esa.int](https://dragon3.esa.int/eogateway/catalog/worldview-esa-archive)): fetch failed (DNS error); the 2009-02-07 to 2020-12-01 claim in the proposal remains report-level and untested here.

### Inferences
- Combining Næsset 2019 (0.19 m mean growth over 6 years, area-level inference only), Thapa 2026 (sapling clusters detectable from about 1.1-1.4 m at 22 pts/m2) and Loghin 2020 (stereo loses most of the height of small objects) supports the proposal's design: ALS aggregated change as the 3D core, stereo for tall stands and gaps only.
- Because Land Tirol epochs are year-mosaics from 2006-2010 and 2017-2023, the interval varies from about 7 to 17 years per tile; vertical alignment between epochs must be estimated from stable terrain (Yu 2024 and the Gretler preprint point to this as the main risk, not point density).
- Marty 2025 makes a historical aerial DSM tier (pre-2006) a concrete option to request from Land Tirol/BEV; availability for Tyrol is unverified.

### Gaps
- No Eastern Alps repeat-ALS forest-line or tree-height-change study found (two web searches plus one targeted search; no Scopus/WoS search).
- No satellite-stereo (WorldView, Pleiades, SPOT, ASTER) treeline height-change study found; Wang 2026 (Taiwan) shows 2D VHR change exists, which narrows the "no VHR" claim, not the "no stereo" claim.
- Historical aerial photo SfM for treeline height: no study found (only Swiss/Mediterranean 2D deep-learning and the Marty DSM product).
- Piermattei sigma-MAD values, Noordermeer numbers and Loghin percentages need full-text check.
- Earliest Land Tirol orthophoto year, first-epoch DOM, WorldView footprints over Tyrol: unresolved.

## Q3. Deep-learning forest and treeline delineation (Nguyen, Carrieri, Wang, Maroschek, UAV)

### Takeaway
Deep learning on aerial imagery is the working route to long, high-resolution treeline records in the Alps (Swiss 1946-2020, Berchtesgaden 1953-2020), and the main weakness is label and definition dependence plus sparse-tree recall; satellite-sensor generalisation is untested for Tyrol.

### Cited Findings
| Ref | Tag | Region, period | Data / method | Finding | Limits | Supports |
|---|---|---|---|---|---|---|
| Nguyen, Kellenberger & Tuia 2022, *Remote Sens Environ* 281:113217, [10.1016/j.rse.2022.113217](https://doi.org/10.1016/j.rse.2022.113217) | wiki (nguyen_2022_forest_mapping_explainable); DOI confirmed by CrossRef | Swiss Alps treeline | explainable CNN | forest definition rules encoded, annotator biases | abstract not re-read here | boundary sensitivity to definitions |
| Nguyen, Rußwurm, Lenczner & Tuia 2024, *Remote Sens Environ* 305:114109, [10.1016/j.rse.2024.114109](https://doi.org/10.1016/j.rse.2024.114109) | wiki (nguyen_2024_treeline_monitoring); [SNIPPET/TLDR-ONLY] here (no publisher abstract obtained); DOI now confirmed by CrossRef, closing the proposal's [verify] | Swiss Alps, 1946-2020 | U-Net with temporal loss from one labelled year | search summary: training loss uses prior knowledge on forest dynamics to improve temporal consistency; an EPFL news item reports Valais forests "rising by about 50 to 70 meters" (news, not peer-reviewed) | news figure not verified in paper | multi-epoch DL from one labelled year |
| Wang et al. 2022 (see Q2) | [ABSTRACT-READ] | Swiss treeline | CNN on B&W images | high agreement for dense forest, lower for tree groups | - | sparse-tree weakness |
| Maroschek et al. EGU24 (see Q2) | [ABSTRACT-READ] | Berchtesgaden | instance segmentation, nine epochs | no consistent treeline shift | conference abstract | multi-sensor integration |
| Carrieri et al. 2025, *Biogeosciences* 22:6393, [10.5194/bg-22-6393-2025](https://doi.org/10.5194/bg-22-6393-2025) | wiki (carrieri_2025_hr_imagery_treeline) | 10 Italian treelines, UAV | Mask R-CNN | 70% (conifers over 50 cm), 86% (over 2 m), leave-one-site-out recall 0.56 (wiki) | does not classify species | detection limit by height |
| Garbarino et al. 2023, *Remote Sens Ecol Conserv*, [10.1002/rse2.351](https://doi.org/10.1002/rse2.351) | wiki; OpenAlex title confirmed ("Treeline remote sensing: from tracking treeline shifts to multi-dimensional monitoring of ecotonal change") | review, 372 papers | - | multiscale, multi-sensor monitoring recommended | - | scope and gap statement |
| Rösch et al. 2022, *Remote Sens* 14(13):3190, [10.3390/rs14133190](https://doi.org/10.3390/rs14133190) | [ABSTRACT-READ] | Sarntal Alps, South Tyrol | PlanetScope 3 m and Sentinel-2 10 m, texture, topography, canopy height | mountain pine "can be accurately mapped (PlanetScope (90.96%) and Senti[nel-2] (90.65%))"; "small-structured patches may remain undetected" | Pinus mugo only; Italian side | S2 can map krummholz when combined with texture and CHM |

- The wiki already holds Nguyen 2022/2024 and Carrieri 2025; Wang 2022 (Swiss B&W, ALS-labelled), Maroschek (Berchtesgaden) and Rösch (Sarntal) are new additions.

### Inferences
- A Tyrolean aerial-photo deep-learning record would follow Nguyen 2024 and Maroschek; the label strategy of Wang 2022 (ALS-derived structure classes) matches Tyrol's ALS availability.
- UAV methods (Carrieri) give a height-dependent recall curve that can be used to set the project's minimum detectable tree height.

### Gaps
- Nguyen 2024 abstract and quantitative temporal consistency not read.
- No deep-learning forest-line study with Tyrolean or Austrian imagery found.
- Nguyen 2025 EPFL thesis exists (search result); not obtained.

## Q4. Driver attribution: spatial CV, area of applicability, ensembles, variance partitioning, counterfactuals

### Takeaway
Methodological sources for spatial validation and applicability are solid and mostly in the wiki; no forest-line study combining spatial CV with multi-driver attribution was found. A cautionary counter-position (Wadoux et al. 2021) argues that spatial CV is not the right accuracy estimator, which the proposal should address.

### Cited Findings
- Meyer & Pebesma 2021, *Methods Ecol Evol* 12(9):1620-1633, [10.1111/2041-210X.13650](https://doi.org/10.1111/2041-210X.13650) [ABSTRACT-READ]: the area of applicability is "the area where we enabled the model to learn about relationships based on the training data, and where the estimated cross-validation performance holds"; dissimilarity index from predictor-space distance. Wiki: area_of_applicability.
- Milà, Mateu, Pebesma & Meyer 2022, *Methods Ecol Evol* 13(6):1304-1316, [10.1111/2041-210X.13851](https://doi.org/10.1111/2041-210X.13851) [ABSTRACT-READ]: NNDM LOO CV matches the nearest-neighbour distance distribution between test-train and prediction-train points.
- Linnenbrink, Milà, Ludwig & Meyer 2024, *Geosci Model Dev* 17(15):5897-5912, [10.5194/gmd-17-5897-2024](https://doi.org/10.5194/gmd-17-5897-2024) [ABSTRACT-READ]: kNNDM is the k-fold version for large datasets; this is the definitional source for kNNDM.
- Roberts et al. 2017, *Ecography* 40(8):913-929, [10.1111/ecog.02881](https://doi.org/10.1111/ecog.02881) [ABSTRACT-READ]: ignoring dependence structure in CV causes "serious underestimation of predictive error"; blocking must be chosen carefully.
- Ploton et al. 2020, *Nat Commun* 11:4540, [10.1038/s41467-020-18321-y](https://doi.org/10.1038/s41467-020-18321-y) [ABSTRACT-READ]: non-spatial validation "suggests that the model predicts more than half of the forest biomass variation, while spatial validation ... reveal quasi-null predictive power" (central Africa biomass).
- Wadoux, Heuvelink, de Bruin & Brus 2021, *Ecol Model* 457:109692, [10.1016/j.ecolmodel.2021.109692](https://doi.org/10.1016/j.ecolmodel.2021.109692) [METADATA-ONLY]: title states that spatial cross-validation "is not the right way to evaluate map accuracy"; abstract not obtained, so position only.
- Meyer & Pebesma 2022, *Nat Commun* 13:2208, [10.1038/s41467-022-29838-9](https://doi.org/10.1038/s41467-022-29838-9) [METADATA-ONLY]: ML global ecological maps and the challenge of assessing them.
- Pontius & Millones 2011, *Int J Remote Sens* 32(15):4407-4429, [10.1080/01431161.2011.552923](https://doi.org/10.1080/01431161.2011.552923) [ABSTRACT-READ]: Kappa is "useless, misleading and/or flawed"; use quantity and allocation disagreement (relevant to map-comparison validation of change).
- Observational attribution of treeline change (all driver-contest sources, not new): Gehrig-Fasel, Guisan & Zimmermann 2007, *J Veg Sci* 18(4):571-582, [10.1111/j.1654-1103.2007.tb02571.x](https://doi.org/10.1111/j.1654-1103.2007.tb02571.x) [ABSTRACT-READ]: GEOSTAT 1985-1997; "Above 1650 m, 10% of the new forest areas were identified as true upward shifts whereas 90% represented ingrowth"; most upward shifts within 300 m below the potential regional tree line, only 4% above it (fetch summary); a moving-window algorithm separates ingrowth from shift, and the potential tree line is the reference surface for a climate test. Frei 2023, Cudlín 2017, Nicoud 2025, Marzini 2025 are wiki notes (see proposal).
- Lewińska 2025 (Q1) is the one source here showing that endmember definition affected trends more than data density; relevant as a definition-sensitivity analogue for attribution inputs.
- Search for variance partitioning of land use vs climate at treelines returned a New Zealand *Nothofagus* study (about half of landscape-scale variation tracking abiotic gradients), a south Norway century of tree and forest line modelling (authors "found it hard to separate" climate and land use) and an Alberta random-forest treeline study, all as search snippets only [SNIPPET/TLDR-ONLY]; none could be matched to a verified DOI in this session, so they are not charted.

### Inferences
- The proposal's "attribution with bounds" fits the Roberts/Ploton/Meyer literature, but it should justify the validation target explicitly (map accuracy vs process inference), since Wadoux et al. dispute spatial CV as a map-accuracy estimator.
- kNNDM and AOA apply to prediction maps; for attribution of observed change, the more relevant risk is predictor collinearity (elevation, abandonment, snow), which none of these sources solve.
- Deep ensembles: see wiki lakshminarayan_2017_uncertainty and deep_ensemble_uncertainty (not re-searched).

### Gaps
- No peer-reviewed variance-partitioning study of land use vs climate at an Alpine forest line verified.
- No study applying kNNDM/AOA to treeline-change attribution found (search-based; no Scopus/WoS search).
- Counterfactual-scenario attribution for forest-line change: only simulation work (iLand, wiki marzini_2025); no observational counterfactual precedent found.
- Wadoux 2021 abstract not read.

## Q5. Sentinel-2 series methods: seasonal baselines, anomalies, snow melt-out, mixed-pixel purity at the forest line

### Takeaway
Snow melt-out products from Landsat and Sentinel-2 now exist for the Alps (30 m, two 12-year periods; and 20 m annual for the French Alps and Pyrenees), but no Sentinel-2 anomaly study at a forest line with tree-ring validation was found; mixed-pixel limits at 10 m are documented only indirectly.

### Cited Findings
- Gascoin et al. 2019, *Earth Syst Sci Data* 11(2):493-514, [10.5194/essd-11-493-2019](https://doi.org/10.5194/essd-11-493-2019) [ABSTRACT-READ]: Theia Snow collection from Sentinel-2 and Landsat-8, four classes (snow, no snow, cloud, no data); "snow detection is more accurate than the Sen2Cor outputs"; "false snow detection in some large clouds" is an open issue.
- Bayle, Gascoin, Corona & Stoffel 2025, *Sci Data*, [10.1038/s41597-025-05044-2](https://doi.org/10.1038/s41597-025-05044-2) [ABSTRACT-READ]: SMOD at 30 m for 1985-1996 and 2011-2022 in Pyrenees, Alps and Caucasus from Landsat aggregated over 12-year periods; validated with station snow depth (R2 about 0.75, MAE about 7 days) and soil temperature (R2 about 0.7, MAE about 10 days). Station network in the Alps is mainly Western; Tyrol coverage not checked.
- Barrou Dumont et al. 2025, *The Cryosphere* 19:2407, [10.5194/tc-19-2407-2025](https://doi.org/10.5194/tc-19-2407-2025) [ABSTRACT-READ]: SMOD at 20 m from ten platforms (SPOT 1-5, Landsat 5-8, Sentinel-2), French Alps and Pyrenees 1986-2023; "median error of 1 d" but "RMSE of 28 d", so pixel-level use is poor and aggregation is needed; reductions of 21.4 d (5.78 d per decade) in the French Alps.
- Löw & Koukal 2020, *Remote Sens* 12(24):4191, [10.3390/rs12244191](https://doi.org/10.3390/rs12244191) (CrossRef confirmed; wiki note löw_2020_phenology_austria_forest): Sentinel-2 disturbance mapping in Austria, closed canopies.
- Bayle 2026, *Glob Change Biol*, [10.1111/gcb.70968](https://doi.org/10.1111/gcb.70968) [ABSTRACT-READ]: perspective, "a positive vegetation-index trend is not an ecological observation in itself"; separates methodological bias from phenomenological ambiguity.
- Rösch 2022 (Q3): S2 10 m vs PlanetScope 3 m for mountain pine, similar accuracy but small patches missed.
- Darabi et al. 2025, *Remote Sens Appl Soc Environ*, [10.1016/j.rsase.2025.101500](https://doi.org/10.1016/j.rsase.2025.101500) [METADATA-ONLY]: review of methodological choices in vegetation trend uncertainty; abstract not obtained.

### Inferences
- A 20-28 d RMSE pixel-level SMOD error (Barrou Dumont) means melt-out predictors in attribution should be aggregated (cell means), consistent with the proposal's hexagon design.
- Mixed-pixel purity at the forest line has no direct quantitative source in this session; the proposal's multiple tree-cover thresholds remain an untested assumption.

### Gaps
- No Sentinel-2 plus tree-ring study at an Alpine treeline (not found; no Scopus/WoS search).
- No source quantifying S2 10 m fractional tree-cover error specifically in sparse treeline canopies.
- No Austrian or Tyrolean SMOD product validated against Austrian stations found.

## Q6. Concepts and their best definitional source

| Concept | Best definitional source found | Status |
|---|---|---|
| Treeline vs forest line vs timberline | Körner & Hoch 2023, *J Biogeogr* 50:838-845, [10.1111/jbi.14593](https://doi.org/10.1111/jbi.14593) (from proposal; not re-checked here) | report-level |
| Forest definition / canopy-cover threshold sensitivity | Sexton et al. 2015, *Nat Clim Change*, [10.1038/nclimate2816](https://doi.org/10.1038/nclimate2816); within-Alps: Nguyen 2022 (wiki) | Sexton METADATA-ONLY |
| Ingrowth vs true upward shift | Gehrig-Fasel et al. 2007 (moving-window algorithm; ABSTRACT-READ) | defined operationally |
| Sub-pixel forest (cover) fraction | Senf et al. 2020, [10.1016/j.rse.2020.111691](https://doi.org/10.1016/j.rse.2020.111691) (regression-based unmixing) | ABSTRACT-READ |
| Observation-density greening artefact | Bayle et al. 2024 (wiki, Ecography) | wiki |
| Landsat sensor harmonisation | Roy et al. 2016 (ETM+/OLI) | TM not covered |
| Landsat geolocation tier | USGS Tier 1 criterion via Earth Engine catalogue (12 m RMSE) and Storey et al. 2014 (OLI) | snippet / OLI only |
| Temporal segmentation of Landsat trajectories | Kennedy et al. 2010, [10.1016/j.rse.2010.07.008](https://doi.org/10.1016/j.rse.2010.07.008) | METADATA-ONLY here; see evergreen review |
| TimeSync (interpreter validation of trajectories) | Cohen et al. 2010, [10.1016/j.rse.2010.07.010](https://doi.org/10.1016/j.rse.2010.07.010) | METADATA-ONLY |
| Map-change error vs real change; quantity and allocation disagreement | Pontius & Millones 2011 (ABSTRACT-READ); Pontius & Lippitt 2006 (evergreen review) | read |
| Area of applicability (AOA), dissimilarity index | Meyer & Pebesma 2021 | ABSTRACT-READ |
| NNDM / kNNDM cross-validation | Milà et al. 2022; Linnenbrink et al. 2024 | ABSTRACT-READ |
| Block and structured CV, SAC inflation | Roberts et al. 2017; Ploton et al. 2020 | ABSTRACT-READ |
| Critique of spatial CV for map accuracy | Wadoux et al. 2021 | METADATA-ONLY |
| Snow melt-out date (SMOD) | Bayle et al. 2025 Sci Data; Barrou Dumont et al. 2025 | ABSTRACT-READ |
| Bi-temporal ALS height-change estimation | Næsset et al. 2019 | ABSTRACT-READ |
| Canopy envelope / CHM differencing choices | Yu et al. 2024 | ABSTRACT-READ |
| Stereo-photogrammetric CHM and small-object bias | Piermattei et al. 2018/2019; Loghin et al. 2020 | partial / numbers unverified |
| Co-registration of DEM differences | Nuth & Kääb 2011, *Cryosphere* 5:271-290 (proposal DOI 10.5194/tc-5-271-2011; not re-checked here) | report-level |
| Deep ensembles | Lakshminarayanan et al. 2017 (wiki) | wiki |

## Q7. Forward citations, resolved [verify] items, and the not-found list

### Takeaway
Forward-citation scans (Semantic Scholar, coverage incomplete) show that the Garbarino 2023 and Bayle 2024 literature has grown fast in 2025-2026, but Menegaldo 2025 has no research citers yet, and Obuchowicz 2024 and Nguyen 2024 citers were not retrieved.

### Cited Findings
Forward citations of Garbarino 2023 (2023-2026, S2 listing; items read are tagged; others title-level only [METADATA-ONLY]):
- Wang et al. 2026, Taiwan WorldView-2 (Q2) [ABSTRACT-READ]; Mishra & Singh 2026, Himalayan UAV LiDAR [ABSTRACT-READ]; Thapa et al. 2026, Scottish ALS [ABSTRACT-READ]; Baglioni et al. 2025 [ABSTRACT-READ]; Corimanya et al. 2025 [ABSTRACT-READ]; Sindewald 2025 [ABSTRACT-READ]; Carrieri 2025 (wiki); Menegaldo 2025 (wiki); Bayle 2025 RSEC [ABSTRACT-READ]; González Le Barbier et al. 2025, *J Veg Sci*, [10.1111/jvs.70018](https://doi.org/10.1111/jvs.70018) [ABSTRACT-READ, partial]: Cantabrian timberline, "temporal dynamics ... over the last 70 years".
- Title-only [METADATA-ONLY]: Lu et al. 2025, *Nat Rev Earth Environ*, "Patterns, dynamics and drivers of alpine treelines and shrublines", [10.1038/s43017-025-00703-9](https://doi.org/10.1038/s43017-025-00703-9) (a review that the final scoping review should read before drafting); "Faster boundary shifts near the cold limit of species' niche", *New Phytol*, [10.1111/nph.70812](https://doi.org/10.1111/nph.70812); a shrubline framework, *Ecol Indic*, [10.1016/j.ecolind.2025.113788](https://doi.org/10.1016/j.ecolind.2025.113788); Altai-Sayan biomass at upper limits, *Forests*, [10.3390/f17040415](https://doi.org/10.3390/f17040415).
- Forward citations of Bayle 2024 (2025-2026): Bayle 2025 RSEC, Bayle 2025 SMOD, Bayle 2026 GCB perspective, Lewińska 2025 RSE, Barrou Dumont 2025, Darabi 2025 review (all above), plus title-only [METADATA-ONLY]: "19th-century afforestation policies have predisposed mountain slopes to forest expansion under recent climate" (*Prog Phys Geogr*, [10.1177/03091333251378970](https://doi.org/10.1177/03091333251378970)); "Climate change limits aboveground primary production and exacerbates post-abandonment woody encroachment in mountains" (*Landsc Ecol*, [10.1007/s10980-025-02173-2](https://doi.org/10.1007/s10980-025-02173-2)); "Landscape-scale analysis of shrub encroachment ... Carpathian Mountains" (*Environ Res Lett*, [10.1088/1748-9326/ae05b2](https://doi.org/10.1088/1748-9326/ae05b2)); "Unabated forest expansion despite increased rockfall frequency at Taeschgufer" (*Geomorphology*, [10.1016/j.geomorph.2025.109985](https://doi.org/10.1016/j.geomorph.2025.109985)). The first two are directly relevant to land-use legacy and abandonment attribution and should be read as abstracts in the next round.
- Forward citations of Menegaldo 2025: only a journal editorial ("One year of VED") in Semantic Scholar. OpenAlex and Google Scholar not available this session.
- Forward citations of Obuchowicz 2024 and Nguyen 2024: not retrieved (not run).

Proposal [verify] items in Theme C:
- Bayle follow-up DOI 10.1002/rse2.430: confirmed, journal is *Remote Sensing in Ecology and Conservation* (2025), authors Bayle, Nicoud, Mansons, Francon et al. (S2). Resolved.
- Nguyen 2024 DOI: 10.1016/j.rse.2024.114109 (CrossRef). Resolved.
- Roy et al. 2016: exists (10.1016/j.rse.2015.12.024), ETM+/OLI only. TM transforms still unchecked.
- Landsat 4/5 TM mountain geolocation: only Tier 1 12 m RMSE; open.
- Piermattei 2018 sigma-MAD and "Salzburg": abstract names Ticino and Ljubljana only; sigma-MAD still unread. Piermattei et al. 2018 lists Marty, Karel, Ressl as co-authors (CrossRef) and Piermattei 2019 covers four Swiss sites.
- Næsset 2019/2021: now ABSTRACT-READ; details above.
- Land Tirol ALS epochs, 8 points/m2, free 50 cm DGM/DOM: confirmed from the web page; per-strip dates queryable in the Laser- und Luftbildatlas (supports the "per-tile flight dates essential" point); first-epoch DOM download unconfirmed. Earliest orthophoto year unconfirmed; aerial photos archived since the 1940s; shown examples 1972, 1982, 1990.
- ESA WorldView coverage claim: fetch failed; still report-level.
- Olofsson/Pontius/LandTrendr: not redone; see evergreen review.

### Inferences
- Beyond the proposal: Bayle 2025's combination of orthorectified diachronic images, dendrochronology and LiDAR is the template for resolving what Landsat greening means at a forest line; it is a close competitor in method, not a Tyrolean study.
- The statement "no satellite VHR treeline change" is now false in 2D (Taiwan WorldView-2); only "no satellite stereo height-change" remains plausible.

### Gaps
Not found list (every item is "not found in a limited web, CrossRef and Semantic Scholar search"; none has had a Scopus or Web of Science search, so none may be claimed as a "first"):
1. Landsat forest-line change study for Austrian Tyrol (only South Tyrol/Menegaldo and Italy-wide Baglioni).
2. Observation-density-corrected Landsat treeline trend.
3. Eastern Alps repeat-ALS forest-line or tree-height-change study.
4. Satellite-stereo (WorldView, Pleiades, SPOT, ASTER) treeline or forest-line height/volume change.
5. Historical aerial-photo SfM/DSM treeline height change in the Alps (Marty 2025 is a general national product, not treeline).
6. Landsat TM mountain geolocation accuracy.
7. Alpine topographic-correction benchmark for TM at forest lines.
8. Sentinel-2 anomaly versus tree-ring at an Alpine treeline.
9. Variance-partitioning or spatial-CV attribution study of Alpine forest-line change.
10. Austrian national Landsat forest-cover product at the forest line.
11. TimeSync or LandTrendr in an Alpine treeline study (nearest: Tatra LandTrendr study, search snippet only, 1984-2022, not charted).
12. Possibly missed: Leonelli et al. 2011 *Ambio* [10.1007/s13280-010-0096-2](https://doi.org/10.1007/s13280-010-0096-2) and Vittoz et al. 2008 *Arct Antarct Alp Res* 40:225-232 are Alpine treeline field/aerial studies that were identified but not read (no abstract obtained): [METADATA-ONLY], not charted. A Trentino 1954-aerial forest cover reconstruction (unitn/FEM, search snippet) is another unread lead.
