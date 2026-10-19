# Remote sensing literature for mapping evergreen broad-leaved species (EVEs), leaf type and tree species from Landsat / Sentinel-2

Method note: Every reference below was matched against the CrossRef API (authors, year, title, journal, volume, pages, DOI as returned by CrossRef on 2026-10-16). The "key finding" text is written from my background knowledge of each paper; I did NOT re-read the full texts in this session (only abstracts/search snippets for Resasco 2007 and the Appalachian/bamboo papers). Treat the findings as [abstract-level, to be confirmed on reading]. Numbers (accuracies etc.) are deliberately omitted because I could not verify them. Papers I could not find are listed as such, not invented.

## 1. Which papers are most important and citable? (ranked)

Rank logic: relevance to the planned paper (40-yr Landsat LTC/DTS maps, EVE change in Italy) x citability x what is missing from the wiki.

### Takeaway
The wiki is strong on tree-species mapping from Sentinel-2 (Hemmerling, Blickensdorfer, Grabska, Kollert, Bolyn) but has almost nothing on (a) multi-decadal Landsat classification consistency / back-casting, (b) area-adjusted change estimation, (c) Landsat Collection 2 / sensor continuity, and (d) the leaf-off/winter-imagery evergreen understory literature beyond Chastain & Townsend. Those four are the main gaps; the items ranked 1-12 below fill them. There is no Landsat/Sentinel-2 paper I could find that maps Prunus laurocerasus, Hedera or Chinese privet specifically (see Gaps).

### Cited Findings

**Tier A - must cite / deep read (missing from wiki)**

1. Olofsson, P., Foody, G.M., Herold, M., Stehman, S.V., Woodcock, C.E., Wulder, M.A. (2014). Good practices for estimating area and assessing accuracy of land change. Remote Sensing of Environment 148, 42-57. DOI 10.1016/j.rse.2014.02.015 — [CrossRef](https://doi.org/10.1016/j.rse.2014.02.015)
   - Finding: Pixel counting from a classified/change map is biased; unbiased change area and its confidence interval must be estimated from a probability sample of reference data with a confusion matrix expressed in area proportions. Gives the sampling design, response design and estimators.
   - Critical: Method paper, not Italy-specific. Weakness for this project: needs independent reference samples for EVE gain/loss in a 40-yr series (time-consuming; NFI plots (INFC) could only partly serve). Without it, a reviewer can attack any "EVE expanded by X ha" statement. Deep read: yes (sections on stratified estimation + response design for change). Cite in: Methods (accuracy/area estimation), Discussion (uncertainty of change areas). Note: classification error in annual maps produces spurious "change" - a point to make explicitly.

2. Hermosilla, T., Wulder, M.A., White, J.C., Coops, N.C., Bater, C.W., Hobart, G.W. (2024). Characterizing long-term tree species dynamics in Canada's forested ecosystems using annual time series remote sensing data. Forest Ecology and Management 572, 122313. DOI 10.1016/j.foreco.2024.122313 — [CrossRef](https://doi.org/10.1016/j.foreco.2024.122313) [author list per CrossRef: Hermosilla T; Wulder M; White J; Coops N; Bater C; Hobart G]
   - Finding [title-level + background]: Annual Landsat-based time series are used to characterise multi-decadal tree species dynamics nationally, i.e. the closest published analogue to a long annual Landsat species-map series analysed for trajectories.
   - Critical: Boreal/temperate Canada, not Mediterranean; species-level dynamics partly driven by disturbance/succession, not by climate-driven invasion of understory evergreens. Must read to see how they handle temporal consistency, label propagation across years and change uncertainty. Cite in: Introduction (annual Landsat species dynamics are feasible), Methods, Discussion. Closest analogue to the user's design.

3. Hermosilla, T., Wulder, M.A., White, J.C., Coops, N.C., Hobart, G.W. (2018). Disturbance-informed annual land cover classification maps of Canada's forested ecosystems for a 29-year Landsat time series. Canadian Journal of Remote Sensing 44(1), 67-87. DOI 10.1080/07038992.2018.1437719 — [CrossRef](https://doi.org/10.1080/07038992.2018.1437719)
   - Finding [background]: Annual land-cover maps are produced from Landsat composites with change detection used to inform/stabilise labels over time, reducing implausible class flipping (e.g. "illogical" transitions) in annual products.
   - Critical: Rules-based post-processing against disturbance may suppress genuine slow compositional change (e.g. gradual EVE spread without a disturbance event) - exactly the signal of interest. Cite in: Methods (temporal consistency, post-classification logic), Discussion (limits of annual maps for gradual change). Worth reading selectively.

4. Thapa, B., Wolter, P.T., Sturtevant, B.R., Townsend, P.A. (2020). Reconstructing past forest composition and abundance by using archived Landsat and national forest inventory data. International Journal of Remote Sensing 41(10), 4022-4056. DOI 10.1080/01431161.2019.1711245 — [CrossRef](https://doi.org/10.1080/01431161.2019.1711245) [CrossRef author list: Thapa B; Wolter P; Sturtevant B; Townsend P]
   - Finding [title-level]: Uses archived Landsat and national forest inventory data to reconstruct past species composition/abundance (back-casting); same group as Chastain-type multi-temporal classification (Townsend).
   - Critical: US Lake States; I have not verified details of training-data transfer or accuracy decay for older years. Directly relevant to the "temporal transfer / training reuse" question. Deep read: yes, check how accuracy degrades backwards in time. Cite in: Methods (back-casting rationale), Discussion (limitations of early-Landsat years).

5. Pasquarella, V.J., Holden, C.E., Woodcock, C.E. (2018). Improved mapping of forest type using spectral-temporal Landsat features. Remote Sensing of Environment 210, 193-207. DOI 10.1016/j.rse.2018.02.064 — [CrossRef](https://doi.org/10.1016/j.rse.2018.02.064)
   - Finding [background]: Harmonic/spectral-temporal (phenology-based) features from dense Landsat time series improve forest-type (incl. deciduous/evergreen, species groups) classification over single-date or seasonal composites in New England.
   - Critical: Temperate mixed forest, not Mediterranean; relies on dense clear observations (a problem for 1980s-1990s Landsat 5 archive in Italy). Cite in: Methods (justification of time-series features for leaf-type separation), Introduction. Worth deep reading.

6. Senf, C., Leitao, P.J., Pflugmacher, D., van der Linden, S., Hostert, P. (2015). Mapping land cover in complex Mediterranean landscapes using Landsat: Improved classification accuracies from integrating multi-seasonal and synthetic imagery. Remote Sensing of Environment 156, 527-536. DOI 10.1016/j.rse.2014.10.018 — [CrossRef](https://doi.org/10.1016/j.rse.2014.10.018)
   - Finding [background]: In a Mediterranean landscape (Portugal), multi-seasonal Landsat plus synthetic/phenology-derived imagery separated Mediterranean cover classes (incl. evergreen vs deciduous woody classes) better than single-date data.
   - Critical: Regional (Portugal), land cover not species; but one of few Landsat Mediterranean evidence points that seasonality is essential. Cite in: Methods/Introduction (Mediterranean spectral confusion, need for multi-seasonal data). Read: yes, moderately.

7. Gomez, C., White, J.C., Wulder, M.A. (2016). Optical remotely sensed time series data for land cover classification: A review. ISPRS Journal of Photogrammetry and Remote Sensing 116, 55-72. DOI 10.1016/j.isprsjprs.2016.03.008 — [CrossRef](https://doi.org/10.1016/j.isprsjprs.2016.03.008)
   - Finding [background]: Reviews how time series (phenology metrics, composites, change-based methods, training-sample reuse) are used for land-cover classification and discusses temporal consistency problems.
   - Critical: Review, predates Sentinel-2 deep-learning era and HLS; use as a citable overview, not for methods detail. Cite in: Introduction/Methods (general justification). Skim.

8. Zhu, Z., Woodcock, C.E. (2014). Continuous change detection and classification of land cover using all available Landsat data. Remote Sensing of Environment 144, 152-171. DOI 10.1016/j.rse.2014.01.011 — [CrossRef](https://doi.org/10.1016/j.rse.2014.01.011)
   - Finding [background]: CCDC fits harmonic models to all clear Landsat observations per pixel, detects breaks and classifies segments; coefficients carry seasonal (phenology) information.
   - Critical: Relevant as methodological alternative to annual independent classifications (consistency by construction). Gradual change (EVE encroachment) is weakly detected as discrete breaks. Cite in: Methods/Discussion as alternative approach. Skim.

9. Roy, D.P., Kovalskyy, V., Zhang, H.K., Vermote, E.F., Yan, L., Kumar, S.S., Egorov, A. (2016). Characterization of Landsat-7 to Landsat-8 reflective wavelength and normalized difference vegetation index continuity. Remote Sensing of Environment 185, 57-70. DOI 10.1016/j.rse.2015.12.024 — [CrossRef](https://doi.org/10.1016/j.rse.2015.12.024)
   - Finding [background]: Quantifies band/NDVI differences between ETM+ and OLI and provides transformation coefficients; shows sensor differences are small but systematic.
   - Critical: Does not cover TM(L5)-to-ETM+ in detail and not Collection 2 specifically. Cite in: Methods (sensor harmonisation), Limitations. Read the relevant tables only.

10. Crawford, C.J., Roy, D.P., Arab, S., Barnes, C., Vermote, E., Hulley, G., et al. (2023). The 50-year Landsat collection 2 archive. Science of Remote Sensing 8, 100103. DOI 10.1016/j.srs.2023.100103 — [CrossRef](https://doi.org/10.1016/j.srs.2023.100103)
    - Finding [background]: Describes Collection 2 reprocessing (improved geometry, calibration, surface reflectance/temperature across Landsat 1-9).
    - Critical: Descriptive; does not itself quantify residual inter-sensor trends in vegetation indices - pair with Roy 2016 and Bayle 2024 (already in wiki, bayle_2024_landsat_greening_inflated) for the trend-artefact argument. Cite in: Methods (data), Limitations.

11. Francini, S., Schelhaas, M.-J., Vangi, E., Lerink, B.J.W., Nabuurs, G.-J., McRoberts, R.E., et al. (2024). Forest species mapping and area proportion estimation combining Sentinel-2 harmonic predictors and national forest inventory data. International Journal of Applied Earth Observation and Geoinformation 131, 103935. DOI 10.1016/j.jag.2024.103935 — [CrossRef](https://doi.org/10.1016/j.jag.2024.103935) [CrossRef author list truncated; Francini, Schelhaas, Vangi, Lerink, Nabuurs, McRoberts + others - check full list on publisher page]
    - Finding [title-level]: Sentinel-2 harmonic (phenology) predictors and NFI plots are combined for species mapping and for estimating species area proportions (model-assisted inference), with Italian-author involvement.
    - Critical: I have not verified study area (probably Netherlands - unverified) or accuracy. Valuable because it links species maps to NFI-based area estimation, which addresses the Olofsson-type question for species. Read: yes. Cite in: Methods (NFI-calibrated area estimation), Discussion.

12. Wulder, M.A., Roy, D.P., Radeloff, V.C., Loveland, T.R., Anderson, M.C., Johnson, D.M., et al. (2022). Fifty years of Landsat science and impacts. Remote Sensing of Environment 280, 113195. DOI 10.1016/j.rse.2022.113195 — [CrossRef](https://doi.org/10.1016/j.rse.2022.113195)
    - Finding: Review of Landsat's 50-year record and science uses. Critical: general citation only. Cite in: Introduction (value of the 40+ yr archive).

**Tier B - evergreen / leaf-off understory (the specific niche)**

13. Chastain, R.A. Jr., Townsend, P.A. (2007). Use of Landsat ETM+ and topographic data to characterize evergreen understory communities in Appalachian deciduous forests. Photogrammetric Engineering & Remote Sensing 73(5), 563-575. DOI 10.14358/pers.73.5.563 — [CrossRef](https://doi.org/10.14358/pers.73.5.563) — ALREADY IN WIKI (chastain_2007_eve_landsat_understory). Note: CrossRef title reads "Landsat ETM" (without "+") and "Chastain, Jr. R" - verify title wording in your note.
    - Critical: The anchor citation for winter imagery + topography; Appalachian Rhododendron/Kalmia, native evergreen understory, not Mediterranean/invasive. Cite: Introduction, Methods (leaf-off logic).

14. Resasco, J., Hale, A.N., Henry, M.C., Gorchov, D.L. (2007). Detecting an invasive shrub in a deciduous forest understory using late-fall Landsat sensor imagery. International Journal of Remote Sensing 28(16), 3739-3745. DOI 10.1080/01431160701373721 — [CrossRef](https://doi.org/10.1080/01431160701373721)
    - Finding (from search snippet of the paper page): Amur honeysuckle (Lonicera maackii), which holds its leaves after canopy trees drop theirs, can be separated at high vs low cover on late-fall Landsat TM/ETM+ imagery, based on Jeffries-Matusita separability. — [Resasco et al. PDF](https://www.colorado.edu/lab/resasco/sites/default/files/attached-files/resasco_et_al_2007_ijrs.pdf)
    - Critical: Phenological-offset (late leaf retention), not truly evergreen; small study; separability, not wall-to-wall map accuracy. Short paper; read fully (it is 7 pages). Cite: Introduction/Methods (phenological offset principle).

15. Wilfong, B.N., Gorchov, D.L., Henry, M.C. (2009). Detecting an invasive shrub in deciduous forest understories using remote sensing. Weed Science 57(5), 512-520. DOI 10.1614/ws-09-012.1 — [CrossRef](https://doi.org/10.1614/ws-09-012.1) [Note: this is the Wilfong paper the user referred to; it is in Weed Science, not Int. J. Remote Sens.]
    - Finding [title-level/background]: Follow-up of Resasco 2007: remote sensing (Landsat imagery of different dates and further data) to detect Amur honeysuckle under deciduous canopies.
    - Critical: Not read; same limitations as Resasco. Cite alongside Resasco only.

16. Atkins, J.W., Epstein, H.E., Welsch, D.L. (2018). Using Landsat imagery to map understory shrub expansion relative to landscape position in a mid-Appalachian watershed. Ecosphere 9(10), e02404. DOI 10.1002/ecs2.2404 — [CrossRef](https://doi.org/10.1002/ecs2.2404)
    - Finding (from search summary): Snow-free, leaf-off Landsat 5 surface reflectance 1986-2011 plus Random Forest used to map evergreen understory shrub (rhododendron/mountain laurel) expansion and relate it to landscape position. — [search result](https://openpolar.no/Record/crwiley:10.1002%2Fecs2.2404)
    - Critical: This is probably the single closest published analogue of "multi-decadal leaf-off Landsat for evergreen expansion" and is MISSING from the wiki. Weaknesses to check: small watershed, training data across years, accuracy over time. Deep read: yes. Cite: Introduction (evergreen understory expansion detected with Landsat time series), Methods, Discussion.

17. Wang, T., Skidmore, A.K., Toxopeus, A.G., Liu, X. (2009). Understory bamboo discrimination using a winter image. Photogrammetric Engineering & Remote Sensing 75(1), 37-47. DOI 10.14358/pers.75.1.37 — [CrossRef](https://doi.org/10.14358/pers.75.1.37) [CrossRef author list: Wang T; Skidmore A; Toxopeus A; Liu X]
    - Finding (search summary): Winter (leaf-off) imagery gave the best discrimination of evergreen understory bamboo; NDVI from the winter image correlated with percent understory bamboo cover in deciduous and mixed forest.
    - Critical: Giant panda habitat (China), Landsat-type data not verified; supports the principle on a second continent. Cite: Methods. Skim.

**Tier C - tree species / forest type products and spectral-temporal methods**

18. Hemmerling et al. 2021 (RSE 267, 112743, DOI 10.1016/j.rse.2021.112743), Blickensdorfer et al. 2024 (RSE 304, 114069, DOI 10.1016/j.rse.2024.114069), Kollert et al. 2021 (IJAEOG 94, 102208, DOI 10.1016/j.jag.2020.102208) — ALREADY IN WIKI. DOIs confirmed with CrossRef. Critical: all are temperate/central Europe, deciduous vs coniferous dominated; none contains Mediterranean EVE classes or multi-decadal change - state this as a gap in the Introduction.

19. Grabska, E., Hostert, P., Pflugmacher, D., Ostapowicz, K. (2019). Forest stand species mapping using the Sentinel-2 time series. Remote Sensing 11(10), 1197. DOI 10.3390/rs11101197 — [CrossRef](https://doi.org/10.3390/rs11101197). Also Grabska, E., Frantz, D., Ostapowicz, K. (2020). Evaluation of machine learning algorithms for forest stand species mapping using Sentinel-2 imagery and environmental data in the Polish Carpathians. Remote Sensing of Environment 251, 112103. DOI 10.1016/j.rse.2020.112103 — [CrossRef](https://doi.org/10.1016/j.rse.2020.112103). (Wiki has grabska_2024_tree_species_map only.)
    - Critical: Carpathian mountain forests, deciduous/conifer; shows value of multi-season S2 + topography. Second is more useful for ML comparison. Skim; cite in Methods only if needed.

20. Bonannella, C., Hengl, T., Heisig, J., Parente, L., Wright, M.N., Herold, M., de Bruin, S. (2022). Forest tree species distribution for Europe 2000-2020: mapping potential and realized distributions using spatiotemporal machine learning. PeerJ 10, e13728. DOI 10.7717/peerj.13728 — [CrossRef](https://doi.org/10.7717/peerj.13728) [CrossRef lists authors incl. "et al."; full author list unverified beyond first six]
    - Finding [background]: 30 m (Landsat-based) probability/distribution maps for many European tree species (incl. Mediterranean species such as Quercus ilex) for 2000-2020, from spatiotemporal ML on harmonised point data.
    - Critical: The only Europe-wide multi-year species map covering Italian EVEs that I know of - a necessary comparison/benchmark for the user's DTS maps. Weakness: modelled potential/realized distributions rather than direct classification, plausible spatial smoothing, uncertain accuracy for rare species; many authors' uncertainty statements should be checked. Deep read: yes. Cite: Introduction (existing products), Discussion (comparison).

21. Immitzer, M., Neuwirth, M., Bock, S., Brenner, H., Vuolo, F., Atzberger, C. (2019). Optimal input features for tree species classification in Central Europe based on multi-temporal Sentinel-2 data. Remote Sensing 11(22), 2599. DOI 10.3390/rs11222599 — [CrossRef](https://doi.org/10.3390/rs11222599)
    - Critical: Austria, finds multi-temporal and red-edge/SWIR features beneficial; moderate importance. Cite for feature design only; skim.

22. Welle, T., Aschenbrenner, L., Kuonath, K., Kirmaier, S., Franke, J. (2022). Mapping dominant tree species of German forests. Remote Sensing 14(14), 3330. DOI 10.3390/rs14143330 — [CrossRef](https://doi.org/10.3390/rs14143330). Critical: similar scope to Blickensdorfer, Germany only, so lower priority; cite only if a count of national maps is needed.

23. Claverie, M., Ju, J., Masek, J.G., Dungan, J.L., Vermote, E.F., Roger, J.-C., et al. (2018). The Harmonized Landsat and Sentinel-2 surface reflectance data set. Remote Sensing of Environment 219, 145-161. DOI 10.1016/j.rse.2018.09.002 — [CrossRef](https://doi.org/10.1016/j.rse.2018.09.002)
    - Critical: Defines HLS (v1.4, starting 2013 at best, Sentinel-2 from 2015); the product does not reach back before Landsat 8, so it only matters for the recent end of the 40-year series. Cite: Methods/Outlook.
    - Companion: Wulder, M.A., Hermosilla, T., White, J.C., Hobart, G.W., Masek, J.G. (2021). Augmenting Landsat time series with Harmonized Landsat Sentinel-2 data products: Assessment of spectral correspondence. Science of Remote Sensing 4, 100031. DOI 10.1016/j.srs.2021.100031 — [CrossRef](https://doi.org/10.1016/j.srs.2021.100031). Directly relevant to extending a Landsat annual series with S2 data.

## 2. Assessment of wiki items listed by the user (all "already in wiki")

### Takeaway
All of the listed wiki papers are legitimate and citable, but none addresses (i) Mediterranean evergreen broad-leaved species change, (ii) multi-decadal consistency, or (iii) area-adjusted change. They should be cited for methods, benchmarks and the "no existing product" gap statement.

### Cited Findings
- yang_2020_modis_evergreen, chastain_2007_eve_landsat_understory: Chastain verified (above). For Yang et al. 2020 I did not re-verify the bibliographic data in this session [unverified here; check your note's DOI].
- hemmerling_2021, blickensdorfer_2024, kollert_2021: verified DOIs above. Temperate focus.
- pflugmacher_2019_lulc_landsat, grabska_2024, bolyn_2022, pu_2021, li_2023, bell_2024, hiebl_2025, hiebl_2026: bibliographic data not re-verified in this session [unverified here]. Bolyn: CrossRef search returned Bolyn et al. 2018 in BASE (DOI 10.25518/1780-4507.16524), a different, earlier paper - ensure the wiki note refers to the correct 2022 paper.
- Wiki also already holds bayle_2024_landsat_greening_inflated (use for Landsat trend artefacts), mauri_2017_EU_tree_data, miettinen_2025_forest_maps_europe, turubanove_2023_canopy_landsat, wessely_2023_tree_species_bottleneck, conedera_2018_drivers_evergreen, fang_2016_eve_mosaics, which are relevant to this paper and need no new search.

### Inferences
- The strongest argument for novelty: no wall-to-wall, multi-decadal, 30 m product of EVE dynamics for Italy was found in this search (absence of evidence from a limited search, not proven).
- Reviewers will likely ask about temporal consistency (Hermosilla 2018/2024, Thapa 2020), sensor continuity (Roy 2016, Crawford 2023) and area-unbiased change estimates (Olofsson 2014). These are the four mandatory additions.

### Gaps
- Yang 2020, Pflugmacher 2019, Li 2023 etc. not re-verified here.

## 3. Rejected / not found

### Takeaway
Several named or expected references could not be verified; they are not to be cited until located.

### Cited Findings (rejected items with reason)
- "Dahlin" (evergreen/leaf-off mapping): CrossRef returned only Dahlin et al. 2012 (Ecological Applications 22(1), 104-118, DOI 10.1890/11-1401.1) and Dahlin et al. 2014 (Landscape Ecology 29(9), 1571-1585, DOI 10.1007/s10980-014-0076-1) - these concern biomass/vegetation patterns on Santa Cruz Island, not evergreen understory mapping. Rejected as irrelevant; the paper the user has in mind was NOT found [unverified].
- "Hobbs" (Chinese privet): no matching Landsat/privet paper found in CrossRef or web search. Not found [unverified].
- Prunus laurocerasus / Hedera / Chinese privet remote-sensing papers: none found with Landsat/Sentinel-2. Web search returned only P. serotina (hyperspectral/LiDAR, Biological Invasions 2018) work - rejected as wrong species and sensor.
- Singh, K.K., Gray, J. (2020). Mapping understory invasive plants in urban forests with spectral and temporal unmixing of Landsat imagery. Photogrammetric Engineering & Remote Sensing 86(8), 509-518. DOI 10.14358/pers.86.8.509. Real (CrossRef) and thematically close (Landsat unmixing for understory invasives), but urban North Carolina and not read; borderline, optional citation for the fractional-cover idea.
- Oreti, L., Barbati, A., Marini, F., Giuliarelli, D. (2020). Very high-resolution true color leaf-off imagery for mapping Taxus baccata L. and Ilex aquifolium L. understory populations in beech forests. Biodiversity and Conservation 29(8), 2605-2622. DOI 10.1007/s10531-020-01991-x. Real, Italy-based, leaf-off evergreen understory (Apennine beech forests), but very high-resolution imagery, not Landsat/S2. Optional supportive citation for the leaf-off principle in Italy.
- Persson et al. 2018 (Remote Sensing 10(11), 1794, DOI 10.3390/rs10111794), Hoscilo & Lewandowska 2019 (Remote Sensing 11(8), 929, DOI 10.3390/rs11080929), Immitzer et al. 2016 (Remote Sensing 8(3), 166, DOI 10.3390/rs8030166): real, but regional/early S2 studies with redundant message vs. Hemmerling/Grabska; rejected for redundancy.
- Ottosen et al. 2020 (IJAEOG 84, 101947, DOI 10.1016/j.jag.2019.101947): tree cover, not species or leaf type; rejected.
- Melaas et al. 2013 (RSE 132, 176-185, DOI 10.1016/j.rse.2013.01.011): deciduous broadleaf phenology from Landsat; useful only for phenology-metric background; rejected as marginal.
- Zhang, H.K. et al. 2018 (RSE 215, 482-494, DOI 10.1016/j.rse.2018.04.031): S2A/L8 reflectance differences; relevant only for S2-extension; optional.
- Hermosilla et al. 2016 (Int. J. Digital Earth 9(11), 1035-1054, DOI 10.1080/17538947.2016.1187673): data processing pipeline; marginal.
- Francini et al. 2024 Sensors 24(12), 3947 (DOI 10.3390/s24123947) "Per-pixel forest attribute mapping and error estimation: GEE and R dataDriven tool": real; tool paper, could be useful for NFI-based mapping/error estimation but not read.
- Not located at all (searches returned nothing usable): Wolter & Townsend multi-temporal Landsat paper (my recalled title could not be matched; instead Thapa 2020 was found), Wilfong is found (see above), Kollert/Bolyn fine. Also a Coweeta Basin evergreen shrub Landsat archive paper (Virginia Tech, vtechworks) appeared in search but is a thesis/dissertation record [unverified, not peer-reviewed article].
- Hemmerling-type Europe-wide leaf-type: Copernicus HRL dominant leaf type product has no peer-reviewed validation paper identified here [unverified].

### Inferences
- The leaf-off/winter evergreen literature is small and North American/Asian; for Italy the practical argument must be built from Chastain 2007, Resasco 2007, Atkins 2018, Wang 2009 plus Mediterranean multi-seasonal evidence (Senf 2015).

### Gaps
- No Landsat/S2 study of laurophyllous/EVE spread in southern Alps or Italy found (not found does not mean none exists; Italian-language or forestry journals such as Forest@, iForest, L'Italia Forestale e Montana were not searched).
- HLS-based tree species/leaf-type mapping with deep learning: not found in this search.
- Training-data reuse across years: only indirect evidence (Hermosilla, Thapa, Pflugmacher 2019, Bell 2024). A dedicated review on temporal transferability was not found.
- Full-text verification of all findings above remains to be done (flagged [background]/[title-level]).
