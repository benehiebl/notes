---
title: "Scoping review (version 3): distribution changes of evergreen broad-leaved species in Italy"
date: 2026-10-16
tags: [forest-ecology, remote-sensing, literature-review, scoping-review]
version: 3
---

# Scoping review v3: evergreen broad-leaved change in Italy

## 0. Purpose, status and how to use

- **Purpose.** Map the existing evidence (studies, designs, methods, findings) and the key concepts behind the paper "Distribution changes of evergreen broad-leaved species in Italy" (outline: `03_papers/04_evergreen_distribution_change.md`). It supports the Introduction and motivation and is a reading starting point. It is not a ranked must-read list; the short reading tiers are in section 6.
- **Status.** Standalone replacement of v2 (`Evergreen distribution review abstracts verified.md`). It rests on the v2 report and its research notes, the 75-entry TRACEVE reference inventory, and three new scoping notes (concepts and spread; dieback and mortality; remote sensing and trajectories). Where the new notes disagree with v2, the new notes win and the conflict is stated.
- **Method limits.** ARS and this workflow have no dedicated scoping mode. The PRISMA-ScR checklist and protocol registration remain the author's responsibility. This is a single-reviewer, AI-assisted scoping review with no dual screening. No PRISMA flow numbers exist (section 1.5).
- **Model output.** The notes are model output. Statements that no note verified are marked "not verified" or carry a weak tag. Nothing here upgrades a tag.
- **How to use.** Section 2 for definitions and wording, section 3 for the evidence map, section 4 for Introduction statements with their evidence strength, section 5 for the full study chart, section 6 for reading, sections 7 and 8 for gaps and housekeeping, section 9 for references.

**Verification legend (use these tags exactly; do not read a weaker tag as a stronger one).**
- **[W]** = a note exists in the user's wiki (`01_notes/`). **[PDF-CHECKED]** = the round-2 wiki-PDF check read the user's PDF against the note.
- **[ABSTRACT-READ]** = abstract text fetched directly from an API or publisher/repository page.
- **[ABSTRACT-VIA-SEARCH]** / **[SEARCH-SUMMARY]** = only a search tool's paraphrase of a repository abstract (weaker; the two names are used by different researchers for the same status).
- **[ABSTRACT-PARAPHRASE]** = abstract only via a summarising fetch tool, not verbatim (weaker). **[SNIPPET/TLDR-ONLY]** = only a Scholar snippet or a machine-generated Semantic Scholar summary (weakest content tag).
- **[FULLTEXT-PARTLY-READ]** = some full text read. **[METADATA-ONLY]** = bibliographic record only, no abstract. **[still unverified]** = a content statement nobody has checked.
- "NOT IN WIKI - add PDF" = no note in `01_notes/`. Wiki papers carry a `[[citekey]]` link in addition to the full reference.

Additional conventions in v3: "CrossRef-checked" = bibliographic data confirmed against CrossRef (only where a note says so). "[ABSTRACT-READ, CrossRef verbatim]" in the new notes is treated as [ABSTRACT-READ]. Evidence-strength words (strong, moderate, weak, only-abstract) are defined in section 4 and are the reviewer's judgement, not a tag.

---

## 1. Protocol

### 1.1 Review questions
1. What is the evidence on spread and expansion of evergreen broad-leaved species (EVE) into deciduous forests, and its drivers, in Italy, the southern Alps and other regions?
2. What is the evidence on dieback and increased mortality of evergreen broad-leaved trees (especially *Quercus ilex*) caused by drought, heat and pathogens in Italy and elsewhere?
3. Which remote-sensing, time-series and trajectory methods have been used to map and analyse such change over decades, and how reliable are they?
4. How do regional differences, climatic drivers and change rates or trajectories interact?

### 1.2 PCC framework
| Element | Definition used |
|---|---|
| Population | Evergreen broad-leaved woody species and forests: sclerophylls (*Q. ilex*, *Q. suber*, *Phillyrea*), native and alien laurophylls and climbers (*Laurus*, *Ilex aquifolium*, *Buxus*, *Hedera*, *Prunus laurocerasus*, *Trachycarpus*) |
| Concept | Distribution change, spread, expansion, dieback, mortality, drivers (climate, land use, propagule pressure, disturbance), detection and trajectory methods |
| Context | Italy and comparable Mediterranean and temperate Europe; other regions (North America, East Asia, Canada) only as analogues, mainly for methods |

### 1.3 Objectives
- Chart studies by theme, design, region, period, target, data/method, driver and finding.
- Define and source the key concepts, and flag terms without a source.
- Identify what is established, contested and missing, per Introduction storyline.
- Test the outline's claims against the evidence and soften "no precedent" statements.
- Give the author a reading starting point.

### 1.4 Eligibility criteria
| Criterion | Include | Exclude |
|---|---|---|
| Design | Any: resurvey or repeat inventory, plot survey, remote sensing, modelling, experiment, palaeo, review | Student theses, press reports, trade items as primary evidence |
| Status | Peer-reviewed articles, book chapters, reviews. Preprints, conference abstracts and grey literature only if labelled, and never as the sole support | Unlabelled grey literature |
| Topic | EVE spread, dieback, drivers, change detection, trajectory and uncertainty methods, Italian land-use and climate context | Herb/understory thermophilization except as concept; tropical forests except as method precedent; crop and urban studies; carbon and soil studies |
| Language | English in practice; Italian, Spanish, French items were searched but only reached as snippets | Non-accessible items are not cited |
| Date | No formal limit. Charted empirical studies run from 1999 to 2026; classic methods papers are older | None applied |

### 1.5 Information sources, search dates and what worked
Dates: the remote-sensing note states work on 2026-10-16; the v2 report is dated 2026-10-16; the other notes do not record dates.

| Source | Status | Consequence |
|---|---|---|
| CrossRef API | Worked fully (metadata, some abstracts; Elsevier and Springer abstracts often elided) | Main metadata check |
| OpenAlex | Free budget exhausted (HTTP 429); only single-DOI lookups worked late | Weak coverage, no forward citations in later rounds |
| Semantic Scholar | A few calls (citation lists capped at 100), then HTTP 429 | Forward citations partial, may miss 2025-2026 |
| Google Scholar | Worked for a few batches only (about 14 + 3 + 3 queries in three v2 notes), then 429 or captcha; not used in round 3 dieback note, not tried in round 3 remote-sensing note | Italian-language queries mostly never run; snippets of about 125 characters |
| Web search tool | Paraphrased summaries only; weak for Italian, Alpine, Balkan topics | Every hit rechecked in CrossRef or kept as snippet |
| Publisher pages | ScienceDirect, Springer, Wiley, OUP, Science blocked; HAL showed Anubis block; iris repositories Cloudflare; docta.ucm.es refused | No full text of most papers |
| User's wiki PDFs, open-access dissertation (Berger 2008), INFC chapter | Read in v2 round 2 | Source of [PDF-CHECKED] and [FULLTEXT-PARTLY-READ] |
| TRACEVE proposal Annex 1 | 75 entries transcribed from a scan; 9 are in the wiki | Proposal is not evidence |

Search strings (broad terms; exact strings were not archived): evergreen broad-leaved, laurophyllisation, mediterranization, holm oak/*Quercus ilex* expansion, range shift, resurvey, Italy; oak decline, dieback, defoliation, mortality, drought, heat, *Phytophthora*, Italy and Mediterranean; Landsat time series, annual land cover, tree species maps, HMM, Markov, trajectory, LandTrendr, CCDC, hotspot, Mann-Kendall, hindcasting, spatial cross-validation; Italian terms (leccio, laurofillizzazione, mediterraneizzazione) in a few Scholar batches. Two quoted CrossRef free-text queries ("Jump 2009 Mediterranean holm oak", "Trindade 2020 evergreen oak") returned nothing relevant. Call counts stated in the notes: about 20 tool calls in the dieback note; about 17 discovery and 12 verification calls in the remote-sensing note.

**Counts.** Identification and screening counts were not logged systematically; no PRISMA flow numbers exist and none are given. The only derivable counts are the charted studies per theme (section 3, generated from the section 5 table) and the 75 TRACEVE entries.

### 1.6 Selection and charting process
- One reviewer (AI-assisted). Researchers (model agents) searched, read what was reachable and tagged verification level; the synthesis step rechecked metadata in CrossRef.
- Selection was iterative and judgement-based; no dual screening, no kappa. Items judged weak, snippet-level or off-topic were dropped or labelled cite-only.
- Charting: one row per study with label, reference and DOI, theme, region and period, target, data or method, driver, finding, design limit, tag, wiki link (section 5). Each study has one primary theme; theme 4 holds climate and land-use context studies.
- No formal risk-of-bias appraisal. Tags describe verification depth, not study quality.

### 1.7 Deviations and limitations of this review
- Absence of evidence is not proof of absence: Scholar, Italian journals (Forest@, iForest, L'Italia Forestale e Montana, Annali di Botanica) and Italian-language grey literature were poorly searched.
- Most abstracts were read, few full texts. Claims about design limits are inferences unless the table says otherwise.
- Researcher notes can conflict; resolutions are stated where they matter (sections 2, 4, 9).
- No protocol was registered.

### 1.8 PRISMA-ScR item mapping
| Item | Topic | Status |
|---|---|---|
| 1 | Title identifies a scoping review | Done |
| 2 | Structured summary | Partly (section 0) |
| 3 | Rationale | Partly (section 4 and outline) |
| 4 | Objectives | Done |
| 5 | Protocol and registration | Not done |
| 6 | Eligibility criteria | Done (retrospective) |
| 7 | Information sources | Partly (dates incomplete) |
| 8 | Search strategy | Not done (full strings not archived) |
| 9 | Selection of sources | Not done (single reviewer, informal) |
| 10 | Data charting process | Partly |
| 11 | Data items | Partly (section 5 columns) |
| 12 | Critical appraisal of sources | Not done (optional in ScR; tags only) |
| 13 | Synthesis methods | Partly |
| 14 | Selection results (flow) | Not done |
| 15 | Characteristics of sources | Done (sections 3, 5) |
| 16 | Critical appraisal within sources | Not done |
| 17 | Results of individual sources | Done (section 5) |
| 18 | Synthesis of results | Done (section 4) |
| 19 | Summary of evidence | Done |
| 20 | Limitations | Done |
| 21 | Conclusions | Partly (section 7) |
| 22 | Funding | Not done (not applicable) |

---

## 2. Concept map

"Working definition" = reviewer's wording from how sources use the term, not a quote. DOIs are in section 9. "No verified source" means none of the notes found one.

| Concept | Working definition (one line) | Best definitional source, tag | Caveat | Suggested wording for the paper |
|---|---|---|---|---|
| Laurophyllisation | Spread of laurel-leaved evergreen broad-leaved species into deciduous forests of the Insubria / southern Alps | Walther 2001 (10.1007/978-94-015-9686-2_13) and Walther, Carraro & Klötzli 2001 (10.1007/978-1-4419-8692-4_10), both [METADATA-ONLY]; usage in Conedera 2018 [W][PDF-CHECKED] | Titles confirm the concept chapters; no abstract read; who coined the word is not verified (Gianoni, Carraro & Klötzli 1988 and Klötzli & Walther 1999 not accessible) | "Laurophyllisation, the spread of evergreen broad-leaved species into deciduous forests of the southern Alps (Walther 2001; Conedera et al. 2018)" |
| Mediterranization | Gain of *Q. ilex* and loss of cooler-adapted species in a bioclimatic transition zone | Hernández et al. 2017 [ABSTRACT-VIA-SEARCH]; summary quotes a "previous hypothesis of a 'mediterranization'" | Iberian use; operational, not a formal definition; no Italian source; the in-text "Hernández / Peñuelas" item in the proposal is probably this paper plus a conflation with Peñuelas & Boada 2003 (unresolved) | Use only with the Iberian citation, or avoid the word for Italy |
| Biome shift (beech to holm oak) | Replacement of a deciduous forest biome element by evergreen oak forest | Peñuelas & Boada 2003 [ABSTRACT-READ] | Montseny only; Fehr et al. 2024 title uses "ongoing biome shift" for the Ticino palm [METADATA-ONLY] | "A biome shift from beech to holm oak was reported in Montseny (Peñuelas & Boada 2003)" |
| Non-equilibrium range / range filling | Species occupy only part of their climatically suitable range (ratio realised/potential) | Svenning & Skov 2004 [ABSTRACT-READ]; Alessi 2019 [W][PDF-CHECKED] | Svenning & Skov: 55 trees, atlas data, not evergreens; Alessi's potential range uses Beals' index, not an SDM | "Native laurophylls fill less than half of their estimated potential range in Italy (Alessi et al. 2019)" |
| Propagule pressure | Number, size and timing of arriving propagules | Simberloff 2009 [ABSTRACT-READ]; application in Conedera 2018 | Invasion-biology review, not forest-specific | Cite Simberloff for the definition, Conedera for the result |
| Thermophilization | Shift of community composition toward warm-adapted species | Gottfried et al. 2012 [METADATA-ONLY]; Bertrand 2011, Zellweger 2020 (herbs, v2 [ABSTRACT-READ]) | No EVE-specific definition; herbs only | Avoid for EVE or define explicitly |
| Forest transition / land abandonment | Shift from net deforestation to net reforestation; abandonment lets forest expand | Meyfroidt, Rudel & Lambin 2010 [ABSTRACT-READ]; Italy: Malandra 2018 [ABSTRACT-READ], Garbarino 2020 [ABSTRACT-VIA-SEARCH] | Meyfroidt is tropical/trade focused; original forest-transition papers (Mather 1992, Rudel 2005) not retrieved | Cite the term from Meyfroidt only; Italian facts from Malandra and Gasparini |
| Land-use legacy / forest densification | Past land use and regrowth, not current climate, drive composition and abundance change | Vayreda 2016 [ABSTRACT-READ]; Padullés Cubino 2024 [ABSTRACT-READ] | Spain, all species or Fagaceae; *Q. ilex* result not in abstracts | "In Spain, regrowth and past land use explained much composition change (Vayreda 2016; Padullés Cubino 2024)" |
| Disturbance-catalysed species shift | Canopy disturbance opens windows for new species | Scherrer et al. 2021 [ABSTRACT-READ, truncated] | Swiss NFI; EVE not isolated in abstract | Mechanism link between dieback, fire and spread |
| Global-change-type drought / hotter drought | Drought under warmer temperatures | Breshears 2005; Allen, Breshears & McDowell 2015 [both ABSTRACT-READ] | Breshears is a piñon-juniper event in SW USA; Allen 2015 article number needs check (CrossRef pages "1-55") | "Hotter droughts (Allen et al. 2015)" |
| Hydraulic failure vs carbon starvation | Two proposed mortality mechanisms and their interaction with biotic agents | McDowell et al. 2008 [ABSTRACT-READ] | Hypothesis framework, partly contested | Cite for definitions only |
| Unexpected mortality in "tolerant" systems | Sudden die-off in ecosystems not considered at risk | Hartmann et al. 2022 [ABSTRACT-READ] | Authors say data are insufficient to call it a global trend | Frame holm oak dieback as unexpected, not as a proven trend |
| Crown dieback vs defoliation vs mortality | Leaf-loss, branch-death and tree-death as separate states | No verified source; Lloret 2004 [ABSTRACT-READ] distinguishes canopy dieback and recovery; ICP Forests manual not fetched | Terms used loosely across sources | Define in Methods (author's own wording) |
| Resprouting, resilience, legacy effects | Recovery of crowns from dormant buds; delayed effects of past stress | Lloret 2004 [ABSTRACT-READ]; Pollastrini 2019 [ABSTRACT-READ] | No verified legacy-effects review (Anderegg 2015 not verified) | Cite Lloret and Pollastrini for resprouting only |
| Oak decline complex | Multi-factor, drought-triggered decline | Alderotti & Verdiani 2023 [ABSTRACT-VIA-SEARCH in the new note; v2 [ABSTRACT-READ]]; Gentilesca 2017 [METADATA-ONLY, summary via search]; Marques 2025 [METADATA-ONLY] | Gentilesca mostly ring-porous deciduous oaks; Manion's decline spiral not found | "Oak decline is a multi-factor complex (Alderotti & Verdiani 2023)" |
| Compound events | Joint hot-summer and dry-year events | Gazol & Camarero 2022 [ABSTRACT-READ] | Pan-European, not Italian | 46 % of 310 mortality events were compound (as in v2) |
| Space-for-time substitution | Using spatial gradients to infer temporal change | Blois 2013; Damgaard 2019 [both ABSTRACT-READ] | About 72 % as accurate as time-for-time in Blois (pollen, N America) | Use as justification for time-for-time hindcasts |
| Class trajectory | Sequence of annual class labels per pixel | Mertens & Lambin 2000 [ABSTRACT-READ]; clustering: Mena 2008 [ABSTRACT-READ] | Tropical deforestation; same word in LandTrendr means a spectral segment fit | Define "class trajectory" vs "spectral trajectory" once |
| Spectral/index trajectory, break detection | Segmented fit to an index series | Kennedy 2010 [ABSTRACT-VIA-SEARCH in v3 note; v2: SNIPPET/TLDR-ONLY]; Verbesselt 2010 [ABSTRACT-VIA-SEARCH]; Zhu & Woodcock 2014 [ABSTRACT-PARAPHRASE] | Built for spectral series, not categorical maps | Cite as method origin only |
| Temporal consistency of annual maps | Removal of implausible year-to-year class flips | Used operationally in Hermosilla 2018/2024, Bogaert 2022, Abercrombie & Friedl 2016, GLC_FCS30D | No single definitional review found | Define in text |
| Map error vs real change | Differences between maps may be classification error | Pontius & Lippitt 2006 [ABSTRACT-READ]; Torchiana 2025 [ABSTRACT-READ]; Olofsson 2014 [ABSTRACT-VIA-SEARCH] | Olofsson abstract only by paraphrase | Cite Pontius & Lippitt for the test, Olofsson for area adjustment |
| Hindcasting / label back-casting | Training on recent labels and applying to earlier imagery | Radoux 2014 [ABSTRACT-READ]; Thapa 2020, Verhulst 2024, Zhou 2020 [ABSTRACT-READ]; [[bell_2024_hindcasting_forest_structure]] [W] | Source-map reliability limits the result | Cite Radoux for the strategy |
| HMM smoothing vs HMM forecasting | Smoothing estimates the true label sequence; forecasting projects transitions | Smoothing: Bogaert 2022, Abercrombie & Friedl 2016; transition estimation then projection: Torchiana 2025; climate-driven latent states: Lu 2022 (preprint, [ABSTRACT-VIA-SEARCH]); Rabiner 1989 [METADATA-ONLY]; McClintock 2020 [ABSTRACT-READ] | The three IEEE HMM papers smooth, none forecasts | Keep the two roles separate in Methods |
| Hotspot analysis | (a) spatial clustering of values (Getis-Ord); (b) locations with significant trend | Getis & Ord 1992 [ABSTRACT-READ]; Baglioni et al. 2026 (EGU abstract, [ABSTRACT-READ] of a conference abstract) | Two meanings; Baglioni is NDVI at forestlines, not peer reviewed | State which meaning is used |
| Trend tests with autocorrelation | Mann-Kendall variants | Yue 2002, Neeti & Eastman 2011 [ABSTRACT-READ]; Hamed & Rao 1998 [SNIPPET/TLDR-ONLY] | Dieback then resprouting is not monotonic | Cite Yue and Neeti |
| Leaf type cover (LTC) vs dominant tree species (DTS) | Fractional evergreen/deciduous cover vs dominant-species class | No verified definitional source; LTC and DTS are the author's own terms. Supporting: Thapa 2020 (grouping improves calibration), Buchhorn 2020 (cover fractions), Sousa & Davis 2020 | Not defined in any note | Define in Methods |
| Greening vs browning | Net NDVI increase vs decrease | Pausas & Millán 2019 [ABSTRACT-READ] | Perspective, no data in abstract | Baseline: abandonment-driven greening |
| Climate relicts / refugia | Populations persisting in past-climate refugia | Hampe & Jump 2011 [ABSTRACT-READ]; Alessi 2019 "ancient refugia" | Hampe & Jump concerns rear edges, not EVE spread (a guess for the unidentified "Jump 2009") | Use only for refugia |
| Spatial validation / area of applicability | Evaluate on spatially separated data | Roberts 2017, Dormann 2007, Ploton 2020, Meyer & Pebesma 2021 [all ABSTRACT-READ] | Roberts issue number and Meyer & Pebesma issue number were filled from memory: not verified | Cite for block CV |
| Submediterranean | Transition between Mediterranean and Eurosiberian vegetation | Sánchez de Dios 2009 [METADATA-ONLY]; Passos 2025 [ABSTRACT-READ] | Defined via marcescent oaks (Iberia) | Optional |
| Mesophication (opposite process) | Shift toward shade-casting mesic species | Nowacki & Abrams 2008 [METADATA-ONLY] | Eastern US, not EVE | Skip |
| Evergreen "encroachment", "tropicalization" of forests | none | No verified source | CrossRef hits were marine, bamboo, urban | Own wording; state this in the text |

---

## 3. Evidence map

Counts are **rows of the section 5 table**, one primary theme per row, generated from that table. A row may hold two to four closely linked papers (for example Pesaresi 2020 x2), so counts are of charted entries, not of unique papers. Only studies charted in section 5 are counted; items dropped or listed only as leads are not. Berger & Walther 2006 (Insubria, Italy and Switzerland) is counted under Italy; Bricca 2026 is counted under Italy by wiki context (not stated in the notes); rows whose region the notes do not state are in "Not stated".

**Total charted rows: 113** (theme 1: 35; theme 2: 26; theme 3: 37; theme 4: 15).

### 3.1 Theme x design

| Theme | Resurvey / repeat inventory | Plot / field study | Remote sensing | Modelling | Experiment | Palaeo | Review / synthesis | Other (climate analysis, records, method test) | Total |
|---|---|---|---|---|---|---|---|---|---|
| 1 Spread and drivers | 11 | 9 | 1 | 8 | 0 | 2 | 2 | 2 | 35 |
| 2 Dieback and mortality | 2 | 10 | 2 | 0 | 1 | 0 | 9 | 2 | 26 |
| 3 Remote sensing, trajectories, methods | 0 | 0 | 33 | 1 | 0 | 0 | 0 | 3 | 37 |
| 4 Interplay: land use, climate, regional context | 1 | 1 | 5 | 0 | 0 | 0 | 2 | 6 | 15 |
| **All** | 14 | 20 | 41 | 9 | 1 | 2 | 13 | 13 | 113 |

### 3.2 Theme x region

| Theme | Italy | Other Mediterranean | Temperate Europe / Alps | Europe-wide / global | Outside Europe | Not stated | Total |
|---|---|---|---|---|---|---|---|
| 1 Spread and drivers | 8 | 11 | 10 | 5 | 0 | 1 | 35 |
| 2 Dieback and mortality | 14 | 7 | 0 | 1 | 4 | 0 | 26 |
| 3 Remote sensing, trajectories, methods | 5 | 6 | 2 | 6 | 16 | 2 | 37 |
| 4 Interplay: land use, climate, regional context | 13 | 1 | 0 | 1 | 0 | 0 | 15 |
| **All** | 40 | 25 | 12 | 13 | 20 | 3 | 113 |

### 3.3 Design x region, theme 1 Spread and drivers

| Design | Italy | Other Mediterranean | Temperate Europe / Alps | Europe-wide / global | Outside Europe | Not stated | Total |
|---|---|---|---|---|---|---|---|
| Resurvey / repeat inventory | 0 | 5 | 5 | 0 | 0 | 1 | 11 |
| Plot / field study | 3 | 3 | 3 | 0 | 0 | 0 | 9 |
| Remote sensing | 0 | 1 | 0 | 0 | 0 | 0 | 1 |
| Modelling | 3 | 2 | 1 | 2 | 0 | 0 | 8 |
| Palaeo | 2 | 0 | 0 | 0 | 0 | 0 | 2 |
| Review / synthesis | 0 | 0 | 0 | 2 | 0 | 0 | 2 |
| Other (climate analysis, records, method test) | 0 | 0 | 1 | 1 | 0 | 0 | 2 |

### 3.4 Design x region, theme 2 Dieback and mortality

| Design | Italy | Other Mediterranean | Temperate Europe / Alps | Europe-wide / global | Outside Europe | Not stated | Total |
|---|---|---|---|---|---|---|---|
| Resurvey / repeat inventory | 1 | 1 | 0 | 0 | 0 | 0 | 2 |
| Plot / field study | 8 | 2 | 0 | 0 | 0 | 0 | 10 |
| Remote sensing | 2 | 0 | 0 | 0 | 0 | 0 | 2 |
| Experiment | 0 | 1 | 0 | 0 | 0 | 0 | 1 |
| Review / synthesis | 2 | 3 | 0 | 1 | 3 | 0 | 9 |
| Other (climate analysis, records, method test) | 1 | 0 | 0 | 0 | 1 | 0 | 2 |

### 3.5 Design x region, theme 3 Remote sensing, trajectories, methods

| Design | Italy | Other Mediterranean | Temperate Europe / Alps | Europe-wide / global | Outside Europe | Not stated | Total |
|---|---|---|---|---|---|---|---|
| Remote sensing | 5 | 6 | 2 | 4 | 14 | 2 | 33 |
| Modelling | 0 | 0 | 0 | 0 | 1 | 0 | 1 |
| Other (climate analysis, records, method test) | 0 | 0 | 0 | 2 | 1 | 0 | 3 |
### 3.6 What the map shows

- **Dense.** Remote-sensing methods (33 of 37 theme-3 rows), but only 5 of them are Italian and none is a multi-decadal evergreen or leaf-type class change map (the Italian rows are Agrillo 2021 and Pesaresi 2020 single-epoch, Mancino 2014 two-date forest/non-forest, Oreti 2020 very high resolution, and Baglioni conference abstracts on NDVI trends). Plot and field studies of dieback in Italy (8 of 26 dieback rows) and reviews of dieback (9 rows) are also numerous, but most are regional case studies.
- **Moderate.** Time-comparison designs for EVE spread exist (11 resurvey / repeat-inventory rows in theme 1), all in Spain, France, Switzerland/Alps, Poland or temperate Europe in general (Perring 2020). Modelling of future suitability (8 rows) is the main Italian-specific design for spread (Noce 2023, Pignatti 2011, Bricca 2026).
- **Thin.** For Italy, theme 1 has 8 rows: 3 plot studies (Alessi 2019, Alessi 2021, Berger & Walther 2006), 3 models, 2 palaeo studies and **0 resurvey, inventory-change or remote-sensing studies of EVE spread**. Dieback quantification is thin: one experiment (Spain), two Italian remote-sensing rows (one preprint, one short letter), one repeat-inventory row (national ICP Forests).
- **Absent in the charted evidence.** No observed multi-decadal change study of *Q. ilex* or EVE for Italy outside Ticino-adjacent work; no study that maps gain and loss of evergreen oaks together in one region; no published winter-minimum-temperature trend paper for Italy; no Mediterranean *Q. ilex* LandTrendr/CCDC study; no HMM-with-climate-covariates study on annual forest-species maps. Absence here means "not found with the searches described in section 1.5".
- **Geography of method precedents.** 16 of 37 theme-3 rows are outside Europe (Canada, USA, tropics); the Mediterranean rows are Iberian or Moroccan.

---

## 4. Synthesis along the four Introduction storylines

**Evidence-strength words (reviewer's judgement, not tags).** *Strong* = full text read via the user's PDF ([PDF-CHECKED]) or several concordant verbatim abstracts, and the design fits the claim. *Moderate* = verbatim abstract ([ABSTRACT-READ]) states the claim and the design fits. *Only-abstract* = the claim rests on a paraphrase-level abstract ([ABSTRACT-VIA-SEARCH], [ABSTRACT-PARAPHRASE]) or on a truncated abstract; wording may change after reading. *Weak* = design or region mismatch, preprint, conference abstract, grey literature or snippet; do not use as the sole support.

### 4.1 Storyline 1: spread and expansion of EVE and its drivers

**What is established.** Spread of evergreen broad-leaved species into deciduous forest is documented at the southern edge of the Alps, but mainly for understory shrubs, climbers and a palm, not for canopy trees. In the Swiss Lago Maggiore area, *Hedera helix*, *Ilex aquifolium*, *Prunus laurocerasus* and *Trachycarpus fortunei* occur under closed deciduous canopy, and propagule pressure from gardens was the main driver of occurrence for three of the four species (Conedera et al. 2018) [W][PDF-CHECKED]. The Insubrian EVE flora partitions by bedrock and precipitation, and *Q. ilex* sits on dry, shallow calcareous sites rather than with the laurophylls (Berger & Walther 2006) [W][PDF-CHECKED]. At the Italian scale, nine of 11 native laurophylls fill less than half of their estimated potential range, so non-equilibrium is the best-supported general statement (Alessi et al. 2019) [W][PDF-CHECKED]. Outside Italy, the evidence for holm oak is richer and uses repeat designs: replacement of beech by holm oak at medium altitudes in Montseny (Peñuelas & Boada 2003), colonisation of new areas at the Atlantic margin in France at 22 to 57 m per year (Delzon et al. 2013), and gain of *Q. ilex* at the expense of cooler-adapted species in a Navarra transition zone between 1971 and 2010 (Hernández et al. 2017, paraphrase-level).

**What is contested.**
- *Climate versus propagule pressure and land use.* Walther et al. (2007) attribute the palm's Swiss spread to winter temperature and growing season "and not by delayed population expansion"; Conedera et al. (2018) find propagule pressure dominant and climate secondary, and note that coldest-month means at Locarno-Monti were already low in 1915-1925 when few gardens with seed-producing evergreens existed. Alessi et al. (2019) call present climate change secondary to historical processes, and Alessi et al. (2021) frame *Laurus nobilis* as recovering a potential niche after abandonment. Berger et al. (2007) use bioclimatic models of potential range, which cannot separate the two. The disagreement is real and the paper should state it.
- *Spain: climate or regrowth.* Peñuelas & Boada (2003) name warming "complemented by" cessation of traditional management without partitioning; Vayreda et al. (2016) find changes "not always consistent with climate warming" and legacy-driven; Padullés Cubino et al. (2024) find abundance change "primarily associated with forest densification". Hernández et al. (2017) conclude warming is the major driver (paraphrase level). These studies mostly address all species or Fagaceae, so they bear on *Q. ilex* only indirectly.
- *Is expansion general?* Urli et al. (2013) found no altitudinal shift for Mediterranean species at their core range in a decade, whereas Hernández (2017) and Delzon (2013) found gain at transition zones or the northern margin. Spread therefore depends on range position and time window.
- *CO2.* Niinemets et al. (2011) offer CO2 as an additional explanation, and Soh et al. (2019) show faster iWUE gains in evergreens; neither tests range expansion, and a correlative trajectory analysis cannot separate CO2 from warming.

**What is missing.** No observed, spatially explicit change study of *Q. ilex* or EVE in Italy was found. The national inventory shows the holm-oak area change as not flagged as considerable (643,052 ha; growing stock +34.2 %), and a +33.6 % rise in "other evergreen broadleaved" that is a residual class (Gasparini & Tabacchi 2022) [W][FULLTEXT-PARTLY-READ]. An Italian-language statement that holm-oak woodland area "is thought to be expanding" (La Marca & Marziliano 1997) reached the review only as a teaching-document snippet and cannot be cited. A Lombardy estimate of laurophyllisation (Cerabolini et al. 2008) is an unread lead. Mechanism studies exist (disturbance windows: Scherrer et al. 2021; shrub facilitation: Cruz-Alonso et al. 2019; fire: Grund et al. 2005; shade plus drought tolerance of evergreen angiosperms: Niinemets & Valladares 2006) but none is Italian and none was tested on remote-sensing maps.

**Citation-ready statements (Storyline 1).**
| # | Statement | Supporting references | Strength |
|---|---|---|---|
| 1.1 | Spread of evergreen broad-leaved climbers, shrubs and a palm into deciduous forest is documented in the southern Swiss Alps, where propagule pressure was the main driver of occurrence. | Conedera et al. 2018 | Strong (not *Q. ilex*; cross-sectional) |
| 1.2 | Nine of 11 native laurophylls in Italy occupy less than half of their estimated potential range, which suggests continuing spread. | Alessi et al. 2019 (Beals' index, one time slice) | Strong for the number, weak for "continuing spread" (inference) |
| 1.3 | Evergreen niche partitioning in Insubria follows bedrock and precipitation; *Q. ilex* is restricted to dry calcareous sites. | Berger & Walther 2006 | Strong (22 sites, targeted) |
| 1.4 | Holm oak has replaced beech at medium altitudes in Montseny since 1945 and colonised new areas at the northern margin in France at 22-57 m per year. | Peñuelas & Boada 2003; Delzon et al. 2013 | Moderate (abstracts; one massif; lateral rate) |
| 1.5 | In Navarra, *Q. ilex* gained in a submediterranean transition zone between 1971 and 2010 while cooler-adapted species declined. | Hernández et al. 2017 | Only-abstract |
| 1.6 | Drivers are disputed: warming, propagule pressure, and land-use legacy each have support, and Spanish inventory studies attribute much composition change to regrowth rather than warming. | Conedera 2018; Alessi 2019; Vayreda 2016; Padullés Cubino 2024 | Moderate to strong |
| 1.7 | Expansion is not universal: core-range Mediterranean species showed no altitudinal shift over one decade in Spain. | Urli et al. 2013 | Moderate (10 years) |
| 1.8 | No observed, spatially explicit change study of EVE or *Q. ilex* in Italy was found ("to our knowledge"). | Absence of evidence; section 7.3 | Weak by nature |

### 4.2 Storyline 2: dieback and increased mortality of evergreen broad-leaved trees

**What is established.** Holm oak dieback is documented in Italy and in other Mediterranean regions. In Italy the sequence is first reports in Tuscany in 2012, more extensive crown loss after the 2017 drought, and widespread dieback in Apulia, Basilicata, Sardinia and Sicily in summer 2024, with resprouting from dormant buds; national ICP Forests Level I data (about 250 trees in 11 plots) show defoliation peaks in 2017, 2022 and 2025 and "sporadic" mortality (Seddaiu et al. 2025) [W][PDF-CHECKED]. The 2017 case is documented in the field: *Q. ilex* and *Phillyrea latifolia* showed total or partial crown desiccation and partly resprouted in 2018, while deciduous oaks shed leaves but kept buds (Pollastrini et al. 2019). Physiology agrees that crown loss can understate damage: 40-50 % loss of hydraulic conductivity in moderately or severely defoliated trees (Alderotti et al. 2025). In Catalonia, up to 76 % of holm oaks had complete canopy dieback after the 1994 drought with extensive resprouting (Lloret et al. 2004), and a 20-year drought experiment raised stem mortality, which was reduced by thinning (Ogaya et al. 2020, search-summary level). Concept anchors are available: hotter drought (Allen et al. 2015), the hydraulic and carbon-starvation mechanisms (McDowell et al. 2008), and unexpected mortality in systems thought tolerant (Hartmann et al. 2022).

**What is contested.**
- *Pathogens versus climate.* Phytophthora cinnamomi is "assumed" the primary agent near Lecce (Frisullo et al. 2018), and Botryosphaeriaceae with *Phytophthora* are involved in Apulia (Bregant et al. 2025); Sicily reports no pathogens (per Seddaiu 2025 as noted in the wiki); the Tuscan regional service finds no single organism and adds defoliator outbreaks (*Lymantria dispar*, *Tortrix viridana*) with drought and heat (grey literature); the Iberian dehesa literature has long favoured *P. cinnamomi*, with its role "debated" (secondary report). Colangelo et al. (2018) found *P. quercina* more often in non-declining deciduous oaks. The figure "48 % of studies pathogens versus 17 % climate", attributed to Marques et al. (2025), could not be traced to that paper (section 8).
- *Tolerant or not.* Puletti et al. (2019) conclude holm oak is tolerant to short extreme events (vegetation-index trajectories, 118 samples), while Pollastrini et al. (2019) and Seddaiu et al. (2025) document crown desiccation. The metrics differ; the field-based evidence outweighs a short letter, but this is a judgement.
- *Is mortality rising?* Bussotti et al. (2021) report stable crown condition nationally but more extremely defoliated and dead trees, with Quercus progressively less defoliated, and Mediterranean evergreen woodland thinly sampled; Hartmann et al. (2022) say data are insufficient to call it a global trend; the Tuscan service reports most surveyed sites recovering.
- *Magnitude.* Experimental stem mortality, plot defoliation, ICP Forests and Sentinel-2 extent figures are not comparable.

**What is missing.** No Italian national or regional mortality statistic for *Q. ilex*; no peer-reviewed spatial quantification of 2022 or 2024 dieback (the Sardinian ~110,000 ha figure rests on one preprint and a conference abstract that are probably not independent: Satta et al. 2025, Seddaiu et al. 2025, Scanu et al. 2025); no Mediterranean LandTrendr or CCDC study of *Q. ilex* dieback; no study showing both gain and loss of evergreen oak in one region. A Port-Cros study with leaf-deficit figures (Cailleret et al., title and DOI not obtained) and Algerian and Moroccan plot studies remain unusable until read. Box (*Buxus*) is a separate, non-climate case: dieback of native stands by an introduced pathogen in Turkey (metadata only) and by the box moth in Liguria (search-summary, 370 ha), which matters for the Alessi (2019) *Buxus* range-filling figure of 3.7 %.

**Citation-ready statements (Storyline 2).**
| # | Statement | Supporting references | Strength |
|---|---|---|---|
| 2.1 | Dieback of *Q. ilex* is documented in central and southern Italy (Tuscany 2012 and 2017; Apulia, Basilicata, Sardinia, Sicily 2024) and in other Mediterranean regions. | Seddaiu et al. 2025; Pollastrini et al. 2019; Lloret et al. 2004 | Strong for Italy (regional overview), moderate for Spain |
| 2.2 | After the 2017 drought and heat wave, holm oak and *Phillyrea* showed crown desiccation and partial resprouting in 2018. | Pollastrini et al. 2019 | Moderate (mortality not quantified) |
| 2.3 | Moderate crown defoliation can conceal severe hydraulic damage. | Alderotti et al. 2025 | Moderate |
| 2.4 | Hotter droughts and compound hot-dry events increase tree mortality, and unexpected die-offs have occurred in ecosystems considered tolerant. | Allen et al. 2015; Hartmann et al. 2022; Gazol & Camarero 2022 | Moderate (global/pan-European; debate noted) |
| 2.5 | The role of pathogens versus drought is region-specific and unresolved in Italy. | Frisullo 2018; Bregant 2025; Seddaiu 2025; Regione Toscana page (grey) | Moderate |
| 2.6 | Experimental drought raised stem mortality of holm oak in Catalonia. | Ogaya et al. 2020 | Only-abstract |
| 2.7 | National ICP Forests data show stable mean crown condition but more extremely defoliated and dead trees. | Bussotti et al. 2021 | Moderate (few evergreen plots) |
| 2.8 | Sentinel-2 mapping suggests about 110,000 ha of Sardinian dieback in 2024. | Satta et al. 2025 (preprint) | Weak (preprint; not independent of Seddaiu 2025) |

### 4.3 Storyline 3: remote sensing, time series and trajectories over decades

**What is established.** Annual 30 m species and class maps over four decades are feasible: 37 species classes in Canada, 1984-2022, overall accuracy 86.1 % (Hermosilla et al. 2024), a European annual land use/cover series 2000-2019 whose accuracy falls to 0.49 at 43 classes (Witjes et al. 2022), and a global 1985-2022 product with 73-81 % overall accuracy and weak leaf-type sub-classes (Zhang et al. 2024). Early years are worse: US yearly checks of GLC_FCS30D rise from 78.91 % (2000) to 80.04 % (2015); exact-year change in LCMAP is mostly below 30 % agreement (search-snippet level); Hermosilla et al. (2018) validated one year only (OA 70.3 %). Temporal consistency is usually improved by HMM filtering or similar rules (Abercrombie & Friedl 2016; Bogaert et al. 2022; Hermosilla 2024 per the catalogue entry), and "much of this apparent land cover change arises from errors in classification". Leaf type is the safer hindcast target: grouping into broadleaf and conifer lifted R2adj to 0.72-0.91 against 0.39-0.78 for individual species (Thapa et al. 2020). Label back-casting from outdated maps is an accepted strategy but limited by source reliability (Radoux et al. 2014), and CORINE change layers can be artefacts of production changes (Garcia-Alvarez & Camacho Olmedo 2022, preprint, Asturias). Map error can explain map differences if accuracy is below about 77 % in the Pontius & Lippitt (2006) case, and uncorrected transition rates are "severely biased" (Torchiana et al. 2025). For trend statistics, Mann-Kendall variants with autocorrelation handling and Theil-Sen have been used on Landsat NDVI for oaks (Aubard et al. 2019) and for Italian forestline hotspots (Baglioni et al. 2025/2026, conference abstracts). Winter or leaf-off imagery detects evergreen understory in US deciduous forests (Chastain & Townsend 2007; Atkins et al. 2018); the Italian counterpart is very high resolution only (Oreti et al. 2020).

**What is contested.**
- *Smoothing versus real slow change.* HMM and rule-based consistency suppress flip-flops, but may remove real slow change (reviewer's inference; no note tested it). Sensitivity runs with and without smoothing are advised.
- *Forecasting skill.* Pixel-based Markov forecasts did not beat a persistence null model at fine resolution (Pontius & Malanson 2005), whereas HMM-corrected transition rates feed scenario projection (Torchiana et al. 2025) and climate-driven latent transitions have been proposed (Lu et al. 2022, preprint). A homogeneous chain assumes constant transition probabilities, which climate forcing violates.
- *Algorithm choice.* Seven disturbance algorithms agree on undisturbed forest but not on affected pixels (Cohen et al. 2017), and NDVI breakpoint over-estimation can reverse trends (Forkel et al. 2013).
- *NDVI as a mortality proxy.* NDVI related to stem mortality at R2 0.43 in an experiment (Ogaya et al. 2020), but a Tuscan Sentinel-2 field comparison (not identified, snippet) reportedly failed on patchy dieback; resprouting may leave class labels unchanged.

**What is missing.** A Mediterranean multi-decadal leaf-type or species map for Italy; any quantitative comparison of HMM-smoothed versus raw annual species maps in independent validation (the Hermosilla 2024 paper text is unread); observation-density studies for classified maps (Bayle et al. 2024 covers alpine non-forest summer NDVI only); a verified European or Italian product that separates evergreen from deciduous broadleaves at 30 m before 2000; CLC 323 (sclerophyllous vegetation) trends for Italy; Getis-Ord or Mann-Kendall on categorical species series; European winter-composite studies for invasive evergreens.

**Citation-ready statements (Storyline 3).**
| # | Statement | Supporting references | Strength |
|---|---|---|---|
| 3.1 | Annual 30 m tree-species maps over four decades have been produced at national scale (Canada, 37 classes, OA 86.1 %). | Hermosilla et al. 2024 | Moderate |
| 3.2 | Accuracy of annual land-cover time series is lower in early Landsat years and weakest for leaf-type forest sub-classes. | Zhang et al. 2024 (GLC_FCS30D); Hermosilla 2018 | Moderate |
| 3.3 | Differencing independent annual maps overstates change because classification errors appear as transitions; HMM filtering is used to correct this. | Bogaert 2022; Abercrombie & Friedl 2016; Pontius & Lippitt 2006; Torchiana 2025 | Moderate |
| 3.4 | Leaf-type groups are hindcast more reliably than single species from archived Landsat. | Thapa et al. 2020 | Moderate (US, regression) |
| 3.5 | Landsat winter or leaf-off imagery can detect evergreen understory beneath deciduous canopy in the eastern US. | Chastain & Townsend 2007; Atkins et al. 2018 | Strong (Chastain, PDF) / moderate (Atkins); not Mediterranean |
| 3.6 | Landsat NDVI trend tests have flagged declining oak stands in Portugal (about 12 % of oak area). | Aubard et al. 2019 | Moderate for existence, only-abstract for the 12 % |
| 3.7 | Landsat-based hotspot analysis of Italian forestline vegetation trends is under way (conference abstracts). | Baglioni et al. 2025, 2026 | Weak (not peer reviewed) |
| 3.8 | We are not aware of a published study combining annual species/leaf-type maps, HMM, climate drivers, hotspot statistics and forecasting for a Mediterranean country. | Hermosilla 2024; Torchiana 2025; Lu 2022; Baglioni; section 7.3 | Weak by nature |

### 4.4 Storyline 4: interplay of regional differences, climatic drivers and change rates

**What is established.** Change rates are available only in fragments and in different units. Beech moved up about 70 m in Montseny (Peñuelas & Boada 2003); holm oak colonised at 22-57 m per year (Delzon 2013); ivy occurrence rose 14 % per site over a median 38 years (Perring 2020). Italian rates are for all forest: INFC forest area +3.7 % between 2005 and 2015 (Gasparini & Tabacchi 2022), a 0.6 % per year expansion in two Italian ranges (Garbarino et al. 2020; search-summary, reference base unclear), and a meta-analysis with forest +78 % and cropland -49 % across Apennine case studies (Malandra et al. 2018). Regional contrast is documented: forest expansion is more extensive at lower elevations in the Apennines (Garbarino 2020, search summary), the Alps and Apennines differ in greening along forestlines with a land-use legacy (Baglioni 2026, conference abstract), and Spanish edge effects differ between cold-wet and warm-dry edges (Padullés Cubino 2024). The Mediterranean baseline is abandonment-driven greening that may switch to browning with warming (Pausas & Millán 2019). Gain and loss coexist at the species level in Iberia (expansion drivers: Padial-Iglesias 2022; dieback: Lloret 2004), but no single study shows both in one region.

**What is contested.** Italian climate drivers are uneven. Warming of about 1 K per century to about 2000 (Brunetti 2006) and seven widespread multi-year droughts since 1901 (Pascale & Ragone 2025) are documented; a drying tendency under SPEI in southern Europe (Spinoni 2017; Padua: Becherini 2024; Sicily: Aschale 2024) conflicts with the Piedmont and Aosta analysis finding no region-wide trend (Mombrini 2025). Future suitability for holm oak is contested: reduced in four of five Italian sections under both scenarios (Noce 2023), diversity of warm evergreen habitats might fall (Bricca 2026), while Mediterranean species are expected to gain on lower mountains and hills (Pignatti 2011) and the submediterranean ecotone to move northwards (Passos 2025).

**What is missing.** A verified Italian winter-minimum-temperature or frost-day trend paper (an ISPRA frost-day indicator and a Basilicata study surfaced only as snippets); a national gridded SPEI trend paper; formal separation of warming and abandonment, which both date from about 1950; any Italian change rate for evergreens; forward citations (OpenAlex and Semantic Scholar were blocked).

**Citation-ready statements (Storyline 4).**
| # | Statement | Supporting references | Strength |
|---|---|---|---|
| 4.1 | Italian forest area increased by 3.7 % between INFC2005 and INFC2015; the holm-oak area change was not flagged as considerable while growing stock rose 34.2 %. | Gasparini & Tabacchi 2022 | Strong (chapter in wiki; samples not independent) |
| 4.2 | Forest expansion after rural abandonment is the dominant landscape transition in Italian mountains. | Malandra 2018; Garbarino 2020; Vitali 2018 | Moderate (Garbarino only-abstract; the 0.6 %/yr is all forest) |
| 4.3 | In the Mediterranean, abandonment-driven greening buffers browning drivers, but the balance may switch with warming. | Pausas & Millán 2019 | Moderate (perspective) |
| 4.4 | Italian drought history includes multiple widespread multi-year droughts since 1901, and SPEI-based studies indicate drying in southern Europe, though regional analyses differ. | Pascale & Ragone 2025; Spinoni 2017; Mombrini 2025 | Moderate |
| 4.5 | Projections for holm oak in Italy are mixed: suitability losses in the Apennines versus gains at cool margins. | Noce 2023; Pignatti 2011; Bricca 2026 | Moderate to weak (models; Bricca region unconfirmed) |
| 4.6 | Warming and land abandonment overlap in time, so correlative attribution needs explicit land-use covariates and spatially aware validation. | Dormann 2007; Roberts 2017; Ploton 2020 | Moderate (inference from methods papers) |

### 4.5 Wording check of the outline (v2 section 5.1 updated)

| Outline claim | Evidence (new items marked) | Verdict | Suggested wording |
|---|---|---|---|
| "Spread of evergreens into deciduous forests" | Documented in Insubria (Conedera 2018; Berger & Walther 2006; Carraro 1999 resurvey); potential-range gap in Italy (Alessi 2019); **Spanish inventory evidence of holm oak gain in a transition zone (Hernández 2017) and no change at the core (Urli 2013)**; INFC: holm-oak area not flagged, residual class +33.6 % | Supported locally, not quantified nationally | "Spread of evergreen broad-leaved species into deciduous forests is documented in the southern Alps and in the Iberian Peninsula, and non-equilibrium ranges suggest further spread in Italy; national, spatially explicit quantification is lacking" |
| Driver "milder winters etc." as headline | Premise only in Berger/Walther abstracts (potential ranges); Conedera, Alessi 2019 and 2021 say climate secondary; **Vayreda 2016 and Padullés Cubino 2024 point to regrowth and legacy in Spain; Peñuelas & Boada 2003 combine warming and abandonment**; no verified Italian winter-minimum trend paper | Weak as headline | "Spread is associated with propagule pressure, land-use change and forest development, with warming relaxing cold limits (disputed weight)" |
| "Documented dieback of Q. ilex in other areas" | Documented inside Italy (Tuscany 2012/2017; south and islands 2024) and Spain | Must be reworded | "Documented dieback of *Q. ilex* in central and southern Italy and other Mediterranean regions" |
| Dieback "due to drought and infections" | Pathogen role regional; **Regione Toscana adds defoliator insects**; Colangelo 2018 deciduous oaks; Marques 48 %/17 % untraceable | Supported for Apulia and cork oak only | "Dieback is attributed to drought and heat, with pathogens and defoliators contributing in some regions" |
| "Increased mortality" | Bussotti 2021: more extremely defoliated and dead trees; Seddaiu: mortality "sporadic"; Hartmann 2022: no global trend shown | Partly supported | "Episodes of severe crown loss and local mortality, with resprouting in many stands" |
| Puletti 2019 vs Pollastrini/Seddaiu | Conflict unresolved; metrics differ | State both | Describe both; a greenness product can under- or over-state loss |
| Maps will show "gain and dieback zones" | Resprouting (Pollastrini, Lloret, Seddaiu); Alderotti 2025; **Saura-Mas 2015: dieback can shift canopy to shrub states**; Satta preprint: models without climate overestimate dieback | False-loss risk | Add persistence rules and a disturbance mask; treat single-year drops as uncertain |
| "Future habitats" | Noce 2023, Bricca 2026 (decline), Pignatti 2011, Passos 2025 (gain); **Suicmez 2023: refugia in southern coastal areas, regional variation** | Direction contested | Present two hypotheses: gain at cool margins and abandoned land, constraint in the dry south |
| Prediction with HMM, space-for-time | Space-for-time ~72 % as accurate (Blois 2013); **pixel Markov forecasts no better than persistence at fine resolution (Pontius & Malanson 2005)** | Not established | Hindcast-validate against a persistence null; time-for-time first |
| "No precedent" for HMM or hotspot | **Hermosilla 2024 (HMM smoothing of species maps, per catalogue), Bogaert 2022, Abercrombie & Friedl 2016, Gong 2017, Salberg & Trier (smoothing); Torchiana 2025 (HMM-corrected transitions then projection); Lu 2022 (climate-driven latent transitions, preprint); Baglioni (trend hotspots, Italy, conference)** | Soften | "To our knowledge, the combination of annual species maps, HMM-based consistency, climate drivers, hotspot statistics and forecasting has not been applied at national scale in the Mediterranean" |
| Novelty of "Landsat can map evergreen change" | Chastain 2007, Atkins 2018 show the principle in the US; **Sousa & Davis 2020 evergreen/deciduous fractions in California** | Do not claim | Claim only the Italian, multi-decadal, species/leaf-type application |

---

## 5. Charted studies

One row per study or closely linked study group; sorted by theme. **Wiki** column: link = paper has a note in `01_notes/`; blank = not in wiki (add PDF, section 8). Short quotes are verbatim only where the tag is [ABSTRACT-READ] or the note supplied a quote; quotes taken from search summaries are said so. "Limit" is the design limit (reviewer's reading unless a note states it). Tag text is copied from the notes.

### 5.1 Theme 1 Spread and drivers

| Label | Reference, DOI | Region, period | Target; data / method | Driver tested | Key finding | Design limit | Tag | Wiki |
|---|---|---|---|---|---|---|---|---|
| **Conedera 2018** | Reg Environ Change 18:425-436, 10.1007/s10113-017-1212-7 | S Swiss Alps (Lago Maggiore), cross-sectional | 200 plots; Hedera, Ilex aquifolium, Prunus laurocerasus, Trachycarpus; tobit regression | propagule pressure, climate, stand | "Propagule pressure resulted to be the main driver of occurrence for three considered species, while meso-climate and stand structure played only a secondary role" | Climbers, shrubs, palm, not Q. ilex; no time series; 30 m detectability open | [W][PDF-CHECKED] | [[conedera_2018_drivers_evergreen]] |
| **Alessi 2019** | J Veg Sci 30:564-574, 10.1111/jvs.12743 | Italy, one time slice | 17,087 forest plots; 11 native laurophylls; Beals' index | history vs climate | "Most of them occupied less than half of their estimated potential range"; nine of 11 below 50 % | Beals' index not an SDM; sampling bias; Q. ilex excluded; no time dimension | [W][PDF-CHECKED] [ABSTRACT-READ] | [[alessi_2019_refugia]] |
| **Alessi 2021** | Rend Lincei 32(2):365-376, 10.1007/s12210-021-00981-7 | 16 central Italian sites | Laurus nobilis population structure | forest cover/age after abandonment | Structures suggest "a potential increase"; framed as recovery of a potential niche, not climate shift | Single species, no time series | [ABSTRACT-READ]; CrossRef-checked |  |
| **Berger & Walther 2006** | Bot Helv 116(1):65-77, 10.1007/s00035-006-0749-8 | 22 sites Lago d'Orta to Garda (Insubria, IT/CH) | EVE-rich stands, bedrock and precipitation | precipitation, bedrock | Species partition W-humid-siliceous vs E-dry-calcareous; Q. ilex profits on shallow calcareous soils from reduced competition | Targeted sampling, one survey | [W][PDF-CHECKED] | [[berger_2006_distribution_eve]] |
| **Berger 2007** | Phytocoenologia 37:523-539, 10.1127/0340-269x/2007/0037-0523 | N European limits of Ilex, P. laurocerasus, Trachycarpus | Bioclimatic models | winter climate | Milder winters consistent with northward expansion of potential ranges | Potential not observed area | [ABSTRACT-READ via dissertation]; CrossRef-checked |  |
| **Walther 2005** | Proc R Soc B 272:1427-1432, 10.1098/rspb.2005.3119 | Scandinavia, holly northern margin | Distribution records vs climate | winter temperature | "a shift in the northern margin ... in concert with gradually increasing winter temperatures" | Correlative; Ilex only (not a Ticino paper) | [ABSTRACT-READ]; CrossRef-checked |  |
| **Walther 2007** | Glob Ecol Biogeogr 16(6):801-809, 10.1111/j.1466-8238.2007.00328.x | Trachycarpus, S Switzerland and native range | Distribution vs climate | winter minimum, growing season | Spread "driven by changes in winter temperature and growing season length and not by delayed population expansion" | Qualified by Conedera 2018 (propagule pressure) | [ABSTRACT-READ]; CrossRef-checked |  |
| **Carraro 1999** | Birkhäuser, pp. 31-51 (TRACEVE: 69-84, unresolved), 10.1007/978-3-0348-8722-9_3 | N and S of the Alps, 1960s vs 1990s | 130 relevés | climate | "milder winters have a strong effect" | Chapter hard to obtain; no rates in abstract | [ABSTRACT-READ]; CrossRef-checked |  |
| **Grund 2005** | Basic Appl Ecol 6(1):47-56, 10.1016/j.baae.2004.07.005 | Ticino | Laurophyll invasion and fire | fire, gardens | Spread from gardens since early 1970s; recolonisation of repeatedly burned sites "very low" | Via search paraphrase | [ABSTRACT-VIA-SEARCH]; CrossRef-checked |  |
| **Peñuelas & Boada 2003** | Glob Change Biol 9(2):131-140, 10.1046/j.1365-2486.2003.00566.x | Montseny NE Spain, 1945 vs current | Beech, holm oak; distribution and recruitment | warming, abandonment | Beech shifted up ca. 70 m; beech forests "being replaced by holm oak" at 800-1400 m; holm oak recruitment three times higher in isolated vs continental stands | Not partitioned; "3x" is a stand contrast not a trend; one massif | [ABSTRACT-READ]; CrossRef-checked |  |
| **Peñuelas 2007** | Ecography 30:829-837, 10.1111/j.2007.0906-7590.05247.x | Catalonia | Beech lower limit, recruitment | warming | Holm oak recruitment "more than three times higher" than beech at lower beech limit | Overlaps P&B 2003; one site | [ABSTRACT-READ]; CrossRef-checked |  |
| **Delzon 2013** | PLoS ONE 8(11):e80443, 10.1371/journal.pone.0080443 | N margin of Q. ilex, Atlantic France, 1880-2010 | Forest inventory presence/absence | time, models | Q. ilex "has colonised substantial new areas"; max rate "22 to 57 m/year", much slower than models predicted | Lateral rate not area; trigger (management change) from search summary only; full text unread | [ABSTRACT-READ]; CrossRef-checked |  |
| **Hernández 2017** | Eur J For Res 136(3):481-492, 10.1007/s10342-017-1047-2 | Navarra, N Spain, 1971 vs 2010 | Q. ilex, Q. subpyrenaica, P. sylvestris, F. sylvatica; NFI, kriging | warming vs human influence (authors' conclusion) | In the transition zone three species declined while Q. ilex expanded; results "supported a previous hypothesis of a 'mediterranization'" (from a search summary) | Presence probability from interpolated plots, two dates; attribution not formally tested; identification with the TRACEVE item probable, not confirmed | [ABSTRACT-VIA-SEARCH] |  |
| **Urli 2013** | J Veg Sci 25:147-159 (online 2013; vol. 25 = 2014), 10.1111/jvs.12079 | Pyrenees and Iberian System, one decade | 5 Fagaceae incl. Q. ilex; two Spanish NFI surveys | altitude/time | "The altitudinal distribution of the Mediterranean species at the core of their latitudinal distribution range presented no sign of change" | 10 years; counter-evidence; cite year to be checked | [ABSTRACT-READ]; CrossRef DOI |  |
| **Vayreda 2016** | Glob Change Biol 22(12):3984-3995, 10.1111/gcb.13394 | Spain, ~33,000 NFI plots, 10-12 yr | 11 species | land-use legacy, fire, climate | Changes "not always consistent with climate warming"; legacies of past land use and fire; Fagaceae expansion over formerly Pinaceae areas | Family level; Q. ilex result not in abstract | [ABSTRACT-READ] |  |
| **Padullés Cubino 2024** | J Ecol 112(12):2785-2797, 10.1111/1365-2745.14419 | Spain, last 25 yr, 68 species, ~445,000 stems | NFI, null model | climate, traits, densification | Abundance changes "primarily associated with forest densification"; random at warm and dry edge | All species; Q. ilex not in abstract | [ABSTRACT-READ] (middle part by reviewer) |  |
| **Cruz-Alonso 2019** | J Ecol 108(3):1125-1137 (online 2019), 10.1111/1365-2745.13309 | Spanish old fields | Shrub facilitation, evergreen and deciduous oaks | succession | Shrubs speed up Q. ilex colonisation | Iberian old fields | [ABSTRACT-READ]; CrossRef-checked |  |
| **Garcia-Fayos 2020** | PLOS ONE 15(10):e0239755, 10.1371/journal.pone.0239755 | Iberian System, 17 plots | Q. ilex recruitment | aridity | Aridity "drastically reduced" recruitment at the lower precipitation limit | Dry edge only | [ABSTRACT-READ] |  |
| **Perring 2020** | Front Ecol Environ 18(10):550-557, 10.1002/fee.2266 | 40 sites, 1,814 resurveyed plots, median 38 yr | Liana (ivy) frequency | drivers incl. ivy | Ivy occurrence +14 % per site on average | Understory climber, not area change | [ABSTRACT-READ]; CrossRef-checked |  |
| **Kucharski 2019** | Folia For Pol 61(3):211-221, 10.2478/ffp-2019-0020 | Central Poland | Hedera helix | climate | Fruiting ivy stands almost 10-fold since mid-1970s | Local | [ABSTRACT-READ]; CrossRef-checked |  |
| **Abrahamczyk 2024** | Biol Invasions 26, 10.1007/s10530-024-03325-2 | Bonn, 24 transects | Prunus laurocerasus | naturalisation | In 19 of 24 transects, mostly established since 2000 | Alien shrub, Germany | [ABSTRACT-READ] |  |
| **Scherrer 2021** | Ecosystems 25:199-214 (online 2021), 10.1007/s10021-021-00649-1 | Switzerland, NFI 1993-95 vs 2009-17 | All tree species | disturbance | "Disturbances led to a shift from conifer to broadleaf tree species at low elevation"; undisturbed sites persisted | EVE not isolated in abstract | [ABSTRACT-READ, truncated] |  |
| **Colombaroli 2009** | J Biogeogr 36(2):314-326, 10.1111/j.1365-2699.2008.01987.x | Peri-Adriatic Italy, Sicily, W Balkans, Holocene | Q. ilex pollen and charcoal | fire vs climate | Tests whether fire contributed to evergreen forest expansion (conclusion in abstract cut; a search summary says climate) | Millennia, not decades | [ABSTRACT-READ, truncated] |  |
| **Beffa 2025** | For Ecosyst 14:100345, 10.1016/j.fecs.2025.100345 | Central Italy, Holocene | Fagus and evergreen Quercus | climate | Fagus declined and Q. ilex expanded after 8,200 cal yr BP | Context only | [ABSTRACT-READ]; CrossRef-checked |  |
| **Niinemets & Valladares 2006** | Ecol Monogr 76(4):521-547, 10.1890/0012-9615(2006)076[0521:TTSDAW]2.0.CO;2 | 806 temperate N Hemisphere species | Trait synthesis | shade, drought tolerance | Evergreen angiosperms are the exception to the negative shade-drought tolerance correlation | Trait argument, no range change | [ABSTRACT-READ]; CrossRef-checked |  |
| **Niinemets 2011** | Trends Ecol Evol 26(3):136-142, 10.1016/j.tree.2010.12.012 | Global | CO2 hypothesis | CO2 | CO2 as "an additional explanation for the current apparent expansion of evergreen sclerophylls" | Hypothesis, untested | [ABSTRACT-READ]; CrossRef-checked |  |
| **Soh 2019** | Sci Adv 5(12):eaax7906, 10.1126/sciadv.aax7906 | ~25 yr of CO2 rise | Evergreen vs deciduous water-use efficiency | CO2 | Evergreen iWUE rose faster than deciduous | iWUE, not range expansion | [ABSTRACT-VIA-SEARCH]; CrossRef-checked |  |
| **Noce 2023** | Front For Glob Change 6:1250651, 10.3389/ffgc.2023.1250651 | Italy, 2021-2050, INFC2005 presences | MaxEnt, Q. ilex n=708 | RCP 4.5/8.5 | Holm-oak suitability change: N-NW Apennines -58.9/-29.4 %, Central Apennines -49.2/-25.3 %, S Apennines -11.3/-31.1 %, Central-E Alps -38.6/-1.8 %, W Alps -29.4/+29.2 % | Model projection; mean suitability 0.05 in W Alps | [W][PDF-CHECKED] | [[noce_2023_altitude_shift_tree_italy]] |
| **Bricca 2026** | Glob Ecol Biogeogr (no DOI in notes) | Region not stated in notes (placed in Italy by wiki context; check) | Warm broadleaved-evergreen forest habitat diversity | summer drought, winter frost | Diversity of warm habitats might fall by 2100; cold habitats gain | Region and design details not in notes | [W] | [[bricca_2026_topo_diversity]] |
| **Hickler 2012** | Glob Ecol Biogeogr 21(1):50-63, 10.1111/j.1466-8238.2010.00613.x | Europe, 2085 | Dynamic vegetation model | climate | 31-42 % of Europe into a different vegetation type; no evergreen or CO2 result stated | Do not cite for EVE or CO2 | [ABSTRACT-READ, truncated] |  |
| **Pignatti 2011** | Forest@ 8, 10.3832/efor0650-008 | Italy | Scenarios, old GCM | climate | "more Mediterranean species on lower mountains, hills and lowlands" | Old GCM | [ABSTRACT-READ] |  |
| **Suicmez & Avci 2023** | Ecol Evol 13(10):e10606, 10.1002/ece3.10606 | Mediterranean Basin, LIG to 2070 | biomod2 SDM, Q. ilex | climate | Refugia in southern coastal areas; future ranges "varied by region" | Prediction; abstract cut | [ABSTRACT-READ, truncated] |  |
| **Passos 2025** | Sci Rep 15:39201, 10.1038/s41598-025-10088-w | S Europe/N Africa, future | Marcescent oaks, niche models | climate | Submediterranean ecotone "is likely to expand its range northwards" | Deciduous marcescent oaks, projection | [ABSTRACT-READ] |  |
| **Herraiz 2025** | Ecol Indic 171:113115, 10.1016/j.ecolind.2025.113115 | Andalusia, 1994-2021 | Landsat NDVI, 2,358 NFI plots | regrowth, CO2 | Q. ilex trend upward, attributed to regrowth, reforestation and CO2 | Not Italy | [W][PDF-CHECKED] | [[herraiz_2025_phen_shifts_mediterranean]] |
| **Midolo 2026** | Sci Adv 12:eaeb2493 (DOI not confirmed from PDF) | Region and design not stated in the notes | Indicator values | light, temperature | Broadleaved evergreen forests become shadier; temperature indicator values largely stable | Note had a sign error (section 8) | [W][PDF-CHECKED] | [[midolo_2026_denser_vegetation]] |

### 5.2 Theme 2 Dieback and mortality

| Label | Reference, DOI | Region, period | Target; data / method | Driver tested | Key finding | Design limit | Tag | Wiki |
|---|---|---|---|---|---|---|---|---|
| **Pollastrini 2019** | Front For Glob Change 2:74, 10.3389/ffgc.2019.00074 | Tuscany, summer 2017 | Fagus, Q. pubescens, Q. cerris, Q. ilex, Phillyrea | drought and heat wave | Deciduous species "shed their leaves ... but apical buds and twigs were preserved"; Q. ilex and Phillyrea "suffered of total or partial crown desiccation" and "partially resprouted in 2018" | Case report; mortality not quantified | [ABSTRACT-READ]; CrossRef-checked |  |
| **Seddaiu 2025** | Forest@ 22:56-65, 10.3832/efor4934-022 | Italy, Tuscany 2012 to 2024 | Regional overview; ICP Forests Level I (~250 trees, 11 plots) | drought, heat, pathogens | Reports from Tuscany 2012, widespread after 2017, Apulia, Basilicata, Sardinia, Sicily 2024; resprouting; mortality "sporadic" | Empirical, non-systematic observations; numbers not comparable; the 48 %/17 % claim in related notes is untraced (section 8) | [W][PDF-CHECKED]; CrossRef-checked | [[seddaiu_2025_quercus_dieback]] |
| **Satta 2025 (preprint)** | SSRN, 10.2139/ssrn.5761729 | Sardinia 2023-24 | Sentinel-2, NGRDI, LogitBoost | SPEI/SPI etc. | NGRDI accuracy 0.95, kappa 0.71, F1 0.74; ~110,400 ha; "models excluding climate variables consistently overestimated dieback extent" | Preprint, not peer reviewed; garbled values in extracted text; no biotic variables; probably not independent of Seddaiu 2025 / Scanu 2025 | [W][PDF-CHECKED] | [[seddaiu_2025_mediterranean_dieback]] |
| **Puletti 2019** | J Appl Remote Sens 13(2):020501, 10.1117/1.JRS.13.020501 | Tuscany, 118 samples | Sentinel-2 vegetation-index trajectories | extreme drought | Holm oak "tolerant to short and occasional extreme events" | 7-page letter; conflicts with Pollastrini | [W][PDF-CHECKED] | [[puletti_2019_drought_forest_health]] |
| **Lloret 2004** | Glob Change Biol 10(12):2092-2099, 10.1111/j.1365-2486.2004.00870.x | Catalonia, 1994 drought | Canopy recovery in holm oak | drought | Up to 76 % of trees with complete canopy dieback; resprouting "fairly extensive"; "progressive loss of resilience" | Single event | [ABSTRACT-READ] |  |
| **Ogaya 2020** | Front For Glob Change 2:89, 10.3389/ffgc.2019.00089 | Prades, Catalonia, 20-yr throughfall exclusion | Stem mortality, thinning; MODIS NDVI | drought, temperature | Mortality higher with higher temperature and lower rainfall (R2 0.17, -0.18); thinning "strongly reduced stem mortality (especially in Q. ilex)"; NDVI vs mortality R2 0.43 | One site; coppice stems; low R2; 500 m MODIS vs small plots | [ABSTRACT-VIA-SEARCH]; CrossRef-checked |  |
| **Saura-Mas 2015** | Eur J For Res 134(2):261-272, 10.1007/s10342-014-0848-9 | Montserrat, six years after drought | Understory community response | canopy loss | Regeneration shifted toward small shrubs and herbs; defoliation could change composition if canopies do not recover | Details unseen | [ABSTRACT-VIA-SEARCH]; CrossRef-checked |  |
| **Alderotti 2023** | Sci Total Environ 904:166809, 10.1016/j.scitotenv.2023.166809 | Two stands | Dendrochronology, δ13C, SSR | genetics | Title: dieback "genetically determined" | Two stands only; claim overreaches the design (reviewer's reading) | [ABSTRACT-READ] |  |
| **Alderotti 2025** | Tree Physiol 45(5):tpaf033, 10.1093/treephys/tpaf033 | Italy | Hydraulics in defoliated Q. ilex | drought | 40-50 % loss of hydraulic conductivity in moderately/severely defoliated trees; "moderate crown defoliation may conceal severe physiological damage" | Physiology, not mapping | [ABSTRACT-READ] |  |
| **Bussotti 2021** | Forests 12(11):1476, 10.3390/f12111476 | Italy, 253 plots, 24 yr | ICP Forests defoliation | climate | Stable crown condition nationally, more extremely defoliated and dead trees; Quercus progressively less defoliated | Mediterranean evergreen woodland thin (11 of 261 plots per Seddaiu) | [ABSTRACT-READ] |  |
| **Frisullo 2018** | For Sci 64(3):290-298, 10.1093/forsci/fxx010 | Lecce, Apulia | Phytophthora cinnamomi | pathogen | P. cinnamomi "assumed" primary agent | Regional | [ABSTRACT-READ] |  |
| **Bregant 2025** | Forests 16(7):1052, 10.3390/f16071052 | Apulia | Botryosphaeriaceae and Phytophthora | pathogens | Multiple species involved in decline | Regional | [ABSTRACT-READ]; CrossRef-checked |  |
| **Colangelo 2018** | Front Plant Sci 9:1595, 10.3389/fpls.2018.01595 | S Italy | Q. cerris/pubescens (not holm oak) | drought, Phytophthora | P. quercina more frequent in non-declining trees | Not holm oak | [ABSTRACT-READ] |  |
| **Seddaiu 2020** | Forests 11(9):971, 10.3390/f11090971 | Sardinia | Q. suber, Phytophthora | pathogens | Overview of Phytophthora species in declining cork oak | Cork oak | [ABSTRACT-READ]; CrossRef-checked |  |
| **Regione Toscana 2025 (grey)** | Web page, updated 10 Dec 2025 (no DOI) | Tuscany | Survey of oak deperimento (Servizio Fitosanitario with CNR-IPSP, CREA) | drought, defoliators, pathogens | No single organism; most sites recovering; defoliators (Lymantria dispar, Tortrix viridana) plus drought and heat; pathogenicity of fungi/bacteria under evaluation | Institutional page, no figures, not peer reviewed | [page fetched, paraphrase]; grey literature |  |
| **Gentilesca 2017** | iForest 10(5):796-806, 10.3832/ifor2317-010 | W Mediterranean | Overview of oak decline | drought, temperature, pathogens, density | Drought main trigger, other causes exacerbate | Mostly ring-porous deciduous oaks | [METADATA-ONLY]; summary [ABSTRACT-VIA-SEARCH] |  |
| **Alderotti & Verdiani 2023** | AoB Plants 15(5):plad051, 10.1093/aobpla/plad051 | Mediterranean Basin | Review | traits, abiotic, biotic | "Triangle" of traits, abiotic and biotic stressors; carbon starvation or hydraulic dysfunction; winter drought hypothesised | Review; winter drought = hypothesis | [ABSTRACT-READ] (v2) / [ABSTRACT-VIA-SEARCH] (v3 note); CrossRef-checked |  |
| **Marques 2025** | Trees For People 19:100803, 10.1016/j.tfp.2025.100803 | Mediterranean-type regions, systematic review | 241 papers up to 2022 (from a secondary page) | factors | No single cause (secondary summary) | Abstract not obtained; 48 %/17 % figures not traced | [METADATA-ONLY] |  |
| **Ripullone 2026** | Forest@ 23(2):6-10, 10.3832/efor5088-023 | Italy | Workshop synthesis | stress factors | Q. ilex "drought-tolerant, is vulnerable to extreme events" | Synthesis | [ABSTRACT-READ]; CrossRef-checked |  |
| **Carnicer 2011** | PNAS 108(4):1474-1478, 10.1073/pnas.1010070108 | S Europe, 1987-2007 | ICP defoliation; Iberian mortality | climate-type drought | Widespread crown condition decline and amplified mortality | Not Italy-specific | [ABSTRACT-READ] |  |
| **Gazol & Camarero 2022** | Sci Total Environ 816:151604, 10.1016/j.scitotenv.2021.151604 | Pan-European | 310 mortality events | compound events | 143 of 310 (46 %) compound hot-summer/dry-year events | Not Italy-specific | [ABSTRACT-READ] |  |
| **Breshears 2005** | PNAS 102(42):15144-15148, 10.1073/pnas.0505734102 | SW North America | Piñon pine die-off; NDVI | global-change-type drought | ">90% of the dominant, overstory tree species ... died"; die-off visible in NDVI | One event, not Mediterranean | [ABSTRACT-READ] |  |
| **Allen 2015** | Ecosphere 6(8):art129 (CrossRef pages "1-55"; check), 10.1890/es15-00203.1 | Global | Perspective | hotter drought | "substantial debate remains" about future mortality risk | Debate paper | [ABSTRACT-READ] |  |
| **McDowell 2008** | New Phytol 178(4):719-739, 10.1111/j.1469-8137.2008.02436.x | Global | Mechanism framework | drought | Isohydric: stomatal closure, carbon starvation, reduced resistance to biotic agents | Hypothesis framework | [ABSTRACT-READ] |  |
| **Hartmann 2022** | Annu Rev Plant Biol 73:673-702, 10.1146/annurev-arplant-102820-012804 | Global | Review | heat, drought | "We currently lack both sufficient data and understanding" to say whether this is a global trend | Review | [ABSTRACT-READ] |  |
| **Mariotti 2017** | Boll Mus Ist Biol Univ Genova 79 (pages/DOI not obtained) | Liguria, Natura 2000 habitat 5110 | Box moth defoliation | Cydalima perspectalis | Six SACs affected, ~370 ha, ~70 % of area (search summary) | Verify before use; not climate or land use | [ABSTRACT-VIA-SEARCH] |  |

### 5.3 Theme 3 Remote sensing, trajectories, methods

| Label | Reference, DOI | Region, period | Target; data / method | Driver tested | Key finding | Design limit | Tag | Wiki |
|---|---|---|---|---|---|---|---|---|
| **Hermosilla 2024** | For Ecol Manage 572:122313, 10.1016/j.foreco.2024.122313 | Canada 1984-2022, 30 m | 37 species classes; RF with local samples; forward-backward HMM (per GEE catalogue) | — | "overall accuracy of 86.1 % +/- 0.14 %"; changes small (conifer share 86 to 84.9 %) | No evergreen broadleaves; early-year accuracy not in abstract; HMM details only from catalogue page; geographic predictors may mute shifts (inference) | [ABSTRACT-READ]; HMM detail [ABSTRACT-VIA-SEARCH]; CrossRef-checked |  |
| **Hermosilla 2018** | Can J Remote Sens 44(1):67-87, 10.1080/07038992.2018.1437719 | Canada 1984-2012 | Annual land cover, post-processing | — | Post-processing reduced "spurious class transitions"; OA 70.3 % +/- 2.5 % for 2005 only | One-year validation; land cover not species | [ABSTRACT-READ]; CrossRef-checked |  |
| **Thapa 2020** | Int J Remote Sens 41(10):4022-4056, 10.1080/01431161.2019.1711245 | Upper Midwest USA, 1970s-2006 | Archived Landsat + FIA; regression | — | Balsam fir R2adj 0.48, total basal area 0.39; broadleaf/conifer grouping "substantially improved" (R2adj 0.72-0.91) | Abundance regression not class maps | [ABSTRACT-READ]; CrossRef-checked |  |
| **Bogaert 2022** | IEEE TGRS 60, 10.1109/TGRS.2021.3123738 | Brazil, China, Mali 2003-2019, 300 m | HMM, Viterbi, ~6 classes | — | HMM filters errors and recovers the actual LCLUC sequence, which is "typically overestimated" in classified images | 300 m, few classes; filtering not forecasting | [ABSTRACT-READ]; CrossRef-checked |  |
| **Abercrombie & Friedl 2016** | IEEE TGRS 54(2):703-713, 10.1109/TGRS.2015.2463689 | MODIS 500 m | HMM post-processing | — | "Much of this apparent land cover change arises from errors in classification" | 500 m | [ABSTRACT-READ]; CrossRef-checked |  |
| **Torchiana 2025** | Rev Econ Stat 107(2):426-441, 10.1162/rest_a_01301 | Brazil Atlantic forest, projection to 2040 | HMM correction of transition rates | — | Uncorrected transition rates "severely biased"; corrected estimates confirmed by longitudinal data | Economics journal; forest vs non-forest; error-independence assumptions unread; no climate covariates; issue number not given by CrossRef | [ABSTRACT-READ]; CrossRef-checked |  |
| **Lu 2022 (preprint)** | arXiv:2208.07398 | Alaska | Latent trajectory model, plots + RS | climate | Climate drivers used to infer land-cover transition rates | Preprint, ecotype level, Alaska | [ABSTRACT-VIA-SEARCH] |  |
| **Salberg & Trier 2011/2012** | IGARSS 2011:2322-2325, 10.1109/igarss.2011.6049674; 2012:6749-6752, 10.1109/igarss.2012.6352556 | Brazil; Tanzania | HMM on Landsat TM (+Radarsat-2) | — | "the most likely state sequence method is recommended" | Tropical, conference papers, visual evaluation | [ABSTRACT-READ] |  |
| **Pontius & Malanson 2005** | Int J Geogr Inf Sci 19(2):243-265, 10.1080/13658810410001713434 | Central Massachusetts, 1971-1985 → 1985-1999 | CA-Markov vs persistence null | — | Models better than the null only at resolutions coarser than 2 km; "added complexity of CA_Markov is of no benefit" | One region; first-author initial (R.G. Pontius Jr) not confirmed in CrossRef (lists "Pontius, G") | [ABSTRACT-READ] |  |
| **Pontius & Lippitt 2006** | Cartogr Geogr Inf Sci 33(2):159-171, 10.1559/152304006777681706 | Massachusetts 1971 vs 1999 | Map error vs change | — | "if the accuracy of the maps were less than 77 percent, then error could explain virtually all of the observed differences" | Bi-temporal; needs confusion matrices | [ABSTRACT-READ]; CrossRef-checked |  |
| **Mertens & Lambin 2000; Mena 2008** | Ann Assoc Am Geogr 90:467-494, 10.1111/0004-5608.00205; PE&RS 74:737-751, 10.14358/pers.74.6.737 | Tropical deforestation | Class trajectories, clustering | — | Trajectory modelling projects change better than one period alone | Tropical, old methods | [ABSTRACT-READ] |  |
| **Witjes 2022** | PeerJ 10:e13573, 10.7717/peerj.13573 | Europe 2000-2019, 30 m | Ensemble ML, LUCAS + CORINE + GLAD | — | OA (weighted F1) 0.49 / 0.63 / 0.83 at 43 / 14 / 5 classes | Starts 2000; CLC-derived labels; evergreen vs deciduous class separation unknown | [ABSTRACT-READ]; CrossRef-checked |  |
| **Zhang 2024 (GLC_FCS30D)** | ESSD 16:1353-1381, 10.5194/essd-16-1353-2024 | Global 1985-2022 | Landsat CCD, 35 classes | — | OA 80.88 % (10 classes), 73.04 % (17); US yearly check 78.91 % (2000) to 80.04 % (2015); mixed-leaf forest user's accuracy 39.34 % | Main validation year 2020; 5-year steps before 2000 | [ABSTRACT-READ]; [FULLTEXT-PARTLY-READ] (page); CrossRef-checked |  |
| **Xian 2022 / Stehman 2021 (LCMAP)** | ESSD 14:143-162, 10.5194/essd-14-143-2022; RSE 265:112646, 10.1016/j.rse.2021.112646 | CONUS 1985-2017 | CCDC annual land cover | — | Agreement 82.5 %; exact-year change classes mostly below 30 % (UA 49 / PA 54 % for change footprint) | Stehman numbers from a search snippet | [ABSTRACT-READ] (Xian); [ABSTRACT-VIA-SEARCH] (Stehman); CrossRef-checked |  |
| **Garcia-Alvarez 2022 (preprint)** | EarthArXiv, 10.31223/x5qd1f | Asturias, CORINE 1990-2018 | CLC status vs change layers | production change 2012 | Mixed categories behind most detected change | Preprint; one region | [ABSTRACT-READ] |  |
| **Baglioni 2025 / 2026 (EGU abstracts)** | EGU24, 10.5194/egusphere-egu24-15620; EGU26, 10.5194/egusphere-egu26-13167 | Italian Alps and Apennines forestlines, 1984-2023 | Landsat NDVI; contextual Mann-Kendall, Theil-Sen | topography, climate, land use | Hotspots of significant trend; Alps vs Apennines contrast attributed to land-use legacy | Conference abstracts, not peer reviewed; treeline ecotone; NDVI | [ABSTRACT-READ] (conference abstracts) |  |
| **Mirici 2018** | Appl Ecol Environ Res 16(1):467-486, 10.15666/aeer/1601_467486 | E Mediterranean Turkey 1990-2014 | MLP-Markov | — | "rate of overlap was found as 89%" | No persistence null in abstract; example of weak validation | [ABSTRACT-READ] |  |
| **Sousa & Davis 2020** | RSE 247:111937, 10.1016/j.rse.2020.111937 | California foothills, ~40 yr Landsat | Temporal mixture models; evergreen/deciduous fractions | — | "74-88% accuracy for annual, deciduous, and evergreen cover fractions (n = 102)" | California; small sample | [ABSTRACT-VIA-SEARCH]; CrossRef-checked |  |
| **Radoux 2014** | Remote Sens 6(5):3965-3987, 10.3390/rs6053965 | Global | Training from outdated land cover | — | Local training on outdated maps improved accuracy over the source | Source reliability limits result | [ABSTRACT-READ] |  |
| **Bonannella 2022** | PeerJ 10:e13728, 10.7717/peerj.13728 | Europe 2000-2020 | 16 species incl. Q. ilex; 6 four-year windows | — | Potential and realised distribution maps | Probability not cover; 585 covariates | [ABSTRACT-READ]; CrossRef-checked |  |
| **Agrillo 2021** | Remote Sens 13(7):1231, 10.3390/rs13071231 | Italy | Sentinel-2 + plots + RF | — | OA 87 % (EUNIS II), 76.14 % (III); broadleaved evergreen 91 % | Single epoch | [ABSTRACT-READ]; CrossRef-checked |  |
| **Pesaresi 2020 (x2)** | Remote Sens 12(7):1132, 10.3390/rs12071132; Diversity 12(8):313, 10.3390/d12080313 | Central Italy | Landsat 8 NDVI functional PCA | — | Separates holm-oak from black-hornbeam communities, OA 87.5 % | Single period | [ABSTRACT-READ]; CrossRef-checked |  |
| **Mancino 2014** | iForest 7(2):75-84, 10.3832/ifor0909-007 | Basilicata, 1984 vs 2010 | Landsat TM NDVI differencing | — | 91.8 % accuracy for forest expansion; forest +19.7 % | Two dates; forest vs non-forest | [ABSTRACT-READ]; CrossRef-checked |  |
| **Padial-Iglesias 2022** | Forests 13(3):475, 10.3390/f13030475 | Iberian transect, 1987-2002-2017, 30 m | 30 m maps, BRT, 30 variables | precipitation, temperature, radiation | For broadleaf evergreen forests drivers were "precipitation, temperature and solar radiation"; proximity to previous forest key | Forest types not species; three dates; spatial CV not stated | [ABSTRACT-READ]; CrossRef-checked |  |
| **Aubard 2019** | Remote Sens 11(5):525, 10.3390/rs11050525 | Portugal 1984-2017 | Landsat NDVI, Mann-Kendall, contextual MK, Theil-Sen | — | "Oak stands are declining in many regions of southern Europe"; 12 % of oak area with significant decreasing trends (search summary) | Index in stable mask, not maps | [ABSTRACT-READ]; CrossRef-checked |  |
| **Viana-Soto 2020** | Remote Sens 12(9):1499, 10.3390/rs12091499 | Spanish pine forests | LandTrendr, K-means, GWR | post-fire climate | Four recovery trajectory classes; recovery "highly sensitive to post-fire climate" | Pine, fire | [ABSTRACT-READ]; CrossRef-checked |  |
| **Giannetti 2020** | Remote Sens 12(22):3720, 10.3390/rs12223720 | Mediterranean coppice (country not stated in notes) | GFC vs new method | — | GFC producer's accuracy 0.00-0.38 | Region not stated | [ABSTRACT-READ]; CrossRef-checked |  |
| **Laidi 2026** | Ecol Eng Environ Technol 9:110-131, 10.12912/27197050/226093 | Morocco 1984-2024 | NDVI, STL, PELT, SPEI | drought | ~187,700 ha dieback, holm oak 142,591 ha (search summary) | Low-tier venue; numbers not to be cited; not looked up in CrossRef | [ABSTRACT-VIA-SEARCH] |  |
| **Verhulst 2024** | Remote Sens 16(14):2653, 10.3390/rs16142653 | Temperate forests, Sentinel-2 | 5 species, cross-year transfer | — | Cross-year OA loss 2.30-14.92 points | Not Mediterranean | [ABSTRACT-READ]; CrossRef-checked |  |
| **Chastain 2007** | Photogramm Eng Remote Sens 73(5):563-575, 10.14358/PERS.73.5.563 | Appalachia | Leaf-off Landsat ETM, evergreen understory | — | OA 87.1 %, Khat .806; 82.9 % in Allegheny Plateau | One date, US | [W][PDF-CHECKED] | [[chastain_2007_eve_landsat_understory]] |
| **Atkins 2018** | Ecosphere 9(10):e02404, 10.1002/ecs2.2404 | W Virginia watershed, 1986-2011 | Leaf-off Landsat 5, RF | — | "0.14 increase in winter NDVI, with a 52 % relative increase in shrub coverage" | One watershed | [ABSTRACT-READ]; CrossRef-checked |  |
| **Oreti 2020** | Biodivers Conserv 29(8):2605-2622, 10.1007/s10531-020-01991-x | Apennine beech forests | VHR leaf-off imagery, Taxus and Ilex | — | Producer 0.77 / user 0.80 | VHR, not Landsat | [ABSTRACT-READ] |  |
| **Bayle 2024** | Ecography e07394, 10.1111/ecog.07394 | Alps, non-forest above 1500 m | Landsat summer NDVI | observation density | "almost 50 %" of estimated greening explained by observation density; bias "less pronounced" in lower forest ecotone, false trends up to 30 % | Non-forest, summer only; transfer to winter EVE is inference | [W][PDF-CHECKED] | [[bayle_2024_landsat_greening_inflated]] |
| **Hiebl 2025** | Int J Appl Earth Obs Geoinf 142:104734, 10.1016/j.jag.2025.104734 | Test sites are parks (region not stated in notes) | Sentinel-2 EVE cover regression | — | RMSE ~17-24 % cover; "all models overestimate EVE cover in all test sites except GEN" | Own prior work; Sentinel-2 only | [W][PDF-CHECKED] | [[hiebl_2025_pretraining]] |
| **Pasquarella 2022 / Cohen 2017 / Forkel 2013** | JAG 110:102806, 10.1016/j.jag.2022.102806; Forests 8(4):98, 10.3390/f8040098; Remote Sens 5(5):2113-2144, 10.3390/rs5052113 | Algorithm comparisons | LandTrendr, CCDC, 7 algorithms, NDVI breakpoints | — | Seven algorithms agree on undisturbed forest but show "little agreement about which pixels were affected"; breakpoint over-estimation can give "wrong or even opposite trend estimates" | Disturbance / NDVI focus | [ABSTRACT-READ]; CrossRef-checked (Pasquarella, Forkel) |  |
| **Blois 2013; Damgaard 2019** | PNAS 110(23):9374-9379, 10.1073/pnas.1220228110; Trends Ecol Evol 34(5):416-421, 10.1016/j.tree.2019.01.013 | Pollen (E North America); critique | Space-for-time | — | Space-for-time ~72 % as accurate as time-for-time; "problematic, especially in nonstationary environments" | Not forest-species mapping | [ABSTRACT-READ]; CrossRef-checked (Blois) |  |
| **Roberts 2017; Ploton 2020; Dormann 2007; Meyer & Pebesma 2021** | Ecography 40(8):913-929, 10.1111/ecog.02881; Nat Commun 11:4540, 10.1038/s41467-020-18321-y; Ecography 30:609-628, 10.1111/j.2007.0906-7590.05171.x; Methods Ecol Evol 12(9):1620-1633, 10.1111/2041-210x.13650 | Validation methods | Spatial CV, autocorrelation, area of applicability | — | Non-spatial CV gives "serious underestimation of predictive error"; spatial validation "quasi-null predictive power" for forest biomass (Ploton) | Issue numbers of Roberts (8) and Meyer & Pebesma (9) filled from memory: not verified | [ABSTRACT-READ]; CrossRef-checked |  |

### 5.4 Theme 4 Interplay: land use, climate, regional context

| Label | Reference, DOI | Region, period | Target; data / method | Driver tested | Key finding | Design limit | Tag | Wiki |
|---|---|---|---|---|---|---|---|---|
| **Gasparini & Tabacchi 2022** | Springer, pp. 545-568, 10.1007/978-3-030-98678-0_13 | Italy INFC2005 vs INFC2015 | Inventory totals | — | Forest 8,759,202 → 9,085,186 ha (+3.7 %); other evergreen broadleaved +33.6 % (residual class); holm oak 643,052 ha, growing stock +34.2 % | Samples not independent; no tests; INFC1985 not harmonised | [W][FULLTEXT-PARTLY-READ] | [[gasparini_2022_nfi_italy]] |
| **Garbarino 2020** | Landsc Ecol 35(12):2679-2694, 10.1007/s10980-020-01013-9 | Italian Alps and Apennines | CLC regional + aerial images, 16 sites | legacy, distance to forest, elevation | Forest expansion "the dominant landscape transition", 0.6 %/yr (search summary) | Rate is all forest, reference unclear; not national | [ABSTRACT-VIA-SEARCH] [SEARCH-SUMMARY] |  |
| **Malandra 2018** | Forests 9(9):551, 10.3390/f9090551 | Apennines, 51 manuscripts / 57 case studies | Meta-analysis | — | Forest +78 %, cropland -49 %, grassland -19 % | Mostly local; mean not defined | [ABSTRACT-READ]; CrossRef-checked |  |
| **Vitali 2018** | J Veg Sci 29(2):189-199, 10.1111/jvs.12598 | 776 municipalities, CORINE 1990-2012 | Land-cover change | population, climate | Broad-leaf forest +1 %, mixed +4 %, conifers +2 %, shrublands +7 % | No evergreen split | [ABSTRACT-READ]; CrossRef-checked |  |
| **Santoro & Piras 2023** | Forests 14(5):921, 10.3390/f14050921 | Italian protected areas since 1936 | Historical maps | — | Forest +33.1 % to +45.2 %; most 1936 forests were coppice | Protected areas | [ABSTRACT-READ]; CrossRef-checked |  |
| **Ottaviano 2026** | Forest@ 23(2):11-25, 10.3832/efor5002-023 | Italy IUTI 1990-2022 | Point inventory | — | Woodland surpasses arable land in 2022 | Coarse classes | [ABSTRACT-READ]; CrossRef-checked |  |
| **Falcucci 2007** | Landsc Ecol 22(4):617-631, 10.1007/s10980-006-9056-4 | Italy 1960-2000 | Three LULC maps | — | Forest increase mostly in mountains (search summary) | Abstract unread | [SEARCH-SUMMARY]; CrossRef-checked |  |
| **Ascoli 2024** | Ann Silvic Res 46(2):4, 10.12899/asr-2264 | Italy IUTI 1990-2008, 1,206,198 points | Land-use change vs fire | — | Change toward forest correlates with large fires | Correlation | [ABSTRACT-READ]; CrossRef-checked |  |
| **Pausas & Millán 2019** | BioScience 69(2):143-151, 10.1093/biosci/biy157 | Mediterranean Basin | Perspective | abandonment, fire, coastal drought | "The current balance is still toward greening ... however, it is likely to switch with increasing warming" | No data in abstract | [ABSTRACT-READ] |  |
| **Brunetti 2006** | Int J Climatol 26(3):345-381, 10.1002/joc.1251 | Italy, two centuries | Homogenised series | — | About 1 K per century; recent maximum rose faster than minimum; series ends about 2000 | Ends about 2000 | [ABSTRACT-READ] |  |
| **Pascale & Ragone 2025** | Int J Climatol 45(8):e8827, 10.1002/joc.8827 | Italy 1901-2023 | Drought identification | — | Seven widespread multi-year droughts incl. 2006-08, 2011-13, 2017-18, 2021-23 | No attribution | [ABSTRACT-READ]; CrossRef-checked |  |
| **Spinoni 2017** | Glob Planet Change 148:113-130, 10.1016/j.gloplacha.2016.11.013 | Pan-Europe | SPEI vs SPI trends | — | SPEI "remarkable drying tendency" in S and E Europe; SPI moderate opposite tendency in the south | Pan-European | [ABSTRACT-READ]; CrossRef-checked |  |
| **Mombrini 2025** | Hydrol Earth Syst Sci 29(10):2255-2273, 10.5194/hess-29-2255-2025 | W Po basin, 60 yr | Meteorological drought | — | Limited significant precipitation decrease; "no trend ... at a region-wide level" | Piedmont/Aosta only | [ABSTRACT-READ] |  |
| **Becherini 2024; Aschale 2024** | Climate 12(12):218, 10.3390/cli12120218; Water 16(18):2593, 10.3390/w16182593 | Padua 1725-2023; Sicily 1950-2023 | Drought indices | — | Supports SPEI drying tendency | Local | [ABSTRACT-READ]; CrossRef-checked |  |
| **Vicente-Serrano 2014** | Environ Res Lett 9(4):044001, 10.1088/1748-9326/9/4/044001 | S Europe / Iberia | Drought severity | temperature | Increasing drought severity caused by temperature rise | Not Italy-specific | [ABSTRACT-READ] |  |
### 5.5 Resolved conflicts and flagged identifiers (for the chart)
- **Hernández 2017.** v2 listed it as [still unverified; as printed in TRACEVE] with DOI 10.1007/s10342-017-1047-2. The v3 note matches it to the "mediterranization" claim through a search summary and the Semantic Scholar record: tag [ABSTRACT-VIA-SEARCH], not higher. The "Peñuelas" part of the proposal's in-text item is most likely a conflation with Peñuelas & Boada 2003; this is **unresolved** and needs the user to check the proposal sentence.
- **Urli 2013 / 2014.** CrossRef year 2013 (online) versus volume 25 (2014): decide which year to cite.
- **Allen 2015.** CrossRef pages "1-55" for article 129: check the article number.
- **Pontius & Malanson 2005.** First-author initial per the paper is R.G. Pontius Jr; CrossRef lists "Pontius, G": not confirmed.
- **Roberts 2017 (issue 8) and Meyer & Pebesma 2021 (issue 9).** Issue numbers were filled from memory in the note: **not verified**.
- **Torchiana 2025.** CrossRef gives volume 107, pages 426-441, issue number not given; v3 note writes 107(2): treat "(2)" as not verified.
- **Kennedy 2010, Verbesselt 2010, Aldwaik & Pontius 2012, Olofsson 2014.** v2: [SNIPPET/TLDR-ONLY] or [ABSTRACT-PARAPHRASE]; v3 note: [ABSTRACT-VIA-SEARCH]. Both statuses mean paraphrase level; the v3 tag is used and the difference is noted.
- **Conedera 2018, Walther 2005, Walther 2001/2002.** Conedera cited as 2018 (online 2017); Walther 2005 is holly in Scandinavia, not Ticino; Walther 2001 chapters are [METADATA-ONLY].
- **Items seen but not charted** (too weak or off-topic): Cailleret et al. Port-Cros (title, DOI, numbers unobtained; HAL hal-05492374); Bec et al. 2020 (unidentified); Ekológia 2025 Algeria and an Ouargla repository study (authors, volume not checked); Montecchio 2004, Gentilesca AISF proceedings, Basilicata and Casentino land-change snippets, Tuscany Sentinel-2 NDVI/NDWI study (all snippet-level); Di Gennaro 2019 (DOI 10.1446/95595 not resolvable, snippet); Cardillo 2020 (bioRxiv) and Pérez Álvarez 2026 (SSRN) (metadata only); Lehtijärvi 2014 (metadata only); Yang 2023 Sentinel-2 understory (snippet); Zenodo 7054338 (snippet); Potapov 2015 (metadata only); Scanu 2025 conference abstract and Alderotti thesis (snippet); Fehr 2024 GEC (metadata only).

---

## 6. Reading starting point

### 6.1 Tier A: deep reads (8)
| # | Paper | DOI | Why (storyline) | Change from v2 |
|---|---|---|---|---|
| 1 | Conedera et al. 2018 [W] | 10.1007/s10113-017-1212-7 | S1 drivers; counterweight to the "milder winters" headline | Unchanged (re-read the wiki note and PDF) |
| 2 | Alessi et al. 2019 [W] | 10.1111/jvs.12743 | S1 non-equilibrium, Italy-wide | Unchanged |
| 3 | Peñuelas & Boada 2003 | 10.1046/j.1365-2486.2003.00566.x | S1 beech-to-holm-oak precedent; origin of the framing in the proposal | Unchanged (get the PDF) |
| 4 | Delzon et al. 2013 | 10.1371/journal.pone.0080443 | S1, S4 only observed *Q. ilex* colonisation rate | Unchanged |
| 5 | **Hernández et al. 2017** | 10.1007/s10342-017-1047-2 | S1 only inventory study of *Q. ilex* gain against cooler-adapted species; read to settle the identification and the driver conclusion | **New.** Replaces Bogaert in the eight because it is the only new item that bears on the central claim and is currently paraphrase-level; also read Vayreda 2016 for *Q. ilex*-specific results |
| 6 | Padial-Iglesias et al. 2022 | 10.3390/f13030475 | S3, S4 closest design twin (30 m maps, drivers, uncertainty) | Unchanged |
| 7 | Hermosilla et al. 2024 | 10.1016/j.foreco.2024.122313 | S3 annual species maps and HMM smoothing; the catalogue entry confirms HMM but the paper is unread | Unchanged, now with an explicit task: read the HMM design and early-year accuracy |
| 8 | Thapa et al. 2020 | 10.1080/01431161.2019.1711245 | S3 leaf type versus species hindcast limits | Unchanged |

Justification for the swap: Bogaert 2022 (300 m, about six classes, filtering only) is demoted to the first Tier B item because Hermosilla 2024 now carries the HMM role at 30 m and Torchiana 2025 carries the transition-rate role. For dieback no new deep read is added: re-read [[seddaiu_2025_quercus_dieback]] and Pollastrini 2019 first, since the wiki already holds the Italian chronology.

### 6.2 Tier B: short reads (abstract plus one section), by storyline

DOIs as recorded in the reference list (section 9); check before BibTeX export.

**S1 spread**

| Paper | DOI |
|---|---|
| Vayreda et al. 2016 | 10.1111/gcb.13394 |
| Padullés Cubino et al. 2024 | 10.1111/1365-2745.14419 |
| Urli et al. 2013/2014 | 10.1111/jvs.12079 |
| Urli et al. 2015 | 10.1007/s11258-014-0426-8 |
| Carraro et al. 1999 | 10.1007/978-3-0348-8722-9_3 |
| Alessi et al. 2021 | 10.1007/s12210-021-00981-7 |
| Berger et al. 2007 | 10.1127/0340-269x/2007/0037-0523 |
| Walther et al. 2007 | 10.1111/j.1466-8238.2007.00328.x |
| Scherrer et al. 2021/2022 | 10.1007/s10021-021-00649-1 |
| Cruz-Alonso et al. 2019/2020 | 10.1111/1365-2745.13309 |
| Niinemets & Valladares 2006 | 10.1890/0012-9615(2006)076[0521:TTSDAW]2.0.CO;2 |
| Svenning & Skov 2004 | 10.1111/j.1461-0248.2004.00614.x |

**S2 dieback**

| Paper | DOI |
|---|---|
| Pollastrini et al. 2019 | 10.3389/ffgc.2019.00074 |
| Alderotti et al. 2025 | 10.1093/treephys/tpaf033 |
| Alderotti & Verdiani 2023 | 10.1093/aobpla/plad051 |
| Lloret et al. 2004 | 10.1111/j.1365-2486.2004.00870.x |
| Ogaya et al. 2020 | 10.3389/ffgc.2019.00089 |
| Bregant et al. 2025 | 10.3390/f16071052 |
| Frisullo et al. 2018 | 10.1093/forsci/fxx010 |
| Bussotti et al. 2021 | 10.3390/f12111476 |
| Hartmann et al. 2022 | 10.1146/annurev-arplant-102820-012804 |
| Allen et al. 2015 (article number to check) | 10.1890/es15-00203.1 |
| Regione Toscana page (grey; defoliators) | no DOI (web page) |

**S3 methods**

| Paper | DOI |
|---|---|
| Bogaert et al. 2022 | 10.1109/TGRS.2021.3123738 |
| Abercrombie & Friedl 2016 | 10.1109/TGRS.2015.2463689 |
| Pontius & Lippitt 2006 | 10.1559/152304006777681706 |
| Pontius & Malanson 2005 | 10.1080/13658810410001713434 |
| Torchiana et al. 2025 | 10.1162/rest_a_01301 |
| Olofsson et al. 2014 | 10.1016/j.rse.2014.02.015 |
| Zhang et al. 2024 | 10.5194/essd-16-1353-2024 |
| Aubard et al. 2019 | 10.3390/rs11050525 |
| Radoux et al. 2014 | 10.3390/rs6053965 |
| Roberts et al. 2017 | 10.1111/ecog.02881 |
| Meyer & Pebesma 2021 | 10.1111/2041-210x.13650 |
| Bayle et al. 2024 [W] | 10.1111/ecog.07394 |

**S4 interplay**

| Paper | DOI |
|---|---|
| Gasparini & Tabacchi 2022, chapter 13 [W] | 10.1007/978-3-030-98678-0_13 |
| Garbarino et al. 2020 | 10.1007/s10980-020-01013-9 |
| Malandra et al. 2018 | 10.3390/f9090551 |
| Pausas & Millán 2019 | 10.1093/biosci/biy157 |
| Noce et al. 2023 [W] | 10.3389/ffgc.2023.1250651 |
| Spinoni et al. 2017 | 10.1016/j.gloplacha.2016.11.013 |

### 6.3 Tier C: cite only
Tool-level or low-evidence items: Kennedy 2010, Verbesselt 2010, Zhu & Woodcock 2014, Hamed & Rao 1998, Getis & Ord 1992, Yue 2002, Neeti & Eastman 2011 (method citations); Walther 2001/2002, Carraro et al. 2001 (metadata only); Gentilesca 2017 (mostly deciduous oaks); Marques 2025 (metadata only until the PDF is read); Hickler 2012 (no EVE content); Mirici 2018 (example of weak validation); Baglioni 2025/2026 and Satta 2025 (label as conference abstract and preprint); Laidi 2026 (do not cite numbers); Palmero-Iniesta 2021, Falcucci 2007, Ferretti 2018, Marchetti 2012, Ottaviano 2026, Santoro & Piras 2023, Vitali 2018 (background land use).

### 6.4 Suggested reading order for building the Introduction
1. Conedera 2018 and Berger & Walther 2006 notes, then Alessi 2019: the southern-Alps baseline and non-equilibrium.
2. Peñuelas & Boada 2003, Hernández 2017, Delzon 2013, then Urli 2013 and Vayreda 2016: holm oak elsewhere, and the climate-versus-regrowth dispute.
3. Gasparini chapter 13, Malandra 2018, Garbarino 2020, Pausas & Millán 2019: Italian land-use baseline and what the inventory does and does not show.
4. Seddaiu 2025 note, Pollastrini 2019, Alderotti 2025, Lloret 2004, Hartmann 2022 and Allen 2015: the loss side and its concepts; then the pathogen papers.
5. Padial-Iglesias 2022, Hermosilla 2024, Thapa 2020, Bogaert 2022: how change maps are built and what they can claim.
6. Pontius & Lippitt 2006, Pontius & Malanson 2005, Torchiana 2025, Olofsson 2014: uncertainty, then forecasting limits.

---

## 7. Gaps and what the paper can claim

### 7.1 Evidence gaps (empirical)
- No observed, spatially explicit change study of EVE or *Q. ilex* in Italy beyond Ticino-region work (all T1 Italian rows are plot, model or palaeo studies).
- No Italian winter-minimum-temperature trend source and no national gridded SPEI trend source.
- No quantified Italian mortality rate for *Q. ilex*; no peer-reviewed spatial quantification of 2022 or 2024 dieback; no data showing gain and loss together in one region.
- Pathogen versus climate attribution unresolved; the Marques 2025 arbitration is unread.
- Mechanism evidence (disturbance windows, coppice abandonment effect on *Q. ilex*) lacks Italian tests; the coppice claim is expert reasoning only.
- Italian-language and Italian-journal literature is largely unsearched.

### 7.2 Method gaps
- No validated early-year (1980s) leaf-type or species accuracy for Mediterranean Europe; reference labels for the 1980s are the bottleneck.
- No independent comparison of HMM-smoothed and raw annual species maps; HMM design in Hermosilla 2024 unread.
- No Mann-Kendall, Theil-Sen or Getis-Ord application to categorical species series; no HMM with climate covariates on annual 30 m forest-species maps.
- Observation-density effects on classified maps untested; winter-signal detectability under deciduous canopy at 30 m untested in Europe.
- Persistence-null validation and spatial block cross-validation are advised by the literature but not yet shown for such maps.

### 7.3 Novelty claim and its honest limits
- **Wording:** "To our knowledge, no published study has quantified decadal changes of evergreen broad-leaved species or leaf-type cover in Italy with annual 30 m maps, and none has combined HMM-based temporal consistency, climate and land-use drivers, hotspot statistics and forecasting for this target."
- **Limits:** absence is not proven. Google Scholar, Italian-language queries and Italian journals were only partly searched; OpenAlex and Semantic Scholar forward-citation checks were blocked; most abstracts but few full texts were read. Partial precedents exist (Hermosilla 2024, Torchiana 2025, Lu 2022, Baglioni, Padial-Iglesias 2022, Witjes 2022, Bonannella 2022, Agrillo 2021, Mancino 2014). Do not claim novelty for the principle that Landsat can map evergreen change (Chastain 2007, Atkins 2018, Sousa & Davis 2020). The EGU24 statement by the TRACEVE team is a self-citation.

### 7.4 Follow-up searches and items to fetch via uibk access
1. Hernández 2017, Urli 2015 (full text), Vayreda 2016: *Q. ilex* results.
2. Walther 2001 chapters, Walther 2002, Carraro 2001, Larcher 2000 (Plant Biosyst 134(3), freezing tolerance, metadata only), Sakai & Larcher 1987.
3. Cailleret et al. Port-Cros study (HAL hal-05492374): title, DOI, 68 %/64 % leaf-deficit figures, 12 %/18 % mortality, Bec et al. 2020.
4. Hermosilla 2024 full text (HMM design, early-year accuracy).
5. Di Gennaro et al. 2019 (CLC 1990-2018 Italy; class 323/324 figures); Zenodo record 7054338 (Mediterranean forest types map: authors, accuracy); Witjes 2022: whether evergreen and deciduous broadleaves are separate classes.
6. ISPRA frost-day indicator and Toreti & Desiato 2007; a peer-reviewed national gridded SPEI trend.
7. Garbarino 2020 post-print (iris.unito.it/handle/2318/1765594) and Malandra 2019 (iris.unito.it/handle/2318/1723103).
8. Verbatim abstracts: Kennedy 2010, Verbesselt 2010, Olofsson 2014, Aldwaik & Pontius 2012, Stehman 2021, Hamed & Rao 1998, Falcucci 2007, Zhu & Woodcock 2014, Pasquarella 2018, Senf 2015.
9. Gehring 2026 and Scherrer 2021 for fire and disturbance by EVE in Ticino; Marques 2025 PDF for the 48 %/17 % figures; the Tuscany Sentinel-2 NDVI/NDWI study (identify authors).
10. Cerabolini et al. 2008 (Varese laurophyllisation estimate); Ferretti et al. 2018 (1936 Forest Map: is holm oak mapped?); INFC holm-oak (lecceta) area tables; De Natale & Gasparini 2011.
11. Google Scholar (Italian): laurofillizzazione, espansione del leccio, mediterraneizzazione dei boschi, cedui di leccio abbandono, leccio and Landsat/serie storica; journal-internal searches in Forest@, iForest, L'Italia Forestale e Montana, Annali di Botanica, Plant Biosystems.
12. Forward citations of Conedera 2018, Alessi 2019, Delzon 2013, Padial-Iglesias 2022, Hermosilla 2024, Seddaiu 2025 when API budgets reset.

### 7.5 Unresolved items needing user input
- **Jump 2009:** not identified. The real Jump paper found is Jump, Hunt & Peñuelas 2006. Hampe & Jump 2011 is only a guess. Please supply title and journal.
- **Trindade 2020:** not identified. Please supply title and journal.
- The proposal sentence behind "Hernández / Peñuelas mediterranization" (see 5.5), and the exact reference for "Hobbs" if still wanted.

---

## 8. Wiki housekeeping

Nothing here claims any wiki file was changed; these are findings only.

### 8.1 Verified errors in wiki notes (from v2, compact)
- **midolo_2026_denser_vegetation:** sign error (PDF p.2: light positive for coniferous, negative for broadleaved evergreen); temperature claim for broadleaved evergreen not stated in text; the 03-paper "even over a 60 year window" overstates; DOI not confirmed.
- **chelli_2017_climate:** lists "EVE expansion" not in the PDF; the 03 paper cites it for wildfires although post-fire ecology was excluded.
- **herraiz_2025_phen_shifts_mediterranean:** species typo (P. pinea listed as P. nigra); study area is Andalusia; "slow changing systems" and "calcareous substrate, core range" not in the PDF.
- **gasparini_2022_nfi_italy:** mixes forest and total wooded land; use forest 9,085,186 ha (+3.7 %) or wooded 11,054,458 ha (+5.6 %).
- **fady_2025:** species inventory, silent on laurophyll/sclerophyll monitoring. **bayle_2024:** correct, but non-forest above 1500 m, summer only.
- **albrich_2019 and albrich_2020:** same paper (GCB 26:4013-4027); keep one. **wessely_2023:** published 2024.
- Notes without EVE-change evidence: dyderski_2025, schuldt_2020, bolyn_2022, mauri_2017, calvia_2022.
- **chastain_2007:** title is "Landsat ETM". **noce_2023:** "15 million hectares" conflicts with Gasparini. **soto_2025:** first author Viana-Soto; 22 %/79 %/12 % are Europe-wide. **seddaiu_2025_mediterranean_dieback:** first author Satta, SSRN preprint; consider renaming.
- **alessi_2019:** "<50 %" and "9 of 11" are both correct. **conedera_2018:** cite as 2018. Several notes lack DOIs; PDF and note filename mismatches; `fischer_2025_glocal_canopy_atlas` and `sattstools` have notes but no PDF; `disskonzept.pdf` has no note; TRACEVE cites Response items for Zellweger and Forzieri.

### 8.2 Citation problems in `03_papers/03_tree_species_cover_landsat.md` (from v2)
| Location | Citation and claim | What the PDF says |
|---|---|---|
| lines 41, 190 | noce_2023: limited by temperature; EVE favoured by milder winters and drought | Contradicts: no evergreen/winter analysis; projects reduced holm-oak suitability in 4 of 5 sections |
| line 42 | chelli_2017: wildfires change composition | Post-fire ecology excluded |
| line 43 | fady_2025: limited monitoring | Not in the PDF |
| lines 41, 79, 86 | herraiz_2025: core-range greening, calcareous substrate | Andalusia NDVI 1994-2021, regrowth and CO2 |
| line 79 | schuldt_2020: submediterranean summers | Central European 2018 beech drought |
| lines 175, 177 | jin_2023: poleward shift; canopy faster than understory | Spatial gradient in 10 Chinese plots; temporal claim hypothesised |
| lines 185, 213 | soto_2025: 22 % of Italian forest disturbed | Europe-wide figures |
| line 191 | albrich_2019: climate-space velocity | iLand simulation in Stubai; duplicate of 2020 |
| line 212 | bayle_2024: overestimation of EVE earlier | Early-year underestimation of annual maximum NDVI in alpine non-forest |
| line 41 (Berger) | EVE expansion "more drought resistant" | Berger attributes it to reduced competition |

### 8.3 New findings in this round
- **The unverified "48 % pathogens versus 17 % climate" figure is repeated in the wiki.** `02_concepts/mediterranean_holm_oak_dieback.md` line 39 states it and attributes it to `[[seddaiu_2025_mediterranean_dieback]]`; `01_notes/seddaiu_2025_quercus_dieback.md` line 88 says other sources report that most oak-decline studies attribute decline to pathogens, citing Marques et al. 2025 via the preprint note. A text search of `seddaiu_2025_mediterranean_dieback.md` found no "48", "17 %" or "Marques", so the chain may not hold. The number could not be traced to Marques 2025 (abstract unobtainable); mark "needs verification" until the PDF is read. The CrossRef first author is "Marques Marco": cite as Marques M. et al.
- **Satta 2025 and Seddaiu 2025 are probably not independent.** Both give about 110,000 ha for Sardinia 2024 (110,400 ha in the Satta note, "~110,000 ha" in the Seddaiu note); authors overlap (Seddaiu, Scanu, Piras, Ruiu). The Scanu 2025 conference abstract (over 100,000 ha in Sardinia by Sentinel-2) is probably the same source. Independence is unverified; do not present them as converging evidence.
- The Seddaiu note also reports "~25 % holm oak mortality in already declining areas" and a 40-60 % figure; the same note states these numbers are not comparable or validated.
- Wiki gaps: no notes on Peñuelas & Boada 2003, Delzon 2013, Hernández 2017, Vayreda 2016, Walther papers, Hermosilla 2024, trajectory-method papers, Pontius papers, Torchiana 2025. Possible concept pages: `landsat_time_series_change_detection`, `area_adjusted_change_estimation`, `space_for_time_substitution`, `land_abandonment_italy`.

### 8.4 PDFs to add to `00_literature/` (priority order)
1. Peñuelas & Boada 2003
2. Delzon et al. 2013
3. Hernández et al. 2017 (and Vayreda 2016)
4. Padial-Iglesias et al. 2022
5. Hermosilla et al. 2024
6. Thapa et al. 2020
7. Bogaert et al. 2022 with Abercrombie & Friedl 2016
8. Pontius & Lippitt 2006, Pontius & Malanson 2005, Olofsson 2014, Torchiana 2025
9. Pollastrini 2019, Alderotti 2025, Marques 2025
10. Garbarino 2020 post-print, Malandra 2019
11. Alessi 2021, Berger 2007, Carraro 1999, Walther 2005 and 2007
12. Urli 2013/2015, Hartmann 2022, Allen 2015
13. Blois 2013, Niinemets 2011, Bonannella 2022, Aubard 2019, Agrillo 2021
14. Roy 2016, Crawford 2023, Bussotti 2021, Alderotti 2023, Lloret 2004, Pascale & Ragone 2025, Spinoni 2017

---

## 9. Reference list

Tags as in section 0. "CrossRef-checked" only where a note says so. [W] entries carry the wiki link. Entries marked [DOI from CrossRef] had the DOI returned by CrossRef in the v3 concepts note (other metadata not separately checked).

### 9.1 Theme 1: spread, drivers, concepts
- Conedera, M., Wohlgemuth, T., Tanadini, M., Pezzatti, G.B. (2018). Drivers of broadleaved evergreen species spread into deciduous forests in the southern Swiss Alps. Regional Environmental Change 18: 425-436. https://doi.org/10.1007/s10113-017-1212-7. [W][PDF-CHECKED] [[conedera_2018_drivers_evergreen]]
- Alessi, N., Tesitel, J., Zerbe, S., Spada, F., Agrillo, E., Wellstein, C. (2019). Ancient refugia and present-day habitat suitability of native laurophylls in Italy. Journal of Vegetation Science 30: 564-574. https://doi.org/10.1111/jvs.12743. [W][PDF-CHECKED] [ABSTRACT-READ] [[alessi_2019_refugia]]
- Alessi, N., Wellstein, C., Spada, F., Zerbe, S. (2021). Population structure of Laurus nobilis L. in Central Italian forests: evidence for its ongoing expansion. Rendiconti Lincei 32(2): 365-376. https://doi.org/10.1007/s12210-021-00981-7. [ABSTRACT-READ] CrossRef-checked
- Berger, S., Walther, G.-R. (2006). Distribution of evergreen broad-leaved woody species in Insubria in relation to bedrock and precipitation. Botanica Helvetica 116(1): 65-77. https://doi.org/10.1007/s00035-006-0749-8. [W][PDF-CHECKED] [[berger_2006_distribution_eve]]
- Berger, S., Söhlke, G., Walther, G.-R., Pott, R. (2007). Bioclimatic limits and range shifts of cold-hardy evergreen broad-leaved species at their northern distributional limit in Europe. Phytocoenologia 37(3-4): 523-539. https://doi.org/10.1127/0340-269x/2007/0037-0523. [ABSTRACT-READ via dissertation] CrossRef-checked
- Walther, G.-R., Berger, S., Sykes, M.T. (2005). An ecological 'footprint' of climate change. Proceedings of the Royal Society B 272(1571): 1427-1432. https://doi.org/10.1098/rspb.2005.3119. [ABSTRACT-READ] CrossRef-checked
- Walther, G.-R., Gritti, E.S., Berger, S., Hickler, T., Tang, Z., Sykes, M.T. (2007). Palms tracking climate change. Global Ecology and Biogeography 16(6): 801-809. https://doi.org/10.1111/j.1466-8238.2007.00328.x. [ABSTRACT-READ] CrossRef-checked
- Walther, G.-R. (2001). Laurophyllisation, a sign of a changing climate? In: Tasks for Vegetation Science, pp. 207-223. https://doi.org/10.1007/978-94-015-9686-2_13. [METADATA-ONLY] [DOI from CrossRef]
- Walther, G.-R., Carraro, G., Klötzli, F. (2001). Evergreen broad-leaved species as indicators for climate change. In: "Fingerprints" of Climate Change, pp. 151-162. https://doi.org/10.1007/978-1-4419-8692-4_10. [METADATA-ONLY] CrossRef-checked
- Walther, G.-R. (2002). Weakening of climatic constraints with global warming and its consequences for evergreen broad-leaved species. Folia Geobotanica 37(1): 129-139. https://doi.org/10.1007/BF02803195. [METADATA-ONLY][still unverified]
- Carraro, G., Gianoni, P., Mossi, R. (1999). Climatic influence on vegetation changes: a verification on regional scale of the laurophyllisation. In: Klötzli, F., Walther, G.-R. (eds) Recent Shifts in Vegetation Boundaries of Deciduous Forests. Birkhäuser, pp. 31-51 (CrossRef; TRACEVE prints 69-84, unresolved). https://doi.org/10.1007/978-3-0348-8722-9_3. [ABSTRACT-READ] CrossRef-checked
- Grund, K., Conedera, M., Schröder, H., Walther, G.-R. (2005). The role of fire in the invasion process of evergreen broad-leaved species. Basic and Applied Ecology 6(1): 47-56. https://doi.org/10.1016/j.baae.2004.07.005. [ABSTRACT-VIA-SEARCH] CrossRef-checked
- Peñuelas, J., Boada, M. (2003). A global change-induced biome shift in the Montseny mountains (NE Spain). Global Change Biology 9(2): 131-140. https://doi.org/10.1046/j.1365-2486.2003.00566.x. [ABSTRACT-READ] CrossRef-checked
- Peñuelas, J., Ogaya, R., Boada, M., Jump, A.S. (2007). Migration, invasion and decline: changes in recruitment and forest structure in a warming-linked shift of European beech forest in Catalonia (NE Spain). Ecography 30: 829-837. https://doi.org/10.1111/j.2007.0906-7590.05247.x. [ABSTRACT-READ] CrossRef-checked
- Delzon, S., Urli, M., Samalens, J.-C., Lamy, J.-B., Lischke, H., Sin, F., Zimmermann, N.E., Porté, A.J. (2013). Field evidence of colonisation by holm oak, at the northern margin of its distribution range, during the Anthropocene period. PLoS ONE 8(11): e80443. https://doi.org/10.1371/journal.pone.0080443. [ABSTRACT-READ] CrossRef-checked
- Hernández, L., Sánchez de Dios, R., Montes, F., Sainz-Ollero, H., Cañellas, I. (2017). Exploring range shifts of contrasting tree species across a bioclimatic transition zone. European Journal of Forest Research 136(3): 481-492. https://doi.org/10.1007/s10342-017-1047-2. [ABSTRACT-VIA-SEARCH] [DOI from CrossRef]; identification with the proposal's "mediterranization" item probable, unconfirmed.
- Urli, M., Delzon, S., Eyermann, A., Couallier, V., García-Valdés, R., Zavala, M. (2013, online; J Veg Sci 25: 147-159, 2014). Inferring shifts in tree species distribution using asymmetric distribution curves. https://doi.org/10.1111/jvs.12079. [ABSTRACT-READ] [DOI from CrossRef]
- Urli, M. et al. (2015). The high vulnerability of Quercus robur to drought at its southern margin paves the way for Quercus ilex. Plant Ecology 216: 177-187. https://doi.org/10.1007/s11258-014-0426-8. [METADATA-ONLY]
- Vayreda, J., Martinez-Vilalta, J., Gracia, M., Canadell, J., Retana, J. (2016). Anthropogenic-driven rapid shifts in tree distribution lead to increased dominance of broadleaf species. Global Change Biology 22(12): 3984-3995. https://doi.org/10.1111/gcb.13394. [ABSTRACT-READ] [DOI from CrossRef]
- Padullés Cubino, J., Vilà-Cabrera, A., Retana, J. (2024). Tree species abundance changes at the edges of their climatic distribution. Journal of Ecology 112(12): 2785-2797. https://doi.org/10.1111/1365-2745.14419. [ABSTRACT-READ, middle part by reviewer] [DOI from CrossRef]
- Cruz-Alonso, V., Villar-Salvador, P., Ruiz-Benito, P., Ibáñez, I., Rey-Benayas, J.M. (2019/2020). Long-term dynamics of shrub facilitation shape the mixing of evergreen and deciduous oaks in Mediterranean abandoned fields. Journal of Ecology 108(3): 1125-1137. https://doi.org/10.1111/1365-2745.13309. [ABSTRACT-READ] CrossRef-checked
- Garcia-Fayos, P., Monleon, V.J., Espigares, T., Nicolau, J.M., Bochet, E. (2020). Increasing aridity threatens the sexual regeneration of Quercus ilex (holm oak) in Mediterranean ecosystems. PLOS ONE 15(10): e0239755. https://doi.org/10.1371/journal.pone.0239755. [ABSTRACT-READ]
- Perring, M.P., De Frenne, P., Hertzog, L.R., et al. (2020). Increasing liana frequency in temperate European forest understories is driven by ivy. Frontiers in Ecology and the Environment 18(10): 550-557. https://doi.org/10.1002/fee.2266. [ABSTRACT-READ] CrossRef-checked
- Kucharski, L., Kloss, M., Sienkiewicz, J., Liszewska, M., Kiełtyk, P. (2019). Impact of climate change on ivy (Hedera helix L.) expansion in forests of Central Poland. Folia Forestalia Polonica 61(3): 211-221. https://doi.org/10.2478/ffp-2019-0020. [ABSTRACT-READ] CrossRef-checked
- Abrahamczyk, S., Otto, A., Böhnert, T., Weigend, M. (2024). Naturalization of Prunus laurocerasus in a forest in Germany. Biological Invasions 26. https://doi.org/10.1007/s10530-024-03325-2. [ABSTRACT-READ]
- Scherrer, D., Ascoli, D., Conedera, M., Fischer, C., Maringer, J., Moser, B. (2021; Ecosystems 25: 199-214, 2022). Canopy disturbances catalyse tree species shifts in Swiss forests. https://doi.org/10.1007/s10021-021-00649-1. [ABSTRACT-READ, truncated] [DOI from CrossRef]
- Colombaroli, D., Tinner, W., van Leeuwen, J., Noti, R., Vescovi, E., Vannière, B. (2009). Response of broadleaved evergreen Mediterranean forest vegetation to fire disturbance during the Holocene: insights from the peri-Adriatic region. Journal of Biogeography 36(2): 314-326. https://doi.org/10.1111/j.1365-2699.2008.01987.x. [ABSTRACT-READ, truncated] [DOI from CrossRef]
- Beffa, G., Gobet, E., Coşgun, S., et al. (2025). Causes of co-existence of cool-temperate Fagus and warm-loving evergreen Quercus forests in central Italy during the Holocene thermal maximum. Forest Ecosystems 14: 100345. https://doi.org/10.1016/j.fecs.2025.100345. [ABSTRACT-READ] CrossRef-checked
- Niinemets, Ü., Valladares, F. (2006). Tolerance to shade, drought, and waterlogging of temperate Northern Hemisphere trees and shrubs. Ecological Monographs 76(4): 521-547. https://doi.org/10.1890/0012-9615(2006)076[0521:TTSDAW]2.0.CO;2. [ABSTRACT-READ] CrossRef-checked
- Niinemets, Ü., Flexas, J., Peñuelas, J. (2011). Evergreens favored by higher responsiveness to increased CO2. Trends in Ecology & Evolution 26(3): 136-142. https://doi.org/10.1016/j.tree.2010.12.012. [ABSTRACT-READ] CrossRef-checked
- Soh, W.K., et al. (2019). Rising CO2 drives divergence in water use efficiency of evergreen and deciduous plants. Science Advances 5(12): eaax7906. https://doi.org/10.1126/sciadv.aax7906. [ABSTRACT-VIA-SEARCH] CrossRef-checked
- Svenning, J.-C., Skov, F. (2004). Limited filling of the potential range in European tree species. Ecology Letters 7(7): 565-573. https://doi.org/10.1111/j.1461-0248.2004.00614.x. [ABSTRACT-READ] [DOI from CrossRef]
- Simberloff, D. (2009). The role of propagule pressure in biological invasions. Annual Review of Ecology, Evolution, and Systematics 40: 81-102. https://doi.org/10.1146/annurev.ecolsys.110308.120304. [ABSTRACT-READ] [DOI from CrossRef]
- Gottfried, M., et al. (2012). Continent-wide response of mountain vegetation to climate change. Nature Climate Change 2: 111-115. https://doi.org/10.1038/nclimate1329. [METADATA-ONLY]
- Meyfroidt, P., Rudel, T.K., Lambin, E.F. (2010). Forest transitions, trade, and the global displacement of land use. PNAS 107(49): 20917-20922. https://doi.org/10.1073/pnas.1014773107. [ABSTRACT-READ]
- Hampe, A., Jump, A.S. (2011). Climate relicts: past, present, future. Annual Review of Ecology, Evolution, and Systematics 42: 313-333. https://doi.org/10.1146/annurev-ecolsys-102710-145015. [ABSTRACT-READ]
- Jump, A.S., Hunt, J.M., Peñuelas, J. (2006). Rapid climate change-related growth decline at the southern range edge of Fagus sylvatica. Global Change Biology 12(11): 2163-2174. https://doi.org/10.1111/j.1365-2486.2006.01250.x. [ABSTRACT-READ] CrossRef-checked
- Nowacki, G.J., Abrams, M.D. (2008). The demise of fire and "mesophication" of forests in the eastern United States. BioScience 58(2): 123-138. https://doi.org/10.1641/b580207. [METADATA-ONLY] (title as commonly known; the note records only journal data)
- Sánchez de Dios, R., Benito-Garzón, M., Sainz-Ollero, H. (2009). Present and future extension of the Iberian submediterranean territories as determined from the distribution of marcescent oaks. Plant Ecology 204(2): 189-205. https://doi.org/10.1007/s11258-009-9584-5. [METADATA-ONLY]
- Passos, I., Vila-Viçosa, C., Gonçalves, J., Ribeiro, M., Figueiredo, A. (2025). Tracking submediterranean ecotone shifts under climate change scenarios using marcescent oaks as indicators. Scientific Reports 15: 39201. https://doi.org/10.1038/s41598-025-10088-w. [ABSTRACT-READ] [DOI from CrossRef]
- Suicmez, B., Avci, M. (2023). Distribution patterns of Quercus ilex ... by ecological niche modeling. Ecology and Evolution 13(10): e10606. https://doi.org/10.1002/ece3.10606. [ABSTRACT-READ, truncated] (title truncated in the note)
- Hickler, T., Vohland, K., Feehan, J., et al. (2012). Projecting the future distribution of European potential natural vegetation zones with a generalized, tree species-based dynamic vegetation model. Global Ecology and Biogeography 21(1): 50-63. https://doi.org/10.1111/j.1466-8238.2010.00613.x. [ABSTRACT-READ, truncated]
- Pignatti, G. (2011). Forest vegetation in view of some scenarios of climate change in Italy. Forest@ 8. https://doi.org/10.3832/efor0650-008. [ABSTRACT-READ]
- Noce, S., Cipriano, L., Santini, M. (2023). Frontiers in Forests and Global Change 6: 1250651. https://doi.org/10.3389/ffgc.2023.1250651. [W][PDF-CHECKED] [[noce_2023_altitude_shift_tree_italy]]
- Bricca et al. (2026). Global Ecology and Biogeography. [W] [[bricca_2026_topo_diversity]] (no DOI in the notes)
- Herraiz et al. (2025). Ecological Indicators 171: 113115. https://doi.org/10.1016/j.ecolind.2025.113115. [W][PDF-CHECKED] [[herraiz_2025_phen_shifts_mediterranean]]
- Midolo et al. (2026). Science Advances 12: eaeb2493. [W][PDF-CHECKED] [[midolo_2026_denser_vegetation]] (DOI not confirmed)
- Fehr, V. et al. (2024). Non-native palm affects arthropod communities and litter decomposition in an ongoing biome shift. Global Ecology and Conservation 56: e03303. https://doi.org/10.1016/j.gecco.2024.e03303. [METADATA-ONLY]
- Cerabolini, B., Brusa, G., et al. (2008). Analisi dei fattori che inducono modificazioni delle comunità forestali insubriche ad opera di specie esotiche. In: Le specie alloctone in Italia. [METADATA-ONLY, lead only; editors and DOI unverified]
- Larcher, W. (2000). Temperature stress and survival ability of Mediterranean sclerophyllous plants. Plant Biosystems 134(3): 279-295. https://doi.org/10.1080/11263500012331350455. [METADATA-ONLY]

### 9.2 Theme 2: dieback, mortality, concepts
- Seddaiu, S., Ruiu, P.A., Piras, G., Scanu, B., Satta, G.G.A., Lentini, A., et al. (2025). Vulnerabilità delle foreste mediterranee a eventi climatici estremi di ondate di calore e siccità: il caso del disseccamento del leccio (Quercus ilex L.) in Italia. Forest@ 22(1): 56-65. https://doi.org/10.3832/efor4934-022. [W][PDF-CHECKED] CrossRef-checked [[seddaiu_2025_quercus_dieback]]
- Satta, G.G.A., Giannetti, F., Deidda, A., Brandano, A., Lentini, A., Piras, G., Ruiu, P.A., Seddaiu, S., Scanu, B. (2025). Detection and modeling of drought-induced forest dieback in Mediterranean ecosystems. SSRN preprint, NOT peer reviewed. https://doi.org/10.2139/ssrn.5761729. [W][PDF-CHECKED] [[seddaiu_2025_mediterranean_dieback]]
- Puletti, N., Mattioli, W., Bussotti, F., Pollastrini, M. (2019). Monitoring the effects of extreme drought events on forest health by Sentinel-2 imagery. Journal of Applied Remote Sensing 13(2): 020501. https://doi.org/10.1117/1.JRS.13.020501. [W][PDF-CHECKED] [[puletti_2019_drought_forest_health]]
- Pollastrini, M., Puletti, N., Selvi, F., Iacopetti, G., Bussotti, F. (2019). Widespread crown defoliation after a drought and heat wave in the forests of Tuscany (Central Italy) and their recovery - a case study from summer 2017. Frontiers in Forests and Global Change 2: 74. https://doi.org/10.3389/ffgc.2019.00074. [ABSTRACT-READ] CrossRef-checked
- Lloret, F., Siscart, D., Dalmases, C. (2004). Canopy recovery after drought dieback in holm-oak Mediterranean forests of Catalonia (NE Spain). Global Change Biology 10(12): 2092-2099. https://doi.org/10.1111/j.1365-2486.2004.00870.x. [ABSTRACT-READ]
- Ogaya, R., Liu, D., Barbeta, A., Peñuelas, J. (2020). Stem mortality and forest dieback in a 20-years experimental drought in a Mediterranean holm oak forest. Frontiers in Forests and Global Change 2: 89 (online 8 Jan 2020; DOI carries 2019). https://doi.org/10.3389/ffgc.2019.00089. [ABSTRACT-VIA-SEARCH] CrossRef-checked
- Saura-Mas, S., Bonas, A., Lloret, F. (2015). Plant community response to drought-induced canopy defoliation in a Mediterranean Quercus ilex forest. European Journal of Forest Research 134(2): 261-272. https://doi.org/10.1007/s10342-014-0848-9. [ABSTRACT-VIA-SEARCH] CrossRef-checked
- Alderotti, F., Sillo, F., Brilli, F., Bussotti, F., et al. (2023). Quercus ilex L. dieback is genetically determined: evidence provided by dendrochronology, δ13C and SSR genotyping. Science of the Total Environment 904: 166809. https://doi.org/10.1016/j.scitotenv.2023.166809. [ABSTRACT-READ]
- Alderotti, F., Bussotti, F., Gori, A., Ferrini, F., et al. (2025). Moderately and severely defoliated Quercus ilex L. trees exhibit hydraulic dysfunction and carbon depletion. Tree Physiology 45(5): tpaf033. https://doi.org/10.1093/treephys/tpaf033. [ABSTRACT-READ]
- Alderotti, F., Verdiani, E. (2023). God save the queen! How and why the dominant evergreen species of the Mediterranean Basin is declining? AoB PLANTS 15(5): plad051. https://doi.org/10.1093/aobpla/plad051. [ABSTRACT-READ] (v2) / [ABSTRACT-VIA-SEARCH] (v3 note); CrossRef-checked
- Bussotti, F., Papitto, G., Di Martino, D., et al. (2021). Defoliation, recovery and increasing mortality in Italian forests. Forests 12(11): 1476. https://doi.org/10.3390/f12111476. [ABSTRACT-READ]
- Frisullo, S., Lima, G., et al. (2018). Phytophthora cinnamomi involved in the decline of holm oak (Quercus ilex) stands in southern Italy. Forest Science 64(3): 290-298. https://doi.org/10.1093/forsci/fxx010. [ABSTRACT-READ]
- Bregant, C., Carloni, F., Borsetto, G., Delle Donne, A., Linaldeddu, B.T., Murolo, S. (2025). Multiple Botryosphaeriaceae and Phytophthora species involved in the etiology of holm oak (Quercus ilex L.) decline in southern Italy. Forests 16(7): 1052. https://doi.org/10.3390/f16071052. [ABSTRACT-READ] CrossRef-checked
- Colangelo, M., Camarero, J.J., Borghetti, M., Gentilesca, T., Oliva, J., Redondo, M.A., Ripullone, F. (2018). Drought and Phytophthora are associated with the decline of oak species in southern Italy. Frontiers in Plant Science 9: 1595. https://doi.org/10.3389/fpls.2018.01595. [ABSTRACT-READ]
- Seddaiu, S., Brandano, A., Ruiu, P.A., Sechi, C., Scanu, B. (2020). An overview of Phytophthora species inhabiting declining Quercus suber stands in Sardinia (Italy). Forests 11(9): 971. https://doi.org/10.3390/f11090971. [ABSTRACT-READ] CrossRef-checked
- Gentilesca, T., Camarero, J.J., Colangelo, M., Nolè, A., Ripullone, F. (2017). Drought-induced oak decline in the western Mediterranean region: an overview on current evidences, mechanisms and management options to improve forest resilience. iForest 10(5): 796-806. https://doi.org/10.3832/ifor2317-010. [METADATA-ONLY]; summary [ABSTRACT-VIA-SEARCH]
- Marques, M., Bugalho, Acácio, Catry (2025; given-name initials not recorded in the note). Disentangling research on oak decline factors in Mediterranean-type climate regions: a systematic review. Trees, Forests and People 19: 100803. https://doi.org/10.1016/j.tfp.2025.100803. [METADATA-ONLY] (CrossRef first author "Marques Marco")
- Ripullone, F., Chiavetta, U., La Mela Veca, D.S., Masiero, M., Bussotti, F., et al. (2026). Italian oak forests facing stress factors and climate change. Forest@ 23(2): 6-10. https://doi.org/10.3832/efor5088-023. [ABSTRACT-READ] CrossRef-checked
- Carnicer, J., Coll, M., Ninyerola, M., Pons, X., Sánchez, G., Peñuelas, J. (2011). Widespread crown condition decline, food web disruption, and amplified tree mortality with increased climate change-type drought. PNAS 108(4): 1474-1478. https://doi.org/10.1073/pnas.1010070108. [ABSTRACT-READ]
- Gazol, A., Camarero, J.J. (2022). Compound climate events increase tree drought mortality across European forests. Science of the Total Environment 816: 151604. https://doi.org/10.1016/j.scitotenv.2021.151604. [ABSTRACT-READ]
- Breshears, D.D., Cobb, N.S., Rich, P.M., Price, K.P., Allen, C.D., Balice, R.G., et al. (2005). Regional vegetation die-off in response to global-change-type drought. PNAS 102(42): 15144-15148. https://doi.org/10.1073/pnas.0505734102. [ABSTRACT-READ] (title not in the note; authors per CrossRef as listed there)
- Allen, C.D., Breshears, D.D., McDowell, N.G. (2015). On underestimation of global vulnerability to tree mortality and forest die-off from hotter drought in the Anthropocene. Ecosphere 6(8): art129. https://doi.org/10.1890/es15-00203.1. [ABSTRACT-READ]; article number to be checked
- McDowell, N., et al. (2008). Mechanisms of plant survival and mortality during drought. New Phytologist 178(4): 719-739. https://doi.org/10.1111/j.1469-8137.2008.02436.x. [ABSTRACT-READ]
- Hartmann, H., et al. (2022). Annual Review of Plant Biology 73: 673-702. https://doi.org/10.1146/annurev-arplant-102820-012804. [ABSTRACT-READ]
- Regione Toscana, Servizio Fitosanitario Regionale, CNR-IPSP, CREA. Querce in Toscana: prime considerazioni sullo stato di deperimento. Web page, updated 10 Dec 2025. Grey literature, not peer reviewed.
- Mariotti, M. (2017). Cydalima perspectalis (Walker, 1859) (Lepidoptera, Crambidae) and the threats for the Natura 2000 habitat 5110 in Liguria (NW Italy). Bollettino dei Musei e degli Istituti Biologici dell'Università di Genova 79. [ABSTRACT-VIA-SEARCH]; pages and DOI not obtained. (Author initial not recorded in the note beyond "Mariotti".)
- Lehtijärvi, A., Doğmuş-Lehtijärvi, H.T., Oskay, F. (2014). Plant Protection Science 50(4): 227-229. https://doi.org/10.17221/18/2014-PPS. [METADATA-ONLY] CrossRef-checked
- Lead only, not cited as evidence: Cardillo et al. 2020 bioRxiv https://doi.org/10.1101/2020.03.27.011304 [METADATA-ONLY]; Pérez Álvarez 2026 SSRN https://doi.org/10.2139/ssrn.6740564 [METADATA-ONLY]; Brasier 1996, Annales des Sciences Forestières 53: 347-358, https://doi.org/10.1051/forest:19960217 [METADATA-ONLY].

### 9.3 Theme 3: remote sensing, trajectories, uncertainty
- Hermosilla, T., Wulder, M.A., White, J.C., Coops, N.C., Bater, C.W., Hobart, G.W. (2024). Characterizing long-term tree species dynamics in Canada's forested ecosystems using annual time series remote sensing data. Forest Ecology and Management 572: 122313. https://doi.org/10.1016/j.foreco.2024.122313. [ABSTRACT-READ] CrossRef-checked. HMM detail: GEE community catalogue entry https://gee-community-catalog.org/projects/ca_species_ts/ [ABSTRACT-VIA-SEARCH]
- Hermosilla, T., Wulder, M.A., White, J.C., Coops, N.C., Hobart, G.W. (2018). Disturbance-informed annual land cover classification maps of Canada's forested ecosystems for a 29-year Landsat time series. Canadian Journal of Remote Sensing 44(1): 67-87. https://doi.org/10.1080/07038992.2018.1437719. [ABSTRACT-READ] CrossRef-checked
- Thapa, B., Wolter, P.T., Sturtevant, B.R., Townsend, P.A. (2020). Reconstructing past forest composition and abundance by using archived Landsat and national forest inventory data. International Journal of Remote Sensing 41(10): 4022-4056. https://doi.org/10.1080/01431161.2019.1711245. [ABSTRACT-READ] CrossRef-checked
- Bogaert, P., Lamarche, C., Defourny, P. (2022). Hidden Markov models for annual land cover mapping: increasing temporal consistency and completeness. IEEE TGRS 60. https://doi.org/10.1109/TGRS.2021.3123738. [ABSTRACT-READ] CrossRef-checked
- Abercrombie, S.P., Friedl, M.A. (2016). Improving the consistency of multitemporal land cover maps using a hidden Markov model. IEEE TGRS 54(2): 703-713. https://doi.org/10.1109/TGRS.2015.2463689. [ABSTRACT-READ] CrossRef-checked
- Gong, W., Fang, S., Yang, G., Ge, M. (2017). Using a hidden Markov model for improving the spatial-temporal consistency of time series land cover classification. ISPRS International Journal of Geo-Information 6(10): 292. https://doi.org/10.3390/ijgi6100292. [ABSTRACT-READ]
- Salberg, A.-B., Trier, Ø.D. (2011). Temporal analysis of forest cover using hidden Markov models. IGARSS 2011: 2322-2325. https://doi.org/10.1109/igarss.2011.6049674; (2012) IGARSS 2012: 6749-6752. https://doi.org/10.1109/igarss.2012.6352556. [ABSTRACT-READ] (conference papers; initial of the second author as "O.D." in the note)
- Torchiana, A.L., Rosenbaum, T., Scott, P.T., Souza-Rodrigues, E. (2025). Improving estimates of transitions from satellite data: a hidden Markov model approach. Review of Economics and Statistics 107(2): 426-441. https://doi.org/10.1162/rest_a_01301. [ABSTRACT-READ] CrossRef-checked; issue number not given by CrossRef
- Lu, X., Hooten, M.B., Raiho, A.M., Swanson, D.K., Roland, C.A., Stehn, S.E. (2022). Latent trajectory models for spatio-temporal dynamics in Alaskan ecosystems. arXiv:2208.07398. [ABSTRACT-VIA-SEARCH] preprint
- McClintock, B.T., Langrock, R., Gimenez, O., Cam, E., Borchers, D.L., Glennie, R., Patterson, T.A. (2020). Uncovering ecological state dynamics with hidden Markov models. Ecology Letters 23(12): 1878-1903. https://doi.org/10.1111/ele.13610. [ABSTRACT-READ] CrossRef-checked
- Rabiner, L.R. (1989). Proceedings of the IEEE 77(2). https://doi.org/10.1109/5.18626. [METADATA-ONLY] CrossRef-checked; pages not read. Waggoner, P.E., Stephens, G.R. (1970). Nature 225: 1160-1161. https://doi.org/10.1038/2251160a0. [METADATA-ONLY] CrossRef-checked (initials not in the note).
- Pontius, R.G., Malanson, J. (2005). Comparison of the structure and accuracy of two land change models. International Journal of Geographical Information Science 19(2): 243-265. https://doi.org/10.1080/13658810410001713434. [ABSTRACT-READ]; first-author initial not confirmed in CrossRef (lists "Pontius, G")
- Pontius, R.G., Lippitt, C.D. (2006). Can error explain map differences over time? Cartography and Geographic Information Science 33(2): 159-171. https://doi.org/10.1559/152304006777681706. [ABSTRACT-READ] CrossRef-checked
- Olofsson, P., Foody, G.M., Herold, M., Stehman, S.V., Woodcock, C.E., Wulder, M.A. (2014). Good practices for estimating area and assessing accuracy of land change. Remote Sensing of Environment 148: 42-57. https://doi.org/10.1016/j.rse.2014.02.015. [ABSTRACT-VIA-SEARCH] (v2: [ABSTRACT-PARAPHRASE][SNIPPET/TLDR-ONLY]) CrossRef-checked
- Aldwaik, S.Z., Pontius, R.G. (2012). Intensity analysis to unify measurements of size and stationarity of land changes by interval, category, and transition. Landscape and Urban Planning 106(1): 103-114. https://doi.org/10.1016/j.landurbplan.2012.02.010. [ABSTRACT-VIA-SEARCH] CrossRef-checked
- Stehman, S.V., Pengra, B.W., Horton, J.A., Wellington, D.F. (2021). Validation of the U.S. Geological Survey's Land Change Monitoring, Assessment and Projection (LCMAP) Collection 1.0 annual land cover products 1985-2017. Remote Sensing of Environment 265: 112646. https://doi.org/10.1016/j.rse.2021.112646. [ABSTRACT-VIA-SEARCH] CrossRef-checked (title as commonly cited; the note gives a shortened form)
- Xian, G., Smith, K., Wellington, D., Horton, J., Zhou, Q., Li, C., et al. (2022). Implementation of the CCDC algorithm to produce the LCMAP Collection 1.0 annual land surface change product. Earth System Science Data 14: 143-162. https://doi.org/10.5194/essd-14-143-2022. [ABSTRACT-READ]
- Zhang, X., Zhao, T., Xu, H., Liu, W., Wang, J., Chen, X., Liu, L. (2024). GLC_FCS30D: the first global 30 m land-cover dynamics monitoring product. Earth System Science Data 16: 1353-1381. https://doi.org/10.5194/essd-16-1353-2024. [ABSTRACT-READ] [FULLTEXT-PARTLY-READ] (page)
- Witjes, M., Parente, L., van Diemen, C.J., Hengl, T., Landa, M., Brodsky, L., et al. (2022). A spatiotemporal ensemble machine learning framework for generating land use/land cover time-series maps for Europe (2000-2019). PeerJ 10: e13573. https://doi.org/10.7717/peerj.13573. [ABSTRACT-READ] CrossRef-checked
- Garcia-Alvarez, D., Camacho Olmedo, M.T. (2022). Analyzing the uncertainty of the CORINE Land Cover time series (1990-2018) for Spain (Asturias case). EarthArXiv preprint. https://doi.org/10.31223/x5qd1f. [ABSTRACT-READ]
- Baglioni, L., Morresi, D., Tonelli, E., Lingua, E., Marzano, R., Urbinati, C. (2025). Forestline detection and treeline ecotone dynamics in the Italian Alps and Apennines by satellite remote sensing. EGU24 abstract. https://doi.org/10.5194/egusphere-egu24-15620. Baglioni, L., Vitali, A., Choler, P., Bayle, A., Garbarino, M., Morresi, D. (2026). Predisposing factors to Landsat based greening trends in the Italian forestline ecotones. EGU26 abstract. https://doi.org/10.5194/egusphere-egu26-13167. [ABSTRACT-READ of conference abstracts]; not peer reviewed
- Mirici, M.E. (2018). Land use/cover change modelling in a Mediterranean rural landscape using multi-layer perceptron and Markov chain (MLP-MC). Applied Ecology and Environmental Research 16(1): 467-486. https://doi.org/10.15666/aeer/1601_467486. [ABSTRACT-READ]
- Mertens, B., Lambin, E.F. (2000). Annals of the Association of American Geographers 90: 467-494. https://doi.org/10.1111/0004-5608.00205. [ABSTRACT-READ]; Mena, C.F. (2008). Photogrammetric Engineering & Remote Sensing 74: 737-751. https://doi.org/10.14358/pers.74.6.737. [ABSTRACT-READ] (author initials and titles not recorded in the notes)
- Sousa, D., Davis, F.W. (2020). Scalable mapping and monitoring of Mediterranean-climate oak landscapes with temporal mixture models. Remote Sensing of Environment 247: 111937. https://doi.org/10.1016/j.rse.2020.111937. [ABSTRACT-VIA-SEARCH] CrossRef-checked
- Radoux, J., et al. (2014). Automated training sample extraction for global land cover mapping. Remote Sensing 6(5): 3965-3987. https://doi.org/10.3390/rs6053965. [ABSTRACT-READ]
- Buchhorn, M., Lesiv, M., Tsendbazar, N.-E., Herold, M., Bertels, L., Smets, B. (2020). Copernicus Global Land Cover Layers - Collection 2. Remote Sensing 12(6): 1044. https://doi.org/10.3390/rs12061044. [ABSTRACT-READ]
- Bonannella, C., Hengl, T., Heisig, J., Parente, L., Wright, M.N., Herold, M., de Bruin, S. (2022). Forest tree species distribution for Europe 2000-2020. PeerJ 10: e13728. https://doi.org/10.7717/peerj.13728. [ABSTRACT-READ] CrossRef-checked
- Agrillo, E., Filipponi, F., Pezzarossa, A., Casella, L., Smiraglia, D., Orasi, A., Attorre, F., Taramelli, A. (2021). Earth observation and biodiversity big data for forest habitat types classification and mapping. Remote Sensing 13(7): 1231. https://doi.org/10.3390/rs13071231. [ABSTRACT-READ] CrossRef-checked
- Pesaresi, S., Mancini, A., Quattrini, G., Casavecchia, S. (2020). Remote Sensing 12(7): 1132. https://doi.org/10.3390/rs12071132; Pesaresi, S., Mancini, A., Casavecchia, S. (2020). Diversity 12(8): 313. https://doi.org/10.3390/d12080313. [ABSTRACT-READ] CrossRef-checked
- Mancino, G., Nolè, A., Ripullone, F., Ferrara, A. (2014). Landsat TM imagery and NDVI differencing to detect vegetation change: assessing natural forest expansion in Basilicata, southern Italy. iForest 7(2): 75-84. https://doi.org/10.3832/ifor0909-007. [ABSTRACT-READ] CrossRef-checked
- Padial-Iglesias, M., Ninyerola, M., Serra, P., González-Guerrero, Ò., Espelta, J.M., Pino, J., Pons, X. (2022). Driving forces of forest expansion dynamics across the Iberian Peninsula (1987-2017): a spatio-temporal transect. Forests 13(3): 475. https://doi.org/10.3390/f13030475. [ABSTRACT-READ] CrossRef-checked
- Aubard, V., Paulo, J.A., Silva, J.M.N. (2019). Long-term monitoring of cork and holm oak stands productivity in Portugal with Landsat imagery. Remote Sensing 11(5): 525. https://doi.org/10.3390/rs11050525. [ABSTRACT-READ] CrossRef-checked
- Viana-Soto, A., Aguado, I., Salas, J., García, M. (2020). Remote Sensing 12(9): 1499. https://doi.org/10.3390/rs12091499. [ABSTRACT-READ] CrossRef-checked
- Giannetti, F., Pegna, R., Francini, S., McRoberts, R.E., Travaglini, D., Marchetti, M., Scarascia Mugnozza, G., Chirici, G. (2020). A new method for automated clearcut disturbance detection in Mediterranean coppice forests using Landsat time series. Remote Sensing 12(22): 3720. https://doi.org/10.3390/rs12223720. [ABSTRACT-READ] CrossRef-checked
- Laidi, Y., El Bouchti, N., Abbas, Y., Benhssaine, K., El Mderssa, M. (2026). Forty years of Landsat and Sentinel-2 retrospective analysis reveal a species-differentiated dieback signal in the Atlas forests of Beni Mellal-Khenifra (Morocco). Ecological Engineering & Environmental Technology 9: 110-131. https://doi.org/10.12912/27197050/226093. [ABSTRACT-VIA-SEARCH]; DOI from the journal page, not looked up in CrossRef
- Verhulst, M., Heremans, S., Blaschko, M., Somers, B. (2024). Temporal transferability of tree species classification in temperate forests with Sentinel-2 time series. Remote Sensing 16(14): 2653. https://doi.org/10.3390/rs16142653. [ABSTRACT-READ] CrossRef-checked
- Chastain, R.A. Jr., Townsend, P.A. (2007). Use of Landsat ETM and topographic data to characterize evergreen understory communities in Appalachian deciduous forests. Photogrammetric Engineering & Remote Sensing 73(5): 563-575. https://doi.org/10.14358/PERS.73.5.563. [W][PDF-CHECKED] [[chastain_2007_eve_landsat_understory]]
- Atkins, J.W., Epstein, H.E., Welsch, D.L. (2018). Using Landsat imagery to map understory shrub expansion relative to landscape position in a mid-Appalachian watershed. Ecosphere 9(10): e02404. https://doi.org/10.1002/ecs2.2404. [ABSTRACT-READ] CrossRef-checked
- Oreti, L., Barbati, A., Marini, F., Giuliarelli, D. (2020). Very high-resolution true color leaf-off imagery for mapping Taxus baccata L. and Ilex aquifolium L. understory populations in beech forests. Biodiversity and Conservation 29(8): 2605-2622. https://doi.org/10.1007/s10531-020-01991-x. [ABSTRACT-READ]
- Bayle, A., Gascoin, S., Berner, L.T., Choler, P. (2024). Landsat-based greening trends in alpine ecosystems are inflated by multidecadal increases in summer observations. Ecography e07394. https://doi.org/10.1111/ecog.07394. [W][PDF-CHECKED] [[bayle_2024_landsat_greening_inflated]]
- Hiebl et al. (2025). Int. J. Appl. Earth Obs. Geoinf. 142: 104734. https://doi.org/10.1016/j.jag.2025.104734. [W][PDF-CHECKED] [[hiebl_2025_pretraining]]
- Pasquarella, V.J., Arévalo, P., Bratley, K.H., Bullock, E.L., Gorelick, N., Yang, Z., Kennedy, R.E. (2022). Demystifying LandTrendr and CCDC temporal segmentation. Int. J. Appl. Earth Obs. Geoinf. 110: 102806. https://doi.org/10.1016/j.jag.2022.102806. [ABSTRACT-READ] CrossRef-checked. Cohen, W.B., Healey, S.P., Yang, Z., Stehman, S.V., et al. (2017). Forests 8(4): 98. https://doi.org/10.3390/f8040098. [ABSTRACT-READ]. Forkel, M., Carvalhais, N., Verbesselt, J., Mahecha, M.D., Neigh, C.S.R., Reichstein, M. (2013). Remote Sensing 5(5): 2113-2144. https://doi.org/10.3390/rs5052113. [ABSTRACT-READ] CrossRef-checked
- Kennedy, R.E., Yang, Z., Cohen, W.B. (2010). Detecting trends in forest disturbance and recovery using yearly Landsat time series: 1. LandTrendr. Remote Sensing of Environment 114(12): 2897-2910. https://doi.org/10.1016/j.rse.2010.07.008. [ABSTRACT-VIA-SEARCH] CrossRef-checked. Verbesselt, J., Hyndman, R., Newnham, G., Culvenor, D. (2010). Detecting trend and seasonal changes in satellite image time series. Remote Sensing of Environment 114(1): 106-115. https://doi.org/10.1016/j.rse.2009.08.014. [ABSTRACT-VIA-SEARCH] CrossRef-checked. Zhu, Z., Woodcock, C.E. (2014). Remote Sensing of Environment 144: 152-171. https://doi.org/10.1016/j.rse.2014.01.011. [ABSTRACT-PARAPHRASE]
- Hamed, K.H., Rao, A.R. (1998). A modified Mann-Kendall trend test for autocorrelated data. Journal of Hydrology 204: 182-196. https://doi.org/10.1016/S0022-1694(97)00125-X. [SNIPPET/TLDR-ONLY] CrossRef-checked. Yue, S., Pilon, P., Phinney, B., Cavadias, G. (2002). Hydrological Processes 16(9): 1807-1829. https://doi.org/10.1002/hyp.1095. [ABSTRACT-READ]. Neeti, N., Eastman, J.R. (2011). Transactions in GIS 15(5): 599-611. https://doi.org/10.1111/j.1467-9671.2011.01280.x. [ABSTRACT-READ]. Getis, A., Ord, J.K. (1992). Geographical Analysis 24(3): 189-206. https://doi.org/10.1111/j.1538-4632.1992.tb00261.x. [ABSTRACT-READ]
- Blois, J.L., Williams, J.W., Fitzpatrick, M.C., Jackson, S.T., Ferrier, S. (2013). Space can substitute for time in predicting climate-change effects on biodiversity. PNAS 110(23): 9374-9379. https://doi.org/10.1073/pnas.1220228110. [ABSTRACT-READ] CrossRef-checked. Damgaard, C. (2019). A critique of the space-for-time substitution practice in community ecology. Trends in Ecology & Evolution 34(5): 416-421. https://doi.org/10.1016/j.tree.2019.01.013. [ABSTRACT-READ]
- Roberts, D.R., et al. (2017). Cross-validation strategies for data with temporal, spatial, hierarchical, or phylogenetic structure. Ecography 40(8): 913-929. https://doi.org/10.1111/ecog.02881. [ABSTRACT-READ]; issue number "8" from memory, **not verified**. Dormann, C.F., et al. (2007). Ecography 30: 609-628. https://doi.org/10.1111/j.2007.0906-7590.05171.x. [ABSTRACT-READ]. Ploton, P., et al. (2020). Spatial validation reveals poor predictive performance of large-scale ecological mapping models. Nature Communications 11: 4540. https://doi.org/10.1038/s41467-020-18321-y. [ABSTRACT-READ]. Meyer, H., Pebesma, E. (2021). Predicting into unknown space? Estimating the area of applicability of spatial prediction models. Methods in Ecology and Evolution 12(9): 1620-1633. https://doi.org/10.1111/2041-210x.13650. [ABSTRACT-READ]; issue "9" from memory, **not verified**.
- Lead only (metadata or snippet; not cited as evidence): Potapov et al. 2015, RSE 159: 28-43, https://doi.org/10.1016/j.rse.2014.11.027 [METADATA-ONLY]; Di Gennaro, Migliozzi, Marotta 2019, Economia della Cultura 3: 371-382, DOI 10.1446/95595 (not resolvable in CrossRef) [SNIPPET/TLDR-ONLY]; Yang et al. 2023, RSE 293: 113601, https://doi.org/10.1016/j.rse.2023.113601 [SNIPPET/TLDR-ONLY]; Zenodo record 7054338 [SNIPPET/TLDR-ONLY].

### 9.4 Theme 4: land use, climate, Italian context
- Gasparini, P., Tabacchi, G. (2022). Changes of Italian forests over time captured by the National Forest Inventories. In: Gasparini, P., et al. (eds) Italian National Forest Inventory - Methods and Results of the Third Survey. Springer, pp. 545-568. https://doi.org/10.1007/978-3-030-98678-0_13. [W][FULLTEXT-PARTLY-READ] [[gasparini_2022_nfi_italy]]
- Garbarino, M., Morresi, D., Urbinati, C., Malandra, F., Motta, R., Sibona, E.M., Vitali, A., Weisberg, P.J. (2020). Contrasting land use legacy effects on forest landscape dynamics in the Italian Alps and the Apennines. Landscape Ecology 35(12): 2679-2694. https://doi.org/10.1007/s10980-020-01013-9. [ABSTRACT-VIA-SEARCH] [SEARCH-SUMMARY] CrossRef-checked
- Malandra, F., Vitali, A., Urbinati, C., Garbarino, M. (2018). 70 years of land use/land cover changes in the Apennines (Italy): a meta-analysis. Forests 9(9): 551. https://doi.org/10.3390/f9090551. [ABSTRACT-READ] CrossRef-checked
- Vitali, A., Urbinati, C., Weisberg, P.J., Urza, A.K., Garbarino, M. (2018). Effects of natural and anthropogenic drivers on land-cover change and treeline dynamics in the Apennines (Italy). Journal of Vegetation Science 29(2): 189-199. https://doi.org/10.1111/jvs.12598. [ABSTRACT-READ] CrossRef-checked
- Santoro, A., Piras, F. (2023). Forests 14(5): 921. https://doi.org/10.3390/f14050921. [ABSTRACT-READ] CrossRef-checked. Ottaviano, M., et al. (2026). Forest@ 23(2): 11-25. https://doi.org/10.3832/efor5002-023. [ABSTRACT-READ] CrossRef-checked. Ascoli, D., Moris, J.V., Marchetti, M., Sallustio, L. (2024). Annals of Silvicultural Research 46(2): 4. https://doi.org/10.12899/asr-2264. [ABSTRACT-READ] CrossRef-checked
- Falcucci, A., Maiorano, L., Boitani, L. (2007). Changes in land-use/land-cover patterns in Italy and their implications for biodiversity conservation. Landscape Ecology 22(4): 617-631. https://doi.org/10.1007/s10980-006-9056-4. [SEARCH-SUMMARY] CrossRef-checked
- Pausas, J.G., Millán, M.M. (2019). Greening and browning in a climate change hotspot: the Mediterranean Basin. BioScience 69(2): 143-151. https://doi.org/10.1093/biosci/biy157. [ABSTRACT-READ]
- Brunetti, M., Maugeri, M., Monti, F., Nanni, T. (2006). Temperature and precipitation variability in Italy in the last two centuries from homogenised instrumental time series. International Journal of Climatology 26(3): 345-381. https://doi.org/10.1002/joc.1251. [ABSTRACT-READ]
- Pascale, S., Ragone, F. (2025). Widespread multi-year droughts in Italy: identification and causes of development. International Journal of Climatology 45(8): e8827. https://doi.org/10.1002/joc.8827. [ABSTRACT-READ] CrossRef-checked
- Spinoni, J., Naumann, G., Vogt, J.V. (2017). Pan-European seasonal trends and recent changes of drought frequency and severity. Global and Planetary Change 148: 113-130. https://doi.org/10.1016/j.gloplacha.2016.11.013. [ABSTRACT-READ] CrossRef-checked
- Mombrini, E., Tamea, S., Viglione, A., Revelli, R. (2025). A 60-year drought analysis of meteorological data in the western Po River basin. Hydrology and Earth System Sciences 29(10): 2255-2273. https://doi.org/10.5194/hess-29-2255-2025. [ABSTRACT-READ]
- Becherini, F., et al. (2024). Multi-secular trend of drought indices in Padua, Italy. Climate 12(12): 218. https://doi.org/10.3390/cli12120218. [ABSTRACT-READ] CrossRef-checked. Aschale, T.M., et al. (2024). Water 16(18): 2593. https://doi.org/10.3390/w16182593. [ABSTRACT-READ] CrossRef-checked
- Vicente-Serrano, S.M., López-Moreno, J.I., Beguería, S., et al. (2014). Evidence of increasing drought severity caused by temperature rise in southern Europe. Environmental Research Letters 9(4): 044001. https://doi.org/10.1088/1748-9326/9/4/044001. [ABSTRACT-READ]

### 9.5 Notes on reference checking
- Bibliographic data marked "CrossRef-checked" were confirmed against CrossRef in the earlier synthesis or the v3 notes; this confirms authors, volume and pages, not that a paper supports a claim.
- Entries without that mark carry metadata as recorded by the researchers; re-check before BibTeX export. Titles of Nowacki & Abrams 2008, Breshears 2005, Allen 2015, McDowell 2008 and Stehman 2021 were not in the notes in full and were added from general knowledge: **not verified**, check against the publisher record. A few other titles are reconstructed from the note's wording and marked as such; check them against the publisher record before use.
- Unresolved: Jump 2009, Trindade 2020 (section 7.5). Not cited because unverified: "Hobbs" (privet remote sensing), the Cailleret et al. Port-Cros study, Bec et al. 2020.
