# Dieback, drought-induced decline and mortality of Mediterranean evergreen broad-leaved trees: scoping round 3

Scope: gap-filling for the Introduction of "Distribution changes of evergreen broad-leaved species in Italy". Items already in the verified review (`03_papers/04_evergreen_distribution_change_litreview.md`, v2) and the wiki (Seddaiu 2025 x2, Puletti 2019, Pollastrini 2019, Lloret 2004, Alderotti 2023/2025, Bussotti 2021, Frisullo 2018, Bregant 2025, Gazol & Camarero 2022, Carnicer 2011, Aubard 2019, Padial-Iglesias 2022, Peñuelas & Boada 2003, Delzon 2013) are NOT re-researched.

**Access and method limits (honest).**
- OpenAlex and Semantic Scholar returned HTTP 429 at once; CrossRef worked for DOI lookups (metadata checked; abstracts only for some publishers). Google Scholar was not used.
- WebFetch paraphrases pages and refuses long verbatim quotes, and ScienceDirect, Springer and HAL (Anubis) were blocked. So **no tag below is a full verbatim abstract fetched from the publisher unless stated "[ABSTRACT-READ, CrossRef verbatim]"**. Search-tool summaries are tagged [ABSTRACT-VIA-SEARCH].
- About 20 tool calls in total. This round is thin on Greece, Turkey (holm oak), California, laurophyll frost damage, Italian-language items and forward citations; those are listed as gaps at the end rather than filled with guesses.

Tags: [ABSTRACT-READ, CrossRef verbatim] = abstract text returned by the CrossRef API; [ABSTRACT-VIA-SEARCH] = search or fetch tool summary of the abstract/page; [METADATA-ONLY] = CrossRef record, no abstract; [SNIPPET/TLDR-ONLY].

---

## Part A. Concept vocabulary and best definitional sources

### Takeaway
Four citeable anchors cover most of the vocabulary: Breshears 2005 (coining "global-change-type drought"), Allen 2015 ("hotter drought"), McDowell 2008 (hydraulic failure vs carbon starvation) and Hartmann 2022 (unexpected mortality in "tolerant" ecosystems). For Mediterranean oaks, Gentilesca 2017 and Alderotti & Verdiani 2023 are the best regional syntheses; Marques 2025 is the systematic review of oak-decline factors. Terms such as "crown dieback", "defoliation" and "decline spiral" have no single definitional paper found in this round.

### Cited findings

**1. Global-change-type drought / hotter drought**
- Breshears et al. 2005, PNAS 102(42):15144-15148, DOI 10.1073/pnas.0505734102 [ABSTRACT-READ, CrossRef verbatim; CrossRef authors: Breshears, Cobb, Rich, Price, Allen, Balice et al.]. "Future drought is projected to occur under warmer temperature conditions as climate change progresses, referred to here as global-change-type drought" ; ">90% of the dominant, overstory tree species (Pinus edulis, a piñon) died" after 15 months of depleted soil water; die-off visible in NDVI. Limit: SW North American piñon-juniper woodland, not Mediterranean; one event. Supports: the definition of global-change-type drought.
- Allen, Breshears & McDowell 2015, Ecosphere 6(8):art129 (CrossRef: pages "1-55"; check article number before citing), DOI 10.1890/es15-00203.1 [ABSTRACT-READ, CrossRef verbatim]. "drought accompanied by warmer temperatures - 'hotter drought', an emerging characteristic of the Anthropocene"; summarises evidence for lesser vs greater vulnerability and states "substantial debate remains" about future mortality risk. Limit: global perspective, debate paper. Supports: definition of hotter drought and the fact that its consequences are contested (CO2 fertilisation and greening on the "lesser vulnerability" side).
- Hartmann et al. 2022, Annu Rev Plant Biol 73:673-702, DOI 10.1146/annurev-arplant-102820-012804 [ABSTRACT-READ, CrossRef verbatim]. "events of sudden and unexpected elevated tree mortality following heat and drought events in ecosystems that previously were considered tolerant or not at risk"; "We currently lack both sufficient data and understanding to identify whether these observations represent a global trend toward increasing tree mortality". Supports: framing of Mediterranean holm oak dieback as an "unexpected" event in a drought-adapted system, and caution against calling it a trend.

**2. Hydraulic failure vs carbon starvation**
- McDowell et al. 2008, New Phytol 178(4):719-739, DOI 10.1111/j.1469-8137.2008.02436.x [ABSTRACT-READ, CrossRef verbatim, first part]. "A common mechanism for plants with isohydric regulation of water status results from avoidance of drought-induced hydraulic failure via stomatal closure, resulting in carbon starvation and a cascade of downstream effects such as reduced resistance to biotic agents." Hydraulic failure per se "may occur for isohydric seedlings or trees near their maximum height"; anisohydric plants are "predisposed to hydraulic failure" (verbatim part truncated by me at that point). Limit: a hypothesis framework, partly contested later; quoted here for definitions only. Supports: definitions of the two mechanisms and their interaction with biotic agents.

**3. Mediterranean oak decline syntheses**
- Gentilesca, Camarero, Colangelo, Nolè & Ripullone 2017, iForest 10(5):796-806, DOI 10.3832/ifor2317-010 [METADATA-ONLY via CrossRef; search summary: drought "reported as the main driver triggering oak decline within the Mediterranean Basin, although other causes (i.e., increasing temperature, pathogens attack or excessive stand density) could exacerbate decline" = [ABSTRACT-VIA-SEARCH]]. Title: "Drought-induced oak decline in the western Mediterranean region: an overview on current evidences, mechanisms and management options to improve forest resilience". Limit (already noted in v2): mostly ring-porous deciduous oaks. Supports: "oak decline" as a multi-factor, drought-triggered complex.
- Alderotti & Verdiani 2023, AoB Plants 15(5):plad051, DOI 10.1093/aobpla/plad051 [ABSTRACT-VIA-SEARCH, PMC page fetched, paraphrase] (already in v2 as [ABSTRACT-READ]; metadata confirmed here). Organises decline as a "triangle" of tree traits, abiotic and biotic stressors; holm oak may fail through "carbon starvation or hydraulic dysfunction"; hypothesises that winter drought spells contribute; reported mainly in Iberia, Italy and southern France. Limit: review; the winter-drought point is hypothesis.
- Marques, Bugalho, Acácio & Catry 2025, Trees, For People 19:100803, DOI 10.1016/j.tfp.2025.100803, "Disentangling research on oak decline factors in Mediterranean-type climate regions: A systematic review" [METADATA-ONLY via CrossRef; abstract not obtainable (ScienceDirect redirect)]. A secondary summary (International Oak Society page, [SNIPPET/TLDR-ONLY]) says: 241 peer-reviewed papers up to 2022, mostly Mediterranean Basin, most-studied species cork oak and holm oak, no single cause. **The "48 % pathogens vs 17 % climate" figure used by Seddaiu 2025 could not be traced to this paper in this round; verify in the PDF before citing the numbers.** Also note the CrossRef first author is "Marques Marco"; the wiki note should cite it as Marques M. et al.
- Seddaiu et al. 2025, Forest@ 22(1):56-65, DOI 10.3832/efor4934-022 [METADATA-ONLY here, already in wiki]. Metadata confirmed by CrossRef; authors Seddaiu, Ruiu, Piras, Scanu, Satta, Lentini.

**4. Other vocabulary (no definitional source found this round)**
- Crown dieback vs mortality vs defoliation: not separately defined in any source retrieved. Lloret 2004 (in v2) distinguishes canopy dieback with resprouting from tree death (1994 drought: "directly killed few trees", per a Catalan report [SNIPPET/TLDR-ONLY]). The ICP Forests manual (defoliation as % leaf loss vs reference tree) should be fetched as the definitional source [not done].
- Resilience, resprouting, legacy effects: Lloret 2004 ("progressive loss of resilience", in v2); no review of legacy effects (e.g., Anderegg 2015) was verified here [not done].
- Compound drought-heat: Gazol & Camarero 2022 (in v2).
- Forest decline spiral (Manion): CrossRef search returned only Manion 1981 "Norway Maple Decline" (J Arboric Urban For 7:38-42, DOI 10.48044/jauf.1981.010 [METADATA-ONLY]) which is not the spiral paper; Manion's 1981 book "Tree Disease Concepts" (predisposing, inciting, contributing factors) was not found. [still unverified]. The Seddaiu "predisposing" logic is not enough to cite Manion.

### Inferences
- The Introduction can define "hotter drought" with Allen 2015 plus Breshears 2005, mechanisms with McDowell 2008, and cite Hartmann 2022 for "unexpected" die-offs. Gentilesca 2017/Alderotti & Verdiani 2023 cover the Mediterranean oak syntheses.

### Gaps
- Definitional papers for "crown dieback", "legacy effects", "decline spiral": not found.

---

## Part B. Charted studies (new this round)

Columns in prose per entry: reference + DOI, tag, region, period, data/method, finding, limits, supports.

### B1. Spain / Catalonia (holm oak, field and experiment)
1. Ogaya, Liu, Barbeta & Peñuelas 2020. "Stem mortality and forest dieback in a 20-years experimental drought in a Mediterranean holm oak forest." Front For Glob Change 2:89, DOI 10.3389/ffgc.2019.00089 (online 8 Jan 2020; DOI carries 2019). Metadata CrossRef-checked. [ABSTRACT-VIA-SEARCH + page fetch paraphrase; short verbatim quotes returned by fetch tool: "Stem mortality was higher when mean annual temperature was higher and rainfall was lower"; "Selective stem thinning strongly reduced stem mortality (especially in Q. ilex)"].
   - Region/period: Prades, Catalonia; throughfall-exclusion (about 15 % reduction) plus control and thinned plots; mortality 1999-2018 (plot design as reported by the fetch tool, check); climate 1975-2018 (mean annual temperature about +1.7 degC; spring-summer temperature +2.7 degC; spring-summer rainfall about -200 mm; annual precipitation trend not significant).
   - Finding: mortality higher in Q. ilex than co-occurring tall shrubs under drought; annual stem mortality correlated with temperature (R2 0.17) and with spring-summer precipitation (R2 -0.18); MODIS NDVI (R2 0.43) and EVI (0.35) related to stem mortality, GPP/NPP not.
   - Limits: one site; stem (not tree) mortality of a coppice stand; low R2; the MODIS link is 500 m-1 km vs a small experiment.
   - Supports: "experimental and observational evidence that warming and drying raise Q. ilex stem mortality" and "NDVI-type indices can track mortality".
2. Saura-Mas, Bonas & Lloret 2015. "Plant community response to drought-induced canopy defoliation in a Mediterranean Quercus ilex forest." Eur J For Res 134(2):261-272, DOI 10.1007/s10342-014-0848-9 (online 2014). Metadata CrossRef-checked. [ABSTRACT-VIA-SEARCH]. Montserrat, Catalonia; six years after a severe drought that killed dominant holm oaks, regeneration changed community structure and composition (more small shrubs and herbs); authors warn that if canopies do not recover, defoliation could permanently change diversity and composition. Limits: community focus, abstract details (year of drought, mortality numbers) not seen. Supports: dieback-driven shift from tree canopy to shrub states (relevant to map "losses" and to the argument that a drought can change leaf-type cover).
3. Doctoral and thesis material (Galiano; Silvestre Carbonell 2024) appeared in search results; not citeable as primary studies here. Galiano et al. (CREAF) "Drought-induced die-off in Pinus sylvestris and Quercus ilex forests of Catalonia" [thesis record, SNIPPET/TLDR-ONLY, metadata not verified]. Do not cite.
4. Items seen only as search snippets, not verified: Iberian soil study with 13 sites, Cáceres dehesa tree-ring study, central Spain coppice growth study, Cardillo et al. 2020 bioRxiv "Spatio-temporal analysis at landscape scale of the Iberian oak decline epidemic caused by Phytophthora cinnamomi" (DOI 10.1101/2020.03.27.011304, CrossRef-confirmed title, preprint, [METADATA-ONLY]); Pérez Álvarez 2026 SSRN "Monitoring the spatial distribution of holm oak mortality in relation to terrain-derived m..." (DOI 10.2139/ssrn.6740564, preprint, [METADATA-ONLY]; potentially relevant to terrain-driven mortality, abstract not read).

### B2. France
5. Cailleret et al. (2025?), Scientific Reports of the Port-Cros National Park (HAL hal-05492374; INRAE). Exact title, DOI and page range not obtained (HAL page blocked by Anubis; search tool summary only) [ABSTRACT-VIA-SEARCH, SNIPPET/TLDR-ONLY]. Search summary: Port-Cros island, 2023 assessment; "68 % of Quercus ilex and 64 % of Quercus suber trees were classified as declining as they showed a leaf deficit above 50 %"; mortality 12 % of basal area and 18 % of stems vs a French national average of 5 %; drought, warming since the 1980s and stand densification/self-thinning named as contributors; 41 % of Q. ilex declining in 2019 vs 5 % in 2000 (credited to Bec et al. 2020, DSF-style data). Strong candidate for a French/Mediterranean-island mortality rate and for the "densification" mechanism, but **cannot be cited until title/DOI/numbers are read from the PDF**. Bec et al. 2020: not identified.
   - Supports (after verification): dieback and mortality are documented on the French Mediterranean coast and islands; stand densification after abandonment is a predisposing factor (links expansion and loss).
6. Delzon 2013 (in v2) remains the only French expansion item. No Provence/Languedoc 2022 holm-oak dieback paper was found.

### B3. North Africa
7. Chettaba forest, Constantine, Algeria: Ekológia 2025 (DOI 10.2478/eko-2025-0005; reference-global page, [ABSTRACT-VIA-SEARCH]); eight plots; altitude, slope, exposure and tree size as drivers of holm oak dieback. A second Algerian study (Univ. Ouargla repository PDF; 54.55 % of trees show weak defoliation, 11.11 % strong) is [SNIPPET/TLDR-ONLY]. Limits: tiny plot networks, local, repository grey literature. Authors, journal volume and pages not checked. Supports only the statement that holm oak dieback is reported from North Africa (also Flora Mediterranea 35 on Morocco, [SNIPPET/TLDR-ONLY], "understanding ... in North Africa remains limited").
   - No Greek or Turkish holm oak dieback paper found; no California/Chile analogue found this round.

### B4. Italy (new items only)
8. Gentilesca et al. 2017 (see A3); relevant to Italian Basilicata/Apulia oaks; note again that it concerns mainly deciduous ring-porous oaks.
9. Regione Toscana, Servizio Fitosanitario Regionale with CNR-IPSP and CREA: "Querce in Toscana: prime considerazioni sullo stato di deperimento" (web page, last updated 10 Dec 2025; grey literature) [page fetched, paraphrase]. Species most affected: cerro (Q. cerris), sughera (Q. suber), leccio (Q. ilex). No single organism found; combination of conditions; most surveyed sites "recovering"; stands on poor shallow soils and stands hit by repeated defoliator outbreaks (Lymantria dispar, Tortrix viridana), worsened by prolonged drought and above-average temperature; pathogenic fungi and bacteria found in some stands, pathogenicity under evaluation. No areas or percentages. Limits: institutional page, not peer reviewed, 2025 survey. Supports: pathogen vs climate is unresolved in Tuscany and defoliator insects are an additional factor (a third agent not mentioned in Seddaiu 2025 per the wiki note); also suggests recovery.
10. Alderotti PhD thesis (Florence, 2024) and Scanu et al. 2025 conference abstract (FORECOMON, Florence repository) [SNIPPET/TLDR-ONLY]: Maremma, absence of autumn NSC recovery after summer drought as a signal of incipient mortality; 2024 dieback in Sardinia, Sicily and Apulia, over 100,000 ha in Sardinia by Sentinel-2. Not citeable as peer-reviewed; Scanu is probably the same 110,000 ha source as Satta/Seddaiu (non-independent).
11. Montecchio et al. 2004 (Phytopathologia Mediterranea; DOAJ link, coastal holm oak forest with saltwater intrusion and falling groundwater; decline linked to drought and salinity) [SNIPPET/TLDR-ONLY, volume/pages not verified]. A coastal-vs-inland nuance. Do not cite until read.
12. Italian-language items: Gentilesca et al., AISF proceedings PDF "123-129 gentilesca.pdf" (tree-ring and isotope study of declining Quercus in southern Italy: declining trees grew slower from about 2000; severe droughts trigger decline with lag; insects and weakness pathogens aggravate) [SNIPPET/TLDR-ONLY]. No Forest@/iForest/L'Italia Forestale e Montana item specific to Q. ilex beyond Seddaiu 2025 and Gentilesca 2017 was found. No RAF Italia / CUFA "Rapporto sullo stato delle foreste" document identified; gap.

### B5. Remote sensing of dieback and browning (new)
13. Aubard 2019 (in v2; abstract confirmed again by CrossRef, verbatim: "Oak stands are declining in many regions of southern Europe"; NDVI 1984-2017 at 30 m; July-August NDVI to focus on the tree layer; Mann-Kendall and contextual Mann-Kendall). Search summary adds: 12 % of oak stand area with significant decreasing trends, mostly mountains with shallow soils, cork-oak agroforestry most declining [ABSTRACT-VIA-SEARCH]. Use as in v2.
14. Padial-Iglesias 2022 (in v2): abstract confirmed again by CrossRef; BEF drivers precipitation, temperature, solar radiation. Authors: Padial-Iglesias, Ninyerola, Serra, González-Guerrero, Espelta, Pino (Catalan group).
15. Tuscany Sentinel-2 field-vs-NDVI/NDWI study 2020-2021 (found through search; "tracked decline only where dieback was severe and uniform; performed poorly on patchy dieback") [SNIPPET/TLDR-ONLY]; authors/DOI not retrieved (ISPRS Archives XLIII-B3-2020 and Florence repository records appeared). Do not cite until identified; it would be the most relevant caveat for using spectral indices on patchy Q. ilex dieback.
16. Madrid Sentinel-2 NDVI vs SPEI 2016-2024 (Spanish abstract, URJC repository), Pléiades Neo for Phytophthora symptoms [SNIPPET/TLDR-ONLY]; not verified.
- No LandTrendr/CCDC study of Q. ilex in the Mediterranean was found in this round.

### B6. Pathogens vs climate
17. Alderotti & Verdiani 2023 and Marques 2025 (see A3): P. cinnamomi long considered main factor in Iberian dehesa (Brasier 1996, Ann Sci For 53:347-358, DOI 10.1051/forest:19960217, CrossRef-confirmed title "Phytophthora cinnamomi and oak decline in southern Europe. Environmental constraints including climate change" [METADATA-ONLY]; a 2013 review on cork and holm oak decline and P. cinnamomi (Camilo-Alves/Nunes da Clara/de Almeida Ribeiro, per a University of Evora PDF link, [SNIPPET/TLDR-ONLY], not verified) says its role is "debated").
   - Conflict: Italian sources disagree regionally (Seddaiu: Sicily no pathogens found; Apulia Botryosphaeriaceae plus Phytophthora (Bregant 2025, in v2); Tuscany page: no single agent, defoliator insects).
   - A Spanish open-woodland tree-ring study found growth decline up to 30 years before death and attributed death to P. cinnamomi while allowing drought as an alternative [ABSTRACT-VIA-SEARCH; study not identified].

### B7. Gain and loss in one region
18. Catalonia/Iberia: Padial-Iglesias 2022 (expansion of broadleaf evergreen forests with drivers); a Catalonia forest-transition paper (1868-2005; forest expanded since the 1950s) appeared in search, not identified (DOI not retrieved) [SNIPPET/TLDR-ONLY]. Corsica: holm oak reforestation of shrubland and cropland 1975-2000 at +3.40 % per year (search summary, paper not identified) [SNIPPET/TLDR-ONLY]. Cáceres dehesas: holm oak cover loss of 0.27 % and 0.04 % per year at two sites, accelerating after 1984 (paper not identified) [SNIPPET/TLDR-ONLY]. Statement supported only after verifying: expansion via abandonment and loss via dehesa management/decline occur in the same country. No single study showing both gain and loss in one region (Provence, Liguria, Tuscany) was found.

### B8. Laurophylls: box (Buxus)
19. Lehtijärvi, Doğmuş-Lehtijärvi & Oskay 2014. "Cylindrocladium buxicola is threatening the native Buxus sempervirens populations in Turkey - short communication." Plant Protect Sci 50(4):227-229, DOI 10.17221/18/2014-PPS. CrossRef-checked [METADATA-ONLY; PDF unreadable]; a search summary reports Trabzon (Black Sea) forests in Nov 2012 with many trees dead or severely defoliated and spread of 3-25 km along valleys [SNIPPET/TLDR-ONLY]. Native box mortality by an introduced pathogen; not climate.
20. Mariotti 2017. "Cydalima perspectalis (Walker, 1859) (Lepidoptera, Crambidae) and the threats for the Nature 2000 Habitat 5110 in Liguria (NW-Italy)." Boll Mus Ist Biol Univ Genova 79 (2017) (page range and DOI not obtained; riviste.unige.it/BMIB/article/view/557) [ABSTRACT-VIA-SEARCH]. Six SACs affected, severe damage on about 370 ha, roughly 70 % of the area (per search summary). Follow-up: Badano, Caracciolo, Mariotti & Raineri 2019 (reported: nearly the whole habitat-5110 area defoliated since 2013, then a population crash after the food resource was depleted; journal not retrieved) [SNIPPET/TLDR-ONLY]. Relevance: Alessi 2019 gives Buxus only 3.7 % of its potential range filled; the moth defoliation is a mortality/defoliation factor that is not climate or land use. Verify before use.
21. Šafránková et al. 2013, Plant Protect Sci 49(4):165-168, DOI 10.17221/82/2012-PPS: boxwood blight in a Czech nursery; not about forests; drop.
- No evidence found for laurophyll frost or drought damage in this round.

---

## Part C. Cross-cutting points and conflicts

- Mortality magnitude: sources are heterogeneous. Experimental stem mortality (Ogaya 2020), plot defoliation (Port-Cros), ICP Forests (about 250 trees in 11 plots in Italy, per Seddaiu 2025 in wiki) and Sardinia remote sensing (about 110,000 ha) are not comparable. No Italian NFI/CUFA mortality statistic for Q. ilex found.
- Spain: climate (Ogaya 2020: 20-year drought experiment, temperature and rainfall) vs Phytophthora (dehesa literature) unresolved; Marques 2025 would be the arbitration but could not be read.
- Tuscany: Puletti 2019 (holm oak "tolerant to short extreme events") vs Pollastrini 2019 and the Regione Toscana page (decline, but most sites recovering): consistent only if recovery is stressed.
- Recovery is a recurrent finding (Regione Toscana: most sites recovering; Pollastrini: partial resprouting), which matters for annual maps: a brief browning may not alter leaf-type class.
- Decline and expansion coexist in the Iberian/Corsican/Italian evidence (B7); the elevation/coastal-inland structure was not found in any new paper.

## Part D. Concepts and best definitional source (summary)

| Concept | Best source found | Tag |
|---|---|---|
| Global-change-type drought | Breshears 2005, DOI 10.1073/pnas.0505734102 | ABSTRACT-READ (CrossRef) |
| Hotter drought | Allen, Breshears & McDowell 2015, DOI 10.1890/es15-00203.1 | ABSTRACT-READ (CrossRef) |
| Hydraulic failure vs carbon starvation | McDowell 2008, DOI 10.1111/j.1469-8137.2008.02436.x | ABSTRACT-READ (CrossRef) |
| Unexpected mortality in "tolerant" systems | Hartmann 2022, DOI 10.1146/annurev-arplant-102820-012804 | ABSTRACT-READ (CrossRef) |
| Compound drought-heat events | Gazol & Camarero 2022 (in v2) | ABSTRACT-READ (v2) |
| Mediterranean oak decline complex | Gentilesca 2017 (iForest, 10.3832/ifor2317-010); Alderotti & Verdiani 2023 (10.1093/aobpla/plad051); Marques 2025 (10.1016/j.tfp.2025.100803, abstract unread) | mixed, see above |
| Resilience and resprouting | Lloret 2004 (in v2); Pollastrini 2019 (in v2) | v2 |
| Crown dieback vs mortality vs defoliation | no single source found; ICP Forests manual suggested, not fetched | gap |
| Forest decline spiral (Manion) | not found | gap |
| Box blight / box moth as laurophyll mortality | Lehtijärvi 2014; Mariotti 2017 | METADATA-ONLY / ABSTRACT-VIA-SEARCH |

## Gaps (what this round could not close)
- Marques 2025 abstract and the 48 %/17 % figures; Port-Cros (Cailleret) title/DOI/numbers; Bec et al. 2020; the Tuscany Sentinel-2 NDVI/NDWI study identity; the Catalan forest-transition and Corsica papers; Cáceres dehesa paper.
- Forward citations (2022-2026) of Pollastrini, Lloret, Carnicer, Gazol & Camarero, Seddaiu: not retrieved (OpenAlex/Semantic Scholar blocked).
- Italian NFI/CUFA/RAF Italia forest-health reports; Greece, Turkey (holm oak), California; laurophyll frost damage; LandTrendr/CCDC on Q. ilex; 2022 and 2023-24 drought studies of evergreen oaks (only Port-Cros and Italian 2024 items).
