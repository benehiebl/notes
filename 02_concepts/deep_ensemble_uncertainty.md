---
name: deep_ensemble_uncertainty
description: Deep ensembles for predictive uncertainty in neural networks — proper scoring rules, β-NLL, epistemic + aleatoric components, and applications in remote sensing regression
type: reference
tags:
  - deep-learning
  - machine-learning
---

# Deep Ensemble Uncertainty

**Summary**: Deep ensembles — training M neural networks from different random initialisations and aggregating their predictions — are the canonical practical approach to predictive uncertainty in deep learning. Combined with proper scoring rules (Gaussian NLL or β-NLL for heteroscedastic regression), they deliver well-calibrated epistemic + aleatoric uncertainty estimates that match or exceed Bayesian neural networks at a fraction of the implementation cost.

**Sources**: [[lakshminarayan_2017_uncertainty]], [[seitzer_2022_uncertainty]], [[hiebl_2025_pretraining]], [[sylvain_2024_tree_species_uncertainty]], [[sylvain_2021_ensemble]], [[lang_2024_canopy_height]]

**Last updated**: 2026-05-14

---

## The Recipe (Lakshminarayanan et al. 2017)

1. **Proper scoring rule** as training objective:
   - Classification: softmax + cross-entropy (= log-likelihood = Brier score)
   - Regression: heteroscedastic Gaussian NLL — predict both mean μ(x) and variance σ²(x)
2. **M independently initialised networks** trained from scratch
3. **(Optional) Adversarial training** to smooth predictive distributions

At test time:
- **Predictive mean** = ensemble mean of individual means
- **Aleatoric uncertainty** = ensemble mean of individual variances σ²(x)
- **Epistemic uncertainty** = variance across individual means
- **Total predictive variance** = aleatoric + epistemic

(source: [[lakshminarayan_2017_uncertainty]])

## The β-NLL Fix for Regression (Seitzer et al. 2022)

Standard heteroscedastic Gaussian NLL has a critical pitfall: the loss `½ log σ² + (y-μ)² / (2σ²)` produces gradients with respect to μ inversely proportional to σ². Badly-predicted points inflate σ² → weaker gradients → stay badly predicted (source: [[seitzer_2022_uncertainty]]).

**β-NLL** fixes this by weighting each sample's loss by its β-exponentiated variance (stop-gradient applied):
- β = 0: recovers standard NLL
- β = 1: completely removes the σ² dependence in the gradient — mean fit equivalent to MSE while σ² is still learned
- β ≈ 0.5: common practical default

**One-line implementation change with large empirical improvements** (source: [[seitzer_2022_uncertainty]]).

## Epistemic vs Aleatoric

| Type | What it captures | How estimated | Spatial pattern |
|------|------------------|---------------|----------------|
| **Epistemic (EU)** | Model uncertainty — lack of training data coverage | Variance across ensemble predictions | Spatially coherent — flags OOD regions |
| **Aleatoric (AU)** | Observation noise / label ambiguity | Learned per-pixel variance | Spatially incoherent — captures local noise |

EU is **reducible** with more or better data; AU is **inherent** in the observation process.

## Applications in the Wiki

**TRACEVE deep ensemble (Hiebl et al. 2025)**
- Shared InceptionTime backbone + M=15 prediction heads (source: [[hiebl_2025_pretraining]])
- β-NLL training (source: [[seitzer_2022_uncertainty]])
- High EU → flags OOD regions (non-forest, shaded slopes, underrepresented forest types)
- Spatially coherent EU maps guide active learning

**CNN super-ensemble (Sylvain et al. 2024)**
- 9 fully separate CNNs (source: [[sylvain_2024_tree_species_uncertainty]])
- Inter-model agreement % as a uncertainty proxy when explicit probabilistic training is not used
- Strong correlation with F1-score → validated as reliable

**Soil mapping ensemble (Sylvain et al. 2021)**
- Triple-resampling (observations + covariates + hyperparameters) + bias correction (source: [[sylvain_2021_ensemble]])
- Ensemble deterministic prediction in top quantile of components
- Conditional bias reduced 25–50%; uncertainty still ~50% under-dispersed

**Canopy height global model (Lang et al. 2024)**
- Ensemble of probabilistic CNNs over GEDI + S2 (source: [[lang_2024_canopy_height]])
- Per-pixel uncertainty + ensemble averaging targets tall-canopy retrieval

## Practical Recommendations

- **M = 5–15 ensemble members** typically sufficient
- **Use β-NLL** (β = 0.5 or 1) instead of standard NLL for regression
- **Compute both EU and AU** — they reveal different problems
- **EU is the right signal for active learning** — direct field data collection where EU is high
- **Compare ensemble outputs across pretraining strategies** to disentangle pretraining contribution from random initialisation variance (cf. [[transfer_learning_remote_sensing]])
- **Triple-resampling** (Sylvain et al. 2021) generalises bootstrap to richer pseudo-model diversity

## Limitations

- M models = M × memory and inference cost — non-trivial at scale
- Ensemble diversity bounded by random initialisation — augment with adversarial training, diverse architectures, or hyperparameter diversity
- Aleatoric estimate fragile under naive NLL — β-NLL essential (source: [[seitzer_2022_uncertainty]])
- Uncertainty often under-dispersed in practice (~40–60% local underestimation; source: [[sylvain_2021_ensemble]])
- Does not directly address distribution shift / spatial transferability (see [[area_of_applicability]], [[spatial_proxies_random_forest]] for complementary tools)

## Related concepts
- [[transfer_learning_remote_sensing]]
- [[neural_network_training]]
- [[area_of_applicability]]
- [[spatial_proxies_random_forest]]
