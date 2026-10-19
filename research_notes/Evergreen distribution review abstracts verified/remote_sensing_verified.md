# Remote sensing of evergreen vs deciduous vegetation, leaf type and tree species cover from Landsat / Sentinel-2: abstract-verified record and gap closing (Round 2)

Date of work: 2026-10-16. Tags used: [ABSTRACT-READ] = abstract text retrieved from OpenAlex/Semantic Scholar/publisher-derived record in this session; [ABSTRACT-PARAPHRASE] = abstract retrieved only via a summarising fetch tool (not verbatim); [FULLTEXT-PARTLY-READ] = none achieved (no full text was read for any paper; the Elsevier/Taylor & Francis/ResearchGate pages returned 403, MDPI/Wiley PDFs were not opened); [METADATA-ONLY] = title/venue/year from index only.

Access limits (honest): Sciencedirect and ResearchGate returned HTTP 403. Semantic Scholar rate-limited (429) repeatedly. Google Scholar: the first 3 queries returned result lists (with a German "system cannot perform this action" banner), later queries (laurophyllisation/Ticino, Quercus ilex Italy forest type, Carta Forestale, Italian-language Forest@/iForest query) were blocked by a captcha and returned nothing. Scholar results are title/author/year lists only. OpenAlex (abstract_inverted_index) was the main abstract source. Quotes below are short (max ~2 sentences) and copied from the OpenAlex abstract text. No accuracy numbers are given unless they appear in the abstract. "Full text not read" applies to every item.

---

## A. Verification of the candidate remote-sensing papers (sections 1-3 of the report and remote_sensing.md)

### Takeaway
Of the papers listed, 8 are directly useful and citable for specific purposes: Atkins 2018 (closest published analogue of leaf-off multi-decadal Landsat for evergreen expansion), Hermosilla 2024 (annual Landsat dominant-species maps with NFI calibration, 86.1% OA), Hermosilla 2018 (VLCE; but only 70.3% OA for a single validation year), Thapa 2020 (a sobering result on back-casting species composition from Landsat), Pasquarella 2018 (harmonic/phenology features), Olofsson 2014 (area-adjusted change estimation), Bonannella 2022 (the only European multi-year species-probability product that includes Quercus ilex), Francini 2024 (NFI-based area proportions, but Netherlands). Several earlier "[background]" statements were checked and need correction (see "Corrections" below).

### Cited Findings (per paper)

**1. Atkins, Epstein & Welsch 2018, Ecosphere 9(10):e02404, DOI 10.1002/ecs2.2404 [ABSTRACT-READ]**
- Abstract: "We use a combination of remotely sensed vegetation indices (e.g., NDVI, tasseled cap indices) derived from snow-free, leaf-off Landsat 5 surface reflectance data from 1986 to 2011 paired with a Random Forest classification model to examine shrub dynamics in the Weimer Run watershed near Canaan Valley, West Virginia". "From 1986 to 2011, there is a 0.14 increase in winter NDVI, with a 52% relative increase in shrub coverage over 25 yr." — [OpenAlex record](https://api.openalex.org/works/doi:10.1002/ecs2.2404)
- Data/classes: Landsat 5 TM, leaf-off, 1986-2011; evergreen understory shrub layer (Rhododendron maximum); one first-order high-altitude watershed. Expansion greatest at lower elevations, along streams, on south-facing slopes; authors attribute it to decreased moisture limitation under changing climate. No classification accuracy number in the abstract (not verified in full text).
- Corrected assessment: Closest published analogue to a multi-decadal leaf-off Landsat series for evergreen expansion, but it is one small watershed and the trend is reported as winter NDVI/shrub cover, not as a species-level wall-to-wall map. Worth a full read for training design over 25 years and accuracy. Citable for: "evergreen understory expansion can be tracked with leaf-off Landsat (principle exists, in a temperate US setting)". Do not claim it validates Mediterranean evergreen-oak mapping.

**2. Hermosilla et al. 2024, Forest Ecol. Manage. 572:122313, DOI 10.1016/j.foreco.2024.122313 [ABSTRACT-READ]**
- Abstract: "we used time-series Landsat imagery to produce annual maps of dominant tree species (n = 37 tree species classes) from 1984 to 2022 at a 30-m spatial resolution for the 650 Mha of Canada's forested ecosystems." "Assessment of the resulting annual species maps using independent validation data resulted in an overall accuracy of 86.1 % ± 0.14 % (95 %-confidence interval)." — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.foreco.2024.122313)
- Other abstract facts: predictors are spectral, geographic, climatic and topographic metrics; calibrated and validated with Canada's National Forest Inventory; "informed by disturbance events and post-processed to ensure consistency of the annual species maps"; reported changes are small (e.g. conifer share 86% to 84.9%; black spruce relative area -4.6%).
- Corrected assessment: Previously only title-level. Now confirmed as the closest design analogue (annual Landsat, 1984-2022, NFI-calibrated, post-processed for temporal consistency). Caveats: (i) geographic and climatic predictors are used, which tends to bake the present distribution into the maps and can mute genuine range shifts (inference, not stated in the abstract); (ii) boreal/temperate, no evergreen-broadleaved classes; (iii) the abstract does not say how OA behaves for early years. Must read in full for validation by year and for consistency post-processing.

**3. Hermosilla et al. 2018, Can. J. Remote Sens. 44(1):67-87, DOI 10.1080/07038992.2018.1437719 [ABSTRACT-READ]**
- Abstract: "Post-processing aimed to reduce spurious class transitions is undertaken integrating change information, land cover transition likelihoods, and year-on-year class membership likelihoods." "Validation was assessed for a single year (2005) using independent data for an overall accuracy of 70.3% (± 2.5%)." — [OpenAlex](https://api.openalex.org/works/doi:10.1080/07038992.2018.1437719)
- Data: annual gap-free best-available-pixel composites and forest change maps for Canada, 1984-2012 (29 years), 650 Mha of forested ecosystems (Virtual Land Cover Engine, VLCE).
- Corrected assessment: The "[background]" description was right in principle. New critical point: validation is for one year only (2005), OA 70.3%, i.e. the temporal accuracy of the other 28 years is not reported in the abstract. Land-cover classes, not tree species. Citable for: change-informed post-processing to suppress implausible class flips, and the limits of such post-processing for gradual change (inference). Read selectively.

**4. Thapa, Wolter, Sturtevant & Townsend 2020, Int. J. Remote Sens. 41(10):4022-4056, DOI 10.1080/01431161.2019.1711245 [ABSTRACT-READ]**
- Abstract: "Model calibration results between Landsat reflectance and FIA ground data for both total forest basal area and balsam fir (Abies balsamea) relative basal area ... were poor to moderate (R2adj 0.39 and 0.48, respectively)." "Groupings of tree species into broadleaved and conifers substantially improved model calibration result (R2adj range: 0.72–0.91)". "Periodic FIA ground data from the early 1990s generated stronger models compared to other FIA-Landsat date combinations tested." — [OpenAlex](https://api.openalex.org/works/doi:10.1080/01431161.2019.1711245)
- Data: archived Landsat (pre/post spruce-budworm outbreak) with U.S. Forest Inventory and Analysis data (periodic 1970s, 1990s; annual 2003-2006) in the Border Lakes Ecoregion, Upper Midwest USA. Continuous abundance models (R2adj), not class maps; aspen R2adj 0.64, spruce 0.78 (RMSE 10.65-15.56 m2/ha).
- Corrected assessment: Earlier note said "US Lake States, accuracy decay unverified". Now: it is regression of species abundance, not a classification; species-level calibration was weak, leaf-type grouping (broadleaf vs conifer) much better. The authors list weak reasons (varying FIA protocols, understory species hidden from remote detection, missing phenology-capturing images). Highly relevant as a cautionary result: back-casting species is hard, leaf-type grouping is more robust. This supports using leaf type (LTC) as the primary hindcast target and DTS more cautiously (inference). Also relevant: "understory species largely hidden from remote detection" applies to understory EVEs.

**5. Pasquarella, Holden & Woodcock 2018, Remote Sens. Environ. 210:193-207, DOI 10.1016/j.rse.2018.02.064 [ABSTRACT-PARAPHRASE]**
- OpenAlex/Crossref/Semantic Scholar returned no abstract. A summarising fetch of the UMass NE CASC library page returned: harmonic metrics (mean annual reflectance, seasonal variation) and phenological metrics (timing of seasonal events) from Landsat time series were tested for eight New England forest types; the spectral-temporal features "consistently and significantly (paired t-test, p << 0.01) outperformed all feature sets" tested; harmonic features such as annual amplitude helped separate deciduous hardwoods from conifers; autumn onset and season length helped separate hardwood classes. — [UMass NE CASC](https://necasc.umass.edu/biblio/improved-mapping-forest-type-using-spectral-temporal-landsat-features)
- Corrected assessment: Earlier "[background]" statement is essentially confirmed (New England, harmonic + phenology features beat single/multi-date). No accuracy numbers retrieved. Citable for: justification of spectral-temporal features for leaf-type separation. Not Mediterranean; evergreen broadleaved classes absent in the eight New England types (not stated, inference from the study area).

**6. Senf, Leitão, Pflugmacher, van der Linden & Hostert 2015, Remote Sens. Environ. 156:527-536, DOI 10.1016/j.rse.2014.10.018 [ABSTRACT-PARAPHRASE]**
- No abstract in the APIs. EOLab (HU Berlin) page, via a summarising fetch: tests multi-seasonal Landsat and STARFM-synthetic Landsat-like images for land cover in complex Mediterranean landscapes (context: low-intensity farmland abandonment/intensification); short quote "multi-seasonal Landsat data from spring and early autumn are crucial for achieving satisfying mapping accuracies"; best overall accuracy 74.5%; synthetic imagery improved on single-date but never matched original multi-seasonal Landsat. — [EOLab](https://eolab.geo.hu-berlin.de/publication/senf_2015a/)
- Corrected assessment: The earlier statement that this paper separated "evergreen vs deciduous woody classes" and was in "Portugal" could NOT be verified from the abstract summary [still unverified]. What is verified: Mediterranean land cover (not species), OA 74.5%, spring and early autumn imagery most important. The 74.5% OA signals that Mediterranean land-cover separation from Landsat is moderate. Citable for: seasonal timing matters in Mediterranean Landsat classification.

**7. Gómez, White & Wulder 2016, ISPRS J. Photogramm. 116:55-72, DOI 10.1016/j.isprsjprs.2016.03.008 [ABSTRACT-READ]**
- Abstract: "The inclusion of time series change in the land cover mapping process provides information on class stability and informs on logical class transitions (both temporally and categorically)." "In this review, we present the issues and opportunities associated with generating and validating time-series informed annual, large-area, land cover products". — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.isprsjprs.2016.03.008)
- Corrected assessment: The review is specifically about annual, change-informed land cover products (same group as Hermosilla 2018/2024). It is the right conceptual citation for temporal consistency/logical transitions and validation issues. The earlier "training-sample reuse" claim is NOT stated in the abstract [unverified].

**8. Zhu & Woodcock 2014, Remote Sens. Environ. 144:152-171, DOI 10.1016/j.rse.2014.01.011 [ABSTRACT-PARAPHRASE]**
- APIs had no abstract. A web search summary of the MODIS-team abstract page reports: CCDC tested on one Landsat scene in New England with 519 images (1982-2011); change detection producer's accuracy 98%, user's accuracy 86%, temporal accuracy 80%; classification uses model coefficients and RMSE in a Random Forest. — [MODIS publications page](https://modis.gsfc.nasa.gov/sci_team/pubs/abstract_new.php?id=10221)
- Assessment: methodological alternative; designed for abrupt breaks, so gradual EVE encroachment is a weak fit (inference). Skim.

**9. Roy et al. 2016, Remote Sens. Environ. 185:57-70, DOI 10.1016/j.rse.2015.12.024 [ABSTRACT-READ]**
- Abstract: "a total of 59 million 30 m corresponding sensor observations extracted from 6317 Landsat-7 ETM+ and Landsat-8 OLI images acquired over three winter and three summer months for all the conterminous United States (CONUS) are compared." — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.rse.2015.12.024)
- Assessment: Confirmed as ETM+ to OLI continuity (CONUS, winter and summer). Not TM-to-ETM+. Winter comparison is useful for a leaf-off-dependent signal. The rest of the abstract (the size of differences) was truncated in my retrieval, so the earlier phrase "small but systematic" is [still unverified].

**10. Crawford et al. 2023, Sci. Remote Sens. 8:100103, DOI 10.1016/j.srs.2023.100103 [ABSTRACT-READ]**
- Abstract: "the USGS reprocessed the Landsat archive as Collection 2 in 2020 ... Collection 2 products have improved geolocation and, for the first time, the USGS provides a global inventory of Level 2 surface reflectance and surface temperature products." — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.srs.2023.100103)
- Assessment: Data description only. Citable for the data source (Collection 2 Level 2 surface reflectance); does not quantify residual inter-sensor trend artefacts.

**11. Wulder et al. 2022, Remote Sens. Environ. 280:113195, DOI 10.1016/j.rse.2022.113195 [ABSTRACT-READ]**
- Abstract: "Since 1972, the Landsat program has been continually monitoring the Earth, to now provide 50 years of digital, multispectral, medium spatial resolution observations." — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.rse.2022.113195)
- Assessment: general citation for the archive length; nothing more.

**12. Claverie et al. 2018, Remote Sens. Environ. 219:145-161, DOI 10.1016/j.rse.2018.09.002 [ABSTRACT-READ]**
- Abstract: "As of version 1.3, the HLS data set covers 10.35 million km2 and spans from first Landsat 8 data (2013); Sentinel-2 data spans from October 2015." "The main known issue of the current data set remains the Sentinel-2 cloud mask". — [Semantic Scholar](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1016/j.rse.2018.09.002?fields=title,abstract)
- Assessment: confirmed; HLS begins in 2013, so only relevant for the last decade of a 40-year series.

**13. Wulder, Hermosilla, White, Hobart 2021, Sci. Remote Sens. 4:100031, DOI 10.1016/j.srs.2021.100031 [ABSTRACT-READ]**
- Abstract: "S30 and BAP had the lowest agreement, with R values ranging from 0.71 to 0.85 for spectral channels and r = 0.90 for NBR." "The level of agreement between S30 and BAP reported herein would enable integration of HLS outputs with historic Landsat data." Note the author list per OpenAlex shows Wulder, Hermosilla, White, Hobart (Masek not confirmed in the OpenAlex first-four list; the report lists Masek as fifth author, unchecked here). — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.srs.2021.100031)
- Assessment: useful, with a quantified caveat: S30-BAP agreement is the weakest (R 0.71-0.85), which matters when extending a Landsat series with Sentinel-2 for a leaf-off-sensitive signal. Also: "Some dependency between spectral agreement and land cover was found, with stronger correspondence for non-vegetated cover types" (so vegetation is the harder case).

**14. Zhang, Roy, Yan, Li 2018, Remote Sens. Environ. 215:482-494, DOI 10.1016/j.rse.2018.04.031 [ABSTRACT-READ]**
- Abstract: "the MSI surface NDVI was greater than the OLI surface NDVI." Study area southern Africa, 4 months in 2016. — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.rse.2018.04.031)
- Assessment: provides regression coefficients to harmonise S2A and L8; optional (not Mediterranean). The earlier listing under "optional" is fine.

**15. Resasco, Hale, Henry & Gorchov 2007, Int. J. Remote Sens. 28(16):3739-3745, DOI 10.1080/01431160701373721 [ABSTRACT-READ]**
- Abstract: "L. maackii cover was measured in eight stands and compared to 15 Landsat 5 TM and Landsat 7 ETM+ images from spring and autumn dates from 1999 to 2006." "These findings justify further investigation of the effectiveness of late fall images to map the historical spread of L. maackii and other forest understory invasives with similar phenology." — [OpenAlex](https://api.openalex.org/works/doi:10.1080/01431160701373721)
- Assessment: proof-of-concept only (eight stands, separability, SARVI2 higher in high-cover plots in November images only). The authors themselves propose historical mapping. Citable for the phenological-offset principle; not for accuracy.

**16. Wilfong, Gorchov & Henry 2009, Weed Sci. 57(5):512-520, DOI 10.1614/ws-09-012.1 [ABSTRACT-READ]**
- Abstract: "The use of image differencing in which a January 2001 image was subtracted from a November 2005 image provided better prediction of Amur honeysuckle cover than the use of the single November 2005 image." "NDVI was the best-performing predictor variable ... a quadratic function providing a better fit (R2 = 0.75) than a linear function (R2 = 0.65). This predictive model was verified with 15 other woodlots (R2 = 0.77)." — [OpenAlex](https://api.openalex.org/works/doi:10.1614/ws-09-012.1)
- Assessment: confirms Resasco follow-up: Landsat 5/7, SW Ohio and E Indiana. Quantified; a fall-minus-winter difference image is the useful trick for an evergreen/late-leaf signal. Cite with Resasco.

**17. Wang, Skidmore, Toxopeus & Liu 2009, Photogramm. Eng. Remote Sens. 75(1):37-47, DOI 10.14358/pers.75.1.37 [ABSTRACT-READ]**
- Abstract: "vegetation indices, especially the normalized difference vegetation index (NDVI) derived from leaf-off (winter) images were significantly correlated with percent understory bamboo cover" and "overall accuracy of 89 percent (k 5 0.59)" for presence/absence; three density classes OA 68% (kappa 0.48). — [OpenAlex](https://api.openalex.org/works/doi:10.14358/pers.75.1.37)
- Assessment: supports winter-image principle; kappa 0.59 with OA 89% shows weaker class agreement than OA implies; "Landsat" is stated as "Landsat vegetation indices" in the abstract. A second continent (China, panda habitat per earlier note, not in abstract).

**18. Bonannella et al. 2022, PeerJ 10:e13728, DOI 10.7717/peerj.13728 [ABSTRACT-READ]**
- Abstract: "distribution maps for 16 forest tree species (... Olea europaea ..., Pinus halepensis ..., Quercus ilex L., Quercus suber L. ...) at high spatial resolution (30 m)"; "High resolution (30 m) probability and model uncertainty maps of realized distribution were produced for each species using a time window of 4 years for a total of 6 distribution maps per species for the studied period". "Results of spatial cross validation show that Olea europaea and Quercus suber achieved the best performances in both potential and realized distribution". — [OpenAlex](https://api.openalex.org/works/doi:10.7717/peerj.13728)
- Data: >3 million occurrence points, 585 covariates incl. Landsat bands/indices and seasonal composites; ensemble ML (stacking). Q. ilex IS one of the 16 species. Abstract gives no Q. ilex-specific score. Worst performers Pinus sylvestris and Salix caprea. Authors: "The produced time-series occurrence predictions can be used to quantify temporal trends and detect potential forest degradation."
- Corrected assessment: Earlier text ("30 m ... for many species ... Italian EVEs") is partly wrong: 16 species only, six 4-year windows (2000-2020), probability maps built on point occurrence data (inputs not purely Landsat). Of EVEs only Q. ilex, Q. suber, Olea, (and conifers); no laurophylls. Essential benchmark and a point of contrast (probability of occurrence, not area-based cover). Whether temporal trends are reliable is not shown in the abstract.

**19. Francini et al. 2024, Int. J. Appl. Earth Obs. Geoinf. 131:103935, DOI 10.1016/j.jag.2024.103935 [ABSTRACT-READ]**
- Abstract: "Forest species maps and area proportion estimates were produced for the Netherlands." "harmonic predictors increased the model performance by 8% in terms of overall accuracy and the kappa coefficient by 9%"; "average deviation between NFI and remote sensing-based area proportion estimates of 9%, with deviations approaching 0% when increasing the number of NFI plots per cell." — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.jag.2024.103935)
- Corrected assessment: Study area confirmed: the Netherlands (earlier note "probably Netherlands - unverified" now verified). Sentinel-2 harmonic predictors (phenology) + NFI plots; compares NFI and map-based area estimates at 10 km cells. Not Mediterranean; useful for the NFI-linked area proportion method (cite INFC-analogue). The absolute OA is not in the abstract.

**20. Grabska et al. 2019, Remote Sens. 11(10):1197, DOI 10.3390/rs11101197 [ABSTRACT-READ]**
- Abstract: "nine tree species" in the Polish Carpathians; "the use of the Sentinel-2 time series instead of single date imagery significantly improved forest tree species mapping, by approximately 5–10% of overall accuracy. In particular, combining images from spring and autumn resulted in better species discrimination." 18 images from 2018. — [OpenAlex](https://api.openalex.org/works/doi:10.3390/rs11101197)
- Assessment: confirmed. Not Mediterranean; no evergreen broadleaved species (nine species list). Only for "time series beat single-date".

**21. Grabska, Frantz & Ostapowicz 2020, Remote Sens. Environ. 251:112103, DOI 10.1016/j.rse.2020.112103 [ABSTRACT-READ]**
- Abstract: "the highest overall accuracy exceeded 85% for SVM classification of all variables (86.9%)"; "From the best five classifications we created a final ensemble map (overall accuracy of 86.6%)"; eleven tree species; "Including elevation information improved the accuracies." — [Semantic Scholar](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1016/j.rse.2020.112103?fields=title,abstract)
- Assessment: confirmed; ~20,000 km2 Polish Carpathians, 114 predictors. Cite for the value of topography and ensemble precision maps only.

**22. Immitzer et al. 2019, Remote Sens. 11(22):2599, DOI 10.3390/rs11222599 [ABSTRACT-READ]**
- Abstract: "the multi-temporal analysis approach improves the out-of-bag overall accuracy from 72.9% to 85.7% for the broadleaved and from 83.8% to 95.3% for the coniferous tree species"; mono-temporal accuracies 48.1% (January 2017) to 78.6% (June 2017); "images from April until August proved most important". — [OpenAlex](https://api.openalex.org/works/doi:10.3390/rs11222599)
- Assessment: confirmed (Austria, 18 S2 scenes, 5 coniferous + 7 broadleaved species). Interesting detail: January single-date accuracy only 48.1%, i.e. winter alone is poor for deciduous species discrimination (but winter is the key for evergreens vs deciduous, a distinct task). Skim.

**23. Welle et al. 2022, Remote Sens. 14(14):3330, DOI 10.3390/rs14143330 [ABSTRACT-READ]**
- Abstract: NFI data train an ML classifier on a dense Sentinel-2 time series, seven dominant species classes; "weighted average F1-score for deciduous tree species ... between 0.77 and 0.91 and for non-deciduous tree species ... between 0.85 and 0.94". — [OpenAlex](https://api.openalex.org/works/doi:10.3390/rs14143330)
- Assessment: confirmed; Germany only, NFI-trained national map; lower priority.

**24. Singh & Gray 2020, Photogramm. Eng. Remote Sens. 86(8):509-518, DOI 10.14358/pers.86.8.509 [ABSTRACT-READ]**
- Abstract: "We compared two approaches to multiple endmember spectral mixture analysis for detecting Ligustrum sinense in the southeastern United States: the use of temporal signatures of endmembers from full and select-date normalized difference vegetation index time series, and conventional spectral unmixing using a single image date." — [OpenAlex](https://api.openalex.org/works/doi:10.14358/pers.86.8.509)
- Assessment: Ligustrum sinense (Chinese privet) is a semi-evergreen understory invader; Landsat NDVI time series unmixing. Earlier "urban North Carolina" is not in the abstract (abstract says southeastern US) [still unverified]. No accuracy numbers in the abstract. Best available remote-sensing paper for a Ligustrum relative of the Ligustrum-type invaders; cite optionally.

**25. Oreti et al. 2020, Biodivers. Conserv. 29(8):2605-2622, DOI 10.1007/s10531-020-01991-x [ABSTRACT-READ]**
- Abstract: "Taxus baccata L. and Ilex aquifolium L. are evergreen tree species and occur as isolated trees or groups in the understory of beech dominated forests." "The thematic accuracy of the target species map resulted in a Producer Accuracy of 0.77 and a User Accuracy of 0.80." Imagery: Google Earth leaf-off true colour, pixel 0.11 m, object-based. — [Semantic Scholar](https://api.semanticscholar.org/graph/v1/paper/DOI:10.1007/s10531-020-01991-x?fields=title,abstract)
- Assessment: Italian Apennine beech forests; not Landsat/S2; PA/UA 0.77/0.80. Supportive Italian example of the leaf-off principle with very high resolution imagery.

**26. Olofsson et al. 2014, Remote Sens. Environ. 148:42-57, DOI 10.1016/j.rse.2014.02.015 [ABSTRACT-PARAPHRASE]**
- No abstract in the APIs; a web search returned abstract text from the Nottingham repository: good practice covers sampling design (probability sampling), response design (reference data with sufficient spatial and temporal detail to label each unit), and analysis (error matrix in proportions of area, overall/user/producer accuracy, area estimates). — [Nottingham ePrints](https://eprints.nottingham.ac.uk/44846/)
- Assessment: standard method; unchanged. Note the abstract itself stresses reference data of "sufficient spatial and temporal representation" (a practical issue for 1980s reference labels).

### Corrections to earlier statements (summary)
- Hermosilla 2024: now verified, 37 classes, 1984-2022, OA 86.1% +/- 0.14, NFI-calibrated.
- Hermosilla 2018: validation only for 2005, OA 70.3% +/- 2.5%.
- Thapa 2020: Border Lakes Ecoregion; abundance regression, not classification; weak species-level R2adj 0.39-0.78, grouped leaf type 0.72-0.91.
- Senf 2015: OA 74.5% (best multi-seasonal scenario); "evergreen vs deciduous" claim and "Portugal" unverified.
- Gómez 2016: about annual change-informed land-cover products; "training-sample reuse" not in abstract.
- Bonannella 2022: only 16 species, six 4-year windows, point-occurrence based; Q. ilex included.
- Francini 2024: Netherlands.
- Singh & Gray 2020: abstract says "southeastern United States", not "urban North Carolina" (urban forests appear only in the title).
- Wang 2009: OA 89% but kappa 0.59 (presence/absence); density classes OA 68%.

### Inferences
- The strongest design analogues for the project (annual Landsat, 40 years) remain Hermosilla 2024/2018 (annual, NFI) and Atkins 2018 (leaf-off evergreen expansion); neither is Mediterranean and neither maps evergreen broadleaved trees.
- Thapa 2020 plus the 70.3% single-year accuracy of Hermosilla 2018 argue for treating early-year accuracy as an explicit uncertainty, not an assumption.

### Gaps
- Full texts were not read for any paper (access limits above); accuracy by year and training reuse details remain to be checked.
- Abstracts of Pasquarella 2018, Senf 2015, Zhu & Woodcock 2014, Olofsson 2014 are paraphrase-only.

---

## B. Gap-closing searches

Search sources actually used: OpenAlex full-text search (about 35 queries), Google Scholar (3 queries worked, 4 captcha-blocked), WebSearch, Semantic Scholar (rate limited). Europe PMC and Crossref were used only as fall-back for abstracts. Italian journals (Forest@, iForest, L'Italia Forestale e Montana) were reached through OpenAlex, not their own sites.

### B1. Landsat/Sentinel-2/MODIS mapping of Quercus ilex / evergreen oaks / sclerophyllous vs deciduous forest (Italy, Mediterranean)

#### Takeaway
No study was found that maps Quercus ilex / evergreen broadleaved forest change over decades with Landsat in Italy. What exists: phenology-based discrimination of holm oak vs hornbeam communities (Pesaresi), a national Italian EUNIS habitat map with a broadleaved evergreen class (Agrillo 2021), long-term Landsat NDVI trends of stable cork/holm oak stands in Portugal (Aubard 2019), and an NDVI-differencing forest-expansion study in Basilicata (Mancino 2013). A not-found result is limited by search tools (Scholar partly blocked).

#### Cited Findings
- Agrillo et al. 2021, Remote Sens. 13(7):1231, DOI 10.3390/rs13071231 [ABSTRACT-READ]: "classify 24 forest habitats according to the EUNIS III level: 12 broadleaved deciduous (T1), 4 broadleaved evergreen (T2) and eight needleleaved forest habitats (T3), and achieved an overall accuracy of 87% at the EUNIS II level classes"; "76.14% at the EUNIS III level"; "The highest overall accuracy value was obtained for the broadleaved evergreen forest equal to 91%". Method: EVA vegetation plots + Sentinel-2 time series + environmental data, Random Forest, national scale Italy. — [OpenAlex](https://api.openalex.org/works/doi:10.3390/rs13071231). Worth reading: it is the only Italy-wide Sentinel-2 product found that has a broadleaved evergreen class (habitat-level, plot-based, single epoch). The 91% is a per-group figure at habitat level; reference plots are phytosociological relevés. Cite as benchmark for the S2 end of the series.
- Pesaresi, Mancini, Quattrini & Casavecchia 2020, Remote Sens. 12(7):1132, DOI 10.3390/rs12071132 [ABSTRACT-READ]: FPCA of Landsat 8 NDVI time series to map Mediterranean forest plant associations, "overall accuracy of 87.5%"; FPCA scores "contributed ... much more than the topographic and lithological features". — [OpenAlex](https://api.openalex.org/works/doi:10.3390/rs12071132). Worth reading for phenology-based discrimination in central Italian forests (Marche region; region not in the abstract).
- Pesaresi, Mancini & Casavecchia 2020, Diversity 12(8):313, DOI 10.3390/d12080313 [ABSTRACT-READ]: NDVI time series with FPCA discriminated "six different forest plant associations ... three dominated by black hornbeam (Ostrya carpinifolia) and three dominated by holm oak (Quercus ilex)"; FPCA components correlated with vegetation abundance (Mantel r = 0.76). — [OpenAlex](https://api.openalex.org/works/doi:10.3390/d12080313). Directly shows holm oak vs deciduous (hornbeam) communities separable by NDVI seasonality in central Italy. Skim.
- Aubard, Paulo & Silva 2019, Remote Sens. 11(5):525, DOI 10.3390/rs11050525 [ABSTRACT-READ]: "NDVI ... for the 1984–2017 period using Landsat-5 TM and Landsat-7 ETM+"; only areas "with a stable land cover of cork oak ... and holm oak"; "TM values were adjusted to those of ETM+"; "Twelve percent of the area of oak stands in Portugal presents significant decreasing trends". — [OpenAlex](https://api.openalex.org/works/doi:10.3390/rs11050525). Relevant for the dieback/browning side and for TM-to-ETM+ adjustment in a Mediterranean evergreen setting; it uses only July-August NDVI "to minimize the spectral contribution of understory", i.e. a stable-cover mask approach (the mask source is not stated in the abstract).
- Mancino, Nolè, Ripullone & Ferrara 2013, iForest 7:..., DOI 10.3832/ifor0909-007 [ABSTRACT-READ]: NDVI differencing of two Landsat TM images (1984, 2010) in Basilicata; "91.8% accuracy in detection of natural forest expansion"; "total regional forest cover increased by 19.7% (70154 ha), consistent with National Forest Inventory data". — [OpenAlex](https://api.openalex.org/works/doi:10.3832/ifor0909-007). Italian two-date Landsat precedent for forest expansion; forest vs non-forest, not leaf type; page numbers not retrieved.
- Modica et al. 2016, J. Agric. Eng., DOI 10.4081/jae.2016.571 [ABSTRACT-READ]: Landsat 8 plus photointerpretation to map cork oak (Quercus suber) woodlands in two Calabrian sites; no accuracy in the abstract. — [OpenAlex](https://api.openalex.org/works/doi:10.4081/jae.2016.571). Marginal (single species, local).
- Bonannella 2022 (above, A18) is the only multi-year product with Q. ilex found.

#### Inferences
- The combination "Italy + Quercus ilex or evergreen-broadleaf + multi-decadal Landsat" appears unoccupied in what was searched (absence of evidence from OpenAlex/Scholar partial coverage).

#### Gaps
- Scholar query "Quercus ilex Landsat OR Sentinel-2 forest type map Italy" was captcha-blocked; MODIS-based Mediterranean evergreen/deciduous studies were not found; Puzzolo et al. 2004 (Landsat TM multi-seasonal forest type discrimination in Mediterranean, listed in Scholar) is [METADATA-ONLY] (World Scientific).

### B2. Remote sensing of laurophyllisation / evergreen spread (Insubria, Ticino, Hedera, Prunus laurocerasus, Trachycarpus, Ligustrum lucidum; aerial/UAV/LiDAR)

#### Takeaway
No remote-sensing study of laurophyllisation or of the spread of Trachycarpus, Prunus laurocerasus, Hedera or Ligustrum lucidum in the southern Alps/Italy was found (OpenAlex searches with 9 query variants; Scholar query on this was captcha-blocked, so Scholar was not able to confirm). Ecological studies exist but are field-plot based.

#### Cited Findings
- Conedera et al. 2018 (Reg. Environ. Change; OpenAlex lists the record as 2017, DOI 10.1007/s10113-017-1212-7) "Drivers of broadleaved evergreen species spread into deciduous forests in the southern Swiss Alps" [METADATA-ONLY here; already a wiki note].
- Fehr, Conedera, Dalle Fratte & Cerabolini 2024, Appl. Veg. Sci., DOI 10.1111/avsc.12765 [ABSTRACT-READ]: "ten deciduous forest sites" on the Swiss-Italian southern Alps with Trachycarpus fortunei; plots of 400 m2 along invasion gradient; native species richness reduced in mesic-moist forests with high palm density. — [OpenAlex](https://api.openalex.org/works/doi:10.1111/avsc.12765). Field plots only, no imagery; useful as ecological impact and as evidence that this EVE is an understory/subcanopy layer that Landsat is unlikely to see (inference).
- Alessi, Wellstein, Spada & Zerbe 2021, Rend. Lincei, DOI 10.1007/s12210-021-00981-7 [ABSTRACT-READ]: "16 sites" in central Italy; population structure of Laurus nobilis indicates "ongoing expansion"; increase of forest cover and age due to abandonment is suggested as key factor. — [OpenAlex](https://api.openalex.org/works/doi:10.1007/s12210-021-00981-7). Field-based; not remote sensing. Useful ecologically (and links forest age/abandonment with EVE regeneration).
- Pautasso 2013, Ann. Bot. (Roma), DOI 10.4462/annbotrm-10092 [ABSTRACT-READ]: review of global change and forests in Insubria; mentions climate change, invasive species, rural abandonment; no evergreen remote-sensing content. Marginal.
- Singh & Gray 2020 (above): Landsat NDVI unmixing for Ligustrum sinense understory — the only moderate-resolution time-series study of a Ligustrum understory invader found (US). Ligustrum lucidum hits were Argentinian/Uruguayan studies (Ateliê Geográfico 2024; Agrociencia Uruguay 2022) [METADATA-ONLY], not read.
- Hedera/Prunus/Trachycarpus: no remote-sensing paper found; the OpenAlex hits were irrelevant (UBC thesis on two invasive species, hyperspectral/LiDAR shrub mapping Frontiers Plant Sci 2016 [METADATA-ONLY]).
- Leaf-off high-resolution Italian precedent: Oreti 2020 (above).

#### Inferences
- Evidence suggests the laurophyll signal is mainly understory/subcanopy, which Landsat sees mostly through winter greenness (Atkins 2018 principle). Validation of such a signal would need field plots (Conedera/Alessi-type) rather than existing RS products.

#### Gaps
- No aerial-imagery, UAV or LiDAR study of laurophyll spread found. A Zurich thesis (2016) on Trachycarpus spread in southern Ticino/Lago Maggiore (DOI 10.5167/uzh-127489) exists [METADATA-ONLY]; it might use historical aerial images but this is unverified.

### B3. Italian national forest-type/species maps and their changes over time

#### Takeaway
Direct products found: IUTI land-use inventory (aerial point sampling, 1990-2022, land use not species), Italian 10 m Copernicus-integrating land cover map 2012-2020, Agrillo 2021 EUNIS forest habitat map. No Italian national tree-species or leaf-type time series from Landsat was found. For a European leaf-type benchmark, the Copernicus Dominant Leaf Type (DLT) HRL has limited published validation.

#### Cited Findings
- Marchetti, Bertani, Corona & Valentini 2012, Forest@ (Forest - Riv. Selvic. Ecol. For.), DOI 10.3832/efor0696-009 [ABSTRACT-READ]: IUTI is "a land use inventory of Italy, based on point sampling" on aerial orthophotos with "about 1.2 million sample points" for 1990, 2000, 2008. — [OpenAlex](https://api.openalex.org/works/doi:10.3832/efor0696-009). Independent land-use change reference for forest area; classes are land uses, not species/leaf types; check whether IUTI forest subclasses distinguish broadleaved evergreen [unverified].
- Ottaviano, Petti, Tonti & Munafò 2026, Forest@, DOI 10.3832/efor5002-023 [ABSTRACT-READ]: IUTI updated 1990-2022; as of 2022 woodland surpasses arable land in extent; main drivers: urban expansion and "recolonization of abandoned farmland by forest in hilly and mountainous areas". — [OpenAlex](https://api.openalex.org/works/doi:10.3832/efor5002-023). Recent, supports the land-abandonment driver context (note: published 2026 per index; verify journal metadata).
- De Fioravante et al. 2021, Land, DOI 10.3390/land11010035 [ABSTRACT-READ]: Italy 10 m land cover 2012-2020 from Copernicus products; "validated and compared with the CORINE Land Cover". — [OpenAlex](https://api.openalex.org/works/doi:10.3390/land11010035). Land cover only; forest not split by leaf type in the abstract.
- Waser et al. 2021, ISPRS J. Photogramm. Remote Sens., DOI 10.1016/j.isprsjprs.2021.08.017 [ABSTRACT-READ]: Dominant Leaf Type for Switzerland from S1/S2 + DTM, RF and UNET, kappa around 0.95; "A comparison with the Copernicus High Resolution Layer (HRL) DLT 2018 revealed overall higher map accuracies with the exception of pure broadleaved forest." — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.isprsjprs.2021.08.017). Only broadleaved vs coniferous; shows the HRL DLT has weaknesses. Switzerland, not Italy.
- Breidenbach et al. 2020, Can. J. For. Res., DOI 10.1139/cjfr-2020-0170 [ABSTRACT-READ]: Norway, S2 + NFI, OA 90% at stand level; model-assisted area estimates. Similar to Francini; lower priority.
- Turubanova et al. 2023, Remote Sens. Environ., DOI 10.1016/j.rse.2023.113797 [ABSTRACT-READ]: tree canopy extent/height change in Europe 2001-2021 from Landsat archive; "user's and producer's accuracies ... are ≥94% for the tree canopy extent maps"; tree canopy extent increased about 1%, with the largest increase in Southern Europe among others. — [OpenAlex](https://api.openalex.org/works/doi:10.1016/j.rse.2023.113797). Already a wiki note (turubanova_2023_canopy_landsat); useful as forest mask and Landsat-based change benchmark. No leaf-type information.
- Giannetti et al. 2018, Ann. For. Sci., DOI 10.1007/s13595-017-0674-6, "European Forest Types: toward an automated classification" [METADATA-ONLY, no abstract retrieved]. Possibly relevant (EFT classes include evergreen broadleaved types), but unverified; do not cite until read.
- Hansen GFC for Italy: no Italy-specific mapping of evergreen change found; GFC is not leaf-type specific [background only].

#### Gaps
- Carta Forestale / INFC-based maps and the Copernicus HRL DLT validation for Italy: not found with the tools (Scholar for "Carta Forestale" was captcha-blocked). A 2025 paper "National Forest Inventory in Italy: new perspectives for forest monitoring" (Ann. For. Sci., DOI 10.1186/s13595-025-01303-9) appeared in the search [METADATA-ONLY]; may be the right source for INFC description.

### B4. Temporal transfer / label reuse for multi-decadal Landsat classification

#### Takeaway
Direct evidence is available for crops and short Sentinel-2 periods; for forest types with Landsat, the closest are LCMAP training-data selection (US), Hermosilla's change-informed approach, Thapa 2020 (historical FIA with Landsat) and Verhulst 2024 (Sentinel-2 cross-year tree species).

#### Cited Findings
- Verhulst, Heremans, Blaschko & Somers 2024, Remote Sens. 16(14):2653, DOI 10.3390/rs16142653 [ABSTRACT-READ]: five tree species in Flanders, S2 2018-2022; "This resulted in a decrease in overall accuracy between 2.30 and 14.92 percentage points depending on the algorithm and evaluated year"; "cross-year classification performance could be improved by using multi-year training data". — [OpenAlex](https://api.openalex.org/works/doi:10.3390/rs16142653). The best direct quantification of cross-year loss for tree species. Worth reading. Limits: same sensor, 5 years, temperate, five species.
- Zhou, Tollerud, Barber, Smith et al. 2020, Remote Sens. 12(4):699, DOI 10.3390/rs12040699 [ABSTRACT-READ]: LCMAP annual land cover; training from NLCD 2001 and 2011; "the NLCD 2001 training data delivered the best classification accuracy"; "improved the annual land cover map accuracy by an average of 10%". — [OpenAlex](https://api.openalex.org/works/doi:10.3390/rs12040699). Evidence on reusing labels from one epoch for annual maps (CONUS, land cover classes). Skim methods.
- Hermosilla 2018/2024, Thapa 2020 (above).
- Wijesingha et al. 2024 (ISPRS J.; agricultural land cover, spatial-temporal transferability, Landsat archive): found in Scholar listing [METADATA-ONLY], not located in OpenAlex; crop focus.
- Crop papers on cross-year label reuse found in OpenAlex (Front. Plant Sci. 2022; Remote Sens. 2023) [METADATA-ONLY], rejected as crops.

#### Gaps
- No tree-species/leaf-type paper doing label propagation across decades with Landsat in the Mediterranean found.

### B5. Deep learning on annual Landsat/Sentinel-2 time series for tree species, Mediterranean

#### Takeaway
Deep learning tree-species mapping with Sentinel-2 exists for temperate Europe (Mouret 2025) and in generic form, but none Mediterranean/Italian evergreen-focused and none on Landsat time series was found.

#### Cited Findings
- Mouret, Morin, Planells & Vincent-Barbaroux 2025, Remote Sens. 17(7):1190, DOI 10.3390/rs17071190 [ABSTRACT-READ]: central France, 10 tree species; DL models "OA of around 95% and an F1-macro score of around 80%" vs RF "92% and 60%"; "all models struggle to predict in areas not well covered by training data". — [OpenAlex](https://api.openalex.org/works/doi:10.3390/rs17071190). Worth reading as a recent benchmark of DL vs RF for minority classes (relevant to rare EVEs). Temperate.
- Tan, Li, Ma & Yan 2025, Front. For. Glob. Change, DOI 10.3389/ffgc.2025.1599510 [ABSTRACT-READ]: Sentinel-1/2 time series with self-supervised pretraining; OA 0.847, macro-F1 0.836 vs 0.764/0.737 for non-pretrained. Study area not given in the abstract [unverified]. Relevant to pretraining.
- Vasilakos et al. 2020 (Lesvos, land cover, ensemble) and Mallinis et al. 2023 (NE Greece; forest type OA 84.13%, species OA 74.89%, Forests 14:2224) [ABSTRACT-READ]: Mediterranean forest types/species from Sentinel-2 with classical ML. Mallinis shows a Mediterranean forest-type to species accuracy drop (84.13% to 74.89%), but these are not evergreen vs deciduous studies per se.
- Scholar listing [METADATA-ONLY]: Praticò et al. 2021 (Remote Sens., ML classification of Mediterranean forest habitats in GEE); De Luca et al. 2022 (Eur. J. Remote Sens., S1/S2 and open-source ML, Calabria presumably); Campos-Taberner 2020 (Sci. Rep., DL land use from S2 time series); Viana-Soto et al. 2026 (RSE, DL forest disturbance detection Landsat Europe). None read.

#### Gaps
- No Landsat deep-learning tree species study found; none for Mediterranean evergreens.

---

## C. Rejected / not worth reading (with reasons)
- Modica 2016 (cork oak Calabria): single species, local, no accuracy in abstract. Marginal.
- Vasilakos 2020 (Lesvos): land cover classifier comparison, not forest species.
- Liu 2024 (Changbai, Remote Sens. 16:293): temperate China, no Mediterranean relevance.
- Pautasso 2013: general review, no RS content.
- Fehr 2024, Alessi 2021: ecological field studies (useful for ecology section, not remote sensing).
- Welle 2022, Breidenbach 2020, Immitzer 2019, Grabska 2019/2020: confirmed as valid but temperate/boreal; keep as brief method citations only.
- Crop transferability papers: wrong domain.
- Giannetti 2018 and Puzzolo 2004: not rejected, but not verified; retrieve before citing.
- Persson 2018, Hoscilo 2019, Immitzer 2016, Ottosen 2020, Melaas 2013, Hermosilla 2016, Francini 2024 (Sensors): not re-checked this round; earlier rejection stands.

## D. Items that remain [still unverified]
- Senf 2015: study area (Portugal) and evergreen/deciduous classes.
- Roy 2016: magnitude of differences.
- Wulder 2021: full author list (Masek).
- Whether IUTI separates broadleaved evergreen forest.
- Everything depends on abstracts; full-text checks (accuracy by year, reference data) are pending for Atkins 2018, Hermosilla 2018/2024, Thapa 2020, Bonannella 2022, Agrillo 2021.
