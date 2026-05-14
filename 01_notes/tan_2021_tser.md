---
title: "Time series extrinsic regression: Predicting numeric values from time series data"
authors:
  - Tan, Chang Wei
  - Bergmeir, Christoph
  - Petitjean, François
  - Webb, Geoffrey I.
year: 2021
source: tan_2021_tser
tags:
  - machine-learning
  - deep-learning
keywords:
  - time series extrinsic regression
  - TSER
  - ROCKET
  - benchmark
  - LFMC
  - crop yield
  - InceptionTime
  - scalar-on-function regression
status: read
---

# Tan et al. 2021 — Time Series Extrinsic Regression (TSER) Benchmark

## Title and Authors
**Time series extrinsic regression: Predicting numeric values from time series data**
Chang Wei Tan, Christoph Bergmeir, François Petitjean, Geoffrey I. Webb — *Data Mining and Knowledge Discovery* 35: 1032–1060 (2021).

## Quick Overview
- **Why is it relevant?** Defines and benchmarks **time series extrinsic regression (TSER)** — predicting a scalar from a time series, e.g. EVE cover from S2 SITS, LFMC from satellite reflectance — the exact task structure used in [[hiebl_2025_pretraining]] and [[hiebl_2026_alphaearth]].
- **What was done?** Assembled the first TSER benchmark (19 datasets including LFMC from satellite spectral series); adapted state-of-the-art TS classification (TSC) and ML methods to regression; benchmarked Rocket, ResNet, InceptionTime, XGBoost, RF, SVR.
- **What is the main outcome?** **Rocket** (adapted from TSC) achieves the highest overall accuracy; most ML methods perform similarly to each other and well below their TSC counterparts on the analogous classification tasks — TSER as a field needs much more work.

## Main Goal and Fundamental Concept
Time series literature has two well-developed strands: **time series classification (TSC)** and **time series forecasting (TSF)**. Many real-world problems — predicting heart rate from accelerometer, crop yield from S2 SITS, **LFMC from satellite reflectance** — don't fit either: the target is a continuous scalar (regression) but it isn't a future value of the series (forecasting). Tan et al. formalise this **third task**, build a benchmark, and adapt existing methods.

## Technical Approach
- **TSER definition**: learn a mapping from a (uni- or multivariate) time series to a continuous scalar; target need not be a future value or depend on recent values.
- **Distinguish from**:
  - TSC: discrete categorical target
  - TSF: continuous target that *is* a future value
  - SoFR (statistics community): scalar-on-function regression — essentially the same problem
- **Benchmark archive**: 19 TSER datasets across domains; varying dimensions, lengths, missingness.
- **Methods adapted to regression**:
  - **TSC methods**: Rocket (random conv kernels + linear regressor), InceptionTime, ResNet, FCN
  - **ML baselines**: XGBoost, Random Forest, Support Vector Regression (with hand-crafted summary features)
- Metric: RMSE/MAE on holdout.

## Distinctive Features
- **First archive + benchmark for TSER as a category** — TSC and TSF had archives for decades; TSER did not.
- **Adapts TSC methods to regression cleanly** — shows what carries over (Rocket) and what doesn't (some CNN architectures).
- **Includes RS-relevant tasks** (LFMC prediction from satellite reflectance series, crop yield from SITS).
- **Identifies large room for improvement** — current best methods are barely better than ML baselines.

## Experimental Setup and Results

**Overall accuracy ranking (across 19 datasets)**
- **Rocket** (TSC algorithm adapted for regression): best overall
- Other TSC adaptations (InceptionTime, ResNet, FCN): competitive but no consistent advantage
- ML baselines (XGBoost, RF, SVR with hand-crafted features): close behind TSC methods
- Performance gap between best and worst methods smaller than in TSC — suggests TSER methods are far from saturated

**RS-relevant findings**
- LFMC dataset (12-month satellite reflectance series): Rocket gives the best results among tested methods; absolute RMSE still leaves room for improvement
- Crop yield prediction: similar pattern

## Advantages and Limitations
- **Advantages**: Formalises a previously under-studied task; provides a standardised benchmark; documents a clear field-level need for better methods; RS-relevant datasets included.
- **Limitations**: Pre-Transformer era for TSER specifically — does not include MTS Transformers like [[zerveas_2020_framework_transformer]] (which appeared concurrently); benchmark heterogeneity makes per-domain conclusions tricky; LFMC and yield are single datasets — not representative of full forest/ecological diversity.

## Conclusion
**TSER is the right framing for many wiki forest mapping tasks** — predict canopy cover, fraction, height, or biomass from a multi-temporal RS series. The benchmark exposes that current methods leave significant headroom; in practice, the wiki workflow has moved on to Transformer-based MTS approaches ([[zerveas_2020_framework_transformer]], [[yuan_2023_pretraining]], [[hiebl_2025_pretraining]]) that post-date Tan et al. but build on similar foundations. Useful as the canonical citation when framing scalar-from-SITS problems.

## Related pages
- [[transformer_sits]]
- [[transformers_time_series]]
- [[zerveas_2020_framework_transformer]]
- [[yuan_2022_sitsformer]]
- [[yuan_2023_pretraining]]
- [[wen_2023_transformers_time_series]]
- [[hiebl_2025_pretraining]]
- [[hiebl_2026_alphaearth]]
- [[reichstein_2019_deep_learning_earth_sciences]]
- [[neural_network_training]]
