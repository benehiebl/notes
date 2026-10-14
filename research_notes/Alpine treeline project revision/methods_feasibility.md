# Feasibility of remote-sensing and modelling methods for Alpine treeline monitoring (Alps-focused)

Verification legend: VERIFIED = metadata confirmed via Crossref API (api.crossref.org) and/or publisher page fetched on 2026-10-13. UNVERIFIED = could not confirm; do not cite without checking. "Content not read" = only metadata/abstract-level checked.

## 1. Landsat (30 m) detection of treeline / forestline shift

### Takeaway
Landsat cannot resolve an individual treeline shift of 0.2-0.5 m/yr (10-20 m over 40 yr, less than one 30 m pixel) as a line displacement. What Landsat can do is detect greenness/wetness trends in buffer zones along a *forestline* (closed forest limit) and flag hotspots, which is exactly (and only) what Baglioni et al. 2025 did. Note also that the newest Alps evidence reports much faster shifts (about 1.1-1.6 m/yr) than the proposal assumes, driven mostly by land abandonment, which changes the detectability calculus and the attribution framing.

### Cited Findings
- Baglioni et al. 2025 (title is "Forestlines in Italian mountains are shifting upward: detection and monitoring using satellite time series"; authors Baglioni, Morresi, Garbarino, Urbinati, Lingua, Marzano, Vitali; Biogeosciences 22(17):4349-4366) is verified: pages 4349-4366, published 4 Sept 2025. — [doi:10.5194/bg-22-4349-2025](https://doi.org/10.5194/bg-22-4349-2025) (publisher page fetched)
- What it did: Landsat TM/ETM+/OLI/OLI-2 (30 m), 1 June - 30 Sept, medoid composites, 1984-2023, contextual Mann-Kendall trend test on greenness and wetness (Tasseled-cap) in buffer zones along forestlines; forestline = "line separating the closed forest from the shrubland and grassland above" (not the treeline of single trees); the ecotone pattern itself was not analysed. — [doi:10.5194/bg-22-4349-2025](https://doi.org/10.5194/bg-22-4349-2025)
- What it reported: mean forestline elevation 2088 +/- 193 m (Alps) and 1758 +/- 161 m (Apennines), maxima 2500 m and 2383 m; forest expansion mostly near the forestline and at lower elevations; trends are given as Mann-Kendall tau, NOT as m/yr. GAM relationships between trend and elevation/distance to forestline were not statistically significant. — [doi:10.5194/bg-22-4349-2025](https://doi.org/10.5194/bg-22-4349-2025)
- Sub-pixel handling: the forestline reference is derived from the Copernicus Tree Cover Density layer (10 m, resampled to 30 m by averaging); the authors state a possible spatial mismatch between resampled TCD and Landsat was ignored; no further sub-pixel method; no independent accuracy assessment of the detected forestline (only the TCD product's stated >=90% accuracy cited). Snow-covered pixels were masked; Landsat 7 SLC-off is not discussed; 1-year gaps interpolated, longer gaps discarded. — [doi:10.5194/bg-22-4349-2025](https://doi.org/10.5194/bg-22-4349-2025)
- Earlier Baglioni/Morresi EGU conference abstract (EGU24-15620, "Forestline detection and treeline ecotone dynamics in the Italian Alps and Apennines by satellite remote sensing") is NOT the Biogeosciences paper; do not cite it as such. — [doi:10.5194/egusphere-egu24-15620](https://doi.org/10.5194/egusphere-egu24-15620)
- Garbarino, Morresi, Anselmetto & Weisberg 2023, Remote Sens. Ecol. Conserv. 9(6):729-742: meta-analysis; only ~10% of treeline studies use remote sensing; monitoring studies use coarser resolution over longer time spans; long-term shifts are usually measured with aerial/oblique photography by photo-interpretation; recent dynamics via greenness trends from pixel-based satellite classification; UAV/LiDAR for tree-scale metrics; argues for multi-scale, multi-sensor, 2-D ecotone monitoring (only 19% of papers multi-scale). — [doi:10.1002/rse2.351](https://doi.org/10.1002/rse2.351)
- Carrieri et al. 2026 (bioRxiv PREPRINT, not peer-reviewed): nine Italian Alps sites, aerial imagery 1954 vs 2017; timberline moved upslope about 1.6 m/yr, tree species line about 1.1 m/yr; ecotone surface shrank about 17%; land-use variables explained more variance than climate ("Treeline ecotone habitat loss and upward shift is driven by land abandonment rather than climate change in the Italian Alps"; authors per page: Carrieri, Nguyen Ha, Meloni, Anselmetto, Morresi, Garbarino). Imagery resolution not stated on the abstract page. — [doi:10.64898/2026.09.30.755293](https://doi.org/10.64898/2026.09.30.755293) (Crossref lists author "Nguyen H"; fetched page says "Trang Nguyen Ha"; check final author names)
- Swiss historical benchmark: Gehrig-Fasel, Guisan & Zimmermann 2007, J. Veg. Sci. 18(4):571-582, "Tree line shifts in the Swiss Alps: Climate change or land abandonment?" (aerial-photo/ map based, land-abandonment emphasis; content not read). — [doi:10.1111/j.1654-1103.2007.tb02571.x](https://doi.org/10.1111/j.1654-1103.2007.tb02571.x)
- Nguyen, Kellenberger & Tuia 2022, Remote Sens. Environ. 281:113217, "Mapping forest in the Swiss Alps treeline ecotone with explainable deep learning" (deep learning on very-high-resolution imagery; content not read). — [doi:10.1016/j.rse.2022.113217](https://doi.org/10.1016/j.rse.2022.113217)
- Nguyen, Rußwurm, Kellenberger & Tuia 2023, EGU23-8798 conference abstract "Mapping forest cover dynamics in the Swiss Alps using 70 years of aerial imagery". A peer-reviewed 2024 Swiss follow-up named in the brief was NOT found: UNVERIFIED. — [doi:10.5194/egusphere-egu23-8798](https://doi.org/10.5194/egusphere-egu23-8798)
- Wallentin, Tappeiner, Strobl & Tasser 2008, Ecol. Model. 218(3-4):235-246, "Understanding alpine tree line dynamics: An individual-based model" (Austria/Tyrol; modelling, not remote sensing). — [doi:10.1016/j.ecolmodel.2008.07.005](https://doi.org/10.1016/j.ecolmodel.2008.07.005)
- Tasser et al. 2007, Agric. Ecosyst. Environ. 118(1-4):115-129, "Land-use changes and natural reforestation in the Eastern Central Alps" (Tyrol; land-use driver of reforestation). — [doi:10.1016/j.agee.2006.05.004](https://doi.org/10.1016/j.agee.2006.05.004)
- Dirnböck, Dullinger & Grabherr 2003, J. Biogeogr. 30(3):401-417 (Austria; regional impact of climate and land-use change on alpine vegetation). — [doi:10.1046/j.1365-2699.2003.00839.x](https://doi.org/10.1046/j.1365-2699.2003.00839.x)
- Pellissier et al. 2013, Appl. Veg. Sci. 16(2):227-236, forest regrowth in mountain grasslands (Swiss Alps). Crossref lists year 2012 (online); issue year is 2013. — [doi:10.1111/j.1654-109x.2012.01215.x](https://doi.org/10.1111/j.1654-109x.2012.01215.x)
- Vitasse et al. 2021, Biol. Rev. 96(5):1816-1835, elevational/phenological shifts in the European Alps (review). — [doi:10.1111/brv.12727](https://doi.org/10.1111/brv.12727)
- Harsch et al. 2009, Ecol. Lett. 12(10):1040-1049, global treeline meta-analysis. — [doi:10.1111/j.1461-0248.2009.01355.x](https://doi.org/10.1111/j.1461-0248.2009.01355.x)
- Time-series / harmonisation methods: Zhu & Woodcock 2014 CCDC, Remote Sens. Environ. 144:152-171 — [doi:10.1016/j.rse.2014.01.011](https://doi.org/10.1016/j.rse.2014.01.011); Claverie et al. 2018 HLS, Remote Sens. Environ. 219:145-161 — [doi:10.1016/j.rse.2018.09.002](https://doi.org/10.1016/j.rse.2018.09.002)
- Other Alps Landsat context (conference abstracts only, not peer-reviewed): Morresi et al. 2023 EGU23-14563 "Reconstructing forest dynamics in the European Alps through a high-dimensional analysis based on Landsat time series" — [doi:10.5194/egusphere-egu23-14563](https://doi.org/10.5194/egusphere-egu23-14563)
- Global Landsat treeline dynamics: Wei & Wilson 2024 "Global Alpine Treeline Ecotone Dynamics (1985-2020)" is an EarthArXiv/ESSOAr PREPRINT; status unknown. — [doi:10.22541/essoar.171629996.63843956/v1](https://doi.org/10.22541/essoar.171629996.63843956/v1)
- Topographic-correction literature exists (e.g. Jiang et al. 2022, Remote Sens. 14(13):3073, integrated SCS+C correction for mountain vegetation monitoring; content not read, not Alps-specific) — [doi:10.3390/rs14133073](https://doi.org/10.3390/rs14133073)

### Inferences
- Arithmetic: 0.2-0.5 m/yr x 40 yr = 8-20 m < 30 m pixel. A line-displacement approach on Landsat is infeasible; this is a physics-of-sampling limit, not a processing problem. Even at 1.1-1.6 m/yr (Carrieri 2026 preprint) the 40-yr shift is 44-64 m, about 1.5-2 pixels, still at the edge of detectability once geolocation error (about 10-15 m for Landsat) and mixed pixels are included.
- Baglioni et al. do not contradict this, because they never measure displacement; they detect greenness/wetness trend hotspots near a mapped forestline. The proposal should phrase Landsat as "trend hotspot / densification detection", not "treeline shift measurement".
- The treeline (isolated individuals, krummholz) is below Landsat's detection scale; only closed-forest forestline is a defensible Landsat target. A forestline derived from a 10 m TCD product is a circular reference if the same forestline is used both as mask and as validation.
- The proposal's 0.2-0.5 m/yr assumption should be reconciled with the Italian 1.1-1.6 m/yr figures (different definition: timberline vs treeline; different sites; preprint). Cite as a range with definitions, not a single rate. Treat the Carrieri preprint as provisional.
- Practical redesign: use Sentinel-2 (10 m) / HLS for post-2015 structure, aerial orthophoto series (1950s-present, Swiss/Austrian/Italian archives) plus deep learning (Nguyen 2022 style) for long-term line displacement, and Landsat only for greenness trends and disturbance. Expect snow, shadow and topographic effects at 30 m (the Baglioni paper only masks snow and notes TCW is weakly topography-dependent in closed conifer stands); apply topographic correction and snow masking explicitly. Landsat 7 SLC-off handling and sensor harmonisation (TM/ETM+/OLI) should be stated explicitly because the Baglioni paper does not discuss SLC.

### Gaps
- No verified Alps study of Landsat minimum-NDVI treeline definitions or sub-pixel unmixing at treeline found; no verified Tyrol/Austria Landsat land-cover-change paper found in searches (search returned irrelevant items).
- Gehrig-Fasel 2007 and Nguyen 2022 content (resolution, shift rates) not read; only metadata verified.
- Bolton (named in brief): no Alps treeline paper found; only unrelated boreal fire-recovery Landsat paper (Bolton, Coops & Wulder 2015, [doi:10.1016/j.rse.2015.03.004](https://doi.org/10.1016/j.rse.2015.03.004)) surfaced. Treat as UNVERIFIED relevance.
- Garbarino, Lingua and Vitasse Alps shift-rate papers beyond those listed not individually verified.
- Quantitative simulation of detectability (Landsat registration error, mixed pixels) not found in literature; would need own analysis.

## 2. Spectral indices (NDVI/NBR/TCW) for stress in sparse tree islands; Sentinel-2 drought anomalies

### Takeaway
At 30 m a sparse tree island (crowns <1-5 m) occupies a small fraction of a pixel, so NDVI/NBR/TCW responses are dominated by grass/dwarf-shrub/rock/snow background; stress detection in sparse treeline stands is not defensible with Landsat. Sentinel-2 (10 m, red-edge) is better but still coarser than most individual treeline crowns. No Austria-specific subalpine Sentinel-2 drought-anomaly study for 2018/2019/2022 was found.

### Cited Findings
- Baglioni et al. 2025 found greenness and wetness trends are separable by canopy class (sparse vs dense) near the forestline, but only for closed-forest-adjacent buffers; GAMs vs elevation/distance were not significant. — [doi:10.5194/bg-22-4349-2025](https://doi.org/10.5194/bg-22-4349-2025)
- Austria-wide Sentinel-2 forest disturbance mapping exists as conference output only: Löw & Koukal 2021 EGU21-7795, "Forest Disturbance Mapping with Sentinel-2 Time Series in Austria" (abstract). — [doi:10.5194/egusphere-egu21-7795](https://doi.org/10.5194/egusphere-egu21-7795); and Löw & Koukal 2020 preprint (Research Square) [doi:10.21203/rs.3.rs-26379/v1](https://doi.org/10.21203/rs.3.rs-26379/v1) (preprint; status unknown).
- Drought-bark beetle link in Austrian Norway spruce: Netherer et al. 2021, J. Pest Sci. 94(3):591-614 (review of spruce-Ips-fungi interactions in times of drought; lowland/montane spruce, not treeline). — [doi:10.1007/s10340-021-01341-y](https://doi.org/10.1007/s10340-021-01341-y)
- European 2018 drought impacts on ecosystems: Bastos et al. 2020 appears as EGU abstract; the Science Advances paper itself was not retrieved in this session: UNVERIFIED (do not cite from this note).
- Web search (non-systematic) found Sentinel-2 spruce bark-beetle stress studies in Wallonia/France, Sweden and Czechia after 2018, with red-edge-based indices (e.g. CCI) most sensitive in Sweden; none for Austrian subalpine stands (search-engine summary, primary papers not individually verified here).

### Inferences
- Mixed-pixel dilution means a stressed tree island changes pixel NDVI by a small, noisy amount versus interannual grass phenology and snow-melt timing; detection requires UAV/aerial pixel sizes (<=10 cm to 1 m) or Sentinel-2 only for closed/dense stands.
- Use red-edge indices (Sentinel-2 B5-B7: CIre, NDRE) and a per-pixel seasonal baseline (modelled expected trajectory) rather than raw NDVI anomaly; limit to pixels with >=50% (suggested threshold, not literature-derived) tree cover.
- Drought years 2018/2019/2022: state as hypothesis to test; no verified subalpine evidence in this note.

### Gaps
- No peer-reviewed, DOI-verified Austrian subalpine Sentinel-2 anomaly paper for 2018/2019/2022.
- Quantitative sensitivity of NBR/TCW to sparse-canopy stress not found.

## 3. UAV-based SIF at treeline

### Takeaway
UAV SIF is an emerging, technically demanding method with proven prototypes on crops and a few forests, but monthly UAV SIF on conifer crowns in steep Alpine terrain is not realistic as a robust monitoring design without major redesign; use PRI/red-edge/thermal from standard multispectral/hyperspectral UAV payloads as the primary stress indicators, with SIF as a small pilot or tower-based spot measurement.

### Cited Findings
- Bendig, Malenovsky, Gautam & Lucieer 2020, IEEE Trans. Geosci. Remote Sens. 58(5):3437-3444, "Solar-Induced Chlorophyll Fluorescence Measured From an Unmanned Aircraft System: Sensor Etaloning and Platform Motion Correction". NOTE: journal is IEEE TGRS, NOT "Remote Sensing" as in the brief. Metadata verified; paper content not read (title indicates two correction problems: sensor etaloning, platform motion). — [doi:10.1109/TGRS.2019.2956194](https://doi.org/10.1109/TGRS.2019.2956194)
- Vargas, Bendig, Mac Arthur et al. 2020, Remote Sens. 12(10):1624, "Unmanned Aerial Systems (UAS)-Based Methods for Solar Induced Chlorophyll Fluorescence (SIF) Retrieval with Non-Imaging Spectrometers: State of the Art" (review; metadata verified, content not read). — [doi:10.3390/rs12101624](https://doi.org/10.3390/rs12101624)
- The brief's "Springer chapter 2024 UAV-borne SIF boreal site" is VERIFIED: Honkanen, Heikkinen, MacArthur, Thum, Kivi, Lindqvist, "UAV-Borne Measurements of Solar-Induced Chlorophyll Fluorescence (SIF) at a Boreal Site", in: New Developments and Environmental Applications of Drones (Springer), pp. 115-135; online 29 Sept 2023, print year 2024. Content/abstract could not be fetched (Springer redirect) so findings are UNREAD. — [doi:10.1007/978-3-031-44607-8_8](https://doi.org/10.1007/978-3-031-44607-8_8)
- Airborne (manned) imaging SIF: Siegmann et al. 2019 HyPlant, Remote Sens. 11(23):2760 — [doi:10.3390/rs11232760](https://doi.org/10.3390/rs11232760); Siegmann et al. 2021 downscaling canopy-to-leaf SIF with HyPlant (crops), Remote Sens. Environ. 264:112609 — [doi:10.1016/j.rse.2021.112609](https://doi.org/10.1016/j.rse.2021.112609)
- UAV hyperspectral/fluorescence for stress: Zarco-Tejada, González-Dugo & Berni 2012, Remote Sens. Environ. 117:322-337 (water-stress detection with micro-hyperspectral UAV; crops) — [doi:10.1016/j.rse.2011.10.007](https://doi.org/10.1016/j.rse.2011.10.007); Hornero et al. 2021, Remote Sens. Environ. 263:112570 (oak decline, Phytophthora; trees, Mediterranean) — [doi:10.1016/j.rse.2021.112570](https://doi.org/10.1016/j.rse.2021.112570)
- SIF seasonality in evergreen conifers: Magney et al. 2019, PNAS 116(24):11640-11645 (SIF tracks photosynthesis seasonality in evergreen conifers, mechanistically; content not read in detail) — [doi:10.1073/pnas.1900278116](https://doi.org/10.1073/pnas.1900278116)
- PRI in conifers: Gamon & Bond 2013, Remote Sens. Environ. 135:141-149 (PRI in Douglas-fir/ponderosa pine affected by irradiance and downregulation) — [doi:10.1016/j.rse.2013.03.032](https://doi.org/10.1016/j.rse.2013.03.032); Garbulsky et al. 2011 PRI review, Remote Sens. Environ. 115(2):281-297 — [doi:10.1016/j.rse.2010.08.023](https://doi.org/10.1016/j.rse.2010.08.023)
- Not found: Tagliabue drone/airborne SIF paper; "Zhang/Wu" UAV SIF paper (searches returned unrelated items): UNVERIFIED. No Alpine/treeline UAV SIF study found.

### Inferences
- SIF is a small signal (far-red radiance of order a few mW/m2/sr/nm vs reflected radiance several hundred times larger; general knowledge, not source-verified here), requiring very-high spectral resolution (<0.3-1 nm FWHM) and stable illumination; clouds and steep, rapidly changing slope illumination and shadowing in Alpine terrain degrade retrievals. Conifer needle clumping and low far-red escape add to difficulty (general knowledge; Cescatti 1998 on needle clumping exists but is not about SIF).
- Platform instability (Bendig 2020 title) and sensor etaloning are known technical issues; steep terrain with wind adds motion problems. Monthly repeat flights at treeline depend on weather windows and snow-free season (about 3-4 months), giving 3-4 flights per year at best.
- TROPOMI/OCO-2/GOME-2 SIF (km scale) is unsuitable for treeline ecotone (<<1 km wide); MODIS GPP is also unsuitable.
- Recommended redesign: UAV multispectral + red-edge + thermal (and PRI if feasible) as primary; optional one-two SIF pilot campaigns or a field spectrometer at fixed points (FloX/Piccolo-type systems, UNVERIFIED as references here).

### Gaps
- No verified study of UAV SIF on small conifers or in mountain terrain.
- Honkanen et al. results unread.
- Equipment vendors (Specim, Headwall, FloX, Piccolo) not verified from literature.

## 4. Planet SuperDove 3 m crown segmentation of juvenile trees (<1 m crowns); cited claim checks

### Takeaway
Infeasible: 3 m pixels cannot segment or even reliably detect juvenile trees with crowns <1 m. Even 5 cm UAV imagery detects only 52% of small trees (<=130 cm) in the Italian Alps. The three cited papers support a UAV/very-high-resolution design, not Planet 3 m.

### Cited Findings
- Teng, Ouaknine, Laliberté, Bengio, Rolnick & Larochelle, "Bringing SAM to new heights: Leveraging elevation data for tree crown segmentation from drone imagery", arXiv:2506.04970, published in Advances in Neural Information Processing Systems 38, pp. 9481-9513 (2025). Compares SAM-based crown instance segmentation on drone imagery in boreal plantations, temperate and tropical forests; BalSAM = SAM + DSM from RGB; off-the-shelf SAM does not beat a custom Mask R-CNN. It is NOT a treeline study and has no Alpine data. — [arXiv abs](https://arxiv.org/abs/2506.04970); Crossref DOI [10.52202/085713-0290](https://doi.org/10.52202/085713-0290)
- Carrieri, Morresi, Meloni, Anselmetto, Lingua, Marzano, Urbinati, Vitali & Garbarino 2025, Biogeosciences 22(21):6393-6409, "Very-high resolution aerial imagery and deep learning uncover the fine-scale patterns of elevational treelines" (note "the fine-scale patterns", wording slightly differs from the brief). 90 ha at 10 Italian Alps treeline sites; DJI Phantom 4 Pro V2 RGB UAV orthomosaics at 5 cm, flown about 30 m above the highest plot point; 14,737 trees mapped; larch and Swiss stone pine dominant; detection rate 67% overall (70% for >50 cm; 52% for small trees <=130 cm; 86% for >2 m); test F1 0.76 (precision 0.92, recall 0.79); spatially independent cross-validation F1 0.68, recall 0.56; position RMSE 59 cm, height RMSE 92 cm; all conifers one "tree" class, no species classification. — [doi:10.5194/bg-22-6393-2025](https://doi.org/10.5194/bg-22-6393-2025) (preprint version: [doi:10.5194/egusphere-2024-3757](https://doi.org/10.5194/egusphere-2024-3757))
- EGUsphere-2025-970 is published: Sindewald, Lagerquist, Cross, Scambos, Anthamatten & Tomback 2025, Biogeosciences 22:6509-6543, "Identifying alpine treeline species using high-resolution WorldView-3 multispectral imagery and convolutional neural networks". Rocky Mountains (Colorado), NOT the Alps. WorldView-3 panchromatic 31 cm, multispectral 1.24 m; six species; overall accuracy only 44.1% (six-class), 46.7% (four-class), 86.2% (two-class; trivial baseline 80.3%). — [doi:10.5194/bg-22-6509-2025](https://doi.org/10.5194/bg-22-6509-2025)

### Inferences
- If the Italian UAV study at 5 cm misses roughly half of trees <=130 cm, Planet 3 m (9 m2 per pixel) will not capture juveniles <1 m crown at all; at most it could detect canopy-cover change in dense stands.
- Species mapping at treeline even with 0.31-1.24 m WorldView-3 reached only 44-47% (multi-class) accuracy, so satellite species mapping at 3 m is not supportable.
- SAM-based pipelines were validated outside treeline; the Teng paper cannot support a claim of feasibility at treeline and, per its abstract, off-the-shelf SAM underperforms a trained Mask R-CNN. Use as methods reference only.
- Suggested redesign: UAV (<=5 cm) RGB/multispectral for sapling census at selected plots; Planet or Sentinel-2 only as a context layer.

### Gaps
- Spatial cross-validation drop (F1 0.68, recall 0.56) means transfer to unseen sites is weaker; Carrieri 2025 full text not read beyond the fetched summary.
- SuperDove-specific tree-detection literature not searched.

## 5. SDM caveats at treeline (MaxEnt/BIOMOD2, CHELSA, microclimate, snow, equilibrium)

### Takeaway
Coarse-grid (about 1 km) CHELSA predictors do not represent the 1-2 K topographic microclimate variation at treeline that controls tree establishment, and climate-envelope SDMs assume equilibrium, which treelines violate (land-use legacies, dispersal/recruitment lags). SDM output (habitat suitability) is therefore not a proxy for treeline shift unless validated against observed shifts. Snow inputs need to be downscaled/observation-based (Austrian SNOWGRID/SPARTACUS-type products) rather than EURO-CORDEX/CHELSA.

### Cited Findings
- Karger et al. 2017, Sci. Data 4:170122 (CHELSA; about 1 km climatologies). — [doi:10.1038/sdata.2017.122](https://doi.org/10.1038/sdata.2017.122)
- Scherrer & Körner 2011, J. Biogeogr. 38(2):406-416 (Crossref issued-date 2010 online), topographically controlled thermal-habitat differentiation buffers alpine plant diversity against warming. — [doi:10.1111/j.1365-2699.2010.02407.x](https://doi.org/10.1111/j.1365-2699.2010.02407.x)
- Scherrer & Körner 2010, Glob. Change Biol. 16(9):2602-2613, infra-red thermometry of alpine landscapes challenges climatic warming projections. — [doi:10.1111/j.1365-2486.2009.02122.x](https://doi.org/10.1111/j.1365-2486.2009.02122.x)
- Körner & Paulsen 2004, J. Biogeogr. 31(5):713-732 (global treeline temperatures; about 6.7 C growing-season mean soil temperature; value from general knowledge, abstract not retrieved here). — [doi:10.1111/j.1365-2699.2003.01043.x](https://doi.org/10.1111/j.1365-2699.2003.01043.x)
- Körner, "Alpine Treelines: Functional Ecology of the Global High Elevation Tree Limits" (Springer, 2012). Only a book review (Cairns 2013, Arct. Antarct. Alp. Res. 45(3):420-421, [doi:10.1657/1938-4246-453.420](https://doi.org/10.1657/1938-4246-453.420)) was found in Crossref; the book's own DOI was not confirmed: cite by publisher/ISBN after checking (DOI UNVERIFIED).
- Lembrechts et al. 2019, Glob. Ecol. Biogeogr. 28(11):1578-1596, comparing temperature data sources for SDMs from in-situ loggers to remote sensing. — [doi:10.1111/geb.12974](https://doi.org/10.1111/geb.12974)
- Zellweger et al. 2019, Trends Ecol. Evol. 34(4):327-341, advances in microclimate ecology from remote sensing. — [doi:10.1016/j.tree.2018.12.012](https://doi.org/10.1016/j.tree.2018.12.012)
- Potter, Woods & Pincebourde 2013, Glob. Change Biol. 19(10):2932-2939, microclimatic challenges in global change biology. — [doi:10.1111/gcb.12257](https://doi.org/10.1111/gcb.12257)
- Randin et al. 2009, Glob. Change Biol. 15(6):1557-1569, local (fine-scale) models predict high-elevation persistence of plants (Swiss Alps) vs coarse models. — [doi:10.1111/j.1365-2486.2008.01766.x](https://doi.org/10.1111/j.1365-2486.2008.01766.x)
- Elith, Kearney & Phillips 2010, Methods Ecol. Evol. 1(4):330-342, the art of modelling range-shifting species. — [doi:10.1111/j.2041-210x.2010.00036.x](https://doi.org/10.1111/j.2041-210x.2010.00036.x)
- Yates et al. 2018, Trends Ecol. Evol. 33(10):790-802, outstanding challenges in transferability of ecological models (extrapolation to new conditions). — [doi:10.1016/j.tree.2018.08.001](https://doi.org/10.1016/j.tree.2018.08.001)
- Meyer & Pebesma 2021, Methods Ecol. Evol. 12(9):1620-1633, area of applicability for spatial prediction models (practical extrapolation diagnostic). — [doi:10.1111/2041-210x.13650](https://doi.org/10.1111/2041-210x.13650)
- Vitasse et al. 2012, J. Biogeogr. 39(8):1439-1449, tree recruitment of European species at their upper elevational limits in the Swiss Alps (recruitment, not distribution, is the relevant process). — [doi:10.1111/j.1365-2699.2012.02697.x](https://doi.org/10.1111/j.1365-2699.2012.02697.x)
- Snow/climate data: Hiebl & Frei 2016 (online 2015), Theor. Appl. Climatol. 124(1-2):161-178, SPARTACUS daily temperature grids for Austria since 1961 (about 1 km) — [doi:10.1007/s00704-015-1411-4](https://doi.org/10.1007/s00704-015-1411-4); Olefs, Koch, Schöner & Marke 2020, Atmosphere 11(12):1330, model-based (SNOWGRID) snow depth and snow cover duration changes in Austria 1961-2020 — [doi:10.3390/atmos11121330](https://doi.org/10.3390/atmos11121330)
- EURO-CORDEX in the Alps: Kotlarski et al. 2014, Geosci. Model Dev. 7(4):1297-1333 (RCM ensemble evaluation) — [doi:10.5194/gmd-7-1297-2014](https://doi.org/10.5194/gmd-7-1297-2014); Frei et al. 2018, The Cryosphere 12(1):1-24 (snowfall evaluation and projections in the Alps) — [doi:10.5194/tc-12-1-2018](https://doi.org/10.5194/tc-12-1-2018); Steger, Bülow, Teichmann & Kotlarski 2026, Clim. Dyn. 64(9):395, "European snow cover in the EURO-CORDEX regional climate model ensemble: model evaluation" — [doi:10.1007/s00382-026-08343-5](https://doi.org/10.1007/s00382-026-08343-5) (content not read; relevant to snow quality)
- Land-use vs climate attribution: Carrieri 2026 preprint (land-use explained more variance than climate); Gehrig-Fasel 2007; Dirnböck 2003; see section 1.

### Inferences
- A habitat-suitability index (HSI) from a climate-envelope SDM is a proxy for potential, not realised, treeline position; it cannot predict shift timing, and land abandonment (not climate) dominated in the Italian preprint, so HSI alone would mis-attribute. State HSI as "climatic suitability", validate against observed shift (e.g. orthophoto-derived), and include land-use/grazing history, seed source distance and microtopography as predictors.
- CHELSA (about 1 km, interpolated from station/reanalysis; microclimate not resolved) vs 1-2 K local variation (Scherrer & Körner) means predictors should be microclimate-informed (loggers, topography-derived temperature, Lembrechts soil-temperature products with caution).
- Snow: use SNOWGRID/SPARTACUS-type observation-driven inputs for the past and bias-adjusted EURO-CORDEX only with documented evaluation; CHELSA-snow limitations: not verified in this session (no source found), flag as UNVERIFIED claim.
- SSP extrapolation: quantify with Meyer & Pebesma AOA; report novel-climate fraction.
- Lembrechts et al. global soil-temperature maps: note a 2025 critique (Uxa 2025, Glob. Change Biol. 31(10):e70574, [doi:10.1111/gcb.70574](https://doi.org/10.1111/gcb.70574); content not read) reports physical inconsistencies in the soil-temperature depth relations; the global-maps paper I found in Crossref is an OSF preprint ([doi:10.32942/osf.io/pksqw](https://doi.org/10.32942/osf.io/pksqw)), published version not confirmed (UNVERIFIED).

### Gaps
- No source found directly stating CHELSA snow-product limitations in the Alps.
- No verified evidence in this note on SNOWGRID spatial resolution/accuracy beyond the Olefs 2020 title.
- Content of Scherrer & Körner and Randin not read here; only metadata verified.

## 6. Dendrochronology of juvenile treeline pines (cross-dating, juvenile effect, thresholds, permits)

### Takeaway
Juvenile Pinus cembra (and larch) at treeline are difficult to cross-date and show age-dependent growth-climate responses; ring-width chronologies from young, slow-growing, possibly missing-ring individuals will have low Rbar/EPS unless sample size is large, so destructive sampling at a scale giving EPS >=0.85 may be unrealistic in protected areas. Prefer non-destructive or minimal sampling (increment cores of larger trees, stem discs only from already dead/windthrown individuals) and use dendro for age structure/recruitment dating, not for climate-growth chronologies.

### Cited Findings
- Carrer & Urbinati 2004, Ecology 85(3):730-740, "Age-dependent tree-ring growth responses to climate in Larix decidua and Pinus cembra" (Alps; growth-climate relationships change with tree age; content not read). — [doi:10.1890/02-0478](https://doi.org/10.1890/02-0478)
- Frank & Esper 2005, Dendrochronologia 22(2):107-121, high-elevation multi-species tree-ring network in the European Alps (includes Pinus cembra; content not read). — [doi:10.1016/j.dendro.2005.02.004](https://doi.org/10.1016/j.dendro.2005.02.004)
- Neuwirth, Schweingruber & Winiger 2007, Dendrochronologia 24(2-3):79-89, central European pointer years 1901-1971. — [doi:10.1016/j.dendro.2006.05.004](https://doi.org/10.1016/j.dendro.2006.05.004)
- Wigley, Briffa & Jones 1984, J. Clim. Appl. Meteorol. 23(2):201-213 (origin of EPS/Rbar statistics). — [doi:10.1175/1520-0450(1984)023<0201:OTAVOC>2.0.CO;2](https://doi.org/10.1175/1520-0450(1984)023%3C0201:OTAVOC%3E2.0.CO;2)
- Bunn 2008, Dendrochronologia 26(2):115-124, dplR. — [doi:10.1016/j.dendro.2008.01.002](https://doi.org/10.1016/j.dendro.2008.01.002)
- Briffa & Melvin 2011 (Crossref "2010"), Regional Curve Standardization chapter in Developments in Paleoenvironmental Research, pp. 113-145 (age-trend removal pitfalls). — [doi:10.1007/978-1-4020-5725-0_5](https://doi.org/10.1007/978-1-4020-5725-0_5)
- General web-sourced thresholds: EPS >0.85 conventionally accepted; Rbar computed over pairs sharing >=25 years (search-engine summary of dendro methods, not a primary paper; the primary source is Wigley 1984). Treeline studies often add fixed years (5-15) to core ring counts to estimate age, depending on coring height (15 cm, 50 cm, 1.3 m); the specific primary source was not identified: UNVERIFIED.
- Pinus cembra at treeline, physiology/ecology context: Wieser et al. 2015, Tree Physiol. 35(3):279-288 (soil warming and whole-tree water use of Pinus cembra at treeline, Tyrol) — [doi:10.1093/treephys/tpv009](https://doi.org/10.1093/treephys/tpv009)

### Inferences
- A 2023 search-summary notes that Pinus cembra multi-century climate reconstructions are few due to weak climate signal (source not individually verified): suggests the growth-climate signal at treeline is weak/complex, so small samples of juveniles are unlikely to meet EPS standards.
- Pointer-year analysis needs a reference chronology; juvenile series (<30-50 yr) lack the overlap needed for robust crossdating, and missing/locally absent rings in krummholz/near-prostrate conifers cause dating errors. The brief's "missing rings in Pinus cembra" has no verified primary reference found.
- Sacrificial sampling in Natura 2000/national-park areas typically needs permits; no reference found; check with park authorities (UNVERIFIED regulatory claim).

### Gaps
- No verified primary source on minimum sample sizes for juvenile conifer chronologies, juvenile-effect magnitude in P. cembra, or missing-ring frequency; Speer (2010) book and Cook & Kairiukstis (1990) not DOI-verified (a Crossref hit for Speer was only a book review, [doi:10.3959/1536-1098-70.2.161](https://doi.org/10.3959/1536-1098-70.2.161)).
- Permit/regulatory evidence not researched.

## 7. SMAP freeze/thaw at 9 km in the Alps; webcam/phenocam snow depth

### Takeaway
SMAP freeze/thaw (about 9 km enhanced, 36 km standard grid, regional scale) is unsuitable for treeline-scale soil freeze/thaw in rugged Alpine terrain: pixel size spans huge elevation, aspect and snow variability and covers many land-cover types. Webcams/phenocams are feasible for snow-cover (presence/duration) and phenology at fixed field of view, but snow DEPTH estimation is harder and needs reference poles/stakes.

### Cited Findings
- Derksen et al. 2017, Remote Sens. Environ. 194:48-62, "Retrieving landscape freeze/thaw state from SMAP radar and radiometer measurements" (northern/boreal focus; Alps validation not found; resolution details not read). — [doi:10.1016/j.rse.2017.03.007](https://doi.org/10.1016/j.rse.2017.03.007)
- Further SMAP F/T validation work found only as IGARSS conference abstracts (Li et al. 2017; Wang et al. 2019 China). No Alps SMAP F/T validation found. — e.g. [doi:10.1109/igarss.2017.8127277](https://doi.org/10.1109/igarss.2017.8127277)
- Portenier, Hüsler, Härer & Wunderle 2020, The Cryosphere 14(4):1409-1423, "Towards a webcam-based snow cover monitoring network: methodology and evaluation" (Swiss webcams; snow cover fraction from webcam imagery; content not read in detail). — [doi:10.5194/tc-14-1409-2020](https://doi.org/10.5194/tc-14-1409-2020)
- Richardson et al. 2018, Sci. Data 5:180028, PhenoCam tracking of phenology across North American biomes (not Alpine; includes data/method standards). — [doi:10.1038/sdata.2018.28](https://doi.org/10.1038/sdata.2018.28)
- Filippa et al. 2016, Agric. For. Meteorol. 220:141-150, "Phenopix: A R package for image-based vegetation phenology" (Filippa and Cremonese are at ARPA Valle d'Aosta, Alpine sites). — [doi:10.1016/j.agrformet.2016.01.006](https://doi.org/10.1016/j.agrformet.2016.01.006)
- Hufkens/Richardson: only R packages and a Hopkins' law PhenoCam paper (Richardson, Hufkens, Li & Ault 2019, Appl. Plant Sci. 7(3):e01228, [doi:10.1002/aps3.1228](https://doi.org/10.1002/aps3.1228)) found. No Alpine PhenoCam snow-depth paper verified.

### Inferences
- Soil freeze/thaw at treeline scale is better obtained from in-situ loggers (soil temperature at 5-10 cm) and optical snow products (Sentinel-2/Landsat snow cover; Portenier-type webcam snow); SMAP at 9 km would be a coarse regional context at best, and L-band signal is also affected by snow wetness and terrain.
- Webcam snow depth: feasible only with calibrated markers or photogrammetry; otherwise report snow-cover fraction and melt-out date, which is the variable most relevant to growing-season length.

### Gaps
- No Alps-specific SMAP validation; no verified phenocam snow-depth Alpine paper; SMAP product grid sizes quoted from general knowledge, not from a fetched source.

## Reference list quick table (all DOIs resolved in Crossref unless noted)

| Ref | DOI | Status |
|---|---|---|
| Baglioni et al. 2025 Biogeosciences 22:4349-4366 | 10.5194/bg-22-4349-2025 | VERIFIED (publisher fetch) |
| Carrieri et al. 2025 Biogeosciences 22:6393-6409 | 10.5194/bg-22-6393-2025 | VERIFIED (publisher fetch) |
| Sindewald et al. 2025 Biogeosciences 22:6509-6543 | 10.5194/bg-22-6509-2025 | VERIFIED (publisher fetch) |
| Teng et al. 2025 NeurIPS 38 / arXiv 2506.04970 | 10.52202/085713-0290 | VERIFIED (arXiv fetch + Crossref) |
| Carrieri et al. 2026 bioRxiv | 10.64898/2026.09.30.755293 | PREPRINT, fetched |
| Honkanen et al. 2024 Springer chapter | 10.1007/978-3-031-44607-8_8 | metadata VERIFIED, content unread |
| Bendig et al. 2020 IEEE TGRS 58:3437-3444 | 10.1109/TGRS.2019.2956194 | VERIFIED (journal differs from brief) |
| Vargas et al. 2020 Remote Sens. 12:1624 | 10.3390/rs12101624 | VERIFIED |
| Körner 2012 Alpine Treelines book | n/a | DOI UNVERIFIED |
| Tagliabue, Zhang/Wu UAV SIF, Bolton Alps, Nguyen 2024 Swiss | n/a | UNVERIFIED (not found) |
