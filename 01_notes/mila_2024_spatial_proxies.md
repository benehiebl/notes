---
title: "Random forests with spatial proxies for environmental modelling: opportunities and pitfalls"
authors:
  - Milà, Carles
  - Ludwig, Marvin
  - Pebesma, Edzer
  - Tonne, Cathryn
  - Meyer, Hanna
year: 2024
source: mila_2024_spatial_proxies
tags:
  - machine-learning
  - remote-sensing
  - methodology
keywords:
  - random forest
  - spatial proxies
  - coordinates as predictors
  - Euclidean distance fields
  - RFsp
  - kNNDM cross-validation
  - spatial autocorrelation
  - area of applicability
  - RF-GLS
  - spatial interpolation
  - spatial extrapolation
status: read
---

# Milà et al. 2024 — Random Forests with Spatial Proxies: Opportunities and Pitfalls

## Title and Authors
**Random forests with spatial proxies for environmental modelling: opportunities and pitfalls**
Carles Milà, Marvin Ludwig, Edzer Pebesma, Cathryn Tonne, Hanna Meyer — *Geoscientific Model Development*, 17, 6007–6033, 2024.

## Quick Overview
- **Why is it relevant?** Spatial proxies (coordinates, Euclidean distance fields, RFsp) are routinely added to random forest predictors without justification — this paper provides the first systematic assessment of when this helps and when it harms.
- **What was done?** A 12,800-model simulation crossed four scenarios × two autocorrelation ranges × four sampling distributions × four model types, complemented by two Spanish case studies (air temperature and PM2.5).
- **What is the main outcome?** Spatial proxies help only under specific conditions (spatial interpolation + residual autocorrelation + regular/random samples); they are never appropriate for spatial-model transfer, and random k-fold CV systematically mis-ranks proxy models — kNNDM CV is recommended.

## Main Goal and Fundamental Concept
Random forests (RFs) are popular in environmental mapping but ignore spatial locations of samples by design. Practitioners often add "spatial proxies" — variables indexed by location whose autocorrelation range exceeds the modelling domain — as a low-effort fix for residual autocorrelation. The paper asks: under which prediction settings does this fix actually improve accuracy, and which validation methods reliably tell us so?

The three proxy types tested:
- **Coordinates**: raw x/y as two predictor columns
- **Euclidean Distance Fields (EDFs)**: distances to N reference points (e.g. corners + centre)
- **RFsp**: distance to every training sample → as many proxy predictors as samples (Hengl et al. 2018)

## Technical Approach

**Simulation study** on a 300×100 grid with separate sampling and extrapolation areas:
- Four response scenarios: *autocorrelated error*, *complete* (no missing predictors), *missing predictors*, *proxies only*
- Two autocorrelation ranges (10 vs 40) for predictor fields with spherical variograms
- Four sampling designs: regular, random, weakly clustered, strongly clustered (n=200)
- 100 iterations × 4 scenarios × 2 ranges × 4 sample types × 4 model types = 12,800 RF fits
- For every fit: compute true RMSE (interpolation + extrapolation), feature extrapolation via Area of Applicability (AOA; Meyer & Pebesma 2021), and variable importance
- Three validation methods compared: independent probability test samples, random 5-fold CV, kNNDM CV (Linnenbrink et al. 2023)
- Benchmarked against **RF–GLS** (Saha et al. 2023), a GLS-style RF that models residual covariance with a Gaussian process

**Case studies**: continental Spain 2019
- Air temperature (195 well-spread AEMET stations, strong autocorrelation)
- PM2.5 (124 clustered MITECO stations, weaker autocorrelation)
- "Naive" (1 driver) vs "complete" (full predictor set incl. DEM, NDVI, LST, road density, NTL, CAMS reanalysis) models tested with the same four proxy configurations
- Spatial point-pattern analyses (Ĝ, F̂, K̂ functions with Monte Carlo envelopes) and empirical variograms inform the diagnosis

## Distinctive Features
- First **systematic factorial simulation** crossing prediction objective, autocorrelation strength, and sampling pattern for RF spatial proxies
- Couples performance metrics with diagnostic statistics (AOA-based feature extrapolation, mean-decrease-impurity importance)
- Compares three validation methods head-to-head for model *ranking* (not just absolute error estimation)
- Real-world case studies deliberately chosen to contrast favourable vs unfavourable conditions
- Explicit comparison with RF–GLS, an "inherently spatial" alternative

## Experimental Setup and Results

**Extrapolation (model transfer to a new area)**
- Baseline (no proxies) always beats proxy models, regardless of scenario, range, or sampling pattern
- AOA analysis shows nearly the entire extrapolation area falls outside the training feature space whenever proxies are used → feature extrapolation is unavoidable
- Random 5-fold CV severely underestimates extrapolation RMSE *and* wrongly ranks proxy models above baseline

**Interpolation (same domain as training)**
- Proxies help **only** when:
  1. Residual autocorrelation exists (autocorrelated error or missing predictors), **and**
  2. Samples are regularly or randomly distributed, **and**
  3. The autocorrelation range is long
- With clustered samples, proxies *increase* feature extrapolation, raise proxy variable importance (sign of overfitting), and typically worsen RMSE
- "Proxies only" interpolation can rival full-predictor models when conditions (1–3) are met
- Among proxies, RFsp and EDFs deliver the largest gains when proxies are appropriate, but the largest losses when they are not

**Validation method ranking**
- Random 5-fold CV: systematically favours proxy models even when wrong, especially with clustered samples (matches Meyer & Pebesma 2022 on CV failures)
- Probability test samples: correctly rank models in all scenarios
- kNNDM CV: matches probability test samples in correctness, and is achievable without independent data — recommended

**RF–GLS comparison**
- RF–GLS equals or beats the best RF (with or without proxies) in *all* parameter combinations, in both interpolation and extrapolation
- Largest gains in autocorrelated-error + regular/random samples for interpolation
- Authors recommend RF–GLS as a candidate for spatial prediction tasks

**Case studies**
- Temperature (well-spread, strongly autocorrelated): naive DEM + proxies almost matches full-predictor model; R²≈0.88–0.90 with proxies vs 0.49 without. Random and kNNDM CV agree.
- PM2.5 (clustered, weakly autocorrelated): random CV says proxies help (R² 0.13→0.44); kNNDM CV shows the gain is illusory (R² stays near 0); large discrepancy between map predictions of different proxy choices → mapping artefacts.

## Advantages and Limitations
- **Advantages**: factorial design isolates causes; uses both true RMSE (simulation) and operationally available validation; explicit guidance produced; freely available R code (`sf`, `terra`, `caret`, `ranger`, `RandomForestsGLS`, `CAST`)
- **Limitations**: RF only (other ML algorithms may differ in extrapolation behaviour); accuracy lens only (not knowledge-discovery / variable interpretation); spatial non-stationarity not explicitly studied; alternative spatial-lag models (Sekulić et al. 2020) not benchmarked

## Conclusion
Use RFs with spatial proxies **only** when (1) the sampling and prediction areas overlap, (2) significant residual spatial autocorrelation is present, **and** (3) samples are regularly or randomly distributed over the prediction area. Never use them for spatial-model transfer. Diagnose conditions *a priori* via spatial point-pattern analysis and empirical variograms, and confirm *a posteriori* with probability test samples or kNNDM CV — random k-fold CV will mislead. RF–GLS is a serious modern alternative worth considering as the default for spatial prediction.

## Related pages
- [[spatial_proxies_random_forest]]
- [[area_of_applicability]]
- [[sampling_bias_remote_sensing]]
- [[transfer_learning_remote_sensing]]
- [[schloegl_2026_reproducibility]]
- [[hiebl_2025_pretraining]]
- [[pebesma_2025_spatial_data]]
- [[kollert_2021_tree_species]]
- [[blickensdörfer_2024_tree_species]]
- [[deep_ensemble_uncertainty]]
- [[zangh_2017_generalization]]
