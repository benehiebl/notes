---
title: "Literature review: distribution changes of evergreen broad-leaved species in Italy"
date: 2026-10-16
tags: [forest-ecology, remote-sensing, literature-review]
---

# Literature review: distribution changes of evergreen broad-leaved species in Italy

**Scope.** This report supports the paper idea in `03_papers/04_evergreen_distribution_change.md` (40 years of annual Landsat leaf-type (LTC) and dominant-tree-species (DTS) cover maps of Italy; trajectory and hotspot analysis; drivers temperature, drought, land use; future prediction). It synthesises five researcher notes (ecology; remote sensing; trajectory and uncertainty methods; Italian context, drivers and holm oak dieback; wiki and TRACEVE inventory). The researchers verified bibliographic metadata (CrossRef) for most papers, but mostly did NOT read abstracts or full texts. Every content statement therefore carries a verification tag (legend below). The TRACEVE proposal is a proposal, not evidence. Its reference list was used only as a source of candidate papers. No new web search was run for this synthesis; "not found" means "not found by the researchers' limited searches (CrossRef, OpenAlex, some web search)".

**Verification legend (applies to every paper in this report)**
- **[W]** = content taken from the user's own wiki note (not re-checked against the PDF here).
- **[A]** = researcher read an abstract or search snippet. Still check the full text before quoting numbers.
- **[M]** = researcher's memory or title-level only. Treat as "to verify against abstract before citing". Not an established fact.
- Metadata (authors, journal, volume, pages, DOI) was checked against CrossRef by the researchers unless marked "[meta unverified]".
- "NOT IN WIKI - add PDF" = no note in `01_notes/`.

---

## 1) Short answer: the 6-8 must-read papers

**Bottom line**
- Eight papers deserve a deep read. I would not pad beyond that.
- Three of them are the only papers that really address your two-sided story (expansion plus dieback) in Italy or a close analogue: Conedera 2018, Alessi 2019, Peñuelas & Boada 2003.
- Italy-specific, quantified evidence for evergreen broad-leaved (EVE) change is thin. Your own two wiki papers (Conedera 2018, Alessi 2019) are the strongest ecological anchors.
- On the remote-sensing and change side, the best analogues come from Canada and the US, not the Mediterranean.

**Selection logic**
- Ecology and drivers (4 papers): Conedera 2018, Alessi 2019, Peñuelas & Boada 2003, Garbarino 2020.
- Dieback and the "loss" side of the maps (1 paper): Pollastrini 2019.
- Remote sensing of evergreen change (1 paper): Atkins 2018.
- Trajectory, temporal consistency and uncertainty (2 papers): Hermosilla 2018, Olofsson 2014.
- Preference went to papers that are in the wiki, have an abstract-level check, or are well-known primary references.
- Two further primary references (Walther 2005 for the climate hypothesis; Kennedy 2010 for LandTrendr-style trajectories) are near misses. Read their abstracts and cite them, but a deep read is not required (section 3).
- Already in the wiki and to be re-read as notes, not new reads: [[bayle_2024_landsat_greening_inflated]] (observation-density artefact, central for your uncertainty section) and [[chastain_2007_eve_landsat_understory]] (leaf-off Landsat principle).

| Rank | Citation | Domain | Why read | Cite it for | Caveat | Verification |
|---|---|---|---|---|---|---|
| 1 | Conedera et al. 2018, Reg Environ Change 18:425-436, [[conedera_2018_drivers_evergreen]] | Ecology | Strongest causal paper on EVE spread. 200 plots around Lago Maggiore, tobit regression; propagule pressure (distance to garden) dominant for 3 of 4 species, winter temperature secondary [W] | Intro, Drivers, Discussion: "climate is permissive, not the trigger"; justification for land-use and proximity covariates | One region (southern Swiss Alps), 4 species (Hedera, Ilex, Prunus laurocerasus, Trachycarpus), cross-sectional; NOT Q. ilex. Proposal prints year 2017 (online) vs volume 18 (2018) | [W] |
| 2 | Alessi et al. 2019, J Veg Sci 30:564-574, [[alessi_2019_refugia]] | Ecology | Only Italy-wide EVE distribution analysis: 17,087 plots, 11 native laurophylls, most below 50 % of potential range, dispersal limitation from refugia [W] | Intro and Discussion: non-equilibrium, further expansion expected; future-habitat framing | Native laurophylls only (no sclerophylls such as Q. ilex); "potential range" depends on SDM assumptions. Wiki note says "<50 %", concept page says "9 of 11": check PDF | [W] |
| 3 | Peñuelas & Boada 2003, Glob Change Biol 9:131-140 (NOT IN WIKI - add PDF) | Ecology | Best peer-reviewed precedent for beech-to-holm-oak replacement. Abstract-level: 1945 vs present, beech up ~70 m, holm oak recruitment ~3x higher, beech recruitment ~41 % lower; cause warming plus cessation of traditional land management [A] | Intro and Discussion: biome-shift framing; precedent for the combined climate x abandonment driver | Single massif in NE Spain, not Italy; climate and abandonment confounded. Note conflict: ecology researcher labelled it [from memory], the Italy researcher read the abstract (Semantic Scholar). I use the abstract-level version, numbers still to check | [A] |
| 4 | Garbarino et al. 2020, Landscape Ecol 35:2679-2694 (NOT IN WIKI - add PDF) | Ecology / land use | Best Italian land-use driver paper: 8 Alpine + 8 Apennine sites, Corine over 28 yr plus aerial images over 58 yr; forest expansion dominant in both ranges, about 0.6 %/yr; distance to forest edge best predictor in the Alps, elevation in the Apennines [A, repository abstract snippet, full text not read] | Drivers: choice of covariates (elevation, distance to forest edge, former agricultural land); expected background forest-gain rate | All forest, no leaf-habit; 16 sites, not wall-to-wall. The 0.6 %/yr number is snippet-level: verify before quoting | [A] |
| 5 | Pollastrini et al. 2019, Front For Glob Change 2:74 (NOT IN WIKI - add PDF) | Ecology / dieback | Most direct Italian evidence for evergreen vs deciduous response to the 2017 drought and heat wave in Tuscany. Abstract-level: Q. ilex and Phillyrea latifolia had crown desiccation and branch dieback and only partly resprouted; deciduous species restored canopy in 2018 [A, OpenAlex abstract] | Intro and Discussion: dieback is real in Italy; "loss" in maps can be transient crown loss | Case study, not wall-to-wall. This is evidence for the loss side that the wiki has only via a preprint and a regional overview | [A] |
| 6 | Atkins, Epstein & Welsch 2018, Ecosphere 9(10):e02404 (NOT IN WIKI - add PDF; in TRACEVE list) | Remote sensing | Closest analogue to your design: snow-free leaf-off Landsat 5 surface reflectance 1986-2011 plus Random Forest to map evergreen understory shrub expansion vs landscape position [A, search summary] | Intro and Methods: multi-decadal leaf-off Landsat can track evergreen expansion; Discussion: accuracy of early years | Small Appalachian watershed, North America, native rhododendron / mountain laurel. Check how training data and accuracy are handled across years | [A] |
| 7 | Hermosilla et al. 2018, Can J Remote Sens 44(1):67-87 (NOT IN WIKI - add PDF) | Trajectory / RS | Annual Landsat land-cover maps informed by detected disturbance to avoid illogical class flips; the nearest published design to annual LTC/DTS maps [M, background] | Methods: temporal consistency of annual maps; Discussion: limits for gradual change | Rule-based post-processing against disturbance may suppress exactly the slow EVE encroachment you want to measure. Canada, not Mediterranean. Content not yet verified: read the abstract first. For Hermosilla et al. 2024 (national tree-species dynamics, title-level only) see section 3 | [M] |
| 8 | Olofsson et al. 2014, Remote Sens Environ 148:42-57 (NOT IN WIKI - add PDF) | Trajectory / uncertainty | The standard for area-adjusted change estimates with confidence intervals from a probability sample of reference data (stratified estimation, response design). Well-known primary reference [M for details, but the content is the field standard] | Methods and Discussion: any statement like "EVE expanded by X ha" needs adjusted areas; pixel counting is biased | Independent reference data for 1985-2005 will be hard to get (INFC plots only partly, large errors by forest type); reviewers will ask this | [M] |

**Honest limits of this shortlist**
- Only 3 of the 8 (Conedera, Alessi, and by wiki note nothing else) are in the wiki. Five need PDFs.
- Ranks 7 and 8 are well-known method papers, but the researchers did not re-read them. Skim the abstract before citing.
- No study maps Mediterranean EVE change with multi-decadal Landsat, so no paper in this list is a direct methodological twin.

---

## 2) Where the literature stands per theme

### 2.1 Ecology and drivers of EVE spread

**What is established (at abstract or wiki-note level)**
- The "laurophyllisation" narrative rests on a small Ticino / Insubria cluster (Walther, Carraro, Klötzli, Gianoni, Berger, Conedera). Much of it is grey literature (book chapters, 1988 ETH reports) that is hard to obtain. The researchers could not find or verify Gianoni et al. 1988 and Klötzli & Walther 1999 in CrossRef [unverified].
- Climate hypothesis: winter-minimum temperature limits evergreens, warming relaxes this limit (Walther 2002, 2005) [M]. Origin of the hypothesis; correlational.
- Counter-evidence in your wiki: propagule pressure and land-use legacy matter more than winter temperature for three of four species ([[conedera_2018_drivers_evergreen]]) [W]. Species partition by precipitation and bedrock across Insubria ([[berger_2006_distribution_eve]]), based on 22 targeted sites [W].
- Non-equilibrium: native Italian laurophylls occupy less than half of their potential range, so more spread is plausible ([[alessi_2019_refugia]]) [W].
- Italian field evidence for ongoing expansion of one species: Laurus nobilis in 16 central Italian sites; stable and dynamic population structures read as expansion; linked to forest cover and age after rural abandonment; ungulate browsing associated with declining structures (Alessi et al. 2021) [A, abstract snippet].
- Biome-shift precedent in the Mediterranean: Montseny, beech replaced by holm oak, attributed to warming plus cessation of land management (Peñuelas & Boada 2003) [A].
- Northern-margin Q. ilex colonisation (Atlantic France; Delzon et al. 2013) [M, numbers not re-checked]. Two-sided counterpoint: aridity reduces Q. ilex regeneration at its dry edge in Spain (Garcia-Fayos et al. 2020) [A, snippet].

**What is weak**
- No quantified, spatially explicit EVE expansion rate for Italy was verified by any researcher. The only expansion-rate numbers (0.6 %/yr; +78 % forest in the Apennines) are for ALL forest, not EVE.
- CO2 as a driver (Niinemets et al. 2011, in TRACEVE list) is untested for EVEs in the wiki; treat it as a hypothesis, not a result.
- "Evergreen broad-leaved" mixes very different groups: native sclerophylls (Q. ilex, Q. suber, Phillyrea), native laurophylls (Laurus, Ilex, Buxus, Viburnum tinus), and alien species (Prunus laurocerasus, Trachycarpus, Ligustrum lucidum, Cinnamomum). Their drivers differ (Conedera's drivers concern the alien-rich Swiss group; Alessi's concern natives). The 30 m maps probably cannot separate them reliably in all areas, so driver claims must be stratified by group.

### 2.2 Remote sensing of evergreen, leaf type and species cover

- The wiki is strong on Sentinel-2 tree species mapping ([[hemmerling_2021_forest_mapping_s2]], [[kollert_2021_tree_species]], [[blickensdoerfer_2024_tree_species]]) but these are temperate / central European, deciduous-vs-conifer products [W]. None has Mediterranean EVE classes or multi-decadal change; this supports a gap statement.
- Leaf-off or winter imagery for evergreen understory: [[chastain_2007_eve_landsat_understory]] (OA above 80 %, best 87.1 %) [W]; Resasco et al. 2007 (late-fall Landsat separates Amur honeysuckle, a late-leaf-retaining shrub; not truly evergreen) [A, snippet]; Wang et al. 2009 (winter image best for understory bamboo) [A, summary]; Atkins 2018 (rank 6).
- Mediterranean evidence that multi-seasonal Landsat is needed to separate cover classes: Senf et al. 2015 (Portugal) [M].
- Europe-wide benchmark product: Bonannella et al. 2022 (30 m, modelled potential and realised distributions of European tree species 2000-2020, including Mediterranean species) [M]; the only multi-year product covering Italian EVEs the researcher knows of. Compare against it.
- No Landsat or Sentinel-2 mapping paper for Prunus laurocerasus, Hedera or Chinese privet was found. Italian-language and forestry journals (Forest@, iForest, L'Italia Forestale e Montana) were not searched.
- Own prior work: [[hiebl_2025_pretraining]] (EVE cover from Sentinel-2 with pretraining and deep-ensemble uncertainty) [W]. Note that taxonomic diversity was the strongest error driver there [W], which matters for hindcasting into Landsat years.

### 2.3 Time-series change, trajectories and uncertainty

- **Algorithms.** LandTrendr (Kennedy et al. 2010), CCDC (Zhu & Woodcock 2014) and BFAST (Verbesselt et al. 2010) are built for spectral pixel series, not classified annual maps [M]. They can be applied to a per-pixel cover-fraction series (inference by the trajectory researcher), but then the input is a model output with its own error.
- **Algorithm choice changes the result.** Cohen et al. 2017 (different algorithms give notably different disturbance maps) and Pasquarella et al. 2022 (LandTrendr vs CCDC) [M]: plan a sensitivity test.
- **Temporal consistency of annual maps.** Hermosilla 2018 (disturbance-informed labels) [M]; hidden Markov model smoothing by Abercrombie & Friedl 2016 and Bogaert et al. 2022 [M]. Independent yearly classifications create flip-flops that inflate gross change. A hidden Markov model used for smoothing is not the same thing as one used for forecasting; keep them apart in the paper.
- **Change area with uncertainty.** Olofsson 2013 / 2014; Pontius & Lippitt 2006 ("can error explain map differences over time?") [M]. Intensity analysis (Aldwaik & Pontius 2012) fits the question "does evergreen gain target specific deciduous classes?" [M].
- **Trend tests.** Mann-Kendall / Sen slope assume monotonic change and are over-optimistic under autocorrelation (Hamed & Rao 1998; Yue et al. 2002) [M]. A dieback followed by resprouting is not monotonic, so segmented trajectories are the better description.
- **Observation-density artefact.** [[bayle_2024_landsat_greening_inflated]]: up to 50 % of Landsat greening above 2400 m can be a sampling-bias artefact [W]. Alpine, summer maxNDVI; transfer to a winter-dependent EVE signal in Italy is an inference. Tolnai et al. 2016 (Landsat observation density over Europe; in TRACEVE list, not read) would be the primary data source for checking it.
- **Sensor continuity.** Roy et al. 2016 (L7 to L8 NDVI continuity), Crawford et al. 2023 (Collection 2) [M]. These do not cover TM-to-ETM+ in detail, and none quantifies the residual effect on classifier output.
- **Gap.** No paper was found on error propagation specific to annual species-dominance maps over 40 years with changing sensors. Bell et al. 2024 on hindcasting forest structure ([[bell_2024_hindcasting_forest_structure]], hindcast models perform comparably to full models, with spatially structured differences [W]) is the nearest.

### 2.4 Italian context: land use, drought and holm oak dieback

**Land use**
- Post-war forest expansion on abandoned land is well documented (Garbarino 2020; Malandra et al. 2018 meta-analysis of 51 manuscripts / 57 case studies, +78 % forest and -49 % cropland [A, OpenAlex abstract, partly truncated]; Falcucci et al. 2007, forest increase 1960-2000 [A, summary]). [[gasparini_2022_nfi_italy]]: 10.98 Mha forest, about +520,000 ha vs INFC2005 [W].
- None of these separates evergreen from deciduous gain. This is the novelty space.
- INFC change is reliable nationally but noisy by forest type (large standard errors, per the chapter abstract [A]). Do not treat INFC as strict ground truth for evergreen-oak trends.

**Drought and dieback**
- Q. ilex dieback in Italy: Tuscany 2012 and 2017 (Pollastrini 2019 [A]; Alderotti et al. 2023 [A]), Apulia (Phytophthora cinnamomi, Frisullo et al. 2018 [A]), Sardinia 2024 (Satta et al. 2025 preprint). National overview: [[seddaiu_2025_quercus_dieback]] (perspective paper, extent poorly quantified [W]).
- **Patchiness and recovery:** two nearby stands can differ strongly (Alderotti 2023, n = 2 stands, so "genetically determined" overreaches; reviewer's reading from the abstract). Holm oak often resprouts (Lloret et al. 2004: after the 1994 drought up to 76 % of trees showed complete canopy dieback, resprouting extensive [A]). So Landsat "loss" can be non-lethal.
- **Not a uniform national decline:** Bussotti et al. 2021 (ICP Forests, 24 yr, 253 plots) found Quercus species showing progressively decreasing defoliation overall, with more extremely defoliated and dead trees nationally [A]. This is a nuance against assuming a holm-oak collapse everywhere.
- **Preprint warning:** Satta et al. 2025 ([[seddaiu_2025_mediterranean_dieback]]) is an **SSRN preprint, not peer reviewed**. Per the wiki note, Sentinel-2 change Aug 2023 to Aug 2024, about 110,400 ha dieback in Sardinia, 12-month SPI the main predictor (AUC 0.95) [W]. No journal version was found as of the researchers' search. Cite only as "preprint".
- [[puletti_2019_drought_forest_health]]: 118 Tuscan plots, Sentinel-2; unhealthy holm oak showed lasting NDVI reduction after 2017 [W]. A short letter with a small sample.
- No peer-reviewed quantification of 2022 Italian holm-oak mortality was found.

**Climate data**
- Brunetti et al. 2006 (about 1 K per century warming, series ends about 2000) [A]. Weak spot: no verified Italy-wide SPEI drought-trend paper and no verified paper on Italian winter-minimum warming (the driver most relevant for evergreen spread).
- SPEI preferred over SPI for temperature-driven drought: Mombrini et al. 2025 (NW Italy) and Vicente-Serrano et al. 2014 (Iberia) [A]. Compound hot-dry events: Gazol & Camarero 2022 (46 % of 310 mortality events coincided with hot summers plus dry years [A]).

### 2.5 Space-for-time and prediction

- The planned "hidden Markov" forecast has no verified precedent for forest species-dominance transitions with climate covariates. The best methodological anchor is Balzter 2000 (non-stationary, covariate-dependent Markov chains for vegetation) [M].
- Markov models are stationary and memoryless; the 40-year transitions contain abandonment-driven expansion and dieback, which will not repeat unchanged.
- Space-for-time substitution is contested: Blois et al. 2013 (works for some responses, fails under no-analogue climates and lags) and Damgaard 2019 (requires equilibrium) [M]. Alessi 2019 already shows EVEs are out of equilibrium, which is exactly what weakens a space-for-time forecast. SDM caveats: Elith & Leathwick 2009 [M].
- Practical consequence: use time-for-time modelling (fit on 1985-2005, predict 2006-2024 as hindcast) and present any space-for-time projection as a sensitivity run.

---

## 3) Additional citeable papers (not deep-dive reads)

Format: paper, status tag, section where it fits. Full references in section 7.

### Ecology and drivers
- Walther, Berger & Sykes 2005, Proc R Soc B, "ecological footprint of climate change" [M]. Intro: origin of the climate hypothesis (read the abstract; candidate for a deep read).
- Walther 2002, Folia Geobot [M]; in TRACEVE. Intro: relaxed frost limit, biome shift. NOT IN WIKI - add PDF.
- Walther et al. 2007, Global Ecol Biogeogr, palms tracking climate change [M]. Intro: thermal limits of alien EVEs.
- Carraro, Gianoni & Mossi 1999, book chapter [M]. Intro: observational baseline; page ranges differ between notes (see section 6). Only if retrievable.
- Alessi et al. 2021, Rend Lincei, Laurus nobilis population structure [A]. Intro and Discussion: Italian field evidence for expansion and the abandonment link.
- Delzon et al. 2013, PLoS ONE, Q. ilex at its northern margin [M]. Intro: poleward spread.
- Garcia-Fayos et al. 2020, PLoS ONE, aridity and Q. ilex regeneration [A, snippet]. Discussion: two-sided picture (gain at cool edge, decline at dry edge).
- Carnicer et al. 2011, PNAS, crown condition decline and drought mortality in southern Europe [A for the 1987-2007 defoliation statement from the Italy note; the ecology note's claim about pests is [M]]. Discussion.
- Palmero-Iniesta et al. 2021, Eur J For Res [M]. Intro: Europe-wide abandonment-driven expansion (coarse, Corine-based).
- Bertrand et al. 2011, Nature, thermophilization lag [M]. Discussion: lag and non-equilibrium (understorey herbs in France; not EVEs).
- Zellweger et al. 2020, Science 368:772-775, forest microclimate [M]. Discussion: canopy buffering. Note the TRACEVE list cites only the Response to Comment (Science 370); cite the original.
- Hickler et al. 2012, Global Ecol Biogeogr, LPJ-GUESS vegetation zones [M]. Discussion: future projections, CO2.
- Niinemets, Flexas & Peñuelas 2011, TREE, evergreens favoured by CO2 [M; metadata as printed in TRACEVE, not CrossRef-checked]. Discussion: CO2 hypothesis.
- Grund et al. 2005, Basic Appl Ecol, fire and EVE invasion [M; metadata as printed in TRACEVE]. Intro, optional.
- Rusterholz et al. 2018 and Abrahamczyk et al. 2024, Prunus laurocerasus consequences and naturalisation [A, snippets]. Intro: alien EVE spread is pan-European.
- Buitenwerf et al. 2018, Glob Change Biol, woody regrowth in European semi-natural vegetation [M; metadata as printed in TRACEVE]. Drivers.
- Hernández et al. 2017, Eur J For Res, range shifts across a bioclimatic transition [M; as printed in TRACEVE]. Intro, optional.
- Wiki papers to cite as they are: [[berger_2006_distribution_eve]] (Intro, Drivers; read once), [[chelli_2017_climate]] (Intro; gap on Mediterranean community change), [[herraiz_2025_phen_shifts_mediterranean]] (Drivers; closest Landsat-trend precedent for Mediterranean evergreens; Spanish NFI plots, NDVI not cover), [[midolo_2026_denser_vegetation]] (Drivers; canopy-closure / eutrophication alternative), [[francioni_2026_canopy_closure]] (Drivers; Italian ICP Forests plots), [[noce_2023_altitude_shift_tree_italy]] (Discussion; 20 major species, not EVEs), [[calvia_2022_pines]] (Discussion; Sardinian abandonment precedent).

### Remote sensing
- Pasquarella, Holden & Woodcock 2018, RSE, spectral-temporal features for forest type [M]. Methods: justification of time-series features for leaf-type separation.
- Senf et al. 2015, RSE, Mediterranean land cover with multi-seasonal Landsat [M]. Methods / Intro.
- Hermosilla et al. 2024, For Ecol Manage 572:122313, annual Landsat tree-species dynamics in Canada [M, title-level only]. Intro and Methods: read the abstract; likely the closest analogue for species. Candidate for a deep read once checked.
- Thapa et al. 2020, Int J Remote Sens, reconstructing past composition from archived Landsat plus NFI [M, title-level]. Methods: back-casting; check accuracy decay into early years.
- Bonannella et al. 2022, PeerJ [M]. Discussion: benchmark product.
- Roy et al. 2016, RSE (sensor continuity); Crawford et al. 2023, Sci Remote Sens (Collection 2); Wulder et al. 2016, RSE (global Landsat archive; TRACEVE list); Tolnai et al. 2016, J Maps (observation density; TRACEVE list) [M]. Methods and Limitations.
- Claverie et al. 2018, RSE (HLS) and Wulder et al. 2021, Sci Remote Sens (spectral correspondence for extending Landsat with HLS) [M]. Methods / Outlook for the recent end of the series.
- Resasco et al. 2007, Int J Remote Sens [A]; Wang et al. 2009, PERS [A]. Introduction: phenological-offset principle.
- Francini et al. 2024, Int J Appl Earth Obs Geoinf 131:103935 [M, title-level; study area unverified]. Methods: NFI-calibrated area proportions.
- Gomez, White & Wulder 2016, ISPRS J (time-series classification review) [M]. Intro (overview).
- Zhu & Woodcock 2014, RSE (CCDC) [M]. Methods: alternative approach.
- Oreti et al. 2020, Biodiv Conserv, very high resolution leaf-off imagery for Taxus and Ilex in Italian beech forests [A, title]. Intro: leaf-off principle in Italy (not Landsat).
- Fassnacht et al. 2016, RSE, tree species classification review (TRACEVE list) [M]. Intro.
- Wiki papers: [[chastain_2007_eve_landsat_understory]], [[pflugmacher_2019_lulc_landsat]] (3-year pooling of spectral-temporal metrics, OA 75.1 % [W]; Methods), [[turubanove_2023_canopy_landsat]] (Methods; forest mask), [[soto_2025_disturbance]] (annual Landsat disturbance atlas 1985-2023; Methods: mask and explain loss pixels), [[senf_2021_disturbance]] (Intro), [[mattioli_2025_carta_forestale]] (forest mask / validation baseline), [[menegaldo_2025_landsat_treeline_dynamics]] (Landsat plus RF change validated against orthophoto), [[tong_2023_forest_densification_china]] (annual Landsat probability maps 1986-2018).

### Time-series change and trajectories
- Kennedy, Yang & Cohen 2010, RSE (LandTrendr) [M]. Methods: trajectory segments. Near miss for the must-read list.
- Kennedy et al. 2014, Front Ecol Environ, ecological view of change [M]. Intro / Methods: trajectories (abrupt, gradual, recovery) rather than two-date differences.
- Kennedy et al. 2018, Remote Sens (LandTrendr on GEE) [M]. Methods.
- Pasquarella et al. 2022, Int J Appl Earth Obs Geoinf (LandTrendr vs CCDC) and Cohen et al. 2017, Forests (algorithm disagreement) [M]. Methods: sensitivity test.
- Zhu 2017, ISPRS J (review) and Woodcock et al. 2020, RSE (monitoring paradigm) [M]. Intro.
- Verbesselt et al. 2010, RSE (BFAST) [M]. Methods, optional.
- Song et al. 2018, Nature (global land change 1982-2016; fractional cover with sample-based area estimation) [M; in TRACEVE list]. Intro and Methods.
- Olofsson et al. 2013, RSE (stratified estimation) and Stehman & Foody 2019, RSE (accuracy assessment issues) [M]. Methods.
- Pontius & Lippitt 2006, CaGIS; Pontius, Shusas & McEachern 2004, Agric Ecosyst Environ (gross vs net change, persistence); Aldwaik & Pontius 2012, Landsc Urban Plan (intensity analysis) [M]. Methods: transition analysis for categorical maps.
- Abercrombie & Friedl 2016, IEEE TGRS and Bogaert et al. 2022, IEEE TGRS (hidden Markov models for annual maps) [M; given names and article number of Bogaert unverified]. Methods: temporal consistency. Gong et al. 2017 (ISPRS Int J Geo-Inf 6:292) [M; given names unverified]: optional.
- Hamed & Rao 1998, J Hydrol; Yue et al. 2002, Hydrol Process; Neeti & Eastman 2011, Trans GIS [M]. Methods: trend tests under autocorrelation. Sen 1968 and Mann 1945 only if those tests are used. Getis & Ord 1992 for hotspots [M].
- Dormann et al. 2007, Ecography and Beale et al. 2010, Ecol Lett (spatial autocorrelation in driver regression) [M]. Methods / Drivers.
- [[bayle_2024_landsat_greening_inflated]] [W] and [[bell_2024_hindcasting_forest_structure]] [W]: see 2.3.

### Italian context, land use, drought and dieback
- Falcucci et al. 2007, Landsc Ecol (LULC 1960-2000) [A]. Intro / Drivers.
- Malandra et al. 2019, Reg Environ Change (Apennines drivers) [A, results not read] and Malandra et al. 2018, Forests (meta-analysis) [A]. Drivers.
- Gasparini & Tabacchi 2022 chapter, INFC2005 vs INFC2015 [A]. Intro / Drivers: change in forest area and its standard errors. The book is in the wiki ([[gasparini_2022_nfi_italy]]), this chapter is not separately noted.
- Alderotti et al. 2023, Sci Total Environ [A]; Alderotti et al. 2025, Tree Physiol [A] (40-50 % loss of hydraulic conductivity in defoliated Q. ilex; explains why canopy loss precedes mortality); Bussotti et al. 2021, Forests [A]; Gentilesca et al. 2017, iForest [A] (mostly deciduous oaks); Frisullo et al. 2018, Forest Sci [A] (pathogen confounding); Colangelo et al. 2018, Front Plant Sci [A] (deciduous oaks, NOT holm oak; the decline of the deciduous matrix); Lloret et al. 2004, Glob Change Biol [A]. All Discussion.
- Brunetti et al. 2006, Int J Climatol [A]; Vicente-Serrano et al. 2014, Environ Res Lett [A]; Gazol & Camarero 2022, Sci Total Environ [A]; Mombrini et al. 2025, HESS [A]; Giorgi & Lionello 2008, Glob Planet Change (TRACEVE list, not read) [M]. Drivers.
- Malavasi et al. 2018, Reg Environ Change, reforestation trajectory analysis in Mediterranean mountains [M, abstract not read]. Methods: only if the trajectory framing is useful.
- Wiki: [[seddaiu_2025_quercus_dieback]] [W], [[seddaiu_2025_mediterranean_dieback]] (**preprint**) [W], [[puletti_2019_drought_forest_health]] [W], [[alessi_2023_sampling_approaches]] (preferential vs probabilistic plots; relevant to training and reference data bias) [W].

### Space-for-time and prediction
- Balzter 2000, Ecol Model [M]; Blois et al. 2013, PNAS [M]; Damgaard 2019, TREE [M]; Elith & Leathwick 2009, Annu Rev Ecol Evol Syst [M]. Methods / Discussion for the prediction part.

---

## 4) Papers considered and rejected

**Rejected for this paper (with reason)**
- Genazzi et al. 2022 (Geogr Helv): social perceptions of Trachycarpus, not ecology.
- Sitzia et al. 2018 (Sci Rep): Robinia (deciduous) in abandoned fields.
- Ohlemüller et al. 2006 (Glob Change Biol): too general (woody species climate risk).
- Fujiwara & Box 1999 chapter: Japan and eastern North America; hard to access. Mazzoleni & Spada 1992: two-page abstract. Barberis et al. 1992 and other 1992 "Quercus ilex ecosystems" chapters: old, about Liguria notes, not expansion trends [relevance unverified].
- Cavin & Jump 2016/17, Kunz 2018, Martin-StPaul 2011: drought physiology and growth, not distribution change.
- Fehr & Burga 2016 (Palms 60:125-136): trade journal of the International Palm Society; title and metadata unverified. Use only if no better source for Trachycarpus spread.
- Peñuelas et al. 2007 (Ecography): redundant if Peñuelas & Boada 2003 is cited.
- Lenoir et al. 2008 and Vitasse et al. 2021 (elevation shifts): no EVEs, marginal.
- Persson 2018, Hoscilo & Lewandowska 2019, Immitzer 2016, Welle 2022, Grabska 2019/2020: regional tree-species maps, redundant with the wiki's Hemmerling / Blickensdörfer. Ottosen 2020: tree cover only. Melaas 2013, Zhang 2018, Hermosilla 2016: marginal. Singh & Gray 2020: urban North Carolina, optional at best.
- Hansen 2013 as a main reference (2000-2012, binary loss/gain); cite only as a benchmark if needed. Lu 2004 (dated). Pettorelli 2005 (NDVI ecology). Fukami & Wardle 2005. Verbesselt 2012 (near-real-time). CA-Markov and ANN land-use forecasting case studies (Choudhary 2025, Kusratmoko 2017): methodologically weak, not read.
- CABI compendium entries, Faculty Opinions entries, bioRxiv duplicates, conference abstracts (EGU, IECPS), press reports: not citable primary sources.
- Colangelo et al. 2025 (vessel features, ring-porous oaks), Pasquini 2023 (BVOC), Recanatesi 2018 (single peri-urban site), Früchtenicht 2018, North African dieback papers, Chauchard 2007 / San Roman Sanz 2013 (French Mediterranean abandonment): off-scope.
- Dahlin 2012/2014: found, but about Santa Cruz Island biomass, not the evergreen mapping paper the user had in mind. The intended paper was not found.
- TRACEVE-only items not relevant: Bae 2019, Kacic 2021, Rocchini 2018, Rocha & Shaver 2009, Camps-Valls 2021, Cavender-Bares 2022, Gillespie 2008, Pereira 2013, Niederheiser 2021, Norberg 2019, Belgiu 2016, Pal 2005; data and policy documents (EEA, COM, CORINE, HII) unless used.
- Unverifiable and not to be cited: "Hobbs" (Chinese privet remote sensing), "Hernández / Peñuelas Mediterranization" paper by that name, Hofgaard (no relevant match), Gianoni 1988 / Klötzli & Walther 1999 (not in CrossRef), an unidentified web hit claiming increasing sclerophyllous oak share in Apennine oak woods, a Holocene Tuscany evergreen-oak paper (J Biogeography 2009, not identified).

**Not worth a deep read even though verified to exist**
- Wulder et al. 2022 (Fifty years of Landsat): general citation only.
- Hemmerling / Kollert / Grabska (temperate species mapping): cite, do not study.
- Walther 2007 palms, Metcalfe 2005 (Hedera monograph): background only.

---

## 5) Gaps and implications for the paper

**Novelty claims the search supports (with honest limits)**
- Claim A: no wall-to-wall, multi-decadal, 30 m quantification of EVE (or Q. ilex) change in Italy was found. Limit: absence of evidence from a limited search (CrossRef, OpenAlex, some web). Italian-language journals and Google Scholar were not searched. Run a targeted search before the claim goes into the abstract; the nearest products are Bonannella et al. 2022 (modelled distributions) and Alessi 2019 (SDM potential).
- Claim B: no Italian study separates evergreen from deciduous forest gain after abandonment. Limit: same search caveat. This is supported by the land-use literature (Garbarino, Malandra, Falcucci) being all-forest.
- Claim C: no verified precedent for a climate-covariate Markov / hidden Markov forecast of species-dominance transitions. Limit: only Balzter 2000 as a methodological anchor.
- Do NOT claim novelty for "Landsat can map evergreen change": Atkins 2018 and Chastain 2007 show the principle exists, though in other biomes and for understory shrubs.

**Tensions to handle explicitly in the text**
1. **Climate-permissive vs land-use-proximate drivers.** Your draft intro says "drivers (milder winters etc.)". The wiki evidence (Conedera, Alessi, Berger) says climate is permissive and propagule pressure, stand maturity and abandonment are proximate. Warming and abandonment are collinear since about 1950, so a correlation design with temperature, drought and land use cannot separate them without explicit land-use covariates (inference by the ecology researcher). Report effect sizes with spatial-autocorrelation-aware models; state that correlation is not causation.
2. **Holm oak dieback as a counter-trend, and what "loss" means.** Dieback is crown loss that often recovers by resprouting (Lloret 2004, Pollastrini 2019). Maps may record transient loss, conversion to shrub, or harvest. Use a disturbance mask ([[soto_2025_disturbance]]) and persistence rules. The loss side currently rests on one overview, one letter and one preprint in the wiki; the new papers above strengthen this. Also: your draft says "dieback of Q. ilex in other areas"; Italian dieback is documented (Tuscany, Apulia, Sardinia), so reword.
3. **Space-for-time.** Alessi 2019 shows non-equilibrium; Blois 2013 and Damgaard 2019 [M] warn that space-for-time fails then. Prefer time-for-time with hindcast validation; show space-for-time as sensitivity only.
4. **Landsat consistency.** Observation density, sensor differences (TM, ETM+, OLI) and training-data transfer into the 1980s all create spurious trends. [[bayle_2024_landsat_greening_inflated]] shows the issue for alpine summer NDVI; transfer to winter-dependent EVE classification is unproven (inference). Mitigate with observation-count covariates, harmonisation (Roy 2016, Crawford 2023), and temporal-consistency filtering. Hermosilla-type rules can erase real slow change; test both.
5. **Area-adjusted change estimation.** Annual-map differencing is dominated by classification error unless corrected (Olofsson 2014, Pontius & Lippitt 2006 [M]). Independent reference data for 1985-2005 is the bottleneck; INFC plots have large errors by forest type; the preferential nature of vegetation plots is a known bias ([[alessi_2023_sampling_approaches]]). Plan a reference-sample design now, or limit claims to relative patterns and report map-based trends as indicative.
6. **Heterogeneous target class.** Sclerophylls, laurophylls and aliens differ in drivers and spectral behaviour. Understory EVEs under deciduous canopy are hard to detect (Chastain 2007 principle needs leaf-off imagery). Expect underestimation of understory spread: the maps may show canopy-level change only.
7. **Other biases.** Preferential training plots, pixel mixing at 30 m, and drought response of deciduous oaks (Colangelo 2018) can raise the evergreen share without any evergreen spread.

---

## 6) Wiki housekeeping found

**Inconsistencies spotted by the inventory researcher**
- `alessi_2019_refugia`: note says most of 11 laurophylls occupy "<50 %" of potential range, concept page says "9 of 11". Check PDF.
- `conedera_2018_drivers_evergreen`: TRACEVE prints year 2017 (online) with Reg Environ Change 18:425-436 (2018). Cite as 2018.
- `albrich_2019_climate_change_mountain_forests` and `albrich_2020_transitions_mountain_forests`: appear to describe the same paper (same title, different years). Merge or fix.
- `seddaiu_2025_mediterranean_dieback`: first author is Satta et al., SSRN preprint; consider renaming the citekey (e.g. `satta_2025_dieback_preprint`) and flag as not peer reviewed.
- `wessely_2023_tree_species_bottleneck`: filename 2023, publication 2024 (Nat Ecol Evol 8:1109-1117).
- `senf_2021_disturbance`: no volume or DOI in note (Nat Sustain 4(1):63-70, DOI 10.1038/s41893-020-00609-y per CrossRef, from the trajectory researcher). Several other notes lack DOIs (Kollert 2021, Hemmerling 2021, Chelli 2017, Conedera, Blickensdörfer, Turubanova, Fady, Dyderski, Francioni).
- `chastain_2007_eve_landsat_understory`: CrossRef title reads "Landsat ETM" (no "+"); check wording.
- Filename mismatches between PDFs in `00_literature/` and notes (kattenborn_2021, Sze_2017, yuan_2025, xu_2022; `blickensdörfer`/`grünig` umlauts): matters for BibTeX export.
- `fischer_2025_glocal_canopy_atlas` and `sattstools` have notes but no PDF. `disskonzept.pdf` has no note.
- Unchecked stretches in `03_tree_species_cover_landsat.md`: [[noce_2023_altitude_shift_tree_italy]] cited for "EVE favoured by milder winters/drought" (note is about 20 major species, not EVEs); schuldt_2020 for Italian deciduous pressure; albrich_2019 for climate-space velocity; herraiz_2025 for Q. ilex greening. Re-check before reuse.
- Conflicts between researcher notes resolved here: (a) Peñuelas & Boada 2003 content: ecology note [M] vs Italy note [A]; used [A] with numbers to verify. (b) Carraro et al. 1999 page range: ecology note says pp. 31-51 (CrossRef-verified chapter), TRACEVE prints pp. 69-84, and TRACEVE lists Klötzli & Walther 1999 at pp. 15-29. Page ranges unresolved: check on the publisher page. (c) Carnicer et al. 2011: ecology note says Catalan inventory with pest amplification [M], Italy note says defoliation increase 1987-2007 in southern European forests [A]; both can hold, but check the abstract (the Catalan claim is the less certain one). (d) Garbarino 2020: "web snippet" in both notes; same status. (e) Walther 2002: ecology note [M], Italy note says abstract not read; both unverified.
- Zellweger and Forzieri entries in TRACEVE cite the "Response to Comment" items, not the primary papers; cite primary papers. Bolton 2020 author names are garbled in the scan; verify.

**Wiki gaps**
- No note on Walther 2002/2005 (original framing), Delzon 2013, Hernández 2017, Peñuelas & Boada 2003, Falcucci 2007, Palmero-Iniesta 2021, any trajectory-method paper (LandTrendr, CCDC, HMM, Mann-Kendall), Landsat Collection 2 / harmonisation, or CHELSA / SPEI driver data.
- Concept pages worth creating: `landsat_time_series_change_detection`, `area_adjusted_change_estimation`, `space_for_time_substitution`, `land_abandonment_italy`.

**PDFs to add to `00_literature/` (priority order)**
1. Peñuelas & Boada 2003; 2. Garbarino et al. 2020; 3. Pollastrini et al. 2019; 4. Atkins et al. 2018; 5. Hermosilla et al. 2018 (and 2024); 6. Olofsson et al. 2014; 7. Walther et al. 2005 and Walther 2002; 8. Kennedy et al. 2010; 9. Alessi et al. 2021 (Laurus); 10. Falcucci 2007; 11. Bonannella 2022; 12. Roy 2016 and Crawford 2023; 13. Bussotti 2021, Alderotti 2023, Lloret 2004; 14. Gasparini & Tabacchi 2022 chapter. The remaining section 3 items can be added as the corresponding sections are drafted.

---

## 7) Full reference list

Tags: [W] wiki note exists (cite with wikilink); [NW] NOT IN WIKI - add PDF. "DOI not in note" means the wiki note gives no DOI. Metadata CrossRef-verified by the researchers unless noted.

### Section 1 papers
1. Conedera, M., Wohlgemuth, T., Tanadini, M., Pezzatti, G.B. (2018). Drivers of broadleaved evergreen species spread into deciduous forests in the southern Swiss Alps. Regional Environmental Change 18: 425-436. DOI 10.1007/s10113-017-1212-7. [W] [[conedera_2018_drivers_evergreen]]
2. Alessi, N., Tesitel, J., Zerbe, S., Spada, F., Agrillo, E., Wellstein, C. (2019). Ancient refugia and present-day habitat suitability of native laurophylls in Italy. Journal of Vegetation Science 30: 564-574. DOI 10.1111/jvs.12743. [W] [[alessi_2019_refugia]]
3. Peñuelas, J., Boada, M. (2003). A global change-induced biome shift in the Montseny mountains (NE Spain). Global Change Biology 9(2): 131-140. DOI 10.1046/j.1365-2486.2003.00566.x. [NW]
4. Garbarino, M., Morresi, D., Urbinati, C., Malandra, F., Motta, R., Sibona, E.M., Vitali, A., Weisberg, P.J. (2020). Contrasting land use legacy effects on forest landscape dynamics in the Italian Alps and the Apennines. Landscape Ecology 35(12): 2679-2694. DOI 10.1007/s10980-020-01013-9. [NW]
5. Pollastrini, M., Puletti, N., Selvi, F., Iacopetti, G., Bussotti, F. (2019). Widespread crown defoliation after a drought and heat wave in the forests of Tuscany (Central Italy) and their recovery - a case study from summer 2017. Frontiers in Forests and Global Change 2: 74. DOI 10.3389/ffgc.2019.00074. [NW]
6. Atkins, J.W., Epstein, H.E., Welsch, D.L. (2018). Using Landsat imagery to map understory shrub expansion relative to landscape position in a mid-Appalachian watershed. Ecosphere 9(10): e02404. DOI 10.1002/ecs2.2404. [NW]
7. Hermosilla, T., Wulder, M.A., White, J.C., Coops, N.C., Hobart, G.W. (2018). Disturbance-informed annual land cover classification maps of Canada's forested ecosystems for a 29-year Landsat time series. Canadian Journal of Remote Sensing 44(1): 67-87. DOI 10.1080/07038992.2018.1437719. [NW]
8. Olofsson, P., Foody, G.M., Herold, M., Stehman, S.V., Woodcock, C.E., Wulder, M.A. (2014). Good practices for estimating area and assessing accuracy of land change. Remote Sensing of Environment 148: 42-57. DOI 10.1016/j.rse.2014.02.015. [NW]
Also cited in section 1: Bayle, A., Gascoin, S., Berner, L.T., Choler, P. (2024). Landsat-based greening trends in alpine ecosystems are inflated by multidecadal increases in summer observations. Ecography e07394. DOI not in note. [W] [[bayle_2024_landsat_greening_inflated]]. Chastain, R.A. Jr., Townsend, P.A. (2007). Use of Landsat ETM and topographic data to characterize evergreen understory communities in Appalachian deciduous forests. Photogrammetric Engineering & Remote Sensing 73(5): 563-575. DOI 10.14358/pers.73.5.563. [W] [[chastain_2007_eve_landsat_understory]]

### Section 3 papers: ecology and drivers
- Walther, G.-R., Berger, S., Sykes, M.T. (2005). An ecological 'footprint' of climate change. Proceedings of the Royal Society B 272(1571): 1427-1432. DOI 10.1098/rspb.2005.3119. [NW]
- Walther, G.-R. (2002). Weakening of climatic constraints with global warming and its consequences for evergreen broad-leaved species. Folia Geobotanica 37(1): 129-139. DOI 10.1007/BF02803195. [NW]
- Walther, G.-R., Gritti, E.S., Berger, S., Hickler, T., Tang, Z., Sykes, M.T. (2007). Palms tracking climate change. Global Ecology and Biogeography 16(6): 801-809. DOI 10.1111/j.1466-8238.2007.00328.x. [NW]
- Carraro, G., Gianoni, P., Mossi, R. (1999). Climatic influence on vegetation changes: a verification on regional scale of the laurophyllisation. In: Klötzli, F., Walther, G.-R. (eds) Recent Shifts in Vegetation Boundaries of Deciduous Forests, Especially Due to General Global Warming. Birkhäuser, Basel, pp. 31-51 (CrossRef per ecology note; TRACEVE prints pp. 69-84; unresolved). DOI 10.1007/978-3-0348-8722-9_3. [NW]
- Alessi, N., Wellstein, C., Spada, F., Zerbe, S. (2021). Population structure of Laurus nobilis L. in Central Italian forests: evidence for its ongoing expansion. Rendiconti Lincei. Scienze Fisiche e Naturali 32(2): 365-376. DOI 10.1007/s12210-021-00981-7. [NW]
- Delzon, S., Urli, M., Samalens, J.-C., Lamy, J.-B., Lischke, H., Sin, F., Zimmermann, N.E., Porté, A.J. (2013). Field evidence of colonisation by Holm oak, at the northern margin of its distribution range, during the Anthropocene period. PLoS ONE 8(11): e80443. DOI 10.1371/journal.pone.0080443. [NW]
- Garcia-Fayos, P., Monleon, V.J., Espigares, T., Nicolau, J.M., Bochet, E. (2020). Increasing aridity threatens the sexual regeneration of Quercus ilex (holm oak) in Mediterranean ecosystems. PLOS ONE 15(10): e0239755. DOI 10.1371/journal.pone.0239755. [NW]
- Carnicer, J., Coll, M., Ninyerola, M., Pons, X., Sánchez, G., Peñuelas, J. (2011). Widespread crown condition decline, food web disruption, and amplified tree mortality with increased climate change-type drought. PNAS 108(4): 1474-1478. DOI 10.1073/pnas.1010070108. [NW]
- Palmero-Iniesta, M., Pino, J., Pesquer, L., Espelta, J.M. (2021). Recent forest area increase in Europe: expanding and regenerating forests differ in their regional patterns, drivers and productivity trends. European Journal of Forest Research 140(4): 793-805. DOI 10.1007/s10342-021-01366-z. [NW]
- Bertrand, R., Lenoir, J., Piedallu, C., et al. (2011). Changes in plant community composition lag behind climate warming in lowland forests. Nature 479(7374): 517-520. DOI 10.1038/nature10548. [NW]
- Zellweger, F., De Frenne, P., Lenoir, J., et al. (2020). Forest microclimate dynamics drive plant responses to warming. Science 368(6492): 772-775. DOI 10.1126/science.aba6880. [NW]
- Hickler, T., Vohland, K., Feehan, J., et al. (2012). Projecting the future distribution of European potential natural vegetation zones with a generalized, tree species-based dynamic vegetation model. Global Ecology and Biogeography 21(1): 50-63. DOI 10.1111/j.1466-8238.2010.00613.x. [NW]
- Niinemets, Ü., Flexas, J., Peñuelas, J. (2011). Evergreens favored by higher responsiveness to increased CO2. Trends in Ecology & Evolution 26: 136-142. DOI 10.1016/j.tree.2010.12.012 [as printed in TRACEVE, not CrossRef-checked]. [NW]
- Grund, K., Conedera, M., Schröder, H., Walther, G.-R. (2005). The role of fire in the invasion process of evergreen broad-leaved species. Basic and Applied Ecology 6: 47-56. DOI 10.1016/j.baae.2004.07.005 [as printed in TRACEVE]. [NW]
- Rusterholz, H.-P., Schneuwly, J., Baur, B. (2018). Invasion of the alien shrub Prunus laurocerasus in suburban deciduous forests: effects on native vegetation and soil properties. Acta Oecologica 92: 44-51. DOI 10.1016/j.actao.2018.08.004. [NW]
- Abrahamczyk, S., Otto, A., Böhnert, T., Weigend, M. (2024). Naturalization of Prunus laurocerasus in a forest in Germany. Biological Invasions 26 (pages/issue not retrieved). DOI 10.1007/s10530-024-03325-2. [NW]
- Buitenwerf, R., Sandel, B., Normand, S., Mimet, A., Svenning, J.-C. (2018). Land surface greening suggests vigorous woody regrowth throughout European semi-natural vegetation. Global Change Biology 24: 5789-5801. DOI 10.1111/gcb.14451 [as printed in TRACEVE]. [NW]
- Hernández, L., Sánchez de Dios, R., Montes, F., Sainz-Ollero, H., Cañellas, I. (2017). Exploring range shifts of contrasting tree species across a bioclimatic transition zone. European Journal of Forest Research 136: 481-492. DOI 10.1007/s10342-017-1047-2 [as printed in TRACEVE]. [NW]
- Berger, S., Walther, G.-R. (2006). Distribution of evergreen broad-leaved woody species in Insubria in relation to bedrock and precipitation. Botanica Helvetica 116: 65-77. DOI not in note. [W] [[berger_2006_distribution_eve]]
- Chelli, S., Wellstein, C., Campetella, G., Canullo, R., Tonin, R., Zerbe, S., Gerdol, R. (2017). Climate change response of vegetation across climatic zones in Italy. Climate Research 71: 249-262. DOI 10.3354/cr01443. [W] [[chelli_2017_climate]]
- Herraiz, A.D., Salazar-Zarzosa, P., Acosta-Muñoz, C., Hernández-Clemente, R., Villar, R. (2025). Aridity-induced phenological shifts and greening trends in Mediterranean forest species: insights from 28 years of Landsat data in southern Spain. Ecological Indicators 171: 113115. DOI 10.1016/j.ecolind.2025.113115. [W] [[herraiz_2025_phen_shifts_mediterranean]]
- Midolo, G., Clark, A.T., Chytrý, M., Essl, F., Dullinger, S., Jandt, U., Bruelheide, H., Dengler, J., Bonari, G., et al. (2026). Sixty years of plant community change in Europe indicate a shift toward nutrient-richer and denser vegetation. Science Advances 12: eaeb2493. DOI 10.1126/sciadv.aeb2493. [W] [[midolo_2026_denser_vegetation]]
- Francioni, M., Bricca, A., Andreetta, A., Brunialti, G., Bussotti, F., Campetella, G., Canullo, R., et al. (2026). Canopy closure and intensifying climate extremes drive understory species loss over 25 years of forest monitoring. npj Biodiversity (online 1 Apr 2026). DOI not in note. [W] [[francioni_2026_canopy_closure]]
- Noce, S., Cipriano, C., Santini, M. (2023). Altitudinal shifting of major forest tree species in Italian mountains under climate change. Frontiers in Forests and Global Change 6: 1250651. DOI 10.3389/ffgc.2023.1250651. [W] [[noce_2023_altitude_shift_tree_italy]]
- Calvia, G., Bonari, G., Angiolini, C., Farris, E., Fenu, G., Bacchetta, G. (2022). Temporal increase in the extent of Sardinian pine formations. Rendiconti Lincei. Scienze Fisiche e Naturali 33: 489-499. DOI not in note. [W] [[calvia_2022_pines]]

### Section 3 papers: remote sensing
- Pasquarella, V.J., Holden, C.E., Woodcock, C.E. (2018). Improved mapping of forest type using spectral-temporal Landsat features. Remote Sensing of Environment 210: 193-207. DOI 10.1016/j.rse.2018.02.064. [NW]
- Senf, C., Leitão, P.J., Pflugmacher, D., van der Linden, S., Hostert, P. (2015). Mapping land cover in complex Mediterranean landscapes using Landsat: improved classification accuracies from integrating multi-seasonal and synthetic imagery. Remote Sensing of Environment 156: 527-536. DOI 10.1016/j.rse.2014.10.018. [NW]
- Hermosilla, T., Wulder, M.A., White, J.C., Coops, N.C., Bater, C.W., Hobart, G.W. (2024). Characterizing long-term tree species dynamics in Canada's forested ecosystems using annual time series remote sensing data. Forest Ecology and Management 572: 122313. DOI 10.1016/j.foreco.2024.122313. [NW]
- Thapa, B., Wolter, P.T., Sturtevant, B.R., Townsend, P.A. (2020). Reconstructing past forest composition and abundance by using archived Landsat and national forest inventory data. International Journal of Remote Sensing 41(10): 4022-4056. DOI 10.1080/01431161.2019.1711245. [NW]
- Bonannella, C., Hengl, T., Heisig, J., Parente, L., Wright, M.N., Herold, M., de Bruin, S. (2022). Forest tree species distribution for Europe 2000-2020: mapping potential and realized distributions using spatiotemporal machine learning. PeerJ 10: e13728. DOI 10.7717/peerj.13728 [author list beyond first seven unverified]. [NW]
- Roy, D.P., Kovalskyy, V., Zhang, H.K., Vermote, E.F., Yan, L., Kumar, S.S., Egorov, A. (2016). Characterization of Landsat-7 to Landsat-8 reflective wavelength and normalized difference vegetation index continuity. Remote Sensing of Environment 185: 57-70. DOI 10.1016/j.rse.2015.12.024. [NW]
- Crawford, C.J., Roy, D.P., Arab, S., Barnes, C., Vermote, E., Hulley, G., et al. (2023). The 50-year Landsat collection 2 archive. Science of Remote Sensing 8: 100103. DOI 10.1016/j.srs.2023.100103. [NW]
- Wulder, M.A., White, J.C., Loveland, T.R., Woodcock, C.E., Belward, A.S., Cohen, W.B., Fosnight, E.A., Shaw, J., Masek, J.G., Roy, D.P. (2016). The global Landsat archive: status, consolidation, and direction. Remote Sensing of Environment 185: 271-283. DOI 10.1016/j.rse.2015.11.032 [as printed in TRACEVE]. [NW]
- Tolnai, M., Nagy, J.G., Bakó, G. (2016). Spatiotemporal distribution of Landsat imagery of Europe using cloud-weighted metadata. Journal of Maps 12: 1084-1088. DOI 10.1080/17445647.2015.1125308 [as printed in TRACEVE]. [NW]
- Claverie, M., Ju, J., Masek, J.G., Dungan, J.L., Vermote, E.F., Roger, J.-C., et al. (2018). The Harmonized Landsat and Sentinel-2 surface reflectance data set. Remote Sensing of Environment 219: 145-161. DOI 10.1016/j.rse.2018.09.002. [NW]
- Wulder, M.A., Hermosilla, T., White, J.C., Hobart, G.W., Masek, J.G. (2021). Augmenting Landsat time series with Harmonized Landsat Sentinel-2 data products: assessment of spectral correspondence. Science of Remote Sensing 4: 100031. DOI 10.1016/j.srs.2021.100031. [NW]
- Resasco, J., Hale, A.N., Henry, M.C., Gorchov, D.L. (2007). Detecting an invasive shrub in a deciduous forest understory using late-fall Landsat sensor imagery. International Journal of Remote Sensing 28(16): 3739-3745. DOI 10.1080/01431160701373721. [NW]
- Wang, T., Skidmore, A.K., Toxopeus, A.G., Liu, X. (2009). Understory bamboo discrimination using a winter image. Photogrammetric Engineering & Remote Sensing 75(1): 37-47. DOI 10.14358/pers.75.1.37. [NW]
- Francini, S., Schelhaas, M.-J., Vangi, E., Lerink, B.J.W., Nabuurs, G.-J., McRoberts, R.E., et al. (2024). Forest species mapping and area proportion estimation combining Sentinel-2 harmonic predictors and national forest inventory data. International Journal of Applied Earth Observation and Geoinformation 131: 103935. DOI 10.1016/j.jag.2024.103935 [full author list unverified]. [NW]
- Gomez, C., White, J.C., Wulder, M.A. (2016). Optical remotely sensed time series data for land cover classification: a review. ISPRS Journal of Photogrammetry and Remote Sensing 116: 55-72. DOI 10.1016/j.isprsjprs.2016.03.008. [NW]
- Zhu, Z., Woodcock, C.E. (2014). Continuous change detection and classification of land cover using all available Landsat data. Remote Sensing of Environment 144: 152-171. DOI 10.1016/j.rse.2014.01.011. [NW]
- Oreti, L., Barbati, A., Marini, F., Giuliarelli, D. (2020). Very high-resolution true color leaf-off imagery for mapping Taxus baccata L. and Ilex aquifolium L. understory populations in beech forests. Biodiversity and Conservation 29(8): 2605-2622. DOI 10.1007/s10531-020-01991-x. [NW]
- Fassnacht, F.E., Latifi, H., Stereńczak, K., Modzelewska, A., Lefsky, M., Waser, L.T., et al. (2016). Review of studies on tree species classification from remotely sensed data. Remote Sensing of Environment 186: 64-87. DOI 10.1016/j.rse.2016.08.013 [as printed in TRACEVE]. [NW]
- Hiebl, B., Alessi, N., Calvia, G., Bricca, A., Bonari, G., Zangari, G., Dorigo, W., Zerbe, S., Rutzinger, M. (2025). Advancing forest mapping: pretraining strategies and deep-ensemble based uncertainty for predicting evergreen broad-leaved cover from Sentinel-2 time series. International Journal of Applied Earth Observation and Geoinformation 142: 104734. DOI 10.1016/j.jag.2025.104734. [W] [[hiebl_2025_pretraining]]
- Pflugmacher, D., Rabe, A., Peters, M., Hostert, P. (2019). Mapping pan-European land cover using Landsat spectral-temporal metrics and the European LUCAS survey. Remote Sensing of Environment 221: 583-595. DOI 10.1016/j.rse.2018.12.001. [W] [[pflugmacher_2019_lulc_landsat]]
- Hemmerling, J., Pflugmacher, D., Hostert, P. (2021). Mapping temperate forest tree species using dense Sentinel-2 time series. Remote Sensing of Environment 267: 112743. DOI 10.1016/j.rse.2021.112743. [W] [[hemmerling_2021_forest_mapping_s2]]
- Kollert, A., Bremer, M., Löw, M., Rutzinger, M. (2021). Exploring the potential of land surface phenology and seasonal cloud free composites of one year of Sentinel-2 imagery for tree species mapping in a mountainous region. International Journal of Applied Earth Observation and Geoinformation 94: 102208. DOI 10.1016/j.jag.2020.102208. [W] [[kollert_2021_tree_species]]
- Blickensdörfer, L., Oehmichen, K., Pflugmacher, D., Kleinschmit, B., Hostert, P. (2024). National tree species mapping using Sentinel-1/2 time series and German National Forest Inventory data. Remote Sensing of Environment 304: 114069. DOI 10.1016/j.rse.2024.114069. [W] [[blickensdoerfer_2024_tree_species]]
- Turubanova, S., Potapov, P., Hansen, M.C., et al. (2023). Tree canopy extent and height change in Europe, 2001-2021, quantified using Landsat data archive. Remote Sensing of Environment. DOI not in note. [W] [[turubanove_2023_canopy_landsat]]
- Viana-Soto, A., Senf, C. (2025). The European Forest Disturbance Atlas: a forest disturbance monitoring system using the Landsat archive. Earth System Science Data. Volume/DOI not in note. [W] [[soto_2025_disturbance]]
- Senf, C., Seidl, R. (2021). Mapping the forest disturbance regimes of Europe. Nature Sustainability 4(1): 63-70. DOI 10.1038/s41893-020-00609-y. [W] [[senf_2021_disturbance]]
- Mattioli, W., et al. (2025). La Carta Forestale d'Italia (CFI2020). Forest@ 22: 39-44. DOI 10.3832/efor4836-022. [W] [[mattioli_2025_carta_forestale]]
- Menegaldo, I., Sforzini, V.M., Tognetti, R., Torresani, M. (2025). Tree line dynamics and forest densification in the European Alps revealed by Landsat images and machine learning: a case study in the Senales/Schnals Valley. Vegetation Ecology and Diversity 62: e177152. DOI 10.3897/ved.177152. [W] [[menegaldo_2025_landsat_treeline_dynamics]]
- Tong, X., Brandt, M., Yue, Y., et al. (2023). Forest densification in China (annual Landsat forest-probability maps 1986-2018). Communications Earth & Environment. DOI not in note. [W] [[tong_2023_forest_densification_china]]
- Bell, D.M., Gregory, M.J., Yang, Z. (2024). Hindcasting and updating Landsat-based forest structure mapping across years to support forest management and planning. Forest Ecology and Management. DOI not in note. [W] [[bell_2024_hindcasting_forest_structure]]

### Section 3 papers: time-series change and trajectories
- Kennedy, R.E., Yang, Z., Cohen, W.B. (2010). Detecting trends in forest disturbance and recovery using yearly Landsat time series: 1. LandTrendr - temporal segmentation algorithms. Remote Sensing of Environment 114(12): 2897-2910. DOI 10.1016/j.rse.2010.07.008. [NW]
- Kennedy, R.E., Andréfouët, S., Cohen, W.B., Gómez, C., et al. (2014). Bringing an ecological view of change to Landsat-based remote sensing. Frontiers in Ecology and the Environment 12(6): 339-346. DOI 10.1890/130066. [NW]
- Kennedy, R.E., Yang, Z., Gorelick, N., Braaten, J., et al. (2018). Implementation of the LandTrendr algorithm on Google Earth Engine. Remote Sensing 10(5): 691. DOI 10.3390/rs10050691. [NW]
- Pasquarella, V.J., Arévalo, P., Bratley, K.H., Bullock, E.L., et al. (2022). Demystifying LandTrendr and CCDC temporal segmentation. International Journal of Applied Earth Observation and Geoinformation 110: 102806. DOI 10.1016/j.jag.2022.102806. [NW]
- Cohen, W.B., Healey, S.P., Yang, Z., Stehman, S.V., et al. (2017). How similar are forest disturbance maps derived from different Landsat time series algorithms? Forests 8(4): 98. DOI 10.3390/f8040098. [NW]
- Zhu, Z. (2017). Change detection using Landsat time series: a review of frequencies, preprocessing, algorithms, and applications. ISPRS Journal of Photogrammetry and Remote Sensing 130: 370-384. DOI 10.1016/j.isprsjprs.2017.06.013. [NW]
- Woodcock, C.E., Loveland, T.R., Herold, M., Bauer, M.E. (2020). Transitioning from change detection to monitoring with remote sensing: a paradigm shift. Remote Sensing of Environment 238: 111558. DOI 10.1016/j.rse.2019.111558. [NW]
- Verbesselt, J., Hyndman, R., Newnham, G., Culvenor, D. (2010). Detecting trend and seasonal changes in satellite image time series. Remote Sensing of Environment 114(1): 106-115. DOI 10.1016/j.rse.2009.08.014. [NW]
- Song, X.-P., Hansen, M.C., Stehman, S.V., Potapov, P.V., Tyukavina, A., Vermote, E.F., Townshend, J.R. (2018). Global land change from 1982 to 2016. Nature 560: 639-643. DOI 10.1038/s41586-018-0411-9. [NW]
- Olofsson, P., Foody, G.M., Stehman, S.V., Woodcock, C.E. (2013). Making better use of accuracy data in land change studies: estimating accuracy and area and quantifying uncertainty using stratified estimation. Remote Sensing of Environment 129: 122-131. DOI 10.1016/j.rse.2012.10.031. [NW]
- Stehman, S.V., Foody, G.M. (2019). Key issues in rigorous accuracy assessment of land cover products. Remote Sensing of Environment 231: 111199. DOI 10.1016/j.rse.2019.05.018. [NW]
- Pontius, R.G., Lippitt, C.D. (2006). Can error explain map differences over time? Cartography and Geographic Information Science 33(2): 159-171. DOI 10.1559/152304006777681706. [NW]
- Pontius, R.G., Shusas, E., McEachern, M. (2004). Detecting important categorical land changes while accounting for persistence. Agriculture, Ecosystems & Environment 101(2-3): 251-268. DOI 10.1016/j.agee.2003.09.008. [NW]
- Aldwaik, S.Z., Pontius, R.G. (2012). Intensity analysis to unify measurements of size and stationarity of land changes by interval, category, and transition. Landscape and Urban Planning 106(1): 103-114. DOI 10.1016/j.landurbplan.2012.02.010. [NW]
- Abercrombie, S.P., Friedl, M.A. (2016). Improving the consistency of multitemporal land cover maps using a hidden Markov model. IEEE Transactions on Geoscience and Remote Sensing 54(2): 703-713. DOI 10.1109/TGRS.2015.2463689. [NW]
- Bogaert, Lamarche, Defourny (2022). Hidden Markov models for annual land cover mapping: increasing temporal consistency and completeness. IEEE Transactions on Geoscience and Remote Sensing 60 (article number and given names not verified). DOI 10.1109/TGRS.2021.3123738. [NW]
- Gong, Fang, Yang, Ge (2017). Using a hidden Markov model for improving the spatial-temporal consistency of time series land cover classification. ISPRS International Journal of Geo-Information 6(10): 292 (given names unverified). DOI 10.3390/ijgi6100292. [NW]
- Hamed, K.H., Rao, A.R. (1998). A modified Mann-Kendall trend test for autocorrelated data. Journal of Hydrology 204(1-4): 182-196. DOI 10.1016/S0022-1694(97)00125-X. [NW]
- Yue, S., Pilon, P., Phinney, B., Cavadias, G. (2002). The influence of autocorrelation on the ability to detect trend in hydrological series. Hydrological Processes 16(9): 1807-1829. DOI 10.1002/hyp.1095. [NW]
- Neeti, N., Eastman, J.R. (2011). A contextual Mann-Kendall approach for the assessment of trend significance in image time series. Transactions in GIS 15(5): 599-611. DOI 10.1111/j.1467-9671.2011.01280.x. [NW]
- Sen, P.K. (1968). Estimates of the regression coefficient based on Kendall's tau. Journal of the American Statistical Association 63(324): 1379-1389. DOI 10.1080/01621459.1968.10480934. [NW]
- Mann, H.B. (1945). Nonparametric tests against trend. Econometrica 13(3): 245-259. DOI 10.2307/1907187. [NW]
- Getis, A., Ord, J.K. (1992). The analysis of spatial association by use of distance statistics. Geographical Analysis 24(3): 189-206. DOI 10.1111/j.1538-4632.1992.tb00261.x. [NW]
- Dormann, C.F., McPherson, J.M., Araújo, M.B., Bivand, R., et al. (2007). Methods to account for spatial autocorrelation in the analysis of species distributional data: a review. Ecography 30(5): 609-628. DOI 10.1111/j.2007.0906-7590.05171.x. [NW]
- Beale, C.M., Lennon, J.J., Yearsley, J.M., Brewer, M.J., Elston, D.A. (2010). Regression analysis of spatial data. Ecology Letters 13(2): 246-264. DOI 10.1111/j.1461-0248.2009.01422.x. [NW]

### Section 3 papers: Italian context, land use, drought and dieback
- Falcucci, A., Maiorano, L., Boitani, L. (2007). Changes in land-use/land-cover patterns in Italy and their implications for biodiversity conservation. Landscape Ecology 22(4): 617-631. DOI 10.1007/s10980-006-9056-4. [NW]
- Malandra, F., Vitali, A., Urbinati, C., Weisberg, P.J., Garbarino, M. (2019). Patterns and drivers of forest landscape change in the Apennines range, Italy. Regional Environmental Change 19(7): 1973-1985. DOI 10.1007/s10113-019-01531-6. [NW]
- Malandra, F., Vitali, A., Urbinati, C., Garbarino, M. (2018). 70 years of land use/land cover changes in the Apennines (Italy): a meta-analysis. Forests 9(9): 551. DOI 10.3390/f9090551. [NW]
- Malavasi, M., Carranza, M.L., Moravec, D., Cutini, M. (2018). Reforestation dynamics after land abandonment: a trajectory analysis in Mediterranean mountain landscapes. Regional Environmental Change 18(8): 2459-2469. DOI 10.1007/s10113-018-1368-9. [NW]
- Gasparini, P., Tabacchi, G. (2022). Changes of Italian forests over time captured by the National Forest Inventories. In: Gasparini, P., et al. (eds) Italian National Forest Inventory - Methods and Results of the Third Survey. Springer Tracts in Civil Engineering, pp. 545-568. DOI 10.1007/978-3-030-98678-0_13. [NW as chapter; book is in wiki: [[gasparini_2022_nfi_italy]]]
- Alderotti, F., Sillo, F., Brilli, F., Bussotti, F., et al. (2023). Quercus ilex L. dieback is genetically determined: evidence provided by dendrochronology, δ13C and SSR genotyping. Science of the Total Environment 904: 166809. DOI 10.1016/j.scitotenv.2023.166809. [NW]
- Alderotti, F., Bussotti, F., Gori, A., Ferrini, F., et al. (2025). Moderately and severely defoliated Quercus ilex L. trees exhibit hydraulic dysfunction and carbon depletion: physiological implications for Mediterranean forest monitoring. Tree Physiology 45: tpaf033. DOI 10.1093/treephys/tpaf033. [NW]
- Bussotti, F., Papitto, G., Di Martino, D., Cocciufa, C., Cindolo, C., Cenni, E., Bettini, D., et al. (2021). Defoliation, recovery and increasing mortality in Italian forests: levels, patterns and possible consequences for forest multifunctionality. Forests 12(11): 1476. DOI 10.3390/f12111476. [NW]
- Gentilesca, T., Camarero, J.J., Colangelo, M., Nolè, A., Ripullone, F. (2017). Drought-induced oak decline in the western Mediterranean region: an overview on current evidences, mechanisms and management options to improve forest resilience. iForest 10: 796-806. DOI 10.3832/ifor2317-010. [NW]
- Frisullo, S., Lima, G., Magnano di San Lio, G., Camele, I., Melissano, L., Puglisi, I., Pane, A., et al. (2018). Phytophthora cinnamomi involved in the decline of holm oak (Quercus ilex) stands in southern Italy. Forest Science 64(3): 290-298. DOI 10.1093/forsci/fxx010. [NW]
- Colangelo, M., Camarero, J.J., Borghetti, M., Gentilesca, T., Oliva, J., Redondo, M.A., Ripullone, F. (2018). Drought and Phytophthora are associated with the decline of oak species in southern Italy. Frontiers in Plant Science 9: 1595. DOI 10.3389/fpls.2018.01595 [author list from memory in the note; check]. [NW]
- Lloret, F., Siscart, D., Dalmases, C. (2004). Canopy recovery after drought dieback in holm-oak Mediterranean forests of Catalonia (NE Spain). Global Change Biology 10(12): 2092-2099. DOI 10.1111/j.1365-2486.2004.00870.x. [NW]
- Brunetti, M., Maugeri, M., Monti, F., Nanni, T. (2006). Temperature and precipitation variability in Italy in the last two centuries from homogenised instrumental time series. International Journal of Climatology 26(3): 345-381. DOI 10.1002/joc.1251. [NW]
- Vicente-Serrano, S.M., López-Moreno, J.I., Beguería, S., Lorenzo-Lacruz, J., Sanchez-Lorenzo, A., García-Ruiz, J.M., Azorin-Molina, C., et al. (2014). Evidence of increasing drought severity caused by temperature rise in southern Europe. Environmental Research Letters 9(4): 044001. DOI 10.1088/1748-9326/9/4/044001. [NW]
- Gazol, A., Camarero, J.J. (2022). Compound climate events increase tree drought mortality across European forests. Science of the Total Environment 816: 151604. DOI 10.1016/j.scitotenv.2021.151604. [NW]
- Mombrini, E., Tamea, S., Viglione, A., Revelli, R. (2025). A 60-year drought analysis of meteorological data in the western Po River basin. Hydrology and Earth System Sciences 29(10): 2255-2273. DOI 10.5194/hess-29-2255-2025. [NW]
- Giorgi, F., Lionello, P. (2008). Climate change projections for the Mediterranean region. Global and Planetary Change 63: 90-104. DOI 10.1016/j.gloplacha.2007.09.005 [as printed in TRACEVE]. [NW]
- Seddaiu, S., Ruiu, P.A., Piras, G., Scanu, B., Satta, G.G.A., et al. (2025). Vulnerabilità delle foreste mediterranee a eventi climatici estremi di ondate di calore e siccità: il caso del disseccamento del leccio (Quercus ilex L.) in Italia. Forest@ 22: 56-65. DOI 10.3832/efor4934-022. [W] [[seddaiu_2025_quercus_dieback]]
- Satta, G.G.A., Giannetti, F., Deidda, A., Brandano, A., Lentini, A., Piras, G., Ruiu, P.A., Seddaiu, S., Scanu, B. (2025). Detection and modeling of drought-induced forest dieback in Mediterranean ecosystems. SSRN preprint, NOT peer reviewed. DOI 10.2139/ssrn.5761729. [W] [[seddaiu_2025_mediterranean_dieback]]
- Puletti, N., Mattioli, W., Bussotti, F., Pollastrini, M. (2019). Monitoring the effects of extreme drought events on forest health by Sentinel-2 imagery. Journal of Applied Remote Sensing 13(2): 020501. DOI 10.1117/1.JRS.13.020501. [W] [[puletti_2019_drought_forest_health]]
- Alessi, N., Bonari, G., et al. (2023). Probabilistic and preferential sampling approaches offer integrated perspectives of Italian forest diversity. Journal of Vegetation Science. DOI not in note. [W] [[alessi_2023_sampling_approaches]]
- Gasparini, P., Di Cosmo, L., Floris, A., De Laurentis, D. (eds) (2022). Italian National Forest Inventory - Methods and Results of the Third Survey (INFC2015). Springer Tracts in Civil Engineering. ISBN 978-3-030-98677-3. [W] [[gasparini_2022_nfi_italy]]

### Section 3 papers: space-for-time and prediction
- Balzter, H. (2000). Markov chain models for vegetation dynamics. Ecological Modelling 126(2-3): 139-154. DOI 10.1016/S0304-3800(00)00262-3. [NW]
- Blois, J.L., Williams, J.W., Fitzpatrick, M.C., Jackson, S.T., Ferrier, S. (2013). Space can substitute for time in predicting climate-change effects on biodiversity. PNAS 110(23): 9374-9379. DOI 10.1073/pnas.1220228110. [NW]
- Damgaard, C. (2019). A critique of the space-for-time substitution practice in community ecology. Trends in Ecology & Evolution 34(5): 416-421. DOI 10.1016/j.tree.2019.01.013. [NW]
- Elith, J., Leathwick, J.R. (2009). Species distribution models: ecological explanation and prediction across space and time. Annual Review of Ecology, Evolution, and Systematics 40: 677-697. DOI 10.1146/annurev.ecolsys.110308.120159. [NW]
