# Remote sensing and time-series trajectory/change studies for evergreen broad-leaved change in Italy (scoping round 3)

**Scope and method.** Gap-filling for `03_papers/04_evergreen_distribution_change_litreview.md` (v2). Items already verified there are NOT repeated except where I upgraded a weak tag. Metadata were checked against the CrossRef API (a record counts as "CrossRef-checked"); abstracts were taken from CrossRef or OpenAlex (verbatim, tagged [ABSTRACT-READ]) or from search/fetch tools (tagged [ABSTRACT-VIA-SEARCH]; the fetch tool limits verbatim quotes to 125 characters, so those quotes are short). Date of work: 2026-10-16.

**Access limits (honest).**
- Elsevier (ScienceDirect/linkinghub) returns only "Redirecting"; Elsevier and Springer abstracts are elided in CrossRef, OpenAlex and Semantic Scholar. So the verbatim abstracts of Kennedy 2010, Verbesselt 2010, Olofsson 2014, Aldwaik & Pontius 2012, Hamed & Rao 1998, Stehman 2021 could NOT be obtained; I only got fetch-tool paraphrases with short quotes.
- Hamed & Rao 1998, Garbarino 2020 and Falcucci 2007 (CrossRef lists it as online Dec 2006, printed 22(4) 2007) stayed unresolved: no abstract from any route, and I did not find an open copy. They keep their old tags ([SNIPPET/TLDR-ONLY] / [SEARCH-SUMMARY]).
- OpenAlex search and Semantic Scholar search were rate-limited (HTTP 429); only single-DOI OpenAlex lookups worked. Google Scholar was not tried. Discovery relied on CrossRef bibliographic search and the web-search tool (whose answers are summaries, so every discovery hit was re-checked against CrossRef before listing).
- About 17 tool calls of discovery plus about 12 of verification; coverage of Italian-language and Spanish/Portuguese grey literature remains weak.

---

## 1) Concept vocabulary and best definitional sources

### Takeaway
Most concepts have an established, citable origin (mostly [ABSTRACT-READ] or [ABSTRACT-VIA-SEARCH]). The vocabulary is fragmented: "trajectory" means a pixel's class sequence in land-change science (Mertens & Lambin) but a spectral segment fit in LandTrendr (Kennedy), so define it explicitly once. A single definitional source for "temporal consistency" and for "map error vs real change" is best taken from Hermosilla/Bogaert/Pontius & Lippitt/Torchiana rather than from algorithm papers.

### Cited Findings
See the final table in section 9 (concept to best source), which carries the tag of each source. Key new definitional sources found in this round:
- Land-cover-change trajectory: "modeling land-cover change trajectories over several observation years allows a better projection of areas with a high probability of change ... than projecting such areas on the basis of observations from the previous time period alone" and "A significant proportion of the areas subject to a land-cover conversion experienced other changes in the following years" — [Mertens & Lambin 2000](https://doi.org/10.1111/0004-5608.00205) [ABSTRACT-READ, OpenAlex].
- Trajectory typology by cluster analysis of Landsat class sequences: Mena 2008 clusters trajectories of a 1974-2002 Landsat classification and derives "probabilities of transitions" — [Mena 2008](https://doi.org/10.14358/pers.74.6.737) [ABSTRACT-READ, OpenAlex].
- Map error vs real change, HMM version: "misclassified imagery can lead to misleading conclusions about transition processes ... transition rates without correction are severely biased" — [Torchiana et al. 2025](https://doi.org/10.1162/rest_a_01301) [ABSTRACT-READ, CrossRef].
- Hotspot of vegetation change defined by significant trend: Baglioni et al. use contextual Mann-Kendall plus Theil-Sen on 40-year Landsat NDVI to "identify significant hotspots of change" — [Baglioni et al. 2026 (EGU abstract)](https://doi.org/10.5194/egusphere-egu26-13167) [ABSTRACT-READ, CrossRef; conference abstract, not peer reviewed].
- Label back-casting / label propagation: "locally trained classification using an automated selection of training samples from existing, but outdated land cover information" — [Radoux et al. 2014](https://doi.org/10.3390/rs6053965) [ABSTRACT-READ, CrossRef].

### Inferences
- Use "class trajectory" (sequence of annual labels per pixel; Mertens & Lambin, Mena) and "spectral/index trajectory" (LandTrendr) as two separate terms.

### Gaps
- No single review defining "temporal consistency" of annual categorical maps was found; the term is used operationally by Hermosilla 2024, Bogaert 2022 and the GLC_FCS30D paper.

---

## 2) European, Mediterranean and Italian multi-decadal studies of tree species, forest type or CLC change

### Takeaway
No new study mapping evergreen-broadleaved or Q. ilex change over decades in Italy was found, confirming the v2 conclusion. New European products are coarse in class detail (Witjes 2022: class-level F1 collapses to 0.49 at 43 classes) and CLC is shown to be unreliable for change (Garcia-Alvarez 2022). Nothing found separates CLC 323 (sclerophyllous vegetation) trends for Italy.

### Cited Findings (charted studies)

**Witjes, M., Parente, L., van Diemen, C.J., Hengl, T., Landa, M., Brodsky, L., et al. (2022).** A spatiotemporal ensemble machine learning framework for generating land use/land cover time-series maps for Europe (2000-2019) based on LUCAS, CORINE and GLAD Landsat. PeerJ 10:e13573. [DOI](https://doi.org/10.7717/peerj.13573). [ABSTRACT-READ, CrossRef; CrossRef-checked]
- Region/period/data: Europe, 2000-2019, GLAD Landsat plus NPP/VIIRS, five million harmonised LUCAS and CORINE-derived training samples; ensemble (random forest, gradient boosted trees, ANN) with spatial k-fold cross-validation.
- Output: most probable class, class probabilities and model variance per pixel; 43 (level 3), 14 and 5 classes.
- Accuracy: "overall accuracy (a weighted F1-score) of 0.49, 0.63, and 0.83 when predicting 43 (level-3), 14 (level-2), and five classes (level-1)". "spatiotemporal models generalize better to unknown years, outperforming single-year models on known-year classification by 2.7% and unknown-year classification by 3.5%".
- Limits: starts 2000 (no 1985-1999); training labels derive from CLC (25 ha minimum mapping unit) and LUCAS points, so fine species/leaf-type classes are not expected to be reliable; accuracy at the finest level is low. Whether evergreen/deciduous broadleaves are separate classes was not in the abstract [still unverified].
- Supports: a European annual 30 m product exists but cannot serve as a DTS/leaf-type reference; the finest-level accuracy (0.49) shows the difficulty of fine classes with CLC-derived labels; spatial CV is used.

**Garcia-Alvarez, D. & Camacho Olmedo, M.T. (2022).** Analyzing the uncertainty of the CORINE Land Cover time series (1990-2018) for Spain (Asturias case). EarthArXiv preprint. [DOI](https://doi.org/10.31223/x5qd1f). [ABSTRACT-READ, CrossRef]
- Region/period: Asturias (Spain), CLC status (CLC) and change (CHA) layers 1990-2018.
- Finding: "CLC and CHA layers provide different information, especially after the change of production of CORINE Spain in 2012 ... mixed categories ... are behind most of detected change in both types of CORINE layers".
- Limits: one region, preprint (publication status unchecked); Spain not Italy.
- Supports: statement that CLC-based change (including any 323/324 shrub-forest transitions) is partly an artefact of production changes and mixed classes; motivates not using CLC as ground truth for change.

**Di Gennaro, A., Migliozzi, A. & Marotta, M. (2019).** Una fase storica nuova per i paesaggi italiani / New interpretative scenarios for the evolution of Italian landscapes. Economia della Cultura 3:371-382. DOI 10.1446/95595 (not resolvable in CrossRef: HTTP 404; metadata taken from RePEc/IRIS as shown by the search tool). [SNIPPET/TLDR-ONLY]
- Region/period/data: Italy, CLC series 1990-2018.
- Finding (search paraphrase): Italian landscapes have entered "a new evolutionary phase without guiding processes", keywords land cover change, agricultural abandonment, urban sprawl. Full text restricted; class-level figures (323/324) NOT seen.
- Limits: metadata unverified in CrossRef; no class numbers; economics/landscape journal.
- Supports: nothing quantitative yet; flag as a lead for the CLC 1990-2018 Italian change story, to be read via uibk access.

**Potapov, P., Turubanova, S., Tyukavina, A., Krylov, A., McCarty, J., Radeloff, V., Hansen, M. (2015).** Eastern Europe's forest cover dynamics from 1985 to 2012 quantified from the full Landsat archive. Remote Sensing of Environment 159:28-43. [DOI](https://doi.org/10.1016/j.rse.2014.11.027). [METADATA-ONLY, CrossRef-checked; no abstract obtainable]
- Relevance: demonstrates a 1985-2012 Landsat-archive design in Europe, but forest cover (tree/no tree), Eastern Europe, no species. Companion driver paper: Alix-Garcia et al. 2016, Land Use Policy [METADATA-ONLY from CrossRef search: [DOI](https://doi.org/10.1016/j.landusepol.2016.08.014)].
- Supports only: precedent for a 30 m Landsat 1985-onward European forest change estimate; do not cite findings.

**Baglioni, L., Morresi, D., Tonelli, E., Lingua, E., Marzano, R., Urbinati, C. (2025).** Forestline detection and treeline ecotone dynamics in the Italian Alps and Apennines by satellite remote sensing. EGU24 abstract. [DOI](https://doi.org/10.5194/egusphere-egu24-15620). [ABSTRACT-READ, CrossRef; conference abstract]
- Region/period/data: Italian Alps and Apennines; Landsat time series of "the last 40 years"; Copernicus Tree Cover Density 2018 for forestline; NDVI, EVI, Tasseled Cap Angle.
- Aim: "to locate hotspots of long-term vegetation dynamics using Landsat-based spectral trend analysis ... Hotspots will serve us to analyse the ecological drivers of vegetation change and to predict future vegetation dynamics."
- Follow-up: Baglioni, Vitali, Choler, Bayle, Garbarino, Morresi (2026), Predisposing factors to Landsat based greening trends in the Italian forestline ecotones, EGU26 abstract [DOI](https://doi.org/10.5194/egusphere-egu26-13167) [ABSTRACT-READ, CrossRef]: 1984-2023 NDVI, "Trend significance was tested with contextual Mann-Kendall statistics, while Theil-Sen slopes quantified the magnitude of change"; assesses topographic, climatic and anthropogenic predisposing factors; Alps vs Apennines contrast attributed to land-use legacy.
- Limits: treeline ecotone only (not Mediterranean evergreen forest); NDVI not class maps; conference abstracts, results truncated in what I read; the same group (Garbarino, Morresi, Urbinati, Vitali) wrote Garbarino 2020.
- Supports: the only Italian Landsat 40-year hotspot (significant-trend) plus predisposing-factor design found; cite as methodological parallel, flag as not peer reviewed.

**Mirici, M.E. (2018).** Land use/cover change modelling in a Mediterranean rural landscape using multi-layer perceptron and Markov chain (MLP-MC). Applied Ecology and Environmental Research 16(1):467-486. [DOI](https://doi.org/10.15666/aeer/1601_467486). [ABSTRACT-READ, OpenAlex]
- Region/period/data: Eastern Mediterranean Turkey watershed; Landsat TM/OLI 1990, 2003, 2014; hybrid classification kappa 0.81 / 0.85 / 0.87.
- Finding: 2014 simulated from 1990 and 2003, "the rate of overlap was found as 89%"; 2025: forest +8.70 %, agriculture +6.51 %, bareground -13.31 %.
- Limits: 89 % overlap not compared with a persistence null model in the abstract (see Pontius & Malanson 2005 below); three dates; coarse classes; Turkey.
- Supports: example that Markov/MLP-MC land-cover forecasting is common in Mediterranean RS literature; illustrates the weak-validation practice the paper should avoid.

**Laidi, Y., El Bouchti, N., Abbas, Y., Benhssaine, K., El Mderssa, M. (2026).** Forty years of Landsat and Sentinel-2 retrospective analysis reveal a species-differentiated dieback signal in the Atlas forests of Beni Mellal-Khenifra (Morocco). Ecological Engineering & Environmental Technology 9:110-131. DOI 10.12912/27197050/226093 (from the ecoeet.com page; not looked up in CrossRef). [ABSTRACT-VIA-SEARCH (fetch-tool summary of the journal page)]
- Region/data: Morocco, Landsat and Sentinel-2 1984-2024, 2,901 Landsat and 2,933 Sentinel-2 sample pixels, six strata of the Second National Forest Inventory, SPEI-3/6/12 and VPD.
- Method: per-pixel NDVI, STL decomposition and PELT change points ("BFAST-like"), autocorrelation-corrected significance tests, bootstrap CIs.
- Finding (as summarised): about 187,700 ha cumulative dieback (20.1 % of forest cover); holm oak largest absolute area (142,591 ha); cork oak 41.4 % of pure stands; SPEI-12 strongest correlate; Sentinel-2 detected 18.3 to 26.3 percentage points more cedar mortality than Landsat.
- Limits: low-tier venue, 2026, tool summary only, no abstract verbatim; NDVI-based dieback, not species maps; North Africa.
- Supports (weakly): Landsat 1984-onward NDVI change-point approach on Q. rotundifolia/ilex strata correlated with SPEI; compare with Aubard 2019. Do not cite numbers without reading the paper.

### Inferences
- The gap statement of v2 ("no Mediterranean multi-decadal Landsat species/leaf-type change study") still holds after this round; the nearest are Padial-Iglesias 2022 (already in v2), Aubard 2019, Laidi 2026 (NDVI/dieback) and Baglioni 2025/2026 (hotspots, NDVI).
- Spanish Forest Map (MFE), Copernicus HRL forest type and Italian Carta Forestale/Carta Uso del Suolo were NOT found as change-analysis sources; they are classes/snapshots, not trajectories.

### Gaps
- No CLC 323 (sclerophyllous vegetation) trend figure for Italy was obtained. ISPRA/SNPA consumo di suolo is soil sealing, not vegetation type.
- A Zenodo "Mediterranean forest types map based on dominant species" (Sentinel-2, more than 80,000 samples, about 100 species grouped into 30 forest classes; [Zenodo record 7054338](https://zenodo.org/records/7054338)) surfaced in search; authors, year and accuracy not read [SNIPPET/TLDR-ONLY]. It is a candidate reference map for Italy and should be opened manually.

---

## 3) Annual land cover, leaf-type and species time-series products worldwide

### Takeaway
Two things matter for the paper: (i) annual 30 m global/national products exist but none gives a validated evergreen-vs-deciduous broadleaf trajectory in Italy; (ii) validations of early years are weak or indirect, and exact-year change accuracy is low (LCMAP: below 30 %). Hermosilla 2024 is confirmed (via the Earth Engine catalogue) to use a forward-backward HMM for post-classification smoothing.

### Cited Findings (charted products)

**Zhang, X., Zhao, T., Xu, H., Liu, W., Wang, J., Chen, X., Liu, L. (2024).** GLC_FCS30D: the first global 30 m land-cover dynamics monitoring product ... 1985-2022 ... Earth System Science Data 16:1353-1381. [DOI](https://doi.org/10.5194/essd-16-1353-2024). [ABSTRACT-READ, CrossRef; plus fetch-tool read of the ESSD page for accuracy sections = FULLTEXT-PARTLY-READ]
- Data/method: Landsat (Google Earth Engine) with continuous change detection (CCD); 35 sub-categories; 26 time steps ("maps were updated every 5 years before 2000 and annually after 2000"); training samples derived from "temporally stable areas"; "a temporal-consistency optimization algorithm ... to improve their temporal stability and suppress some false changes".
- Accuracy (page, via fetch tool): validated with 84,526 samples from 2020 only; overall accuracy 80.88 % (basic 10-class), 73.04 % (17-class LCCS level 1); EU third-party check 81.91 %; US yearly check 78.91 % (2000) to 80.04 % (2015) "slightly lower at the early stage" because only Landsat 5 was available; with forest split into five sub-categories forest producer's accuracy ranges 58.29 to 82.39 %, and the mixed-leaf forest user's accuracy is 39.34 % (section 4.2).
- Change finding: "forest and cropland variations have dominated global land-cover change"; net forest loss about 2.5 million km2 (abstract). No evergreen-specific finding in the abstract.
- Limits: the main validation year is 2020; 1985-1999 maps are 5-year steps; the leaf-type forest sub-classes are the weakest; northeastern Asia had no valid Landsat before 2000. Whether Italian Q. ilex stands are separable at 30 m in this product was not tested.
- Supports: statements that early-period annual 30 m maps have less data and lower accuracy; that leaf-type sub-classes are the weak part of a generic product; that a temporal-consistency step is standard.

**Xian, G., Smith, K., Wellington, D., Horton, J., Zhou, Q., Li, C., et al. (2022).** Implementation of the CCDC algorithm to produce the LCMAP Collection 1.0 annual land surface change product. ESSD 14:143-162. [DOI](https://doi.org/10.5194/essd-14-143-2022). [ABSTRACT-READ, CrossRef]
- CONUS, 1985-2017, 30 m, CCDC; "overall agreement for all years of the LCMAP primary land cover product reached 82.5 %" against about 25,000 reference samples.
- Limits: classes are coarse (the abstract does not list them; I believe tree cover is a single class [from background knowledge, not fetched]); US only.
- Companion: **Stehman, S.V., Pengra, B.W., Horton, J.A., Wellington, D.F. (2021)**, Validation of ... LCMAP Collection 1.0 annual land cover products 1985-2017, Remote Sensing of Environment 265:112646 ([DOI](https://doi.org/10.1016/j.rse.2021.112646)) [ABSTRACT-VIA-SEARCH, verbatim only from the search-tool snippet; CrossRef-checked]: footprint of change "UA was 49% (+/-0.3) and PA was 54% (+/-0.3)"; for class-specific change with exact-year agreement most classes were below 30 %, tree-cover loss best (UA 25 %, PA 31 %); reference sample of nearly 25,000 pixels labelled for every year.
- Supports: the strongest published evidence that exact-year change in annual Landsat land cover is poorly mapped even in a well-resourced programme; use to motivate decadal windows and uncertainty bounds. Directly relevant to the Pontius & Lippitt argument in v2.

**Hermosilla et al. 2024 (HMM detail).** The Earth Engine community catalogue states the annual species maps (Canada, 1984-2022, 30 m) use a "regionally representative Random Forests model using local training samples" followed by "a forward-backward Hidden Markov Model to improve the temporal consistency of tree species transitions", overall accuracy 86.1 % +/- 0.14 % — [GEE community catalogue entry](https://gee-community-catalog.org/projects/ca_species_ts/) [ABSTRACT-VIA-SEARCH; catalogue page, not the paper]. No accuracy by year is given there.
- Importance: this is a direct precedent for HMM smoothing of 30 m annual species maps. The paper's text should be read to see how the emission/transition matrices were set (not in the catalogue).

**Li, W., MacBean, N., Ciais, P., Defourny, P., Lamarche, C., Bontemps, S., et al. (2018).** Gross and net land cover changes in the main plant functional types derived from the annual ESA CCI land cover maps (1992-2015). ESSD 10:219-234. [DOI](https://doi.org/10.5194/essd-10-219-2018). [ABSTRACT-READ, CrossRef]
- 300 m, 1992-2015; "Gross forest loss and gain during 1992-2015 are 1.5 and 0.9 million km2 respectively, resulting in a net forest loss of 0.6 million km2" and the gross changes in ESA CCI are smaller than in other datasets (abstract).
- Supports: coarse annual product, PFT level, no species; use only as context for between-product disagreement.

**Buchhorn, M., Lesiv, M., Tsendbazar, N.-E., Herold, M., Bertels, L., Smets, B. (2020).** Copernicus Global Land Cover Layers - Collection 2. Remote Sensing 12(6):1044. [DOI](https://doi.org/10.3390/rs12061044). [ABSTRACT-READ, CrossRef]
- 100 m global map with cover-fraction layers ("20 layers"), "reaching around 80% or more overall accuracy", annual updates operational. The fraction layers are conceptually the same idea as a continuous leaf-type cover (LTC) representation: "represents areas of heterogeneous land cover better than the standard discrete classification scheme".
- Limits: 100 m, 2015-2019 epoch only (not multi-decadal).
- Supports: continuous cover fractions are an accepted representation for heterogeneous pixels.

**Sulla-Menashe, D. et al. (2019)**, MODIS Collection 6 Land Cover, RSE 222:183-194 ([DOI](https://doi.org/10.1016/j.rse.2018.12.013)) and **Friedl, M. et al. (2010)**, RSE 114:168-182 ([DOI](https://doi.org/10.1016/j.rse.2009.08.016)): [METADATA-ONLY, CrossRef-checked]. Annual 500 m global land cover from 2001; includes leaf-type hierarchy. Mention only if a global leaf-type reference is needed; I could not read the abstracts.

**Sousa, D. & Davis, F.W. (2020).** Scalable mapping and monitoring of Mediterranean-climate oak landscapes with temporal mixture models. Remote Sensing of Environment 247:111937. [DOI](https://doi.org/10.1016/j.rse.2020.111937). [ABSTRACT-VIA-SEARCH (AGRIS record via fetch tool); CrossRef-checked]
- Region/data: California Sierra Nevada foothills oak woodland (about 1,200 km2), nearly 40 years of Landsat plus Sentinel-2.
- Method: temporal mixture models with temporal endmembers "annual grasses, evergreen perennials, deciduous perennials plus shadow, and unvegetated"; validation against PhenoCam (correlation 0.8-0.9) and orthophotos: "74-88% accuracy for annual, deciduous, and evergreen cover fractions (n = 102)".
- Limits: California, not Europe; fractions not species; the 74-88 % are from a small sample (n = 102).
- Supports: a continuous evergreen/deciduous cover-fraction model from Landsat in a Mediterranean-climate oak system; the closest analogue to a leaf-type cover (LTC) concept; note a quoted accuracy of the fraction layer is modest.

**Radoux, J. et al. (2014).** Automated training sample extraction for global land cover mapping. Remote Sensing 6(5):3965-3987. [DOI](https://doi.org/10.3390/rs6053965). [ABSTRACT-READ, CrossRef]
- Method: train locally on samples extracted from "existing, but outdated land cover information", cleaned morphologically; "improvement of the overall accuracy compared with the original reference datasets"; aim: maps "both accurate and consistent over time".
- Supports: the label back-casting/propagation strategy (train on a recent map, apply to earlier imagery); reliability of the source map limits the result ("partly controls the reliability of existing land cover maps as sources of training samples").

### Inferences
- LCMAP/GLC_FCS30D numbers imply that if the paper's 1985 maps are built by back-casting, expect OA several points below the recent period and expect exact-year transitions to be mostly noise; report decadal change and area-adjusted estimates.
- A product that gives continuous evergreen vs deciduous broadleaf cover for Europe at 30 m before 2000 was not found.

### Gaps
- GLAD/Potapov global land cover 2000-2020 and Pflugmacher DE (already [W]) not re-searched; Winkler et al. 2021 (HILDA+, [DOI](https://doi.org/10.1038/s41467-021-22702-2), [ABSTRACT-READ]) is 1 km land-use not land-cover and not useful for evergreen questions.
- The class names of GLC_FCS30D forest sub-categories were not read.

---

## 4) HMM, Markov, state-space and trajectory/hotspot methods: confirm or challenge "no precedent found"

### Takeaway
The earlier statement needs refinement. Precedents exist for (a) HMM smoothing of annual maps including species maps (Hermosilla 2024, Bogaert 2022, Abercrombie & Friedl 2016, Gong 2017, Salberg & Trier 2011/2012), (b) HMM correction of misclassified transitions followed by scenario projection (Torchiana 2025, economics), and (c) climate-driven latent-state transition models for ecotypes (Lu et al. 2022, Alaska, preprint). I still found no study that applies an HMM with climate covariates to annual 30 m forest-species maps for forecasting, and none that applies Mann-Kendall/Getis-Ord to categorical species series. Pixel-based Markov forecasting is of dubious skill against persistence (Pontius & Malanson 2005).

### Cited Findings

**Torchiana, A.L., Rosenbaum, T., Scott, P.T., Souza-Rodrigues, E. (2025).** Improving estimates of transitions from satellite data: a hidden Markov model approach. Review of Economics and Statistics 107(2):426-441 (CrossRef: issued March 2025, volume 107, pages 426-441; issue number not given by CrossRef). [DOI](https://doi.org/10.1162/rest_a_01301). [ABSTRACT-READ, CrossRef]
- Method: correction of transition-rate estimates from noisy classifications using measurement-error methods; "No ground-truth data are required in the implementation."
- Finding: "Our proposed correction produces consistent estimates of transition rates, confirmed by longitudinal validation data, while transition rates without correction are severely biased"; application to Brazil's Atlantic forest to 2040.
- Limits: economics journal; forest vs non-forest style classes in Brazil (from abstract: deforestation); identification assumptions (classification errors independent over time) not read; no climate covariates.
- Supports: map-error-vs-real-change at the level of transition matrices, and the use of an HMM to estimate true transition rates for scenarios. Strongest new find for the Methods motivation.

**Pontius, R.G. & Malanson, J. (2005).** Comparison of the structure and accuracy of two land change models. International Journal of Geographical Information Science 19(2):243-265. [DOI](https://doi.org/10.1080/13658810410001713434). [ABSTRACT-READ, OpenAlex] (CrossRef lists the first-author initial as "Pontius, G; Malanson, J"; the first author is R.G. Pontius Jr per the paper — [still unverified in CrossRef].)
- Finding: calibrated on 1971-1985 and predicting 1985-1999 in central Massachusetts, "the predictive models are more accurate than the null model [pure persistence] at resolutions coarser than two kilometres, but not at resolutions finer than one kilometre ... For this particular study area, the added complexity of CA_Markov is of no benefit."
- Limits: one region; land-use classes; but exactly the design question.
- Supports: any pixel-level Markov/HMM forecast must be tested against a persistence null model; skill may exist only at coarse aggregation.

**Salberg, A.-B. & Trier, O.D. (2011).** Temporal analysis of forest cover using hidden Markov models. IGARSS 2011, pp. 2322-2325. [DOI](https://doi.org/10.1109/igarss.2011.6049674). [ABSTRACT-READ, OpenAlex] And **Salberg & Trier (2012)**, IGARSS 2012, pp. 6749-6752 ([DOI](https://doi.org/10.1109/igarss.2012.6352556)) [ABSTRACT-READ, OpenAlex]: "the most likely state sequence method is recommended" for change detection (Brazil, Landsat TM); multi-source Landsat TM and Radarsat-2 (Tanzania); evaluation "by visual inspection". Limits: tropical forest, conference papers, visual evaluation only. Supports: HMM/Viterbi as established for pixel-wise Landsat forest change with "most likely state sequence".

**Lu, X., Hooten, M.B., Raiho, A.M., Swanson, D.K., Roland, C.A., Stehn, S.E. (2022).** Latent trajectory models for spatio-temporal dynamics in Alaskan ecosystems. arXiv:2208.07398. [arXiv](https://arxiv.org/abs/2208.07398). [ABSTRACT-VIA-SEARCH (fetch-tool paraphrase with short quotes)]
- Method: dynamic hierarchical model with latent annual state probabilities, from which transition probabilities between ecotypes are derived; handles irregular survey intervals; "uses climate drivers to infer land cover transition rates"; plots plus remote sensing; claims scenario prediction.
- Limits: preprint (publication status not checked), Alaska, plot-based ecotypes; computational scale at 30 m over Italy unlikely.
- Supports: climate-driven latent transition models for ecosystem states exist; a methodological precedent for "HMM with climate" at ecotype level.

**Bogaert, Abercrombie & Friedl, Gong 2017** are already in v2 (not repeated). Added observation: the three IEEE HMM papers all smooth/filter; none forecasts.

**Mertens & Lambin 2000; Mena 2008 (trajectory modelling).** [ABSTRACT-READ, OpenAlex]. Mertens & Lambin: spatial multivariate model of deforestation trajectories from Landsat MSS and SPOT XS, spanning two decades; Mena 2008: Landsat classification 1974-2002, trajectories clustered, spatial logistic regression with socio-economic data. Limits: tropical deforestation, 1990s-2000s methods, few time points. Supports: definition of class trajectory and trajectory clustering with drivers.

**Maus, V., Camara, G., Appel, M., Pebesma, E. (2019).** dtwSat: time-weighted dynamic time warping for satellite image time series analysis in R. Journal of Statistical Software 88(5). [DOI](https://doi.org/10.18637/jss.v088.i05). [ABSTRACT-READ, OpenAlex] (CrossRef gives no page/article number.) Dynamic time warping is "flexible to handle irregular sampling and out-of-phase time series" for land cover classification with sequences of satellite images. Limits: DTW targets spectral/phenological series, not label sequences; no species example. Supports: DTW as an option for NDVI-type temporal patterns only.

**Markov-forecasting leads found only as search-tool snippets (not citable):** a Pastor-era LCLUC project report that built Markov transition matrices from "near species level" Landsat classes in the Upper Midwest and warned that error-matrix adjustments only hold if ground survey and imagery share the same period; a Logofet abstract on inhomogeneous Markov chains whose transition probabilities depend on environmental factors. Both [SNIPPET/TLDR-ONLY], grey; use only as pointers to the homogeneity problem of Markov chains.

**Classic Markov forest references.** Waggoner & Stephens 1970, Nature 225:1160-1161 ([DOI](https://doi.org/10.1038/2251160a0)) [METADATA-ONLY, CrossRef-checked]; Rabiner 1989, Proc IEEE 77(2) ([DOI](https://doi.org/10.1109/5.18626)) [METADATA-ONLY, CrossRef-checked; the issue/page numbers were not read]. I did not verify a Horn (1975) "Markovian properties of forest succession" entry (CrossRef returned a different Horn 1975 item).

**Intensity analysis (upgrade of Aldwaik & Pontius 2012).** Landscape and Urban Planning 106(1):103-114, [DOI](https://doi.org/10.1016/j.landurbplan.2012.02.010) (CrossRef-checked). [ABSTRACT-VIA-SEARCH] Tool summary: cross-tabulation matrices per time interval, three levels (interval, category, transition), tests of stationarity; seven land categories at Plum Island (Massachusetts); compares with Markov-based approaches arguing intensity analysis "explains more about why transitions vary across time and space". Short quote: "The unique contribution of this article is that it combines all three levels of analysis into one unified framework". Verbatim abstract not obtained.

**LandTrendr (Kennedy 2010) and BFAST (Verbesselt 2010).** Both [ABSTRACT-VIA-SEARCH] (fetch-tool paraphrase plus short quote); CrossRef-checked metadata.
- [Kennedy, Yang & Cohen 2010](https://doi.org/10.1016/j.rse.2010.07.008), RSE 114(12):2897-2910: quote "change is not simply a contrast between conditions at two points in time, but rather a continual process" (Treesearch record); tested "on several hundred points in western Oregon and Washington" and performs "well, even against subtle recovery and stability targets" (tool paraphrase).
- [Verbesselt et al. 2010](https://doi.org/10.1016/j.rse.2009.08.014), RSE 114(1):106-115: "BFAST iteratively estimates the time and number of changes, and characterizes change by its magnitude and direction"; tested on simulated 16-day NDVI series (detects changes larger than 0.1 NDVI at noise levels sigma 0.01-0.07) and MODIS NDVI in south-eastern Australia. Note: the v2 reference list gave the right paper; the DOI above is the CrossRef value.
- Both are spectral-series methods, not designed for categorical annual maps (as v2 says).

**Olofsson et al. 2014** ([DOI](https://doi.org/10.1016/j.rse.2014.02.015)). [ABSTRACT-VIA-SEARCH, paraphrase only, no verbatim quote]. The repository record (Nottingham) summarised by the search tool: recommendations on sampling design, response design and analysis, probability sampling, error matrix with overall/user's/producer's accuracy, area estimates from reference samples. The abstract could not be read verbatim. Stays a short read.

**Hamed & Rao 1998**: CrossRef confirms the reference ([DOI](https://doi.org/10.1016/S0022-1694(97)00125-X), J Hydrol 204:182-196) but no abstract was obtained. [METADATA-ONLY]. Keep the v2 tag [SNIPPET/TLDR-ONLY] at best.

**Hotspot / Mann-Kendall.** Baglioni 2025/2026 (section 2) is the only Italian Landsat design with significant-trend "hotspots". No Getis-Ord Gi* use on forest change was found with quality (CrossRef search returned an Australian Forestry management-unit paper, [Rossi et al. 2019](https://doi.org/10.1080/00049158.2019.1678714), [METADATA-ONLY, not read] and irrelevant social-science hits). No Mann-Kendall on categorical class fractions was found.

### Inferences
- "No precedent" should be restated as: no precedent for the specific combination (annual species maps + HMM + climate covariates + forecasting + hotspot statistics in a Mediterranean country). Partial precedents: Hermosilla 2024 (HMM smoothing, species maps), Torchiana 2025 (HMM-corrected transitions to scenario projection), Lu 2022 (climate-driven latent transitions), Baglioni (hotspots, Italy).
- Treat the HMM in two roles in Methods: (1) emission-corrected smoothing of annual labels, (2) transition-matrix forecasting. Validate role 2 against persistence (Pontius & Malanson).
- A homogeneous first-order Markov chain assumes constant transition probabilities; the climate/drought forcing violates that (Logofet pointer, Lu 2022).

### Gaps
- No quantitative comparison of HMM-smoothed vs raw annual species maps in an independent validation across years was found (Hermosilla 2024's paper text not read).
- No sequence-analysis (optimal matching) paper on remote-sensing class trajectories surfaced in CrossRef; may exist in geography journals.

---

## 5) Phenology/winter signal for evergreen broadleaves under deciduous canopies

### Takeaway
Little new European evidence. The transferable method is the spring pre-leaf-out Sentinel-2 time series of Yang 2023 (understory communities), and the continuous temporal-endmember approach of Sousa & Davis 2020. No Landsat/Sentinel study mapping Hedera, Ilex, Buxus, Ruscus or Prunus laurocerasus was found. Invasive evergreen detection in Europe remains unsupported.

### Cited Findings
- **Yang, X., Qiu, S., Zhu, Z., Rittenhouse, C., Riordan, D., Cullerton, M. (2023).** Mapping understory plant communities in deciduous forests from Sentinel-2 time series. Remote Sensing of Environment 293:113601. [DOI](https://doi.org/10.1016/j.rse.2023.113601). [SNIPPET/TLDR-ONLY; CrossRef-checked metadata, abstract elided] Search-tool summary: Connecticut, 10 m, dense time series, imagery before canopy leaf-out; invasive shrub cover about 649 km2, roughly 53 % of the shrub understory. These numbers come from a tool summary and need checking. Supports: the principle that leaf-off/pre-leaf-out dates carry understory signal, and that dense time series are needed.
- Oreti 2020 (v2, very high resolution) remains the only Italian understory-evergreen mapping paper; a Sentinel-2/Landsat counterpart was not found.
- A phenology-index evergreen-forest map (annual, 10 m, China, Ecological Indicators 2023) was reported by the search tool with overall accuracy 99.73 % and kappa 0.98 [SNIPPET/TLDR-ONLY; authors and DOI not identified; accuracy is implausibly high for mixed forest and probably reflects an easy sampling design — do not cite].
- Reported by the search tool without identification: a NASA abstract stating that spectrally deciduous forests are hard to distinguish from non-forest "when leaves are absent", so leaf-off dates can produce errors in forest change products [SNIPPET/TLDR-ONLY; source not identified]. This is the logical reverse risk for a winter-based evergreen signal; check against Chastain 2007 and Wang 2009 in v2.
- For the Landsat 8 NDVI separation of holm-oak communities Pesaresi 2020 (v2) stays the Italian anchor.

### Inferences
- With a 30 m pixel, evergreen understory under deciduous canopy is detectable only as an increased winter greenness; this is the same sensitivity as Atkins 2018 and Chastain 2007 (v2); the new sources do not change that.

### Gaps
- No European study with Landsat/Sentinel winter composites for invasive evergreen shrubs (Prunus laurocerasus, Hedera helix) was found.

---

## 6) Greening/browning studies including Mediterranean evergreen vs deciduous forests

### Takeaway
New conceptual anchor: Pausas & Millán 2019. Italian Landsat greening studies concentrate on forestline ecotones (Baglioni). No Italian study splits greening by evergreen vs deciduous forest type was found.

### Cited Findings
- **Pausas, J.G. & Millán, M.M. (2019).** Greening and browning in a climate change hotspot: the Mediterranean Basin. BioScience 69(2):143-151. [DOI](https://doi.org/10.1093/biosci/biy157). [ABSTRACT-READ, OpenAlex] — three local processes: "rural abandonment that increases wildlands, population changes that boost fire ignitions, and coastal degradation that enhances drought"; "The current balance is still toward greening, because land abandonment is buffering the browning drivers; however, it is likely to switch with increasing warming." Limits: a perspective, no data analysis in the abstract. Supports: that land-abandonment-driven greening is the expected baseline against which dieback/browning signals should be read.
- Baglioni 2025/2026 (section 2): greening along Italian forestlines, 1984-2023.
- Laidi 2026 (section 2): Morocco species-differentiated NDVI decline.
- [[bayle_2024_landsat_greening_inflated]], [[herraiz_2025_phen_shifts_mediterranean]], [[kempf_2023_greening]] and Aubard 2019 are already in the wiki/v2.

### Inferences
- Greening of "forest" NDVI cannot be attributed to evergreen oak gain without a class map; the maps in the paper would be the first such split for Italy (as far as found).

### Gaps
- A Gran Paradiso Landsat NDVI paper (Di Gennaro et al. 2023, [DOI](https://doi.org/10.3390/rs15153847)) shows up as deglaciated terrain, not forest: dropped.

---

## 7) Drivers analysis in RS change studies: climate, land use, terrain; spatial CV and autocorrelation

### Takeaway
Four standard references for spatial-autocorrelation handling and spatial validation, all [ABSTRACT-READ]. They matter because trajectory/driver models fit on neighbouring 30 m pixels give inflated skill.

### Cited Findings
- **Roberts, D.R. et al. (2017).** Cross-validation strategies for data with temporal, spatial, hierarchical, or phylogenetic structure. Ecography 40(8):913-929. [DOI](https://doi.org/10.1111/ecog.02881) [ABSTRACT-READ, CrossRef]: "when performing cross-validation, these structures are regularly ignored, resulting in serious underestimation of predictive error"; block cross-validation recommended, but blocking "may also unwittingly induce extrapolations". (CrossRef gives volume 40, pages 913-929; issue 8 is from my memory [still unverified].)
- **Dormann, C.F. et al. (2007).** Methods to account for spatial autocorrelation in the analysis of species distributional data: a review. Ecography 30:609-628. [DOI](https://doi.org/10.1111/j.2007.0906-7590.05171.x) [ABSTRACT-READ, CrossRef]: autocorrelated residuals "may bias parameter estimates and can increase type I error rates"; six methods (autocovariate regression, spatial eigenvector mapping, GLS, CAR/SAR, GEE).
- **Ploton, P. et al. (2020).** Spatial validation reveals poor predictive performance of large-scale ecological mapping models. Nature Communications 11:4540. [DOI](https://doi.org/10.1038/s41467-020-18321-y) [ABSTRACT-READ, CrossRef]: nonspatial validation suggests a model "predicts more than half of the forest biomass variation, while spatial validation methods ... reveal quasi-null predictive power". Limits: forest biomass in Central Africa.
- **Meyer, H. & Pebesma, E. (2021).** Predicting into unknown space? Estimating the area of applicability of spatial prediction models. Methods in Ecology and Evolution 12(9):1620-1633 (CrossRef: vol. 12, pp. 1620-1633; issue number from memory). [DOI](https://doi.org/10.1111/2041-210x.13650) [ABSTRACT-READ, CrossRef]: dissimilarity index to delimit where a model can be applied; relevant to hindcasting (early years out of the training domain). Meyer et al. 2018 (Environ Model Softw 101:1-9, [DOI](https://doi.org/10.1016/j.envsoft.2017.12.001)) [METADATA-ONLY].
- Witjes 2022 (section 2) uses spatial k-fold CV in a Landsat LULC time series; Padial-Iglesias 2022 (v2) did not state spatial CV.

### Inferences
- Spatial block CV plus a persistence null model is the defensible validation for both the driver model and the HMM forecast.

### Gaps
- No remote-sensing evergreen-expansion study with explicit spatial CV was found.

---

## 8) Italian-language items

### Takeaway
Only snippet-level leads; nothing citable beyond what v2 holds. Regional Landsat or aerial-photo studies report forest expansion on abandoned land; none separates holm oak.

### Cited Findings (all [SNIPPET/TLDR-ONLY], from one web-search answer; none opened)
- Basilicata (Alta Val d'Agri), Landsat 1985 vs 2009: net forest increase of 11 % at the expense of pasture and grassland (probably a different study from Mancino 2014 in v2; not identified).
- Latina and Circeo (Lazio), Landsat 1987-2017 at ten-year intervals: change detection of land-use transitions (not identified).
- Casentino (Tuscany), aerial-photo interpretation 1954 vs 2010: forest +about 2,800 ha, mostly from former pasture/cultivation (not identified).
- Tuscany agrarian landscapes 1933-2016 (Rivista di Agraria, 2017): forest minimum about 1954 then increase, "naturalness" not equivalently recovered ([source page](https://rivistadiagraria.org/articoli/anno-2017/cambiamenti-nella-naturalita-dei-paesaggi-agrari-toscani-dal-1933-al-2016/)).
- ISPRA presentation (Marchetti): differences up to about +/-30 % in national forest area between IUTI, CLC and other sources ([ISPRA PDF](https://www.isprambiente.gov.it/files/copernicus/UFNCopernicusWSAgricolturaMarcoMarchettiAISSA.pdf)) — this is the search tool's reading, not verified on the document.
- Di Gennaro et al. 2019 (section 2).

### Inferences
- The ISPRA between-source spread, if verified, is a useful number for the map-vs-map disagreement argument.

### Gaps
- No Italian-language paper on "serie storica Landsat leccio" or "carta forestale storica" was found.

---

## 9) Concepts and their best definitional source

Tags: A = [ABSTRACT-READ], S = [ABSTRACT-VIA-SEARCH], M = [METADATA-ONLY]. "v2" = already in the v2 review.

| Concept | Best definitional/review source | Tag | Notes |
|---|---|---|---|
| Land-change trajectory (class sequence) | Mertens & Lambin 2000, Ann Assoc Am Geogr 90:467-494 ([DOI](https://doi.org/10.1111/0004-5608.00205)) | A | Also Mena 2008 (clustering of trajectories) |
| Trajectory typology / clustering | Mena 2008, PE&RS 74:737-751 ([DOI](https://doi.org/10.14358/pers.74.6.737)); Viana-Soto 2020 (v2, K-means on LandTrendr trajectories) | A | Spectral-trajectory typology: Viana-Soto |
| Spectral/index trajectory | Kennedy, Yang & Cohen 2010 ([DOI](https://doi.org/10.1016/j.rse.2010.07.008)); Pasquarella 2022 (v2) | S | Verbatim abstract not read |
| Break detection in series | Verbesselt et al. 2010 ([DOI](https://doi.org/10.1016/j.rse.2009.08.014)); Zhu & Woodcock 2014 (v2) | S | |
| Temporal consistency of annual maps | Hermosilla 2018/2024 (v2; HMM per GEE catalogue); Bogaert 2022 (v2); Abercrombie & Friedl 2016 (v2); GLC_FCS30D "temporal-consistency optimization" ([DOI](https://doi.org/10.5194/essd-16-1353-2024)) | A | No single definitional review found |
| Map error vs real change | Pontius & Lippitt 2006 (v2); Torchiana et al. 2025 ([DOI](https://doi.org/10.1162/rest_a_01301)); Olofsson et al. 2014 | A / A / S | Olofsson only paraphrase |
| Exact-year change accuracy | Stehman et al. 2021 ([DOI](https://doi.org/10.1016/j.rse.2021.112646)) | S | Snippet-level numbers |
| Landsat time series (concept) | Kennedy et al. 2014 Frontiers Ecol Environ (v2); Wulder 2022 (v2) | A (v2) | |
| Post-classification comparison | Pontius & Lippitt 2006 (v2); Mancino 2013 (v2, two-date example) | A | No dedicated definitional abstract read in this round |
| Intensity analysis | Aldwaik & Pontius 2012 ([DOI](https://doi.org/10.1016/j.landurbplan.2012.02.010)) | S | |
| Hotspot analysis | Getis & Ord 1992 (v2); Baglioni et al. 2026 EGU abstract (significant-trend hotspots) | A | Trend hotspots on NDVI, not categorical |
| Trend test with autocorrelation | Yue et al. 2002, Neeti & Eastman 2011 (v2); Hamed & Rao 1998 ([DOI](https://doi.org/10.1016/S0022-1694(97)00125-X)) | A / M | Hamed & Rao abstract not obtained |
| Markov chain for forest | Waggoner & Stephens 1970 ([DOI](https://doi.org/10.1038/2251160a0)) | M | Classic; also McClintock 2020 (v2) |
| HMM (method definition) | Rabiner 1989 ([DOI](https://doi.org/10.1109/5.18626)) | M | |
| HMM for remote sensing | Salberg & Trier 2011/2012; Bogaert 2022 (v2) | A | |
| Pixel- vs map-based forecasting | Pontius & Malanson 2005 ([DOI](https://doi.org/10.1080/13658810410001713434)) (persistence null model) | A | Also Mirici 2018 as a typical weak-validation example |
| Hindcasting / label back-casting | Radoux et al. 2014 ([DOI](https://doi.org/10.3390/rs6053965)); Thapa 2020, Verhulst 2024, Zhou 2020 (v2) | A | |
| Spatial CV / autocorrelation | Roberts et al. 2017; Dormann et al. 2007; Ploton et al. 2020; Meyer & Pebesma 2021 | A | |
| Land abandonment greening vs browning | Pausas & Millán 2019 ([DOI](https://doi.org/10.1093/biosci/biy157)) | A | |
| Continuous cover fractions | Buchhorn et al. 2020 ([DOI](https://doi.org/10.3390/rs12061044)); Sousa & Davis 2020 | A / S | |
| CLC reliability for change | Garcia-Alvarez & Camacho Olmedo 2022 ([DOI](https://doi.org/10.31223/x5qd1f)) | A | Preprint, Asturias |

### Items dropped from this round (not worth citing)
- Gargano NDVI master's thesis (student thesis), Gran Paradiso deglaciated NDVI (not forest), Egyptian/Turkish Markov-CA generic LULC case studies other than Mirici 2018 as one example, the unidentified Ecological Indicators evergreen map (implausible accuracy).

### Still to verify manually (priority)
1. Hermosilla 2024 full text: HMM design and early-year accuracy.
2. Verbatim abstracts of Kennedy 2010, Verbesselt 2010, Olofsson 2014, Aldwaik & Pontius 2012, Hamed & Rao 1998, Stehman 2021, Garbarino 2020, Falcucci 2007 via uibk access (all blocked here).
3. Di Gennaro et al. 2019 (CLC Italy 1990-2018), the Zenodo Mediterranean forest-type map record 7054338 (authors, accuracy), Yang 2023 abstract.
4. Witjes 2022: whether evergreen and deciduous broadleaves are separate classes at level 3.
