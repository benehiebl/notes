# Design sanity check: "Alpine forest tree line under stress" (Pinus cembra, Tyrol, 2026-2029)

Scope: critical review of /home/c7161037/Desktop/repos/notes/04_projects/02_tree_line_stress.md (not modified). Research date 2026-10-13. DOIs were checked against the Crossref API (title/author/journal/year/volume/pages) unless marked. Abstract content was read where Crossref or the publisher exposed it. Several publisher pages returned HTTP 403 (Wiley, MDPI, ScienceDirect), so some claims rest on abstracts only. "UNVERIFIED" = could not be confirmed in this session. Items marked "(expert judgement)" are my own reasoning, not a sourced finding.

Search effort was limited (about 15 tool calls). Absence of a hit is NOT proof of absence (relevant to all novelty checks).

---

## 1. Are O1-O3 testable with the proposed design?

### Takeaway
As written, none of O1-O3 is formally testable. No hypotheses are stated, the design has 3 unreplicated transects with elevation, canopy position and (probably) aspect confounded, and O2 (recruitment) has no recruitment measurement in any work package.

### Cited Findings
- Transect layout in proposal: (a) open ecotone, (b) transition, (c) closed forest "at ~1800 m a.s.l.", one transect each of 3 types or 3 transects total (ambiguous: "3 permanent study transects") (proposal WP1). The proposal itself places the ecotone at about 1900-2400 m, so position and elevation are confounded by construction.
- O2 asks about "seedling recruitment and ecotone advance"; the WPs contain sensors, webcams (GCC, snow depth), SMAP and GLORIA reference data, and 3-year crown tracking of trees at least 0.5 m. There is no seedling census, seed rain, cache or germination measurement (proposal WP1/WP2; O2 text).
- GLORIA records vascular plant cover (visual cover plus 100-point framing in 16 1 m2 quadrats), abundance in 8 summit-area sections, photos and soil temperature (4 loggers per summit); the page lists no tree density and no resurvey interval — [GLORIA multi-summit approach](https://gloria.ac.at/methods/multi-summits). The proposal's claim "species cover and tree density from GLORIA Austria network" is therefore not supported by the method description I could read.
- GLORIA is a summit (alpine-nival) design: at least 4 summits along an elevation gradient per target region [GLORIA](https://gloria.ac.at/methods/multi-summits). Austrian examples: Schrankogel master site (Tyrol/Stubai, major resurvey 2004) and Hochschwab (Styria; resurveyed 2008 and 2015, i.e. about 7 years) — [LTER Austria Schrankogel](https://www.lter-austria.at/schrankogel-gloria-master-site/), as summarised by a web search; the 5-year cycle was found only for the Great Basin programme, not Austria. Resurvey interval for Austria: UNVERIFIED (check Field Manual 5th ed., https://gloria.ac.at/downloads/Manual_5thEd_ENG.pdf).
- Drought as limiting factor at the Tyrolean treeline is weakly supported. Oberhuber (2004): July temperature is the long-term stable driver of P. cembra ring width at Patscherkofel; divergence since the mid-1980s is attributed to "extreme events or increasing drought stress" with only a <10% increment gain in 2003 vs 2002 as support — DOI 10.1093/treephys/24.3.291. Related Innsbruck work: Gruber et al. 2009 (stem radius reflects tree water status), DOI 10.1051/forest/2009038; Wieser et al. 2015 (soil warming increased whole-tree water use at Central Tyrolean treeline), DOI 10.1093/treephys/tpv009; Gruber et al. 2018 (N addition/understory removal/soil warming experiment on radial growth), DOI 10.3389/fpls.2018.00711.
- Land-use control dominates in the Eastern Alps ecotone: iLand simulations show the current upper forest-grassland ecotone is "mainly constrained by land use rather than climate" and forest would expand rapidly after grassland abandonment regardless of warming — Marzini et al. 2025, Landscape Ecology 40, DOI 10.1007/s10980-025-02070-8 (Tasser is co-author; study area likely South Tyrol, UNVERIFIED). The proposal lists this paper but does not use it.
- Facilitation citation does not match the claim: Camarero-coauthored "Facilitation drives tree seedling survival at alpine treelines" (J Plant Ecol 17, DOI 10.1093/jpe/rtae033; first author Chen) is a transplant experiment with Abies georgei on the SE Tibetan Plateau (4300-4500 m), not an Alpine or Pinus cembra study — [JPE](https://academic.oup.com/jpe/article/17/3/rtae033/7659250). Using it as support for "canopy facilitation buffers drought in P. cembra" is an over-extension.

### Inferences
- CRITICAL: Pseudo-replication and confounding. With 1 transect per position, "open vs closed" differences are inseparable from site, elevation (about 300-600 m between (a) and (c)), aspect, soil and microsite. Statistical inference about "open vs closed" has n = 1 at the site level; trees within a transect are subsamples. Fix: (i) paired design with open and closed positions within the same elevation band and aspect at each of at least 6 sites (e.g. 3 siliceous + 3 calcareous or 3 N + 3 S aspects), (ii) analyse with mixed models (site random, tree nested), canopy position as a continuous covariate (neighbour basal area/competition index, crown openness from drone CHM, DNI/TWI), (iii) do a power analysis on pilot data before committing sample sizes. If only 3 sites are affordable, state explicitly that the study is a case study with descriptive inference, not a test.
- CRITICAL: Facilitation is a microsite effect. "Drought stress differential between open and closed positions" will mix canopy buffering with snow redistribution, wind, soil depth, tree age and size, and genotype. SIF additionally depends on canopy structure (LAI, shadows, background snow/grass mix): open sparse crowns and closed stands are not radiometrically comparable without normalisation (fluorescence yield, NIRv/structure correction) (expert judgement). Fix: define the response as tree-level SIF yield and leaf water potential, and measure the structural covariates explicitly.
- CRITICAL: O2 is not covered by any measurement. Recruitment needs seedling/sapling census in permanent plots (<0.5 m cohort), seed-cache/seedling establishment, browsing scoring and microsite description. Pinus cembra is nutcracker-dispersed; cache sites and establishment microsites can mismatch (conference abstract, [ESA 2013](https://eco.confex.com/eco/2013/webprogram/Paper42071.html), weak source). Fix: either add a WP "Recruitment" (permanent 2x2 m or belt plots, annual census of germinants/seedlings with microsite classification, snow-manipulation optional) or rewrite O2 as "environmental constraints on the microsites available to recruits" and drop "recruitment".
- MAJOR: GLORIA plots are not a tree validation dataset. Summit plots lie above the treeline, record herb/shrub cover in 1 m2 quadrats, and (per the method page read) record no tree density. They can only provide (a) soil temperature loggers and vascular cover context above the ecotone and (b) a co-located alpine vegetation record. Fix: replace "validation" by "regional context"; for tree validation use the Austrian Forest Inventory (ÖWI), Landesforstdienst Tirol aerial image archive, historical orthophotos (Tirol, 1950s onward), or own plots. Also, "final GLORIA reference survey in Year 3" is outside project control; GLORIA surveys follow multi-year cycles run by designated teams, so coordination with the Austrian GLORIA coordinators is a prerequisite (confirm via gloria.ac.at).
- MAJOR: The dual-stressor claim cannot be separated observationally. No manipulation (snow removal, rain exclusion, shading) is planned, yet the title and Paper 5 assume attribution to "drought + snow deficit". The motivation also mixes mechanisms (drought, spring frost, soil frost/freeze-thaw, snow loss) without a priori hypotheses linking each to a measurement. O1 mentions "spring frost" but no needle/shoot frost damage measurement exists (sensors are soil T/moisture; frost damage would need leaf-level scoring or ground-truth browning surveys).
- MAJOR: Charra-Vaskou et al. (New Phytol 250:1492-1509, DOI 10.1111/nph.70926) used a snow-removal experiment on saplings of five species other than Pinus cembra at 1700 m; its mechanism is not transferable to P. cembra without testing. The proposal acknowledges this but still builds O2 around it. Fix: pilot a snow-removal/ice-encasement or sapling freeze-thaw exposure at the transects (small plots, n ≥ 5 per site) or soften O2 wording.
- MAJOR: No hypotheses. Suggested rewrite, e.g. O1: "H1: Predawn water potential and SIF yield of P. cembra decline more strongly during drought in open than in closed positions, after accounting for elevation, aspect and structure. H0: no difference." Define effect size and the drought index threshold (e.g. SPEI-3 < -1) a priori.

### Gaps
- Number of sites is ambiguous ("3 permanent study transects"); personnel and budget are not stated, so feasibility cannot be judged quantitatively.
- Austrian GLORIA resurvey interval and whether any Tyrolean target region includes a summit at or just above the treeline: UNVERIFIED.

---

## 2. Novelty claims

### Takeaway
"First integrated framework", "novel dataset for the Alps" and "first for the Eastern Alps" are not substantiated and probably over-stated; integrated treeline research exists in Tyrol (Innsbruck Patscherkofel group, Tasser/Eurac, WSL Switzerland). Drone-SIF specifically might be new for the Alpine treeline, but my search was too limited to claim this.

### Cited Findings
- Search for drone SIF in Alpine/subalpine forest found no study on Pinus cembra or Alpine treeline. Closest: a WSL (Switzerland) project 2024-2025 using airborne SIF over drought-stressed pine forest with a drone multispectral component — [WSL project page](https://www.wsl.ch/en/projects/solar-nduced-luorescence/); UAV-SIF has been done in boreal forest and oak FACE (UK) — [Open University ORO 58503](https://oro.open.ac.uk/58503), [ORO 58505](https://oro.open.ac.uk/58505). A DFG project (since 2024) develops a drone SIF camera — [GEPRIS 541028765](https://gepris.dfg.de/gepris/projekt/541028765). Alps/Eastern Alps SIF literature otherwise: UNVERIFIED, not exhaustively searched (no Google Scholar/Scopus access).
- Prior integrated treeline monitoring in Tyrol: Innsbruck plant-ecophysiology group at Patscherkofel (Oberhuber, Gruber, Wieser, many FWF projects), combining dendrometers, wood formation, gas exchange and soil-warming/nutrient manipulations (DOIs above, plus Gruber et al. 2008 Trees 23:623-635, DOI 10.1007/s00468-008-0307-7). Land-use/vegetation change: Tasser & Tappeiner 2002, DOI 10.1111/j.1654-109x.2002.tb00547.x; Tasser et al. 2017, DOI 10.1016/j.landusepol.2016.10.019; Dirnböck et al. 2003, DOI 10.1046/j.1365-2699.2003.00839.x.
- Remote sensing treeline in the Alps: Nguyen et al. (Swiss Alps, deep learning, multi-decadal; cited in proposal), Baglioni et al. 2025 (Italian mountains, Landsat; DOI 10.5194/bg-22-4349-2025, correct); Frei et al. 2023 Forests 14:412, DOI 10.3390/f14020412 (Central Swiss Alps ground resurvey).
- Planet/Landsat/Sentinel-2 treeline mapping and UAV tree mapping at the treeline are established; the proposal's novelty therefore lies only in the combination and in SIF.

### Inferences
- MAJOR: Replace "first integrated monitoring and modelling framework for the dual-stressor regime" with a defensible statement, e.g. "To our knowledge, this is the first study to combine tree-level UAV-based SIF/PRI with juvenile dendrochronology and 40-year satellite treeline records along a canopy-position gradient at the Pinus cembra treeline in Tyrol." Add "to our knowledge" and document a systematic search (Scopus/WoS/Google Scholar query string and date) in the application.
- MAJOR: "Novel dataset for Alps" and "first for the Eastern Alps" for drone SIF/PRI: acceptable only after a documented search; reduce to "first publicly available UAV-SIF time series at the P. cembra treeline, to our knowledge".
- MINOR: Contact Patscherkofel/Innsbruck (Botany/Plant Physiology), Eurac, WSL and BOKU groups before submission; the proposal currently ignores the existing long-term Tyrolean treeline work and sites, which could provide long-term climate/phenology baselines and reduce cost.
- Technical risk (expert judgement): UAV SIF retrieval needs a spectrometer with sub-nm spectral resolution (FWHM roughly 0.3-1 nm) in the O2 bands; typical hyperspectral push-broom cameras (several nm FWHM) are inadequate. The proposal specifies "hyperspectral UAV payload" with SIF from both O2-A and O2-B but names no instrument. Specify payload, spectral resolution, SNR target and a go/no-go criterion (it already names PRI as fallback; PRI, however, is sensitive to illumination/structure and is a weak "stress" indicator in evergreen conifers on snow-patchy ground).

### Gaps
- Complete literature search for Alpine UAV-SIF/PRI and for treeline integrated monitoring in Austria (LTSER/LTER Austria, Obergurgl, Kühtai) — not done to completeness here.

---

## 3. Timeline, drought years, logistics and funding

### Takeaway
The timeline is already out of date (today is 2026-10-13; Year 1 "2026-2027" is under way and no funding is secured), the named "drought years" 2017/2019/2022 do not match the documented Alpine/Central-European drought years (2003, 2015, 2018, 2022), FWF 1000 Ideas cannot fund a 3-year project, and two of the named EU schemes could not be verified.

### Cited Findings
- Documented Alpine drought events: 1976, 2003, 2015 and 2018 produced the most impact reports (NHESS inventory of Alpine drought impact reports, https://nhess.copernicus.org/preprints/nhess-2021-24/nhess-2021-24-manuscript-version3.pdf, found via search; not read in full). 2018 was climatically more extreme than 2003 and hit forests in Austria, Germany, Switzerland — Schuldt et al. 2020, Basic and Applied Ecology 45:86-103, DOI 10.1016/j.baae.2020.04.003. 2018 north-of-Alps precipitation below 90% of normal; Upper Austria 60-75% — [Klimastatusbericht 2018](https://opac.geologie.ac.at/ais312/dokumente/Klimastatusbericht_OE_und_W_2018_20190812_Onlineversion.pdf) (no Tyrol-specific figures extracted). Europe 2022: second hottest/driest year on record in a summary (source weak). 2025 multi-country forest-vitality analysis (Zenodo, https://zenodo.org/records/14710420, summary only, UNVERIFIED) reports that the Alpine zone showed least impact, possibly due to altitude.
- 2017 and 2019 as Tyrolean Alpine drought years: no supporting source found; UNVERIFIED. The proposal omits 2018.
- FWF 1000 Ideas: €50,000-175,000, 6-24 months, about 20 projects per round, PI salary at most 50%, no doctoral positions — [FWF](https://fwf.ac.at/en/funding/portfolio/projects/1000-ideas) (via search summary; one aggregator says €150k; FWF page is authoritative; confirm current call text). A 3-year, 3-site, multi-sensor design plus juvenile dendro is far outside it.
- "Forest4Climate" (Horizon Europe): no matching call found; UNVERIFIED. "BiodivClima": the Biodiversa ERA-NET Cofund is "BiodivClim" (call launched 2 Sep 2019, running 2019-2024, a closed call) — [TACR BiodivClim](https://tacr.gov.cz/en/biodivclim/); current Biodiversa+ calls should be checked instead. "BMBWF OeAD bilateral Alps cooperation": not found; UNVERIFIED (OeAD does run bilateral WTZ programmes, but none verified for this purpose). FWF Stand-Alone Projects exist and are the realistic fit (programme page not re-fetched; assumption).
- Austrian drone rules: EU open category (A1-A3), operator registration, insurance, max 120 m; remote-pilot certificate required for many drones — [dronespace.at / Austro Control](https://dronespace.at/en), commercial guides summarised by search. Protected-area bans (Hohe Tauern, state nature-conservation laws) were stated by a guide but are UNVERIFIED; check Tiroler Naturschutzgesetz 2005, the Hohe Tauern NP administration, and Natura 2000/hunting-law (wildlife disturbance) constraints.
- Anthropogenic treeline depression in Tyrol: Holocene P. cembra timberline at about 2450 m in the Western Tyrolean Central Alps was cleared by pasturing and burning and depressed by several hundred metres at some sites (Staffler et al. 2011, https://opac.geologie.ac.at/ais312/dokumente/Staffler_2011_Waldgrenzentwicklung.pdf; DOI not found, UNVERIFIED; Crossref search failed). Motta et al. 2006 (W. Italian Alps): grazing 1850-1930 reduced larch and nearly suppressed stone pine establishment, DOI 10.1051/forest:2006055. Swiss Alps: Gehrig-Fasel et al. 2007, DOI 10.1111/j.1654-1103.2007.tb02571.x (climate vs land abandonment).
- Nutcracker dependence: stone pine seeds are heavy and dispersed almost exclusively by spotted nutcrackers, caches about 5 km from harvest sites — [Waldwissen](https://waldwissen.net/en/forest-ecology/forest-fauna/birds/spotted-nutcracker-and-swiss-pine), [Springer Movement Ecology s40462-022-00338-1](https://link.springer.com/article/10.1186/s40462-022-00338-1) (via search; not read in full).

### Inferences
- CRITICAL: Timeline. Application, FWF decision and contract typically take many months (assumption, check programme); realistic project start is 2027 at the earliest. Re-label as Y1-Y3 relative to start, and drop calendar dates. Landsat "1984-2025" should be updated to the last full year at analysis time.
- CRITICAL: Drought years. Fix: "Sentinel-2 (2017-2025) includes the documented Central-European/Alpine drought summers 2018 and 2022 (verify with GeoSphere SPEI/precipitation anomalies for Tyrol); 2017 and 2019 are included only if SPEI/soil-moisture anomalies for the study sites exceed a pre-set threshold". Use site-specific SPEI/ERA5-Land soil moisture to select events a priori; do not name years in advance. Note 2018 is absent from the proposal and is the most relevant event for validation; but Sentinel-2 2018 pre-dates the project sensors (no SIF), so only satellite-vs-dendro comparisons are possible.
- CRITICAL: Only 3 field seasons and no guarantee of a drought. The probability that 2027-2029 contains an event comparable to 2018 is unknown; the design must function in a normal year (as comparison of normal-year gradients) and be framed as "monitoring baseline", not "drought response" unless a drought occurs. Add retrospective power through dendro (2003, 2015, 2018, 2022 are all in the juvenile record only if trees are old enough).
- MAJOR: Monthly UAV flights April-October at 1800-2400 m. Snow typically covers sites into May-June at upper elevations (expert judgement), so April-May flights deliver snow cover not tree stress; weather windows (10:00-14:00 clear sky) at treeline limit successful flights, roughly 7 campaigns x 3 sites x 3 years. Fix: 4-5 targeted campaigns per year (snowmelt/early season, peak, drought peak, post-drought, senescence), with weather-contingent backups and fixed solar-zenith windows; carry reflectance panels and a ground-based spectrometer for each flight. Reserve funds for safety (two-person teams, alpine safety training, flight permits).
- MAJOR: Legal. Add permit work package: drone registration/insurance, state nature-conservation approval, landowner/Agrargemeinschaft/ÖBf consent, wildlife-disturbance rules, Natura 2000 compatibility assessment. Landowners in Tyrol include ÖBf and Agrargemeinschaften (expert judgement; UNVERIFIED).
- MAJOR: Juvenile dendrochronology. "Naturally fallen or thinned" juvenile trees (<10 cm DBH) are rare at the treeline; destructive sampling in Natura 2000/protected terrain needs approval; cross-sections of 20-40 year-old stems have very narrow rings, false/missing rings and short series, so COFECHA crossdating (needs usually longer overlapping segments, expert judgement) and pointer-year analysis over "the 20th-21st century" are infeasible from juveniles. For adults, "target 50 per transect" is fine. Fix: use juveniles only for climate-sensitivity over their short span and analyse age/size effects with the SCI approach as stated; drop century-scale pointer-year claims for juveniles; consider increment cores from larger saplings (non-destructive) and wood anatomy (Lopez-Saez et al. 2023 for P. cembra, DOI 10.1016/j.scitotenv.2022.158605).
- MAJOR: Papers 1-5 in 3 years from one project is not realistic. SIF Paper 1 in Y2 needs a first full season of data; Paper 2 (dendro) and Paper 3 (Landsat) can run in parallel; Papers 4 and 5 depend on year-3 data and a validated SDM. Suggest 3 core papers (SIF/PRI + dendro as one integrated paper; Landsat/historical treeline; SDM/synthesis) plus one methods/data paper; keep Paper 4 optional.
- MAJOR: Funding scheme. Remove FWF 1000 Ideas (24-month cap, high-risk exploratory); target FWF Stand-Alone Project; verify Forest4Climate and OeAD scheme or delete; check Biodiversa+ and Euregio/Land Tirol options (Euregio Science Fund and Interreg Alpine Space: UNVERIFIED).
- MAJOR: Planet SuperDove 3 m (monthly) access is commercial; check licence/ budget (UNVERIFIED), and it cannot resolve crowns <1 m. The proposal's mitigation ("focus on juvenile trees ≥0.5 m") contradicts this: 0.5 m trees have crowns well below 1 m diameter. Use drone orthomosaics for individual-crown work and Planet only for stand-level indices.
- Forest definitions and resolution. Landsat 30 m detects a forest-line shift only at tens-of-metres scale; Baglioni et al. use "forestline", not tree-island treeline. Nguyen et al. showed forest definition (height/density) shifts the boundary substantially (as cited in proposal). The Landsat record also has sensor gaps (Landsat 7 SLC-off, post-2011 gap in Landsat 5) (expert judgement), and NDVI/Mann-Kendall mostly captures greening (shrubs, grass) rather than tree establishment.

### Gaps
- GeoSphere/Tyrol-specific drought indices for 2017, 2019, 2022 not retrieved; the same applies for snow-cover duration at 1800-2400 m for scheduling flights.
- Official FWF Stand-Alone Project terms and current Biodiversa+ call topics not retrieved.

---

## 4. Natura 2000 and stakeholders

### Takeaway
Habitat code 9420 is correct, but the habitat is a forest type, and the proposed 3-site monitoring will not deliver data usable for Article 17 reporting.

### Cited Findings
- 9420 "Alpine Larix decidua and/or Pinus cembra forests": Annex I, non-priority; subalpine/montane forests of the Alps and Carpathians, subtypes include eastern Alpine siliceous larch and arolla forests (42.31) and calcicolous (42.32) — [EUNIS 205](https://eunis.eea.europa.eu/habitats/205), [BfN](https://www.bfn.de/en/natura-2000-habitats/alpine-larix-decidua-andor-pinus-cembra-forests). Italy rates it U1 (inadequate) in the IV report (threats: forest management, avalanches, warming) — [ISPRA](https://reportingdirettivahabitat.isprambiente.it/documents/monitoraggio_IV_report/habitat/9420m_mon.pdf). French source: nutcracker-driven spread and grazing abandonment expand stone pine forests ([DREAL PACA](https://www.dre.paca.developpement-durable.gouv.fr/IMG/pdf/1_H9420_cle21adac.pdf)).
- Land Tirol and Bundesforste: no verification done of their role; no letters of support or data agreements in the proposal.

### Inferences
- MINOR: Rewrite "Data for Natura 2000 habitat reporting" to "supports understanding of pressures/trends of habitat 9420 in Tyrol; contributes structure/function indicators" and name the Tyrol Natura 2000 sites; the treeline ecotone (tree islands, krummholz, grassland mosaic) partly lies outside the forest habitat definition.
- MINOR: Get letters of support from Land Tirol (Abteilung Waldschutz/Naturschutz), landowners and the GLORIA coordinators.
- The mismatch between Natura 2000 reporting scale (national/biogeographic region, cycles of 6 years) and a 3-site study should be acknowledged.

### Gaps
- Tyrolean Natura 2000 site names and monitoring schemes covering 9420: not retrieved.

---

## 5. Checks of specific claims and citations

### Takeaway
Several citations in the Motivation are misattributed or misdescribed, and the +2 °C claim is stretched. These are quick fixes but affect credibility with reviewers.

### Cited Findings (verified against Crossref)
| Proposal citation | Finding | Fix |
|---|---|---|
| "Camarero et al. 2025, NREE" | Authors are Lu, Zheng, Liang, Piao, Babst, Elliott, Sigdel, Wang (+ others); NREE 6:489-502, DOI 10.1038/s43017-025-00703-9. Camarero co-authorship: UNVERIFIED | Cite as Lu et al. 2025 |
| "Grünig et al. 2023, Sci Total Environ" | Actual: Huang, Wang, Bie, Jiang et al., Forest Ecosystems 10:100106, DOI 10.1016/j.fecs.2023.100106; the PII in the proposal URL (S2197562023000210) is the Forest Ecosystems article. Region: UNVERIFIED (likely Asian mountains; Bie Qiang is Lanzhou-based, so check) | Correct authors/journal; check region before using for Alps |
| "Nikolova et al. 2022 Sci Total Environ" (VPD) and "Nikolova 2023 Ecol Indic" | Ecol Indic 148:110102 (2023) is Izworska, Muter, Matulewski, Zielonka (cliff forests, Polish/Slovak karst; DOI 10.1016/j.ecolind.2023.110102). No "Nikolova 2022" found; VPD claim UNVERIFIED | Correct or remove |
| "Mdt, F. et al. 2023" (Evidence for 40 years of treeline shift) | Frei, Barbeito, Erdle, Leibold, Bebi; Forests 14:412; DOI 10.3390/f14020412; Central Swiss Alps; mean 10 m/decade (1972/73-2012), max 42 m/decade | Fix author names; replace "0.4 m/yr in the Alps over the last century" |
| "0.4 m/year over the last century in the Alps" | Not in the cited abstract (which gives 10 m/decade, i.e. about 1 m/yr in one Swiss valley over 40 years; vertical vs horizontal not stated in the abstract); attributes advance also to land-use abandonment | Remove or cite a source that gives this exact figure; UNVERIFIED |
| "Lévesque et al. 2014, Ecol Monogr" | Actual: Agric Forest Meteorol 197:1-12, DOI 10.1016/j.agrformet.2014.06.001 (five conifers across a Central-European (Swiss) climatic gradient). Whether P. cembra is "growth-limited by drought at rear-edge" there: UNVERIFIED | Correct journal; verify claim |
| "Barbeito et al. 2019, Forests 10(10)" | DOI 10.3390/f10100864 resolves to Johnson & Yeakley (not Barbeito) | Correct authors |
| "Camarero et al. 2024 JPE" | Chen, Li, Camarero et al.; Tibetan Plateau transplant of Abies georgei; DOI 10.1093/jpe/rtae033 (correction DOI 10.1093/jpe/rtae054) | Do not use as support for P. cembra; Alpine alternative needed |
| "Albrich 2019 GCB" | Albrich, Rammer, Seidl; GCB 26:4013-4027; published 2020; DOI 10.1111/gcb.15118 | Fix year |
| "Simulation modelling for the Eastern Alps demonstrates irreversible critical transitions in mountain forest composition at just +2 °C" | Abstract: iLand simulation of "a mountain forest landscape in the Eastern Alps"; above +2 °C mean annual warming the system tips from conifer-dominated large trees to smaller predominantly broadleaved trees; topographic complexity buffers; hysteresis, "irreversible at millennial time scales". Not a treeline study (focus on forest composition/size structure; the abstract states no treeline analysis); the exact study landscape (I recall Kalkalpen NP area, 385-1963 m; UNVERIFIED) is montane, not treeline | Reword: "A simulation of one Eastern Alpine mountain forest landscape found a tipping point toward broadleaf-dominated, smaller-tree states above about +2 °C (Albrich et al. 2020); this concerns montane/subalpine forest composition and says nothing directly about treeline position" |
| "Körner 2012 assumes uniform temperature limitation" | Körner (2012, Alpine Treelines) discusses temperature limitation as the global common denominator but also local modifiers (e.g. disturbance, snow, wind). Not verified here; the Mongolian Klinge 2018 paper is not Alpine | Reword to "the globally dominant thermal limitation" and drop the "assumption of uniformity" framing unless a quote is verified; keep Mongolian example out (non-Alps) |
| "canopy facilitation buffers drought" | No Alpine P. cembra evidence cited (cited paper is Tibetan fir) | Add Alpine evidence or present as hypothesis |
| "Frank et al. 2022 (P. cembra tree-ring anatomy)" | Actual authors Lopez-Saez, Corona, von Arx, Fonti et al., STOTEN 855:158605 (2023), DOI 10.1016/j.scitotenv.2022.158605 | Correct authors/year |

### Inferences
- Motivation overstates drought: Tyrolean evidence (Oberhuber 2004) still points to summer temperature as the primary control, with drought a possible modifier since the 1980s. Rewrite O1/Motivation to "test whether drought has become co-limiting".
- Land-use history: Tyrolean treelines were depressed by pasture/burning/logging over millennia (Staffler et al. 2011; Motta 2006), and Marzini et al. 2025 show present ecotone position is land-use limited. A causal "stagnation under drought" requires controlling for grazing abandonment, ungulate browsing, avalanches, wind and fire, none of which is mentioned as covariate. Fix: add land-use history and browsing layers (historical orthophotos, alp register, ungulate density) and fit them as covariates in Paper 3/5.
- The Paper 3 title "satellite evidence for stagnation under drought" presupposes both the outcome and the cause. Suggested: "Forty years of treeline ecotone change in the Tyrolean Alps from Landsat time series: patterns and climatic and land-use correlates". Same for Paper 5: "dual-stressor SDM" implies a result; use "Climate- and snow-driven scenarios of P. cembra treeline suitability in the Eastern Alps". Pre-register analyses; state a stagnation null and test it.
- SDM/CMIP6 vs lag: correlative SDMs assume equilibrium; P. cembra is slow-growing, nutcracker-dispersed, with land-use legacy. SSP2-4.5/SSP5-8.5 to 2100 from 3-year monitoring data is a stretch. Fix: restrict to 2050 (or a mechanistic/iLand-style approach), provide dispersal/lag scenarios, and compare with Marzini et al. simulations; document presence data source (ÖWI, Tyrol forest inventory) since transects provide no SDM training data.
- "Dual-stressor regime" and "under stress": there is no stress manipulation; the term should become "exposure to low snow and summer drought".

### Gaps
- Körner (2012) full text not checked for the exact wording on "uniform temperature limitation".
- Albrich et al. study landscape and elevation range not verified in this session.

---

## 6. Ranked issue list with concrete fixes

### Takeaway
Three critical design/logic problems (replication/confounding; O2 unmeasured; circular framing) plus an infeasible timeline/funding mapping must be solved before submission.

### Cited Findings
See sections 1-5 for sources.

### Inferences
CRITICAL
1. Design cannot test open-vs-closed effect (n=1 per position, elevation/aspect/microsite confounded). Fix: at least 6 paired sites or reframe as case study; mixed models; power analysis.
2. O2 recruitment is not measured. Fix: add seedling census/microsite WP or rename O2.
3. Circular/outcome-presupposing framing (Paper 3 title, "dual-stressor", "stagnation under drought") and absence of formal hypotheses. Fix: explicit H1-H3, neutral titles, pre-registration, null models.
4. Timeline and funding mismatch (Year 1 already started; 1000 Ideas max 24 months; unverified schemes). Fix: relative project years; FWF Stand-Alone; verify or drop Forest4Climate/OeAD.
5. Drought years mismatch (2017/2019 unsupported; 2018 missing); no guarantee of drought during 3 seasons. Fix: event selection by site-specific SPEI/soil-moisture; design for normal years.

MAJOR
6. Land-use legacy, grazing, browsing, avalanches not treated; literature shows treeline in Tyrol is land-use limited (Marzini 2025; Staffler 2011).
7. GLORIA misdescribed (summit, no tree density); drop as tree validation.
8. SIF feasibility (instrument spec, structure confound, snow background) and flight frequency; legal permits; safety.
9. Juvenile dendro infeasible as stated (sacrificial trees, short series, crossdating).
10. Planet 3 m vs sub-metre crowns; contradictory mitigation; Landsat 30 m and NDVI trend cannot isolate tree advance.
11. Five papers in 3 years; consolidate to 3-4.
12. Citation errors (table in section 5), including +2 °C Albrich claim and 0.4 m/yr claim.
13. Novelty wording ("first", "novel") without documented search; ignores Innsbruck Patscherkofel group.
14. SDM to 2100 with equilibrium assumptions; no presence-data source.

MINOR
15. Natura 2000 overstatement; no stakeholder letters.
16. "Spring frost" in O1 without leaf-level frost measurement.
17. SMAP 9 km irrelevant for site-level; remove or label as context only.
18. Use of non-Alpine evidence (Mongolia, Kosciuszko, Tibet, High Tatras) in the Motivation; replace with Alpine examples where possible (Charra-Vaskou is Tyrolean and appropriate).

Suggested replacement aim texts:
- O1: "Test whether Pinus cembra at the Tyrolean treeline shows stronger physiological drought responses (predawn water potential, UAV-SIF yield, ring-width) in open than in closed positions, controlling for elevation, aspect and canopy structure, across at least six paired sites."
- O2: "Quantify the microsite conditions (snow cover duration, soil freeze-thaw frequency, moisture) associated with P. cembra seedling and sapling presence and survival in permanent census plots across the ecotone."
- O3: "Reconstruct the 1984-2025 change in the upper forest line in Tyrol from Landsat, and test its association with climate indices and land-use/browsing covariates before projecting suitability under CMIP6 scenarios to 2050."

### Gaps
- No budget, staffing, or site list in the proposal; feasibility is assessed qualitatively only.
- The research tools used cannot replace a systematic literature search; run a documented Scopus/WoS search before keeping any "first" claim.

---

## DOI list used (Crossref-verified metadata unless marked)
- Albrich, Rammer, Seidl 2020, GCB 26:4013-4027 - 10.1111/gcb.15118
- Marzini, Tasser, Wellstein, Albrich, Rammer, Mina 2025, Landscape Ecology 40 - 10.1007/s10980-025-02070-8
- Frei, Barbeito, Erdle, Leibold, Bebi 2023, Forests 14:412 - 10.3390/f14020412
- Lu, Zheng, Liang, Piao, Babst et al. 2025, NREE 6:489-502 - 10.1038/s43017-025-00703-9
- Huang, Wang, Bie et al. 2023, Forest Ecosystems 10:100106 - 10.1016/j.fecs.2023.100106
- Chen, Li, Camarero et al. 2024, J Plant Ecol 17 - 10.1093/jpe/rtae033
- Izworska, Muter, Matulewski, Zielonka 2023, Ecol Indic 148:110102 - 10.1016/j.ecolind.2023.110102
- Lévesque, Rigling, Bugmann, Weber, Brang 2014, AFM 197:1-12 - 10.1016/j.agrformet.2014.06.001
- Johnson & Yeakley 2019, Forests 10:864 - 10.3390/f10100864
- Charra-Vaskou, Charrier, Ganthaler et al. 2026, New Phytol 250:1492-1509 - 10.1111/nph.70926
- Baglioni, Morresi, Garbarino, Urbinati 2025, Biogeosciences 22:4349-4366 - 10.5194/bg-22-4349-2025
- Oberhuber 2004, Tree Physiol 24:291-301 - 10.1093/treephys/24.3.291
- Gruber, Zimmermann, Wieser, Oberhuber 2009, Ann For Sci 66:503 - 10.1051/forest/2009038
- Gruber, Baumgartner, Zimmermann, Oberhuber 2008/2009, Trees 23:623-635 - 10.1007/s00468-008-0307-7
- Wieser, Grams, Matyssek et al. 2015, Tree Physiol 35:279-288 - 10.1093/treephys/tpv009
- Gruber, Oberhuber, Wieser 2018, Front Plant Sci 9:711 - 10.3389/fpls.2018.00711
- Lopez-Saez, Corona, von Arx, Fonti et al. 2023, STOTEN 855:158605 - 10.1016/j.scitotenv.2022.158605
- Schuldt, Buras, Arend et al. 2020, Basic Appl Ecol 45:86-103 - 10.1016/j.baae.2020.04.003
- Senf & Seidl 2021, Nat Sustain 4:63-70 - 10.1038/s41893-020-00609-y
- Gehrig-Fasel, Guisan, Zimmermann 2007, J Veg Sci 18:571-582 - 10.1111/j.1654-1103.2007.tb02571.x
- Motta, Morales, Nola 2006, Ann For Sci 63:739-747 - 10.1051/forest:2006055
- Tasser & Tappeiner 2002, Appl Veg Sci 5:173-184 - 10.1111/j.1654-109x.2002.tb00547.x
- Tasser, Leitinger, Tappeiner 2017, Land Use Policy 60:60-72 - 10.1016/j.landusepol.2016.10.019
- Dirnböck, Dullinger, Grabherr 2003, J Biogeogr 30:401-417 - 10.1046/j.1365-2699.2003.00839.x
- Körner 2012 chapter "Treeline patterns" in Alpine Treelines - 10.1007/978-3-0348-0396-0_3 (book DOI not checked)
- Staffler et al. 2011 (Waldgrenzentwicklung, Geologische Bundesanstalt) - DOI UNVERIFIED, URL only
