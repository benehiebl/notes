---
title: "Assessing climate-driven treeline dynamics via the habitat suitability index"
authors:
  - Le Li
  - Shuheng Li
  - Siqin Zhao
  - Maoxin Du
  - Ziyi Yang
  - Fei Hu
  - Zhiqi Zhang
  - Jiahao Guo
  - Kailiang Zhao
  - Yuanxiao Xu
year: 2026
tags:
  - remote-sensing
  - climate-change
keywords:
  - alpine treeline
  - Larix chinensis
  - habitat suitability index
  - species distribution model
  - SHAP
  - CMIP6
status: unread
---

## Title and Authors of the Paper

Assessing climate-driven treeline dynamics via the habitat suitability index.
Le Li, Shuheng Li, Siqin Zhao, Maoxin Du, Ziyi Yang, Fei Hu, Zhiqi Zhang, Jiahao Guo, Kailiang Zhao, Yuanxiao Xu.
Journal of Environmental Management, 411 (2026), 130173.

## Quick Overview
- **Why is it relevant?** Combines remote-sensing-derived species occurrence data, ensemble species distribution modeling (SDM), and SHAP-based explainability to project alpine treeline dynamics under CMIP6 climate scenarios — directly relevant to forest-ecotone response modeling.
- **What was done?** An ensemble SDM (GLM, RF, MAXNET, XGBoost, selected from 12 candidate algorithms) was trained on RapidEye-derived *Larix chinensis* occurrence points and 10 climatic/topographic predictors to model habitat suitability index (HSI) at Mount Taibai (Qinling Mountains, China), then projected to 2040s/2070s/2100s under SSP126/370/585.
- **What is the main outcome?** Suitable habitat is projected to expand overall (4.65-18.96 km² by the 2100s, ~4-16% of the study area), but with a pronounced aspect-dependent pattern: stable increase on southern slopes, stable decrease on northern slopes, and elevation/growing-season temperature (Bio5, GDD) as the dominant drivers.

## Main Goal and Fundamental Concept

- Predict long-term spatial dynamics of an alpine treeline ecotone under future climate change, using habitat suitability as a proxy for treeline position rather than a fixed elevational threshold.
- Core premise: treeline shifts can be inferred from spatiotemporal change in HSI trajectories (with bootstrapped confidence intervals), rather than from a single climatic threshold or a static treeline line.
- Focus species: *Larix chinensis*, the sole dominant tree species in the Mount Taibai treeline ecotone (Qinling Mountains, China).

## Technical Approach

- **Occurrence data**: extracted from RapidEye imagery (5 m, foliage vs. leaf-off acquisitions) via object-based classification + manual interpretation; spatially de-clustered using 50 m grid cells, repeated 5x for robustness.
- **Environmental predictors**: 24 CHELSA bioclimatic variables (1 km) + ALOS DEM-derived topographic variables (slope, aspect, TWI, TRI, SPI, 12.5 m), downscaled to 50 m via a random-forest regression (climate ~ topography), validated against independent temperature records (RMSE 0.41, R²=0.92). Reduced to 10 variables after collinearity (|r|>0.90) and VIF (<10) filtering.
- **Modeling framework**: BIOMOD2 in R; 12 algorithms benchmarked via 10-fold cross-validation; only models with ROC>0.9 and TSS>0.8 (RF, XGBoost, MAXNET, GLM) retained for the ensemble.
- **Explainability**: SHAP (via random forest) used for global feature importance and non-linear response curves.
- **Future projections**: CHELSA CMIP6 bioclimatic data for SSP126/370/585 at 2040s/2070s/2100s.
- **Spatial statistics**: weighted Standard Deviational Ellipse (SDE) to track the centroid and dispersion of suitable habitat over time.
- **Treeline shift detection**: HSI values sampled in a 100 m buffer around the 2010 treeline; Smoothed Bootstrap (1000 resamples) used to build 95% CIs on HSI change per scenario/period, classifying locations as stable increasing / stable decreasing / unstable.

## Distinctive Features

- Treeline dynamics inferred from HSI trajectories with explicit uncertainty quantification (bootstrapped CIs), rather than from a single suitability threshold or fixed treeline boundary — a methodological alternative to typical SDM-threshold approaches.
- Uses SHAP dependence plots to identify concrete non-linear thresholds: e.g. Bio5 (max temperature of warmest month) inflection at ~13.6-13.7°C, GDD facilitation onset at 52.7°C·day (plateauing ~102.4°C·day), optimal elevation window 2803-3091 m.
- Explicitly reframes elevation's dominant SHAP importance as a proxy for an embedded "temperature signal" rather than a causal driver itself.
- Aspect-resolved treeline projection (north- vs. south-facing slopes) rather than a single area-wide trend.

## Experimental Setup and Results

- Study area: 117.1 km² eastern sector of Mount Taibai (up to 3771 m), Qinling Mountains, China.
- Model validation: high spatial concordance between observed (2010) and predicted *L. chinensis* distribution; Schoener's D = 0.921; observed elevation peak 3459 m vs. predicted medium/high suitability peak 3452 m; confusion matrix on a 20% held-out sample: 731/774 "YES" and 1729/1961 "NO" correctly classified.
- Driving factors (SHAP): elevation (DEM) most important, followed by Bio5 (max. temp of warmest month) and GDD (growing degree days > 5°C); precipitation variables comparatively weak.
- Future HSI change: general expansion under all scenarios by the 2100s (4.65-18.96 km², ~4-16% of study area); SSP585 shows the most sustained expansion (up to 73.8% of area as "stable increasing" by 2100), while SSP126/SSP370 show mid-century expansion followed by later contraction/stabilization.
- SDE: major axis stays east-west (following topography) across scenarios; centroid shifts southwestward over time, interpreted as "climate tracking" toward warmer/more humid conditions.
- Aspect pattern: stable decreasing zones concentrated on northern slopes, stable increasing zones on southern slopes, consistent across all three SSP scenarios — attributed to differential solar radiation, growing-season length, and snow persistence between aspects.

## Advantages and Limitations

- **Advantages**: multi-algorithm ensemble with explicit performance screening (ROC/TSS thresholds); explainable-AI (SHAP) layer beyond simple variable-importance rankings; uncertainty-aware treeline-shift detection via bootstrapped CIs instead of a single deterministic threshold; aspect-resolved spatial analysis adds ecological nuance beyond simple area totals.
- **Limitations (critical reading)**:
  - Single study site (117.1 km², one mountain) and single species (*L. chinensis*) — generalizability to other treeline systems/species is unverified and the authors themselves only claim the pattern is "ubiquitous" by citing other regions, not by testing it.
  - Occurrence data is from 2010 imagery only; the "current" model is thus already ~15 years out of date relative to publication, and no repeated/independent validation imagery is used.
  - HSI is explicitly acknowledged by the authors as a proxy for potential suitability, not the actual/physical treeline position — the paper's own limitations section states that equating HSI change with treeline migration "may lead to biases," which is a significant caveat for the headline conclusions.
  - Non-climatic drivers (biotic interactions, soil properties/nutrients, disturbance, regeneration ecology) are excluded from the model entirely, despite being flagged in the introduction as locally important (e.g., shrub-tree facilitation, topography-dominated systems).
  - Correlative model (SDM/HSI), not a mechanistic/process-based one — reported "thermal thresholds" (Bio5, GDD) are statistical inflection points in SHAP curves, not experimentally verified physiological limits; causal language ("primary limiting factors," "governing establishment and migration") somewhat overstates what a correlative ensemble SDM can support.
  - No field validation of the projected future scenarios (2040s-2100s) is possible by construction; results are projections only, appropriately framed as "indicative" in the conclusion but summarized more strongly in the abstract.
  - Downscaling of bioclimatic variables relies on a random-forest regression against topography validated with only one external temperature dataset (Qin et al., 2018, summer temperature only) — validation of other bioclimatic variables (e.g., precipitation-related) is not reported.

## Conclusion

- Growing-season thermal variables (Bio5, GDD) are identified as the proximate limiting factors for *L. chinensis* establishment and upward migration at the Mount Taibai treeline, with elevation acting as an integrative proxy for these thermal gradients.
- Future climate scenarios point to a general net expansion of suitable habitat, but with strongly aspect-dependent spatial heterogeneity: southern slopes gain, northern slopes lose suitability, under all emission pathways.
- The authors caution that HSI-based projections indicate *potential* treeline dynamics, not confirmed range shifts, and call for future work integrating high-resolution remote sensing with field monitoring to validate actual treeline movement.

## Related pages
- [[noce_2023_altitude_shift_tree_italy]]
- [[dyderski_2025_species_shift]]
- [[albrich_2019_climate_change_mountain_forests]]
- [[species_distribution_models]]
- [[topographic_microclimate]]
- [[treeline_ecotone_theory]]
- [[treeline_remote_sensing_monitoring]]
