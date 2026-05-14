---
name: spatial_proxies_random_forest
description: Adding coordinates, Euclidean distance fields, or RFsp as random-forest predictors — when this helps spatial prediction and when it overfits
type: reference
tags:
  - machine-learning
  - remote-sensing
  - methodology
---

# Spatial Proxies in Random Forests

**Summary**: Spatial proxies are spatially indexed variables (coordinates, Euclidean distance fields, distance-to-sample matrices) added as predictors to "aspatial" machine-learning models to absorb residual spatial autocorrelation. Their suitability is conditional, not universal — they are useful only for spatial interpolation when residual autocorrelation is strong and samples are well-spread, and never for spatial-model transfer.

**Sources**: [[mila_2024_spatial_proxies]]

**Last updated**: 2026-05-13

---

## What Counts as a "Spatial Proxy"

A spatial proxy is a predictor with infinite or very long autocorrelation range that has no causal relationship to the response but encodes location. Three types are common (source: [[mila_2024_spatial_proxies]]):

- **Coordinates**: raw geographic or projected x/y added as two predictors. Simplest and most widely used.
- **Euclidean distance fields (EDFs)** (Behrens et al. 2018): distances from each cell to a small set of reference points (e.g. four corners + centre). Designed to handle both autocorrelation and non-stationarity.
- **RFsp** (Hengl et al. 2018): one distance field per training sample → as many proxy predictors as samples. Mimics regression kriging but inside an RF.

The number of proxy predictors grows from 2 (coordinates) → ~5 (EDFs) → n (RFsp). More proxies amplify both potential gains and potential harms.

## When Proxies Help (Decision Rules)

From the 12,800-model simulation in (source: [[mila_2024_spatial_proxies]]):

| Condition | Required for proxies to help? |
|----|----|
| Sampling and prediction areas overlap (interpolation, not extrapolation) | **Yes — necessary** |
| Residual spatial autocorrelation exists (missing predictors or autocorrelated error) | **Yes — necessary** |
| Samples regularly or randomly distributed | **Yes — strongly preferred** |
| Long autocorrelation range | Strengthens the benefit |

If any condition fails, proxies are at best neutral and often harmful.

## Why Proxies Fail in Each Failure Mode

- **Spatial-model transfer (extrapolation)**: proxies are spatially restricted to the sampling area; predicting elsewhere always lies outside the proxy feature range → 100% feature extrapolation per the [[area_of_applicability]] (source: [[mila_2024_spatial_proxies]]).
- **No residual autocorrelation present**: proxies act as irrelevant noise predictors; RF is robust but not immune, and occasionally degrades.
- **Clustered samples**: proxies can perfectly predict cluster identity → spatial overfitting; the model "memorises" sample locations. Proxy variable importance is actually *higher* under clustering, the opposite of what would be useful.
- **RFsp / EDFs amplify both directions**: when conditions are right, they outperform plain coordinates; when conditions are wrong, they fail harder.

## Detecting When Proxies Are Appropriate

A two-step diagnosis (source: [[mila_2024_spatial_proxies]]):

1. **A priori — spatial exploratory analysis**
   - Point-pattern statistics (Ĝ, F̂, K̂ with Monte Carlo envelopes) to test departure from complete spatial randomness → clustering?
   - Empirical variograms of response and baseline-model residuals → strength and range of autocorrelation
2. **A posteriori — model selection**
   - Probability test samples (if available) or kNNDM CV correctly rank proxy vs no-proxy models.
   - **Random k-fold CV should not be used** — it systematically favours proxy models, especially with clustered samples, even when proxies hurt true performance.

## Case-study Contrast (Continental Spain 2019)

(source: [[mila_2024_spatial_proxies]])

| Case | Samples | Autocorr | Proxies help? | Confirmed by |
|---|---|---|---|---|
| Air temperature (AEMET, n=195) | Well spread | Strong | Yes — naive + proxies ≈ full model (R² 0.88–0.90) | Random CV and kNNDM CV agree |
| PM2.5 (MITECO, n=124) | Clustered | Weak | No — random CV said yes but kNNDM CV exposed it as overfit (R² stays near 0) | Strong divergence between CV strategies + mapping artefacts |

## Alternative: RF–GLS

RF–GLS (Saha et al. 2023) replaces proxy predictors with an explicit Gaussian-process residual covariance, a global GLS-style split criterion, contrast resampling, and residual kriging. In Mila et al.'s simulations it matched or beat the best standard RF (with or without proxies) across all 64 parameter combinations, with the largest gains under autocorrelated-error scenarios with regular/random samples (source: [[mila_2024_spatial_proxies]]). It is positioned as a serious modern alternative to proxy hacks for spatial prediction.

## Related concepts
- [[area_of_applicability]]
- [[sampling_bias_remote_sensing]]
- [[transfer_learning_remote_sensing]]
