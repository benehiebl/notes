---
title: "Simple and Scalable Predictive Uncertainty Estimation using Deep Ensembles"
authors:
  - Lakshminarayanan, Balaji
  - Pritzel, Alexander
  - Blundell, Charles
year: 2017
source: lakshminarayan_2017_uncertainty
tags:
  - deep-learning
  - machine-learning
keywords:
  - deep ensembles
  - predictive uncertainty
  - calibration
  - proper scoring rules
  - adversarial training
  - out-of-distribution
  - Bayesian NN
  - dropout
status: read
---

# Lakshminarayanan et al. 2017 — Simple and Scalable Predictive Uncertainty Estimation Using Deep Ensembles

## Title and Authors
**Simple and Scalable Predictive Uncertainty Estimation using Deep Ensembles**
Balaji Lakshminarayanan, Alexander Pritzel, Charles Blundell (DeepMind) — *NeurIPS 2017* (arXiv:1612.01474v3).

## Quick Overview
- **Why is it relevant?** Foundational paper establishing **deep ensembles** — the uncertainty-quantification approach used in [[hiebl_2025_pretraining]], [[sylvain_2024_tree_species_uncertainty]], [[hiebl_2026_alphaearth]], and most modern probabilistic vegetation regression workflows.
- **What was done?** Proposed a simple recipe: train M independently initialised neural networks with a proper scoring rule (NLL); aggregate predictions at test time; (optionally) add adversarial training to smooth distributions.
- **What is the main outcome?** Deep ensembles produce well-calibrated uncertainty estimates that match or exceed approximate Bayesian neural networks, are much easier to implement, and scale to ImageNet.

## Main Goal and Fundamental Concept
Bayesian neural networks are the textbook approach to predictive uncertainty but require approximations (variational inference, MCMC) that complicate training and don't scale. Lakshminarayanan et al. argue that **a frequentist alternative — train multiple networks from different random initialisations, treat them as an ensemble** — gives equal or better uncertainty quality with vastly simpler implementation.

## Technical Approach
- **Recipe**:
  1. Train each network with a **proper scoring rule** (NLL for regression and classification — for regression, predict both mean and variance of a Gaussian; for classification, use softmax + cross-entropy)
  2. Train **M independent networks** with different random initialisations
  3. **(Optional) Adversarial training** to smooth predictive distributions
- **Output**:
  - Mean prediction = ensemble mean of individual means
  - Total predictive variance = ensemble mean of individual variances (aleatoric) + variance of individual means (epistemic)
- **Evaluation metrics**:
  - **Calibration**: log-likelihood, Brier score on in-distribution data
  - **Out-of-distribution detection**: higher uncertainty on novel inputs
  - Benchmarks: regression (UCI), classification (MNIST, CIFAR-10, ImageNet)

## Distinctive Features
- **Simplicity**: minimal modifications to standard training — just train M networks.
- **Parallelisable**: each ensemble member trains independently → trivially distributed.
- **Proper-scoring-rule training** (Gaussian NLL for regression) jointly estimates mean and variance.
- **First non-Bayesian method evaluated on ImageNet for predictive uncertainty**.
- Theoretically motivated by Bayesian model averaging but practically a frequentist ensemble.

## Experimental Setup and Results

**Vs Bayesian baselines (MC-Dropout, variational inference, MCMC)**
- Deep ensembles match or outperform on calibration metrics
- Better OOD uncertainty (higher uncertainty on novel inputs)
- Much faster to train (no specialised optimisation)

**Effect of M (ensemble size)**
- Modest gains from M=1→5; saturation typically by M=10–15
- Larger M improves calibration steadily but with diminishing returns

**Adversarial training**
- Smooths predictive distributions
- Improves calibration on harder benchmarks
- Adds cost but optional

**ImageNet demonstration**
- Scalable to large architectures (ResNet)
- Uncertainty estimates remain useful at scale

## Advantages and Limitations
- **Advantages**: Simple, scalable, parallelisable; minimal training-pipeline changes; gives both aleatoric and epistemic uncertainty; competitive with much more complex Bayesian methods.
- **Limitations**: Requires M models to be stored and inferred — proportional memory and compute; epistemic uncertainty quality depends on ensemble diversity (which can be limited if all members converge to similar minima); does not address fundamental distribution-shift problems; aleatoric variance estimate fragile under naive NLL training (see [[seitzer_2022_uncertainty]] for the β-NLL fix).

## Conclusion
**Deep ensembles are the canonical practical approach to predictive uncertainty in deep learning** — simple, scalable, and competitive with Bayesian methods. The recipe (M independent networks + proper scoring rule + optional adversarial training) is directly used in the wiki's research pipeline: [[hiebl_2025_pretraining]] uses a shared-backbone deep ensemble with M=15 heads; [[sylvain_2024_tree_species_uncertainty]] uses a 9-model CNN super-ensemble; [[lang_2024_canopy_height]] uses an ensemble for tall-canopy retrieval. The β-NLL refinement of [[seitzer_2022_uncertainty]] is a critical follow-up.

## Related pages
- [[deep_ensemble_uncertainty]]
- [[neural_network_training]]
- [[transfer_learning_remote_sensing]]
- [[seitzer_2022_uncertainty]]
- [[sylvain_2024_tree_species_uncertainty]]
- [[sylvain_2021_ensemble]]
- [[hiebl_2025_pretraining]]
- [[hiebl_2026_alphaearth]]
- [[lang_2024_canopy_height]]
- [[area_of_applicability]]
- [[zangh_2017_generalization]]
