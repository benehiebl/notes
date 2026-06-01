
# Title:
**Predictor spatial autocorrelation range determines cross-validation buffer distance in satellite-based canopy height modelling**

*(alternative: "How predictor choice shapes spatial autocorrelation and cross-validation bias in remote sensing regression")*

---

> [!abstract] Motivation
> Machine learning models for vegetation mapping combine predictors of fundamentally different spatial autocorrelation (SA) ranges: spectral reflectance varies at forest-stand scale (tens of meters to ~1 km), topography at landscape scale (~1–5 km), and climate over regional gradients (tens to hundreds of km). Standard random cross-validation (CV) treats nearby and distant observations as exchangeable, inflating apparent accuracy whenever the predictor SA range exceeds the typical train–test separation distance. The required buffer distance in spatially stratified CV (e.g. kNNDM) is typically chosen heuristically — but should logically scale with the SA range of the predictor set. **No study has empirically measured how predictor type controls variogram range and the resulting CV inflation in a satellite-based regression model.** We propose an empirical framework using globally available, methodologically independent data (GEDI canopy height as Y; S2 spectral, SRTM topography, and CHELSA climate as predictors) to provide this missing quantification.

> [!question] What research questions will be answered?
> 1. What are the empirical variogram ranges of spectral, topographic, and climate predictors, and of the target variable (canopy height), within a single alpine Sentinel-2 tile?
> 2. How does adding predictors of progressively longer SA range increase the CV inflation gap (random CV accuracy minus spatially-stratified CV accuracy)?
> 3. What minimum train–test separation in kNNDM eliminates SA-driven inflation for each predictor combination — and does this match the measured variogram range of the dominant predictor?
> 4. Do longer-range predictors reduce residual spatial autocorrelation (genuine ecological signal) or enable spatial memorisation without improving generalisability?

> [!info] What will be done?
> Empirical study within one 100×100 km alpine Sentinel-2 tile (e.g. 32TNT, Tyrol). Target variable: GEDI canopy height at 10 m resolution. Predictors: Sentinel-2 seasonal composites (spectral), SRTM-derived terrain variables (topography), CHELSA bioclimatic variables (climate). Design has three parts:
> 1. **Variogram analysis** — measure SA ranges for each predictor group and for Y
> 2. **CV inflation experiment** — four nested predictor sets × two CV strategies; quantify inflation per combination
> 3. **Residual variogram** — separate genuine ecological explanation from spatial memorisation

> [!success] What are the expected results?
> - SA ranges ordered: reflectance (< 1 km) < topography (~1–5 km) < Y canopy height (~1–10 km) < climate (> 10 km within tile, potentially beyond tile extent)
> - CV inflation near-zero for spectral-only; increases with each predictor group added; largest for climate predictors
> - Optimal kNNDM buffer distance scales predictably with dominant predictor SA range — providing a practical design rule
> - Residual variogram: climate predictors reduce residual SA range (genuine signal), but this coexists with the largest CV inflation — both effects are simultaneously true and separable

---

## Introduction

- Random CV is the dominant evaluation strategy in remote sensing vegetation mapping despite documented spatial autocorrelation problems [[mila_2024_spatial_proxies]] [[schloegl_2026_reproducibility]]
- kNNDM CV and block CV have been proposed as solutions, but the appropriate buffer distance is unclear and chosen heuristically [[mila_2024_spatial_proxies]]
- Predictor types span fundamentally different SA scales:
  - **Spectral reflectance** (S2): patch-scale SA, bounded by canopy cover continuity — typically < 1 km at 10 m resolution [[hemmerling_2021_forest_mapping_s2]]
  - **Topography** (elevation, slope, aspect, TPI): landscape-scale SA, controlled by terrain units — hundreds of meters to ~5 km; strongly controls canopy height via microclimate and species composition [[topographic_microclimate]]
  - **Climate** (temperature, precipitation): regional to continental SA; in alpine terrain, lapse-rate elevation effects compress the effective climate gradient within a tile, but SA range may still exceed spectral and topographic ranges
- The theoretical link between predictor SA range and CV inflation exists in the spatial statistics literature [[mila_2024_spatial_proxies]] but has not been measured empirically for common RS predictor combinations
- GEDI canopy height provides an ideal target: acquired by LiDAR (independent from S2 spectral features), globally available, continuous, with quasi-regular orbital sampling well-suited for variogram estimation [[lang_2024_canopy_height]]
- Single alpine tile: strong within-tile gradients in all three predictor types across elevation (500–3000 m a.s.l.); diverse forest types (spruce, fir, larch, beech, pine); fully public data stack

**Core hypothesis**: CV inflation (RMSE_random − RMSE_kNNDM) is a monotone increasing function of the maximum SA range in the predictor set, because longer-range predictors create feature similarity between nearby train/test samples that random CV exploits.

---

## Methods

### Study area

- Single Sentinel-2 tile 32TNT (Tyrol, Eastern Alps), 100×100 km, ~600–3800 m elevation range
- Covers the full elevation gradient from valley-floor mixed forests through montane spruce-fir, subalpine larch, to timberline
- Climate gradient: MAT −5°C to +12°C across the elevation range; MAP 700–1800 mm
- Tile contains strong SA gradients in all predictor types within 100 km → all predictor groups contribute real ecological variance
- *Optional extension*: include 2–3 adjacent tiles (32TNS, 32TPT) to better estimate climate SA range, which may approach or exceed the 140 km diagonal of a single tile

### Target variable Y

**GEDI canopy height**:
- GEDI L2A relative height metrics (RH95 as canopy top height proxy) within the tile; ~2020–2023 acquisitions
- Filter: quality flag = 1, sensitivity > 0.9, non-urban land cover
- Expected ~50,000–200,000 GEDI footprints within tile depending on orbital coverage (quasi-regular along-track spacing ~60 m, across-track spacing ~600 m)
- Footprint geolocation at 25 m; aggregate to 30 m grid for predictor matching
- Canopy height provides strong, spatially coherent signal (stand-level SA) independent of spectral predictors

### Predictor groups

Four nested predictor sets of increasing SA complexity:

| Set | Contents | Expected max SA range |
|-----|----------|-----------------------|
| **S** | Spectral — S2 four-season composite medians (10 bands × 4 seasons = 40 features) + NDVI/EVI/NBR | < 1 km |
| **S+T** | Spectral + topography — SRTM elevation, slope, aspect (cos/sin), TPI at 300 m and 1 km, TWI | ~1–5 km |
| **S+C** | Spectral + climate — CHELSA MAT, MAP, temperature seasonality, aridity index, frost days | > 10 km (within-tile; true range may exceed tile extent) |
| **S+T+C** | All three groups | climate-dominated |

### Part 1 — Variogram analysis

**Goal**: empirical SA ranges per predictor group and for Y.

1. Compute empirical omnidirectional variograms from GEDI sample pairs:
   - For Y (canopy height): γ(h) = ½ E[(Y(s) − Y(s+h))²]
   - For each predictor dimension: same formulation
   - Lag classes: 100 m width from 100 m to max lag = 70 km (half the tile diagonal); minimum 30 pairs per lag class
2. Fit spherical or exponential models via weighted least squares; extract nugget (c₀), partial sill (c), practical range (a)
3. Summarise each predictor group by median fitted range across its principal components (PCA capturing 90% of within-group variance)
4. Assess isotropy: compare E–W vs N–S variograms; alpine terrain may show strong directional SA due to valley orientation
5. Key comparison: SA range of Y vs predictor group SA ranges — this determines which predictor groups operate above vs below the target's SA scale
6. If tile extent limits reliable climate variogram estimation (nugget still rising at max lag), note this explicitly and flag range estimate as lower bound; use the optional multi-tile extension to refine

### Part 2 — CV inflation experiment

**Goal**: quantify RMSE gap between random CV and spatially stratified CV for each predictor combination.

1. Train **Random Forest** (RF) regression on each of the four predictor sets using GEDI footprints as training samples:
   - RF chosen for interpretability and AOA compatibility; fixed hyperparameters across all models (mtry = p/3, ntree = 500) to isolate predictor effects from model selection
   - Exclude any spatial coordinates or EDF proxies from all predictor sets
2. Evaluate each model under two CV strategies:
   - **Random 10-fold CV**: GEDI footprints randomly assigned to folds
   - **kNNDM CV** (R package `CAST`): fold assignment matches geographic distance distribution between training data and prediction raster [[mila_2024_spatial_proxies]]
3. **Primary outcome**: inflation = RMSE_random − RMSE_kNNDM (negative = random CV is optimistic)
4. Sensitivity analysis — vary kNNDM buffer distance (100 m, 500 m, 2 km, 10 km, 50 km):
   - Plot RMSE_kNNDM vs buffer distance per predictor set
   - The buffer at which RMSE stabilises = empirical "effective SA range" of the prediction model for that predictor set
   - Test whether this stabilisation distance matches Part 1's variogram range estimate
5. Compute Area of Applicability [[area_of_applicability]] for each predictor set; report % of forest pixels outside AOA; test whether climate predictors shrink AOA in subalpine/high-elevation zones underrepresented in GEDI sampling

### Part 3 — Residual variogram analysis

**Goal**: distinguish genuine ecological explanation from spatial memorisation.

1. For each of the four models, extract kNNDM out-of-fold residuals ε = y − ŷ
2. Compute empirical variogram of ε; fit model; extract residual range and nugget-to-sill ratio
3. Interpretation framework:
   - If adding predictor group X reduces residual range **and** RMSE_kNNDM improves → genuine ecological signal
   - If residual range unchanged but RMSE_random improves → spatial memorisation only
   - Mixed case (RMSE_kNNDM improves slightly, residual range reduces moderately) → partial genuine signal
4. Compute Moran's I of residuals at 5 lag distances per model; test significance via 999 permutations
5. Expected finding: climate genuinely explains canopy height variation along the elevation gradient (shorter residual range) while simultaneously enabling the largest CV inflation — both effects coexist

### Baseline and diagnostics

- **RF–GLS** (Saha et al. 2023): explicit Gaussian-process residual covariance as reference that directly models SA; compare performance to standard RF under kNNDM CV across predictor sets
- **Moran's I of predictors** at 5 fixed lag distances: direct SA measurement without variogram model fitting; complementary diagnostic to variogram range
- All analysis in R (`gstat`, `CAST`, `spdep`, `ranger`)

---

## Expected Results

### Variogram ranges (hypothesised for alpine tile)

| Variable | Expected SA range |
|----------|------------------|
| Y — canopy height | 1–10 km (stand/landscape scale) |
| Spectral (S2 composites) | 0.3–1 km |
| Topography | 1–5 km |
| Climate (within tile) | 10–60 km (elevation-compressed gradient; true range may exceed tile) |

In alpine terrain, climate SA range is shortened by the tight elevation–temperature coupling (lapse rate), which may bring it closer to topographic range. This would reduce the clean separation between S+T and S+C — an empirically interesting null result if confirmed.

### CV inflation (hypothesised)

| Predictor set | RMSE random CV (m) | RMSE kNNDM CV (m) | Inflation (m) |
|--------------|-------------------|-------------------|---------------|
| S | 4.5 | 5.2 | −0.7 |
| S+T | 4.0 | 5.0 | −1.0 |
| S+C | 3.2 | 5.1 | −1.9 |
| S+T+C | 3.0 | 4.8 | −1.8 |

Note: absolute RMSE values are speculative; the *pattern* of increasing inflation with climate predictors is the testable hypothesis.

### kNNDM stabilisation distances

| Predictor set | Expected stabilisation distance |
|---|---|
| S | ~500 m–1 km |
| S+T | ~3–5 km |
| S+C | ~15–50 km (potentially at tile extent) |

### Residual variograms

- S model: residuals show clear SA (range 5–15 km); Moran's I significant at all lags → unmapped ecological gradients remain
- S+T model: residual range reduced (~2–8 km); topography explains within-stand canopy structure variation
- S+C model: residual range further reduced (~1–5 km); climate explains along-elevation gradient
- S+T+C model: nugget-to-sill ratio highest; residuals approach white noise at short lags → most ecological signal explained

---

## Discussion

- **Primary recommendation**: set kNNDM buffer = variogram range of dominant predictor group, not a fixed constant. For spectral-only models: 1 km. For models including topography: 3–5 km. For models including climate: determine from variogram, expect ≥10–50 km in alpine settings.
- **Both things can be true simultaneously**: climate predictors genuinely explain canopy height (reduced residual SA) AND inflate random CV accuracy (longer-range SA leakage). These are not contradictory. The implication is that removing climate predictors would hurt real-world performance — the solution is appropriate spatial CV, not simpler models.
- **Alpine terrain specificity**: the elevation–climate compression may make SA ranges more uniform across predictor types than in flat terrain. Replication in boreal (long climate SA range, flat terrain) or Mediterranean (strong macroclimatic gradient) settings would test whether the alpine finding generalises.
- **GEDI coverage limitation**: GEDI sampling is orbital and may be denser at tile edges (higher latitude). This could introduce directional bias in variogram estimation — anisotropy analysis in Part 1 is a necessary check.
- **Single target variable**: canopy height is structurally simple compared to species composition or fractional cover. SA range of target Y may differ substantially for compositional targets — the inflation pattern could be stronger (longer target SA range) or weaker (shorter) for species-based mapping.
- **Deep learning open question**: RF is used here for interpretability. Whether DL models (TSTpad, InceptionTime) show the same inflation pattern is unknown — weight sharing across spatial locations may create different leakage mechanisms than RF's local feature partitioning.

---

## Conclusion

We provide an empirically grounded answer to the question: which predictor types drive spatial autocorrelation inflation in remote sensing regression, and by how much? Using a globally reproducible, fully public data stack (GEDI, S2, SRTM, CHELSA) within a single alpine tile, we show that climate predictors dominate CV inflation, requiring spatial CV buffers of tens of kilometres to obtain honest accuracy estimates. Spectral-only models need only ~1 km buffers. A simple workflow — variogram the predictors, set buffer to max SA range, compare random and kNNDM CV — can be applied to any RS regression problem. The study is directly replicable in any Sentinel-2 tile with GEDI coverage.

---

## Literature

- [[mila_2024_spatial_proxies]] — kNNDM CV; spatial proxy decision rules; SA detection; RF–GLS
- [[spatial_proxies_random_forest]] — concept page
- [[area_of_applicability]] — AOA predictor-space diagnostics
- [[lang_2024_canopy_height]] — GEDI + S2 canopy height; GEDI data characteristics and limitations
- [[schloegl_2026_reproducibility]] — reproducibility standards; open data stack
- [[topographic_microclimate]] — topographic SA and ecological relevance
- [[hemmerling_2021_forest_mapping_s2]] — spectral TS SA context; S2 for forest mapping
- [[hiebl_2025_pretraining]] — spatial CV approach in vegetation RS context
- [[pebesma_2025_spatial_data]] — spatial data infrastructure
