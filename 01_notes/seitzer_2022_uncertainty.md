---
title: "On the Pitfalls of Heteroscedastic Uncertainty Estimation with Probabilistic Neural Networks"
authors:
  - Seitzer, Maximilian
  - Tavakoli, Arash
  - Antić, Dimitrije
  - Martius, Georg
year: 2022
source: seitzer_2022_uncertainty
tags:
  - deep-learning
  - machine-learning
keywords:
  - heteroscedastic uncertainty
  - negative log-likelihood
  - β-NLL
  - aleatoric uncertainty
  - probabilistic neural network
  - regression
status: read
---

# Seitzer et al. 2022 — On the Pitfalls of Heteroscedastic Uncertainty Estimation with Probabilistic NNs

## Title and Authors
**On the Pitfalls of Heteroscedastic Uncertainty Estimation with Probabilistic Neural Networks**
Maximilian Seitzer, Arash Tavakoli, Dimitrije Antić, Georg Martius — *ICLR 2022* (arXiv:2203.09168).

## Quick Overview
- **Why is it relevant?** Identifies a critical pitfall of the standard Gaussian-NLL training used in [[lakshminarayan_2017_uncertainty]] and derived workflows (e.g. [[hiebl_2025_pretraining]]); proposes **β-NLL**, a one-line fix that the wiki research pipeline already adopts.
- **What was done?** Demonstrated empirically and analysed theoretically that the heteroscedastic-Gaussian NLL loss can produce poor mean fits when used with gradient-based optimisers; introduced β-NLL which weights each sample's loss by its β-exponentiated variance.
- **What is the main outcome?** β-NLL with β = 1 completely removes the gradient dependence on variance for the mean fit (recovering MSE-like training while keeping uncertainty estimation); large empirical improvements across regression benchmarks.

## Main Goal and Fundamental Concept
Standard heteroscedastic-Gaussian training assumes targets follow `N(μ(x), σ²(x))` and minimises NLL = ½ log σ² + (y-μ)² / (2σ²). The gradient of this NLL with respect to μ is inversely proportional to σ²: **points with high predicted variance contribute weaker gradients** than well-predicted points. Result: badly-predicted regions get *under*-trained because the model has learned to inflate σ² there, dampening their gradient and stabilising at a poor mean fit.

## Technical Approach
- **Setup**: predict heteroscedastic Gaussian `N(μ̂(x), σ̂²(x))` via two output heads.
- **Standard loss**: NLL = ½ log σ² + (y-μ)² / (2σ²).
- **β-NLL**: `L_βNLL = ⌊σ̂^{2β}⌋ · NLL`, where ⌊·⌋ is the stop-gradient operator (treat σ̂^{2β} as a constant for gradient computation).
- **β = 0**: recovers standard NLL.
- **β = 1**: completely removes gradient dependence on variance for the mean fit; gradient w.r.t. μ becomes equivalent to MSE while σ² is still learned for uncertainty.
- **Synthetic example**: sinusoidal regression where standard NLL fails; β-NLL recovers correct mean fit.
- **Benchmarks**: UCI regression datasets, multi-asset depth estimation, model-based RL.

## Distinctive Features
- **Sharp diagnostic**: synthetic sinusoidal example where NLL fails dramatically while MSE succeeds — exposes the issue intuitively.
- **Single-parameter family**: β-NLL interpolates smoothly between NLL (β=0) and pure MSE (β=1 for mean) while retaining variance estimation.
- **Drop-in replacement**: one line change in implementation.
- **Robust to hyperparameters**: less sensitive to learning rate and architecture choice than standard NLL.

## Experimental Setup and Results

**Synthetic sinusoidal**
- NLL: even after 10⁷ updates, fits very poorly with overconfident variance estimates
- MSE: optimal mean fit in 10⁵ updates (no uncertainty though)
- β-NLL (β=1): matches MSE mean fit + recovers calibrated uncertainty

**UCI regression**
- β-NLL outperforms NLL on RMSE and log-likelihood across most benchmarks
- β ≈ 0.5 often a good default
- Robustness to learning rate, initialisation, architecture

**Model-based RL**
- Better dynamics models lead to better downstream control performance

## Advantages and Limitations
- **Advantages**: Tiny code change with large improvement; recovers MSE mean fit with uncertainty preserved; consistently more robust to hyperparameters; theoretically and empirically motivated.
- **Limitations**: Choice of β still requires some tuning; aleatoric uncertainty quality may differ slightly from pure NLL when β=1 (downweighted variance gradients); does not address epistemic uncertainty (still requires ensembling, see [[lakshminarayan_2017_uncertainty]]).

## Conclusion
**β-NLL is the standard fix to a critical pitfall in heteroscedastic NN training and is used directly in the TRACEVE deep-ensemble pipeline** ([[hiebl_2025_pretraining]], [[traceve_pretraining]], [[ae_training]]). Combined with [[lakshminarayan_2017_uncertainty]]'s deep-ensemble recipe, β-NLL completes the canonical aleatoric + epistemic uncertainty toolbox for vegetation regression workflows.

## Related pages
- [[deep_ensemble_uncertainty]]
- [[neural_network_training]]
- [[transfer_learning_remote_sensing]]
- [[lakshminarayan_2017_uncertainty]]
- [[hiebl_2025_pretraining]]
- [[hiebl_2026_alphaearth]]
- [[traceve_pretraining]]
- [[ae_training]]
- [[sylvain_2024_tree_species_uncertainty]]
- [[sylvain_2021_ensemble]]
