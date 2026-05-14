---
title: "Using bias correction and ensemble modelling for predictive mapping and related uncertainty: A case study in digital soil mapping"
authors:
  - Sylvain, Jean-Daniel
  - Anctil, François
  - Thiffault, Évelyne
year: 2021
source: sylvain_2021_ensemble
tags:
  - machine-learning
  - remote-sensing
keywords:
  - bias correction
  - ensemble modelling
  - uncertainty
  - digital soil mapping
  - equifinality
  - conditional bias
  - quantile regression
status: read
---

# Sylvain et al. 2021 — Bias Correction + Ensemble Modelling for Predictive Mapping

## Title and Authors
**Using bias correction and ensemble modelling for predictive mapping and related uncertainty: A case study in digital soil mapping**
Jean-Daniel Sylvain, François Anctil, Évelyne Thiffault — *Geoderma* 403: 115153 (2021).

## Quick Overview
- **Why is it relevant?** Tackles three pervasive predictive-mapping pathologies — equifinality, uncertainty assessment, and conditional bias — with a generic ensemble + bias-correction framework that transfers cleanly to RS regression tasks like canopy cover and forest type proportions.
- **What was done?** Built an ensemble model with resampling of observations, covariates, and hyperparameters; corrected conditional bias inherited from ML smoothing; validated for six soil properties (sand, silt, clay, pH, CEC, OC) in Québec; benchmarked against global soil products.
- **What is the main outcome?** Bias correction reduces conditional bias by 25–50%; ensemble performance always in the top quantile of its components; uncertainty maps still underdispersed (40–60% local underestimation) — but framework substantially outperforms global products (R² −0.48 → +0.13).

## Main Goal and Fundamental Concept
Predictive mapping with ML faces three structural problems:
1. **Equifinality**: many sub-optimal hyperparameter sets give similar performance but different maps
2. **Uncertainty assessment**: hard to derive spatially explicit prediction intervals
3. **Conditional bias**: ML methods tend to smooth — they underestimate extremes (high values too low, low values too high)
Sylvain et al. propose a unified framework using resampling-based ensembles + post-hoc bias correction to address all three.

## Technical Approach
- Study area: Province of Québec, Canada.
- Variables: sand, silt, clay (texture), pH, cation exchange capacity, organic carbon — six soil properties with skewed distributions.
- Reference: 8,790 soil profiles, 13,800 horizons.
- **Resampling triple**: observations + covariates + hyperparameters — generates a set of "pseudo-models".
- **Ensemble prediction**: average of pseudo-models → deterministic value; PDF across pseudo-models → uncertainty.
- **Bias correction**: ratio-of-variance correction to recover full distribution variance (addresses smoothing-induced conditional bias).
- Benchmarking: comparison with global soil mapping products (SoilGrids, Hengl et al.).

## Distinctive Features
- **Joint treatment of equifinality + uncertainty + conditional bias** — most prior work tackles only one.
- **Triple resampling** (samples + covariates + hyperparameters) → richer pseudo-model diversity than bootstrap alone.
- **Explicit bias correction** for ML's smoothing tendency.
- Easy to implement, not computationally heavy.
- Generalises beyond soil mapping to any spatial regression.

## Experimental Setup and Results

**Bias correction effect**
- Conditional bias reduced by **25–50%** across the six soil properties
- Variance ratio (simulated/observed) improves toward 1.0 (less smoothing)
- Linearity of predictions improved

**Ensemble performance**
- Deterministic ensemble always in the first quantile of pseudo-model performance — strictly better than median pseudo-model
- More stable than any single ML realisation

**Uncertainty quality**
- Local uncertainty underestimated 40–60% of the time (under-dispersion) — main remaining limitation

**Vs global soil products**
- Global products: R² −0.48 to 0.13, alpha 0.23–0.59 (strong conditional bias)
- Sylvain framework: substantially better R² + lower conditional bias

## Advantages and Limitations
- **Advantages**: Generic framework; addresses three pathologies in one pass; computationally light; large gains vs global products; bias correction novel for digital soil mapping context.
- **Limitations**: Under-dispersed uncertainty maps (local intervals too narrow ~50% of time); soil-specific case study (transferability to other tasks asserted but not proven); requires sufficient observations for resampling; no formal spatial CV (cf. [[spatial_proxies_random_forest]]).

## Conclusion
**A triple-resampling ensemble + conditional-bias correction substantially improves digital soil maps and remains relatively simple to implement.** The three pathologies it addresses (equifinality, uncertainty estimation, conditional bias) appear in *any* RS regression task — canopy cover, AGB, EVE fraction — making the framework a useful template for the wiki's forest mapping work. Connects directly to [[deep_ensemble_uncertainty]] and [[lakshminarayan_2017_uncertainty]].

## Related pages
- [[deep_ensemble_uncertainty]]
- [[transfer_learning_remote_sensing]]
- [[lakshminarayan_2017_uncertainty]]
- [[seitzer_2022_uncertainty]]
- [[sylvain_2024_tree_species_uncertainty]]
- [[area_of_applicability]]
- [[spatial_proxies_random_forest]]
- [[miettinen_2025_forest_maps_europe]]
- [[hiebl_2025_pretraining]]
