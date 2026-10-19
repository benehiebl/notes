# Time-series change and trajectory analysis literature for 40 years of annual Landsat-derived cover-fraction maps (evergreen broad-leaved vegetation, Italy)

Method note: All bibliographic data below (authors, year, title, journal, volume, pages, DOI) were checked against the CrossRef API on 2026-10-16 (each DOI resolved to a record with matching title/authors/year). The "key finding" descriptions are from my background knowledge of these well-known papers; I did NOT re-read the full texts in this session (no page-fetch tool used), so statements about content are marked "(content from memory, not re-read)" and should be skimmed against the abstract before citing. Link format: https://doi.org/DOI.

## Q1. Which break/trend-detection algorithms for Landsat time series are the canonical citations, and what do they imply for annual maps?

### Takeaway
LandTrendr, CCDC and BFAST are designed for spectral (pixel-level) time series, not for already-classified annual maps; they are citable as methodological background and for the lesson that segmentation/breakpoint logic and temporal filtering are needed to separate real change from noise. The best conceptual bridge to annual maps is Pasquarella 2022 plus Cohen 2017 (algorithm disagreement).

### Cited Findings
- Kennedy, R.E., Yang, Z., Cohen, W.B. (2010). Detecting trends in forest disturbance and recovery using yearly Landsat time series: 1. LandTrendr - Temporal segmentation algorithms. Remote Sensing of Environment 114(12): 2897-2910. — [doi:10.1016/j.rse.2010.07.008](https://doi.org/10.1016/j.rse.2010.07.008). Fits piecewise linear segments to annual spectral trajectories to identify disturbance, recovery and stable periods; the foundational "trajectory" paper (content from memory, not re-read).
- Kennedy, R.E., Yang, Z., Gorelick, N., Braaten, J., et al. (2018). Implementation of the LandTrendr Algorithm on Google Earth Engine. Remote Sensing 10(5): 691. — [doi:10.3390/rs10050691](https://doi.org/10.3390/rs10050691). Describes GEE implementation and the segment-based outputs (magnitude, duration, rate) used in later work (content from memory). CrossRef lists more than four authors; full list [unverified].
- Zhu, Z., Woodcock, C.E. (2014). Continuous change detection and classification of land cover using all available Landsat data. Remote Sensing of Environment 144: 152-171. — [doi:10.1016/j.rse.2014.01.011](https://doi.org/10.1016/j.rse.2014.01.011). Harmonic regression per pixel with breaks on all observations, land cover updated after each break; explicitly models seasonality, which reduces observation-density/phenology artefacts (content from memory).
- Verbesselt, J., Hyndman, R., Newnham, G., Culvenor, D. (2010). Detecting trend and seasonal changes in satellite image time series. Remote Sensing of Environment 114(1): 106-115. — [doi:10.1016/j.rse.2009.08.014](https://doi.org/10.1016/j.rse.2009.08.014). BFAST: iterative decomposition into trend, season, remainder with breakpoint tests (content from memory).
- Pasquarella, V.J., Arevalo, P., Bratley, K.H., Bullock, E.L., et al. (2022). Demystifying LandTrendr and CCDC temporal segmentation. Int. J. Applied Earth Observation and Geoinformation 110: 102806. — [doi:10.1016/j.jag.2022.102806](https://doi.org/10.1016/j.jag.2022.102806). Compares the two segmentation approaches on equal footing and shows how parameter and input choices change outputs (content from memory; full author list [unverified] beyond those shown by CrossRef).
- Cohen, W.B., Healey, S.P., Yang, Z., Stehman, S.V., et al. (2017). How similar are forest disturbance maps derived from different Landsat time series algorithms? Forests 8(4): 98. — [doi:10.3390/f8040098](https://doi.org/10.3390/f8040098). Different algorithms give notably different disturbance maps; agreement is limited and omission is substantial (content from memory).
- Zhu, Z. (2017). Change detection using Landsat time series: A review of frequencies, preprocessing, algorithms, and applications. ISPRS J. Photogrammetry and Remote Sensing 130: 370-384. — [doi:10.1016/j.isprsjprs.2017.06.013](https://doi.org/10.1016/j.isprsjprs.2017.06.013). Review/taxonomy of Landsat time-series change algorithms.
- Woodcock, C.E., Loveland, T.R., Herold, M., Bauer, M.E. (2020). Transitioning from change detection to monitoring with remote sensing: A paradigm shift. Remote Sensing of Environment 238: 111558. — [doi:10.1016/j.rse.2019.111558](https://doi.org/10.1016/j.rse.2019.111558). Argues for continuous monitoring with full time series rather than bi-temporal comparison (content from memory).
- Verbesselt, J., Zeileis, A., Herold, M. (2012). Near real-time disturbance detection using satellite image time series. RSE 123: 98-108. — [doi:10.1016/j.rse.2012.02.022](https://doi.org/10.1016/j.rse.2012.02.022). BFAST Monitor; less relevant (near-real-time).
- Kennedy, R.E., Andrefouet, S., Cohen, W.B., Gomez, C., et al. (2014). Bringing an ecological view of change to Landsat-based remote sensing. Frontiers in Ecology and the Environment 12(6): 339-346. — [doi:10.1890/130066](https://doi.org/10.1890/130066). Argues for describing change as trajectories (abrupt, gradual, recovery) with ecological meaning rather than as two-date differences (content from memory).

### Inferences
- The user's inputs are annual classified cover/dominant-species maps, so LandTrendr/CCDC/BFAST cannot be applied directly to them; they could be applied to the underlying spectral series or to per-pixel cover-fraction series (LandTrendr accepts any annual index, including a fraction). Using LandTrendr-style segmentation on a fraction series is a defensible way to derive gain/loss/duration/rate per pixel, but the user must state that the input is a model output with its own error (see Q3).
- Cohen 2017 supports a methodological caveat: trajectory-derived "change" depends on the algorithm, so sensitivity tests on segmentation parameters are advisable.

### Gaps
- No fetch of full texts was done; exact numbers (agreement percentages etc.) deliberately omitted.
- I did not find (and do not assert) a paper applying LandTrendr specifically to evergreen-broadleaf encroachment in Mediterranean/Italian forests; not searched exhaustively.

## Q2. How should trajectories, trends and hotspots of annual cover maps be analysed (classification of trajectories, Mann-Kendall/Theil-Sen, hotspot statistics)?

### Takeaway
Trajectory typologies from annual maps are best grounded in Hermosilla 2015/2018 and Kennedy 2014; trend significance must account for autocorrelation (Hamed & Rao 1998, Yue 2002) and, for image series, spatial context (Neeti & Eastman 2011); hotspots are formalised by Getis-Ord Gi*.

### Cited Findings
- Hermosilla, T., Wulder, M.A., White, J.C., Coops, N.C., Hobart, G.W. (2015). Regional detection, characterization, and attribution of annual forest change from 1984 to 2012 using Landsat-derived time-series metrics. RSE 170: 121-132. — [doi:10.1016/j.rse.2015.09.004](https://doi.org/10.1016/j.rse.2015.09.004). Annual change detection, characterisation (type, year, magnitude) and attribution (e.g. fire, harvest) over a long record (content from memory).
- Hermosilla, T., Wulder, M.A., White, J.C., Coops, N.C., et al. (2018). Disturbance-informed annual land cover classification maps of Canada's forested ecosystems for a 29-year Landsat time series. Canadian Journal of Remote Sensing 44(1): 67-87. — [doi:10.1080/07038992.2018.1437719](https://doi.org/10.1080/07038992.2018.1437719). Uses detected disturbances to constrain annual land-cover labels so illogical transitions are suppressed; very close analogue to the user's annual-map setting (content from memory).
- Song, X.-P., Hansen, M.C., Stehman, S.V., Potapov, P.V., et al. (2018). Global land change from 1982 to 2016. Nature 560: 639-643. — [doi:10.1038/s41586-018-0411-9](https://doi.org/10.1038/s41586-018-0411-9). Annual global fractional-cover time series (tree, short vegetation, bare, water) from AVHRR/MODIS-based records; example of fractional-cover change accounting with sample-based area estimation (content from memory).
- Hansen, M.C., Potapov, P.V., Moore, R., Hancher, M., et al. (2013). High-resolution global maps of 21st-century forest cover change. Science 342(6160): 850-853. — [doi:10.1126/science.1244693](https://doi.org/10.1126/science.1244693). Landsat-based global tree-cover loss/gain; the benchmark for gain/loss on a continuous cover field, but only 2000-2012 and with loss/gain defined on thresholds.
- Sexton, J.O., Song, X.-P., Feng, M., Noojipady, P., et al. (2013). Global, 30-m resolution continuous fields of tree cover: Landsat-based rescaling of MODIS vegetation continuous fields with lidar-based estimates of error. Int. J. Digital Earth 6(5): 427-448. — [doi:10.1080/17538947.2013.786146](https://doi.org/10.1080/17538947.2013.786146). Relevant for treating tree-cover fractions as continuous fields with explicit error estimates.
- Mann, H.B. (1945). Nonparametric tests against trend. Econometrica 13(3): 245-259. — [doi:10.2307/1907187](https://doi.org/10.2307/1907187). Page range 245-259 is from Baldwin's note title in CrossRef; CrossRef item itself shows start page 245.
- Sen, P.K. (1968). Estimates of the regression coefficient based on Kendall's tau. J. American Statistical Association 63(324): 1379-1389. — [doi:10.1080/01621459.1968.10480934](https://doi.org/10.1080/01621459.1968.10480934).
- Hamed, K.H., Rao, A.R. (1998). A modified Mann-Kendall trend test for autocorrelated data. J. Hydrology 204(1-4): 182-196. — [doi:10.1016/S0022-1694(97)00125-X](https://doi.org/10.1016/s0022-1694(97)00125-x). Corrects the variance of S for serial correlation; standard fix when MK is applied to autocorrelated series (content from memory).
- Yue, S., Pilon, P., Phinney, B., Cavadias, G. (2002). The influence of autocorrelation on the ability to detect trend in hydrological series. Hydrological Processes 16(9): 1807-1829. — [doi:10.1002/hyp.1095](https://doi.org/10.1002/hyp.1095). Shows positive autocorrelation inflates false trend detection and that pre-whitening has its own power problems (content from memory).
- Neeti, N., Eastman, J.R. (2011). A contextual Mann-Kendall approach for the assessment of trend significance in image time series. Transactions in GIS 15(5): 599-611. — [doi:10.1111/j.1467-9671.2011.01280.x](https://doi.org/10.1111/j.1467-9671.2011.01280.x). Incorporates neighbouring pixels to handle spatial dependence of significance in image series (content from memory).
- Getis, A., Ord, J.K. (1992). The analysis of spatial association by use of distance statistics. Geographical Analysis 24(3): 189-206. — [doi:10.1111/j.1538-4632.1992.tb00261.x](https://doi.org/10.1111/j.1538-4632.1992.tb00261.x). Origin of Gi/Gi* hotspot statistic.
- de Jong, R., de Bruin, S., de Wit, A., Schaepman, M.E., Dent, D.L. (2011). Analysis of monotonic greening and browning trends from global NDVI time-series. RSE 115(2): 692-702. — [doi:10.1016/j.rse.2010.10.011](https://doi.org/10.1016/j.rse.2010.10.011). Shows trend results depend on method and that monotonic trend tests miss breaks (content from memory).
- de Jong, R., Verbesselt, J., Schaepman, M.E., de Bruin, S. (2012). Trend changes in global greening and browning: contribution of short-term trends to longer-term change. Global Change Biology 18(2): 642-655. — [doi:10.1111/j.1365-2486.2011.02578.x](https://doi.org/10.1111/j.1365-2486.2011.02578.x). CrossRef "issued" year for the record is 2011 (online); journal volume 18 is 2012; cite as 2012.
- Pettorelli et al. (2005), TREE 20(9): 503-510, [doi:10.1016/j.tree.2005.05.011](https://doi.org/10.1016/j.tree.2005.05.011) — NDVI/ecology overview; peripheral.

### Inferences
- With ~40 annual values per pixel, serial autocorrelation in a cover-fraction series is likely strong (cover changes persist), so unadjusted MK p-values are probably too optimistic; use Hamed-Rao or block/pre-whitened variants and report Sen slopes as descriptive (inference, not directly demonstrated for these maps).
- MK/Sen assume monotonic change; abrupt dieback followed by regrowth (expected for Quercus ilex dieback) is better described by segmented trajectories (Kennedy 2010/2014) than by a single slope.
- Getis-Ord Gi* requires choice of neighbourhood and is sensitive to map-error spatial structure; apply to change counts/probabilities rather than raw slopes with unknown error.

### Gaps
- Did not verify any paper that applies Gi* or MK specifically to categorical annual species-dominance maps; there appears to be little guidance for categorical series (the user's DTS maps), where transition-based statistics (Q3) are more appropriate.
- Original Theil (1950) citation not verified; Sen 1968 is verified and sufficient.

## Q3. How should uncertainty, error propagation and temporal consistency in change from classified annual maps be handled?

### Takeaway
Change estimated by differencing independent classified maps is dominated by classification error unless corrected; the key references are Olofsson 2013/2014 (sample-based change area with confidence intervals), Pontius & Lippitt 2006 (can error explain apparent change), and HMM/temporal-consistency papers (Abercrombie & Friedl 2016, Gong 2017, Bogaert 2022).

### Cited Findings
- Olofsson, P., Foody, G.M., Stehman, S.V., Woodcock, C.E. (2013). Making better use of accuracy data in land change studies: Estimating accuracy and area and quantifying uncertainty using stratified estimation. RSE 129: 122-131. — [doi:10.1016/j.rse.2012.10.031](https://doi.org/10.1016/j.rse.2012.10.031). Error-matrix-based adjusted area estimates with standard errors; map-pixel counting is biased (content from memory).
- Olofsson, P., Foody, G.M., Herold, M., Stehman, S.V., Woodcock, C.E., Wulder, M.A. (2014). Good practices for estimating area and assessing accuracy of land change. RSE 148: 42-57. — [doi:10.1016/j.rse.2014.02.015](https://doi.org/10.1016/j.rse.2014.02.015). Recommended design for change accuracy (sampling, response design, estimators); rare-change classes need stratification (content from memory). Sixth author Wulder confirmed only as "et al." by CrossRef display; author list otherwise [unverified].
- Stehman, S.V., Foody, G.M. (2019). Key issues in rigorous accuracy assessment of land cover products. RSE 231: 111199. — [doi:10.1016/j.rse.2019.05.018](https://doi.org/10.1016/j.rse.2019.05.018).
- Pontius, R.G., Lippitt, C.D. (2006). Can error explain map differences over time? Cartography and Geographic Information Science 33(2): 159-171. — [doi:10.1559/152304006777681706](https://doi.org/10.1559/152304006777681706). Methodological test of whether observed map change exceeds what classification error could create (content from memory).
- Pontius, R.G., Shusas, E., McEachern, M. (2004). Detecting important categorical land changes while accounting for persistence. Agriculture, Ecosystems & Environment 101(2-3): 251-268. — [doi:10.1016/j.agee.2003.09.008](https://doi.org/10.1016/j.agee.2003.09.008). Transition matrices, gross gains/losses vs net change, persistence.
- Aldwaik, S.Z., Pontius, R.G. (2012). Intensity analysis to unify measurements of size and stationarity of land changes by interval, category, and transition. Landscape and Urban Planning 106(1): 103-114. — [doi:10.1016/j.landurbplan.2012.02.010](https://doi.org/10.1016/j.landurbplan.2012.02.010). Framework to test whether a category gains/loses faster or slower than uniform; natural fit for "is evergreen gain targeting particular deciduous classes".
- Abercrombie, S.P., Friedl, M.A. (2016). Improving the consistency of multitemporal land cover maps using a hidden Markov model. IEEE Trans. Geoscience and Remote Sensing 54(2): 703-713. — [doi:10.1109/TGRS.2015.2463689](https://doi.org/10.1109/tgrs.2015.2463689). Applies an HMM with class transition probabilities to class-probability time series to remove spurious flips (content from memory).
- Gong, J., Fang, H., Yang, J., Ge, ? (2017). Using a hidden Markov model for improving the spatial-temporal consistency of time series land cover classification. ISPRS Int. J. Geo-Information 6(10): 292. — [doi:10.3390/ijgi6100292](https://doi.org/10.3390/ijgi6100292). Given names/exact full author list [unverified]; CrossRef shows surnames Gong, Fang, Yang, Ge. Verify before citing.
- Bogaert, Lamarche, Defourny (2022). Hidden Markov models for annual land cover mapping - increasing temporal consistency and completeness. IEEE TGRS 60: 1-14 (article number not verified). — [doi:10.1109/TGRS.2021.3123738](https://doi.org/10.1109/tgrs.2021.3123738). Given names [unverified]. Directly on annual maps; good for method justification.
- Gomez, C., White, J.C., Wulder, M.A. (2016). Optical remotely sensed time series data for land cover classification: A review. ISPRS J. Photogramm. Remote Sens. 116: 55-72. — [doi:10.1016/j.isprsjprs.2016.03.008](https://doi.org/10.1016/j.isprsjprs.2016.03.008).
- Lu, D., Mausel, P., Brondizio, E., Moran, E. (2004). Change detection techniques. Int. J. Remote Sensing 25(12): 2365-2401. — [doi:10.1080/0143116031000139863](https://doi.org/10.1080/0143116031000139863). Classic review of post-classification comparison error accumulation; dated.
- Already in wiki and relevant: senf_2021_disturbance (Senf & Seidl 2021, Nature Sustainability 4(1): 63-70, [doi:10.1038/s41893-020-00609-y](https://doi.org/10.1038/s41893-020-00609-y), CrossRef-verified), pflugmacher_2019_lulc_landsat, hermosilla-type annual-map workflow.

### Inferences
- If the annual LTC/DTS maps are produced independently each year, year-to-year noise will inflate gross change (apparent flip-flops); apply temporal filtering/HMM or at minimum report persistence-based change rather than raw per-year differences.
- Reporting evergreen gain/loss areas should use Olofsson-style adjusted areas with confidence intervals, which requires multi-year reference data (a gap for historical decades where no reference exists; hindcasting error is not covered by these papers).
- An HMM used for smoothing (Abercrombie & Friedl) is conceptually distinct from an HMM used for forecasting; do not conflate in the paper.

### Gaps
- No paper found on error propagation specific to annual species-dominance maps over 40 years with changing sensor/observation density; Bell 2024 (hindcasting, in wiki) is the nearest.
- Exact Gong and Bogaert given names/page data unverified.

## Q4. Observation-density artefacts and spatial autocorrelation in driver regression

### Takeaway
Bayle 2024 (already in wiki) is the key warning on Landsat trend artefacts; for driver analysis, spatial autocorrelation must be handled following Dormann 2007 and Beale 2010.

### Cited Findings
- Bayle et al. 2024, Ecography e07394 — already in wiki as bayle_2024_landsat_greening_inflated; DOI not re-checked here [unverified].
- Dormann, C.F., McPherson, J.M., Araujo, M.B., Bivand, R., et al. (2007). Methods to account for spatial autocorrelation in the analysis of species distributional data: a review. Ecography 30(5): 609-628. — [doi:10.1111/j.2007.0906-7590.05171.x](https://doi.org/10.1111/j.2007.0906-7590.05171.x). Compares SAC-handling methods (SAR, GAM, GEE, autocovariate); SAC inflates significance and can alter coefficient estimates (content from memory).
- Beale, C.M., Lennon, J.J., Yearsley, J.M., Brewer, M.J., Elston, D.A. (2010). Regression analysis of spatial data. Ecology Letters 13(2): 246-264. — [doi:10.1111/j.1461-0248.2009.01422.x](https://doi.org/10.1111/j.1461-0248.2009.01422.x). Warns that methods differ in estimated coefficients and recommends reporting and comparing approaches (content from memory).

### Inferences
- With millions of pixels, p-values are meaningless without SAC treatment; use block/subsampled sampling, spatial cross-validation or mixed models and report effect sizes (inference).
- Observation-density artefact: Bayle's finding concerns NDVImax; whether it transfers to classifier-derived cover fractions is untested; CCDC-style harmonic modelling or per-year observation-count covariates can check this.

### Gaps
- No verified paper quantifying observation-density effects on classified species maps.
- Gascoin/Berner-related follow-ups not searched.

## Q5. Markov/HMM forecasting, space-for-time substitution and future habitat projection

### Takeaway
Markov chains are easy but stationary and memoryless, so forecasts are unreliable under climate non-stationarity; space-for-time (SFT) is useful but contested; future habitat is typically done with SDM-type models whose limits are reviewed by Elith & Leathwick 2009.

### Cited Findings
- Balzter, H. (2000). Markov chain models for vegetation dynamics. Ecological Modelling 126(2-3): 139-154. — [doi:10.1016/S0304-3800(00)00262-3](https://doi.org/10.1016/s0304-3800(00)00262-3). Introduces extensions (non-stationary, covariate-dependent, spatial) to Markov chain vegetation models (content from memory).
- Blois, J.L., Williams, J.W., Fitzpatrick, M.C., Jackson, S.T., Ferrier, S. (2013). Space can substitute for time in predicting climate-change effects on biodiversity. PNAS 110(23): 9374-9379. — [doi:10.1073/pnas.1220228110](https://doi.org/10.1073/pnas.1220228110). Pollen-based test: SFT works reasonably for some responses but fails under no-analog climates and with lagged responses (content from memory).
- Damgaard, C. (2019). A critique of the space-for-time substitution practice in community ecology. Trends in Ecology & Evolution 34(5): 416-421. — [doi:10.1016/j.tree.2019.01.013](https://doi.org/10.1016/j.tree.2019.01.013). SFT requires equilibrium and identical dynamics assumptions (content from memory).
- Pickett, S.T.A. (1989). Space-for-time substitution as an alternative to long-term studies. In: Likens (ed.) Long-Term Studies in Ecology, Springer, pp. 110-135. — [doi:10.1007/978-1-4615-7358-6_5](https://doi.org/10.1007/978-1-4615-7358-6_5). Book chapter, not a journal paper.
- Fukami, T., Wardle, D.A. (2005). Long-term ecological dynamics: reciprocal insights from natural and anthropogenic gradients. Proc. R. Soc. B 272(1577): 2105-2115. — [doi:10.1098/rspb.2005.3277](https://doi.org/10.1098/rspb.2005.3277). Discusses limits of chronosequences; peripheral.
- Elith, J., Leathwick, J.R. (2009). Species distribution models: ecological explanation and prediction across space and time. Annu. Rev. Ecol. Evol. Syst. 40: 677-697. — [doi:10.1146/annurev.ecolsys.110308.120159](https://doi.org/10.1146/annurev.ecolsys.110308.120159). Extrapolation, equilibrium and no-analog caveats for future habitat prediction (content from memory).

### Inferences
- A climate-covariate-driven (non-homogeneous) HMM/Markov model using the 40-year transition record is a time-for-time approach and avoids pure SFT, but it extrapolates past transition rates (that include dieback and land-abandonment dynamics) into a future with different climate; validate by hindcast (fit on 1985-2005, predict 2006-2024).
- Using spatial climate gradients to forecast (SFT) should cite Blois 2013 and Damgaard 2019 and be framed as a sensitivity comparison.

### Gaps
- No peer-reviewed paper found/verified that uses HMM or Markov chains to forecast forest species-dominance transitions with climate covariates; Balzter 2000 is the best verified methodological anchor. Verified-existence search for Mediterranean evergreen oak land-cover trajectories gave only Costa et al. 2011 (Landscape and Urban Planning 102(3): 164-176, [doi:10.1016/j.landurbplan.2011.04.002](https://doi.org/10.1016/j.landurbplan.2011.04.002)), a landscape-change study in SW Iberia, not read.
- CA-Markov land-use modelling papers surfaced were low quality; not recommended.

## Q6. Ranked shortlist (15) and rejected papers

### Takeaway
Deep-read priority is below; ranking reflects direct usefulness for annual-map trajectory/hotspot/driver/forecast analysis.

### Cited Findings
Ranked (D = deep read, S = skim/cite only):
1. Olofsson et al. 2014 RSE 148:42-57 (D) - area/uncertainty of change; essential. [doi](https://doi.org/10.1016/j.rse.2014.02.015)
2. Hermosilla et al. 2018 CJRS 44:67-87 (D) - closest annual-map precedent. [doi](https://doi.org/10.1080/07038992.2018.1437719)
3. Pasquarella et al. 2022 JAG 110:102806 (D) - segmentation choices. [doi](https://doi.org/10.1016/j.jag.2022.102806)
4. Kennedy et al. 2010 RSE 114:2897-2910 (D) - trajectory foundation. [doi](https://doi.org/10.1016/j.rse.2010.07.008)
5. Abercrombie & Friedl 2016 TGRS 54:703-713 (D) - HMM temporal consistency. [doi](https://doi.org/10.1109/tgrs.2015.2463689)
6. Bogaert et al. 2022 TGRS 60 (D) - HMM annual maps. [doi](https://doi.org/10.1109/tgrs.2021.3123738)
7. Pontius & Lippitt 2006 CaGIS 33:159-171 (D) - can error explain change. [doi](https://doi.org/10.1559/152304006777681706)
8. Zhu & Woodcock 2014 RSE 144:152-171 (S/D) - CCDC. [doi](https://doi.org/10.1016/j.rse.2014.01.011)
9. Hamed & Rao 1998 J Hydrol 204:182-196 (S) - MK autocorrelation. [doi](https://doi.org/10.1016/s0022-1694(97)00125-x)
10. Yue et al. 2002 Hydrol Process 16:1807-1829 (S). [doi](https://doi.org/10.1002/hyp.1095)
11. Neeti & Eastman 2011 Trans GIS 15:599-611 (S) - spatially contextual MK. [doi](https://doi.org/10.1111/j.1467-9671.2011.01280.x)
12. Blois et al. 2013 PNAS 110:9374-9379 (D) - SFT. [doi](https://doi.org/10.1073/pnas.1220228110)
13. Damgaard 2019 TREE 34:416-421 (S). [doi](https://doi.org/10.1016/j.tree.2019.01.013)
14. Dormann et al. 2007 Ecography 30:609-628 (S). [doi](https://doi.org/10.1111/j.2007.0906-7590.05171.x)
15. Balzter 2000 Ecol Model 126:139-154 (S) - Markov vegetation. [doi](https://doi.org/10.1016/s0304-3800(00)00262-3)
16. Aldwaik & Pontius 2012 LUP 106:103-114 (S) - intensity analysis. [doi](https://doi.org/10.1016/j.landurbplan.2012.02.010)
17. Kennedy et al. 2018 Remote Sens 10:691 (S) - GEE LandTrendr. [doi](https://doi.org/10.3390/rs10050691)
18. Verbesselt et al. 2010 RSE 114:106-115 (S) - BFAST. [doi](https://doi.org/10.1016/j.rse.2009.08.014)
19. Song et al. 2018 Nature 560:639-643 (S) - fractional-cover change. [doi](https://doi.org/10.1038/s41586-018-0411-9)
20. Cohen et al. 2017 Forests 8:98 (S) - algorithm disagreement. [doi](https://doi.org/10.3390/f8040098)
Also useful: Getis & Ord 1992 (Geographical Analysis 24:189-206), Beale 2010, Elith & Leathwick 2009, Kennedy 2014, Woodcock 2020, Pickett 1989 (chapter).

Rejected / deprioritised:
- Verbesselt et al. 2012 (BFAST Monitor) - near-real-time, not retrospective trajectory analysis.
- Hansen 2013 as a main reference - 2000-2012 only, binary loss/gain; cite only as a benchmark.
- Lu et al. 2004 - dated review, superseded by Zhu 2017/Woodcock 2020.
- Pettorelli 2005 - NDVI ecology overview, not change methodology.
- Fukami & Wardle 2005 - peripheral to SFT.
- CA-Markov/ANN land-use forecasting papers found by search (e.g. Choudhary et al. 2025; Kusratmoko 2017) - regional case studies, methodologically weak, not read; rejected.
- Mann 1945 / Sen 1968 - cite only if trend tests are used; classical not "deep reading".
- Faculty Opinions entries and preprint duplicates (e.g. bioRxiv version of Senf & Seidl) - not citable.
- Bayle 2024 - already in wiki (not re-evaluated; DOI [unverified] here).

### Inferences
- Core methodological story for the paper: (1) temporal consistency (HMM, Q3), (2) adjusted change areas with uncertainty (Olofsson), (3) trajectory typology (Kennedy/Hermosilla), (4) autocorrelation-aware trend and driver tests (Hamed-Rao, Dormann), (5) hindcast-validated forecasting (Balzter, Elith & Leathwick) with SFT caveats (Blois, Damgaard).

### Gaps
- Open web fetch/full-text reading was not performed; all "key findings" need abstract-level confirmation before they are used in claims.
- Not covered: Italy-specific evergreen-expansion or Q. ilex dieback trajectory studies (other researchers' scope).
