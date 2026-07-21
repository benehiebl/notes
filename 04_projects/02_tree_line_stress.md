# Alpine forest tree line under stress

---

### Motivation

Alpine treeline ecotones — the transition zone between closed subalpine forest and open alpine grassland — are among Earth's most climate-sensitive biome boundaries and constitute early-warning ecosystems for detecting climate change impacts on mountain ecosystems (Körner 2012; Camarero et al. 2025, *Nature Reviews Earth & Environment*). In the Eastern Alps, this boundary is primarily defined by *Pinus cembra* (Swiss stone pine) and *Larix decidua* (European larch), with *Pinus cembra* forming the slow-advancing tree island clusters characteristic of the Tyrolean high-altitude landscape above approximately 1900–2400 m a.s.l.

For much of the 20th century, treeline advance was primarily temperature-driven: warming growing seasons expanded the thermal energy budget for tree establishment above former climatic limits. Evidence from tree-ring networks, aerial photography, and satellite time series confirms average upward shifts of ~0.4 m/year in the Alps over the last century (Evidence for 40 Years of Treeline Shift, *Forests* 14(2), 2023), with recent remote sensing work demonstrating systematic forestline advance in Italian mountains using 40-year Landsat time series (Baglioni et al. 2025, *Biogeosciences* 22:4349–4366). However, treeline advance is spatially variable and strongly constrained by local conditions — many treelines have not shifted position despite decades of warming. The classical assumption that treeline is uniformly temperature-limited (Körner 2012) also does not hold everywhere: comparative evidence from Mongolian boreal treelines shows that while the *upper* treeline is thermally limited (mean growing-season temperature minimum ~6 °C), the *lower* treeline boundary of the same forest–steppe system is instead set by mean annual precipitation, with snow cover and humidity acting as distinct secondary controls by forest type (source: [[klinge_2018_climate_treeline]]) — a reminder that "the treeline" can be governed by different limiting factors at its different margins, a distinction this project's SDM work (WP2) should test explicitly rather than assume away.

Two compounding climate stressors are now challenging the assumption of temperature-driven unimpeded upward expansion:

**1. Summer drought intensification.** The 20th-century redistribution of tree growth limitation from energy- to water-limitation [[babst_2019_redistribution]] now reaches subalpine elevations. *Pinus cembra* growth is drought-limited at rear-edge and low-elevation populations (Lévesque et al. 2014), and radial growth of *Pinus cembra* responds negatively to low summer precipitation and high VPD (Nikolova et al. 2022, *Science of the Total Environment*). Critically, isolated trees in open ecotone positions lack the canopy facilitation buffering that closed subalpine forest stands provide: they are exposed to higher radiation, higher VPD, and lower soil moisture, making them physiologically more vulnerable than trees in closed stands [[topographic_microclimate]]. This is consistent with the broader finding that facilitation drives tree seedling survival at alpine treelines (Camarero et al. 2024, *Journal of Plant Ecology*). The pattern is not unique to *Pinus cembra*: 31-year moving-window dendrochronology at the High Tatras Norway spruce treeline (Slovakia) shows an *emerging*, size-dependent drought sensitivity — the largest trees developed a significant sensitivity to previous-year late-summer drought (SPEI3) that was absent earlier in the 1950–2019 record, even though the site remains generally temperature-limited overall (source: [[maerker_2025_drought_spruce]]). This directly supports WP1's planned juvenile-vs-adult dendrochronological comparison and implies that tree size/age class should be treated as an explicit, time-varying covariate — not just a fixed grouping variable — in the response-function analysis (see WP1 methodological note below).

**2. Winter snow cover reduction.** Climate change is progressively reducing snow cover duration and depth in Alpine winters. A two-winter snow-removal field experiment at the alpine treeline (1700 m a.s.l., Tyrolean Central Alps) found that snow-free soils do not simply freeze solid — they instead cycle through far more freeze–thaw events (53 cycles vs. 0 over one winter) at temperatures fluctuating between −3.6 and 4.2 °C at 10 cm depth (vs. −0.2 to 0.8 °C under snow) — and that this significantly increases spring hydraulic conductivity loss (77.8% vs. 31.3%), living-cell mortality, and summer mortality, and reduces growth, in saplings of five treeline-relevant species (*Acer pseudoplatanus*, *Sorbus aucuparia*, *Juniperus communis*, *Larix decidua*, *Picea abies*) (source: [[charra_2025_snow_treeline]]). Species diverged sharply between **resistance** (avoiding damage — e.g. *Picea abies*, via embolism refilling) and **recovery** strategies (restoring function afterward — e.g. resprouting in *Sorbus* and *Acer*); *Larix decidua* showed high mortality with no apparent recovery mechanism. *Pinus cembra* was not among the species tested, so where it falls on this resistance–recovery spectrum is an open, directly testable question for WP1's microclimate and dendrochronology design. This sapling-stage mechanism should not be conflated with regeneration-stage (seed bank) sensitivity: a factorial snow/fire/drought experiment on alpine and treeline soil seed banks (Kosciuszko National Park, Australia — a *Eucalyptus pauciflora* treeline system, ecologically and taxonomically distinct from *Pinus cembra*) found that simulated snow reduction significantly harmed germination only in the *alpine herbfield* seed bank; the *treeline* seed bank was comparatively robust to snow loss and instead most strongly affected by drought (44% germinant reduction vs. control) (source: [[vazques_2023_drought_treeline]]) — this **corrects** an earlier draft's claim that snow removal drives treeline seed-bank mortality, and instead suggests that at the regeneration stage, drought — not snow-cover loss — may be the dominant seed-bank stressor, with snow loss acting primarily through the sapling-stage hydraulic-damage mechanism identified by Charra-Vaskou et al. above. Both findings are, however, consistent with — and add mechanistic detail to — the broader finding that seasonal snow cover explains treeline elevation better than temperature at regional scale (Grünig et al. 2023, *Science of the Total Environment*).

These two stressors interact synergistically: drought-stressed trees have impaired root systems and reduced non-structural carbohydrate reserves; snow-frost-damaged saplings are more vulnerable to summer desiccation. The combined effect may progressively slow — or in some years reverse — the upward advance of the *Pinus cembra* treeline ecotone, even as warming continues to favour it thermally. Simulation modelling for the Eastern Alps demonstrates irreversible critical transitions in mountain forest composition at just +2°C of mean annual warming [[albrich_2019_climate_change_mountain_forests]], suggesting that the window for treeline expansion may be narrowing faster than warming trends alone would predict.

**A further open mechanistic question.** Why treeline growth ultimately arrests is itself debated. The classical carbon-limitation hypothesis (insufficient photosynthate for growth) is increasingly challenged by observations that photosynthesis and non-structural carbohydrate reserves often remain adequate at treeline even as meristem growth declines sharply — motivating a competing hypothesis that chronic cold suppresses growth through hormonal/regulatory signalling (cold-induced gibberellin suppression and DELLA growth-repressor stabilisation via the CBF pathway) rather than carbon supply (source: [[dietrich_2026_treeline_della]]). This is a conceptual synthesis with essentially no direct evidence yet in treeline-forming conifers — WP1's planned combination of SIF/gas-exchange (photosynthetic capacity) with ring-width growth data is well positioned to contribute empirical evidence to this debate in *Pinus cembra*, though this was not an original project aim and would require targeted meristem-level sampling beyond the current WP1 design to test the hormonal mechanism directly rather than just detect the carbon-growth mismatch.

This project proposes the first integrated monitoring and modelling framework for the dual-stressor regime at the *Pinus cembra* treeline in Tyrol, combining drone-based solar-induced fluorescence (SIF), dendrochronology of juvenile trees, phenological webcam monitoring, and multi-resolution satellite time series (Planet, Sentinel-2, Landsat) to quantify physiological stress at individual tree and stand level, and to model the long-term trajectory of the treeline ecotone under CMIP6 climate projections.

---

### Zielsetzung

**O1:** Quantify photosynthetic stress responses of *Pinus cembra* to summer drought and spring frost across the open-ecotone–closed-forest gradient using drone-based SIF, ground gas exchange, and juvenile dendrochronology; test whether canopy facilitation buffers drought stress in closed-forest positions.

**O2:** Characterise the role of winter snow cover deficit and soil frost as constraints on *Pinus cembra* seedling recruitment and ecotone advance at Tyrolean study sites, combining in situ sensor monitoring, phenological webcam imagery, and GLORIA plot reference data.

**O3:** Map and model the 40-year trajectory of the *Pinus cembra* treeline ecotone in the Tyrolean Alps using multi-resolution satellite time series, individual tree crown segmentation via deep learning, and species distribution modelling under CMIP6 scenarios.

---

### Work packages

#### WP1 — Photosynthetic stress monitoring across the treeline ecotone gradient (Year 1–3)

**Objective:** Quantify intra-seasonal and inter-annual variation in photosynthetic activity and physiological stress of *Pinus cembra* across the open ecotone–closed forest gradient, and relate SIF and ring-width anomalies to climatic drivers.

**Methods:**

*Drone-based SIF and hyperspectral imaging*
- Monthly UAV flights (April–October) over 3 permanent study transects in the Tyrolean Alps: (a) open ecotone with isolated tree islands, (b) ecotone–forest transition, (c) closed subalpine forest at ~1800 m a.s.l.
- Hyperspectral UAV payload capturing the Fraunhofer oxygen absorption bands (O2-A at 760 nm, O2-B at 687 nm) for SIF retrieval; PRI (531/570 nm) as a complementary xanthophyll-cycle proxy for photosynthetic efficiency; campaigns timed to capture spring snowmelt, peak growing season, drought peak (August), and post-drought recovery
- Ground validation: simultaneous manual SIF spot measurements at flagged sample trees; LI-COR leaf gas exchange (A/Ci curves, stomatal conductance); pre-dawn leaf water potential with pressure bomb during drought events; leaf chlorophyll content (SPAD)
- Note: UAV-SIF has been demonstrated at boreal sites (Springer chapter 2024) but remains methodologically demanding; PRI will serve as primary proxy if SIF signal-to-noise is insufficient in initial campaigns

*Dendrochronology of juvenile *Pinus cembra**
- Non-destructive increment core sampling of adult trees (DBH > 15 cm; target 50 per transect) and cross-section sampling of juvenile sacrificial trees (DBH < 10 cm, naturally fallen or thinned; target 30 per transect)
- Ring widths measured to 0.01 mm precision, crossdated using COFECHA; standardisation via negative exponential or cubic spline (ARSTAN); pointer year analysis to identify negative (stress) years in the 20th–21st century record
- Response function analysis against gridded climate data (CHELSA, ERA5): temperature, precipitation, SPEI, snow depth, VPD — to isolate drought and frost signal years; run as 31-year moving-window correlations, not only a single whole-period correlation, since climate-growth sensitivity can be *non-stationary* and drought sensitivity can emerge only in recent decades even when a static correlation shows no size-ranked pattern (source: [[maerker_2025_drought_spruce]])
- Age-dependent sensitivity comparison between juvenile and adult trees (following Koch et al. 2025 [[01_notes/koch_2025_intraspecies_variation_s2]] for intraspecific variation context); consider the size-class-isolation (SCI) method — building chronologies with constant stem diameter over time rather than splitting by final DBH — to decouple tree size from age when comparing climate sensitivity across size classes (source: [[maerker_2025_drought_spruce]]); note the High Tatras spruce study needed ≥10 trees per size-class-year (with >500 recommended for robustness) — WP1's target sample sizes (50 adult, 30 juvenile per transect) should be checked against this benchmark before committing to fine size-class splits

*Webcam / phenocam monitoring*
- Year-round camera installations at each transect (near-infrared-capable, 15-min intervals); automated GCC (green chromatic coordinate) time series computation for phenological tracking (budburst, senescence)
- Snow depth estimation from image-based calibration with physical gauges; snow cover presence/absence day-of-year extraction
- Time-lapse analysis of browning events coinciding with drought/frost episodes

*Microclimate instrumentation*
- Continuous temperature, soil moisture, and soil frost sensors at 3 cm and 10 cm depth in open vs. closed-canopy positions at each transect
- VPD loggers (coupled T/RH sensors); soil temperature dataloggers recording freeze–thaw cycle frequency, duration, and intensity — not just binary frozen/unfrozen state, since freeze-thaw *cycling* (rather than sustained freezing) is the more physiologically damaging exposure at snow-free treeline sites (source: [[charra_2025_snow_treeline]])
- Link sensor records to webcam snow cover data and drone SIF campaign dates
- Cross-check point-sensor freeze/thaw records against satellite L-band passive microwave freeze/thaw retrievals (SMAP, 9 km) to place the 3 transect sites within the broader regional freeze/thaw regime and growing-season length, following the metric framework of [[melser_2024_freeze_constraints]]; SMAP's finer resolution resolves topographically complex terrain better than SMOS (25 km) and is therefore the preferred product for Alpine deployment — though at 9 km it can only provide regional context, not site-level validation, given the sub-km scale of the transects

**Key uncertainties and mitigation:**
- SIF retrieval from UAV is sensitive to viewing geometry and atmospheric conditions → standardise flight conditions (10:00–14:00, clear sky); compute SIF from both O2-A and O2-B bands as cross-check
- Juvenile tree ring series are short and may lack pointer-year replication → pool juvenile chronologies per transect to increase signal; validate against established adult chronologies from the International Tree Ring Data Bank (ITRDB)

**Expected outputs:**
- SIF and PRI time series across ecotone gradient for ≥3 growing seasons (novel dataset for Alps)
- Adult and juvenile *Pinus cembra* ring-width chronologies per transect
- Continuous microclimate and soil frost records; phenocam time series
- Quantified drought stress differential between open and closed-forest positions

---

#### WP2 — Individual tree mapping and treeline ecotone shift detection from satellite time series (Year 1–3)

**Objective:** Quantify decadal treeline ecotone dynamics in the Tyrolean Alps using multi-resolution satellite time series and individual tree crown segmentation; project future trajectories under CMIP6 scenarios.

**Methods:**

*40-year historical treeline mapping with Landsat*
- Annual seasonal composites (summer, June–September) from Landsat 5/7/8/9 archive (1984–2025) over the Tyrolean Alps; spectral indices: NDVI, NBR, TCW (Tasseled Cap Wetness) as proxy for canopy water content
- Contextual Mann-Kendall trend test for monotonicity of spectral time series in the elevation band 1700–2300 m a.s.l. (following Baglioni et al. 2025 methodology for Italian mountains)
- Forest line position extraction from annual composites: upper forest boundary delineation using automated threshold approach; inter-annual tracking of treeline elevation
- GLORIA summit plots in Tyrol as ground reference for validation (surveyed every 5–10 years; species cover and tree density from GLORIA Austria network)
- Methodological upgrade to consider over a purely threshold/Mann-Kendall pipeline: a Swiss Alps treeline study trained a U-Net + temporal-GRU segmentation model with a **domain-knowledge loss** (encoding the prior that forest boundaries change slowly except under abrupt disturbance) that substantially improved boundary accuracy (F1c 66.7%→80.9%) on a heterogeneous, multi-decadal (1946–2020) aerial-photo archive using segmentation labels from only a single year (source: [[nguyen_2024_treeline_monitoring]]) — directly transferable in spirit to this WP's 40-year Landsat archive, though the loss term and network would need redesigning for Landsat's coarser (30 m), spectrally different input; their companion rule-informed CNN, which explicitly predicts tree height + canopy density and applies the forest-definition rule mechanistically rather than learning a black-box mapping (source: [[nguyen_2022_forest_mapping_explainable]]), is also relevant for making the automated threshold-based forest-line delineation step interpretable — the same study shows that different forest definitions (height/density thresholds) can produce substantially different treeline boundary locations, a real risk for this WP's single-threshold approach

*Sentinel-2 SITS anomaly detection*
- Dense Sentinel-2 time series (2017–2025) at pixel level; Whittaker-smoothed seasonal phenology curves as baseline; anomaly magnitude relative to baseline per pixel (methodology from sattstools [[01_notes/sattstools]])
- Detection of acute stress events in known drought years (2017, 2019, 2022) for open ecotone vs. closed forest pixel classes; anomaly maps linked to WP1 SIF campaign results
- Classification of ecotone pixels into open / transitional / closed-forest using canopy cover maps derived from Planet imagery

*High-resolution individual tree crown segmentation*
- Planet SuperDove (3 m, monthly) time series over study transects; SAM (Segment Anything Model) adapted for tree crown delineation using drone-derived CHM (Canopy Height Model) as elevation prior (following "Bringing SAM to New Heights", arxiv 2025, DOI:10.48550/arXiv.2506.04970)
- Alternatively: VHR aerial or drone orthomosaics (0.1–0.5 m) at biennial intervals for precise crown area and per-crown NDVI/SIF time series
- Per-tree tracking of crown area change (expansion = healthy establishment; shrinkage/gap = mortality or dieback) across 3-year observation window
- Species classification at treeline ecotone following Identifying Alpine Treeline Species with WorldView-3 + CNNs (EGUsphere preprint 2025)
- Very-high-resolution aerial imagery deep learning approach for fine-scale ecotone pattern characterisation (Biogeosciences 2025, DOI:10.5194/bg-22-6393-2025)

*SDM and future projections*
- MaxEnt / BIOMOD2 ensemble SDMs for *Pinus cembra* regeneration suitability under current conditions; predictors: summer temperature, SPEI, VPD, winter snow water equivalent (SWE), topographic microclimate indices (DNI, TWI, RSP)
- Project under CMIP6 SSP2-4.5 and SSP5-8.5 scenarios (2050, 2100); explicitly separate the warming effect (expanding suitable zone) from drought/snow deficit effect (contracting regeneration potential)
- Include snow water equivalent (SWE) projections from EURO-CORDEX as an explicit predictor, since snow cover explains treeline better than temperature alone
- Given regional evidence that lower treeline boundaries can be primarily moisture- rather than temperature-limited while upper treeline remains thermally limited (source: [[klinge_2018_climate_treeline]]), fit and compare separate limiting-factor models for the upper vs. lower margin of the Tyrolean ecotone rather than assuming one (thermal) limiting factor throughout
- Layer SHAP-based explainability on the ensemble SDM output (beyond standard variable-importance rankings) to extract non-linear climate response thresholds, and resolve projections by aspect (north- vs. south-facing slopes) in addition to elevation band: a *Larix chinensis* treeline SDM found consistent, scenario-robust aspect asymmetry (habitat gains on south slopes, losses on north slopes under all CMIP6 SSPs) driven by differential solar radiation, growing-season length, and snow persistence (source: [[li_2026_climate_treeline]]); their bootstrapped-CI method for classifying habitat-suitability trajectories as stable-increasing/stable-decreasing/unstable is a more defensible treeline-shift detection approach than a single deterministic suitability threshold — though their own paper cautions that HSI change is only a *proxy* for treeline migration, which is exactly the gap this WP's independent satellite-based historical treeline tracking (above) is positioned to close by validating projected against observed shift
- Connect to broader Eastern Alps forest transition simulations [[albrich_2019_climate_change_mountain_forests]] and European species vulnerability ranking [[01_notes/dyderski_2025_species_shift]]

**Key uncertainties and mitigation:**
- Planet 3 m resolution may not reliably delineate individual *Pinus cembra* crowns < 1 m diameter → focus crown analysis on juvenile trees ≥ 0.5 m; use CHM from drone to filter detections by height class
- Mann-Kendall treeline analysis sensitive to cloud contamination in Alpine terrain → mask with cloud/shadow algorithm [[01_notes/li_2022_cloud_detection]]; use seasonal composites not single scenes

**Expected outputs:**
- 40-year annual treeline position map for the Tyrolean Alps (published open-access)
- Sentinel-2 anomaly maps for drought/frost events 2017–2025; open vs. closed-forest stress differential quantified
- Individual tree crown segmentation dataset (Planet + drone) for study transects across 3 years
- SDM projections for *Pinus cembra* ecotone under SSP2-4.5 and SSP5-8.5 to 2100

---

### Outcome

**Scientific publications (planned):**

| Paper | Focus | Target journal |
|-------|-------|---------------|
| Paper 1 (Y2) | Drone-based SIF and PRI stress dynamics across the *Pinus cembra* open–closed ecotone gradient | *Agricultural and Forest Meteorology* / *Remote Sensing of Environment* |
| Paper 2 (Y2–3) | Juvenile *Pinus cembra* dendrochronology — drought-frost signal and open vs. closed position differential | *Dendrochronologia* / *Global Change Biology* |
| Paper 3 (Y2–3) | 40-year Landsat-based treeline ecotone dynamics in the Tyrolean Alps — satellite evidence for stagnation under drought | *Biogeosciences* / *Remote Sensing of Environment* |
| Paper 4 (Y3) | Individual crown tracking and stress monitoring at the Alpine treeline with Planet SuperDove and deep learning | *Remote Sensing* |
| Paper 5 (Y3) | Future *Pinus cembra* treeline trajectory in the Eastern Alps under CMIP6: dual-stressor SDM integrating drought and snow deficit | *Global Change Biology* / *Nature Climate Change* |

**Data outputs:**
- Annual Tyrolean treeline position maps 1984–2025 (Landsat-based, open-access)
- Drone SIF/PRI dataset for the Alpine *Pinus cembra* treeline (first for the Eastern Alps)
- Juvenile *Pinus cembra* dendrochronology dataset for Tyrolean ecotone sites
- Individual tree crown segmentation and per-crown spectral time series (Planet + drone)
- Continuous microclimate and soil frost sensor records for 3 sites

**Policy and stakeholder relevance:**
- Direct input for Austrian forest management adaptation strategies (Bundesforste, Land Tirol)
- Reference contribution to the GLORIA monitoring network through RS integration
- Data for Natura 2000 habitat reporting (*Pinus cembra* forests, EU Habitats Directive Annex I: 9420)
- Methodological framework transferable to treeline monitoring across the entire European Alps

---

### Zeitrahmen

| Phase | Year 1 (2026–2027) | Year 2 (2027–2028) | Year 3 (2028–2029) |
|-------|-------------------|-------------------|-------------------|
| **Field setup** | Site selection and characterisation; webcam/sensor/logger installation; first dendro sampling (adults); Landsat historical analysis | Full monitoring: monthly drone SIF campaigns, continuous sensors; juvenile dendro sampling; Sentinel-2 anomaly detection | Repeat drone SIF and dendro coring; sensor data consolidation; final GLORIA reference survey |
| **RS analysis** | Landsat trend analysis (1984–2025); Planet crown segmentation baseline; Sentinel-2 preprocessing | Sentinel-2 stress event detection; Planet crown area time series; VHR aerial campaign | SDM projections; synthesis of multi-scale RS findings |
| **Outputs** | Study site characterisation publication; first SIF campaign results; Landsat treeline position map | Paper 1 (SIF); Paper 3 (Landsat); crown segmentation dataset | Paper 2 (dendro); Paper 4 (crown tracking); Paper 5 (SDM synthesis) |

**Total duration:** 3 years (2026–2029)
**Target funding:** FWF (Austrian Science Fund) — Stand-Alone or 1000Ideas call; EU Horizon Europe (Forest4Climate; BiodivClima); BMBWF (OeAD bilateral Alps cooperation)

---

### Key references

**Foundational ecology:**
- Körner, C. (2012). *Alpine Treelines*. Springer, Basel. — foundational reference on treeline thermal limitation and ecotone structure
- Körner, C. (2021). *Alpine Plant Life* (3rd ed.). Springer. — chapter on snow cover and treeline regulation
- Camarero, J.J. et al. (2025). Patterns, dynamics and drivers of alpine treelines and shrublines. *Nature Reviews Earth & Environment*. https://www.nature.com/articles/s43017-025-00703-9

**Stress physiology and snow:**
- Charra-Vaskou, K. et al. (2026). Reduced snow cover at the alpine treeline: resistance and recovery of saplings. *New Phytologist*. DOI:10.1111/nph.70926. [[charra_2025_snow_treeline]]
- Vázquez-Ramírez, J. & Venn, S.E. (2023/2025). Snow, fire and drought: how alpine and treeline soil seed banks are affected by simulated climate change. *Annals of Botany* 135:223–238. [[vazques_2023_drought_treeline]]
- Camarero, J.J. et al. (2024). Facilitation drives tree seedling survival at alpine treelines. *Journal of Plant Ecology* 17(3). https://academic.oup.com/jpe/article/17/3/rtae033/7659250
- Grünig, M. et al. (2023). Seasonal snow cover patterns explain alpine treeline elevation better than temperature at regional scale. *Science of the Total Environment*. https://www.sciencedirect.com/science/article/pii/S2197562023000210
- Barbeito, I. et al. (2019). Microsites and climate zones: seedling regeneration in the alpine treeline ecotone worldwide. *Forests* 10(10). https://doi.org/10.3390/f10100864
- Lévesque, M. et al. (2014). Drought response of five conifers in mountain forests: growth reaction and climatic drivers. *Ecological Monographs* — growth limitation of *Pinus cembra* at drought margins
- Dietrich, L. & Zeidler, M. (2026). A potential role for DELLA signaling in global treeline formation. *New Phytologist* (Viewpoint). [[dietrich_2026_treeline_della]] — conceptual hormonal-signalling alternative to the carbon-limitation hypothesis; untested in treeline conifers

**Treeline dynamics and dendrochronology:**
- Mdt, F. et al. (2023). Evidence for 40 years of treeline shift in a Central Alpine Valley. *Forests* 14(2). https://www.mdpi.com/1999-4907/14/2/412
- Frank, D. et al. (2022). Tree-ring anatomy of *Pinus cembra* opens new avenues for climate reconstructions in the European Alps. *Science of the Total Environment*. https://www.sciencedirect.com/science/article/pii/S0048969722057047
- Nikolova, P.S. et al. (2023). Tree rings as ecological indicators of *Pinus cembra* reaction to climate change and disturbance in cliff forests. *Ecological Indicators*. https://www.sciencedirect.com/science/article/pii/S1470160X23002443
- Märker, F. et al. (2025). Emerging drought sensitivity for large Norway spruce trees at high elevation in the High Tatras, Slovakia. *Trees* 39:7. [[maerker_2025_drought_spruce]] — size-class isolation (SCI) method; direct methodological precedent for WP1's juvenile-vs-adult comparison
- Klinge, M. et al. (2018). Climate effects on vegetation vitality at the treeline of boreal forests of Mongolia. *Biogeosciences* 15:1319–1333. [[klinge_2018_climate_treeline]] — upper treeline thermally limited, lower treeline moisture limited
- Babst, F. et al. (2019). Twentieth century redistribution in climatic drivers of global tree growth. *Science Advances* 5:eaat4313. [[01_notes/babst_2019_redistribution]]
- Albrich, K. et al. (2019). Climate change causes critical transitions and irreversible alterations of mountain forests. *Global Change Biology*. [[01_notes/albrich_2019_climate_change_mountain_forests]]
- Dyderski, M.K. et al. (2025). Species distribution shifts of 20 European tree species under CMIP6 SSPs. [[01_notes/dyderski_2025_species_shift]]

**Remote sensing of treeline and forest stress:**
- Baglioni, L. et al. (2025). Forestlines in Italian mountains are shifting upward: detection and monitoring using satellite time series. *Biogeosciences* 22:4349–4366. https://bg.copernicus.org/articles/22/4349/2025/
- Very-high resolution aerial imagery and deep learning uncover fine-scale patterns of elevational treelines. *Biogeosciences* 22:6393 (2025). https://bg.copernicus.org/articles/22/6393/2025/
- Identifying alpine treeline species using WorldView-3 multispectral imagery and CNNs. *EGUsphere* preprint (2025). https://egusphere.copernicus.org/preprints/2025/egusphere-2025-970/
- Bringing SAM to New Heights: Leveraging elevation data for tree crown segmentation from drone imagery. *arXiv* (2025). https://arxiv.org/html/2506.04970
- UAV-Borne Measurements of Solar-Induced Chlorophyll Fluorescence (SIF) at a Boreal Site. *Springer* (2024). https://link.springer.com/chapter/10.1007/978-3-031-44607-8_8
- Nguyen, T.-A. et al. (2022). Mapping forest in the Swiss Alps treeline ecotone with explainable deep learning. *Remote Sensing of Environment*. [[nguyen_2022_forest_mapping_explainable]] — rule-informed CNN; forest-definition sensitivity of treeline boundary
- Nguyen, T.-A. et al. (2024). Multi-temporal forest monitoring in the Swiss Alps with knowledge-guided deep learning. *Remote Sensing of Environment* 305:114109. [[nguyen_2024_treeline_monitoring]] — knowledge-guided temporal loss for sparsely-labelled, multi-decadal treeline monitoring
- Li, L. et al. (2026). Assessing climate-driven treeline dynamics via the habitat suitability index. *Journal of Environmental Management* 411:130173. [[li_2026_climate_treeline]] — SHAP-explained ensemble SDM, aspect-resolved, bootstrapped-CI shift detection
- Melser, R. et al. (2024). Characterizing satellite-derived freeze/thaw regimes through spatial and temporal clustering for the identification of growing season constraints on vegetation productivity. *Remote Sensing of Environment* 309:114210. [[melser_2024_freeze_constraints]] — SMAP/SMOS freeze/thaw regionalisation, boreal Canada (methodological precedent, not directly Alpine)
- Torres, M. et al. (2021). Remote sensing for forest health monitoring — systematic review [[01_notes/torres_2021_forest_health_remote_sensing]]
- Landscape Ecology (2025). Future expansion of upper forest-grassland ecotone under land-use and climate change in the Eastern Alps. https://link.springer.com/article/10.1007/s10980-025-02070-8

**Wiki synthesis pages:** [[treeline_ecotone_theory]] · [[snow_cover_treeline]] · [[treeline_remote_sensing_monitoring]]
