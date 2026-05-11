---
name: neural_network_training
description: Neural network training via backpropagation — optimisation, input normalisation, activations, weight initialisation, learning rates, regularisation, and modern optimizers
type: reference
tags:
  - deep-learning
  - machine-learning
---

# Neural Network Training

**Summary**: Neural network training via backpropagation requires careful choices at every stage — input preprocessing, activation functions, weight initialisation, learning rate, and optimizer — to avoid slow convergence, saturation, and overfitting; the underlying principle is that gradient descent converges fastest when the loss surface is locally spherical.

**Sources**: [[lecun_1998_efficient_backprop]], [[hiebl_2025_pretraining]]

**Last updated**: 2026-05-05

---

## Backpropagation

Backpropagation is the standard algorithm for computing gradients in multilayer neural networks:
- Forward pass: compute outputs layer by layer using current weights
- Backward pass: propagate error gradients from output to input using the chain rule (Jacobian at each layer)
- Weight update: W(t) = W(t−1) − η ∂E/∂W

The gradient at any layer depends on the product of Jacobians of all downstream layers — making the loss surface highly non-convex in deep networks (source: [[lecun_1998_efficient_backprop]])

## Stochastic vs Batch Learning

| Mode | Update rule | When to prefer |
|------|-------------|---------------|
| **SGD (online)** | One example per update; noisy gradient | Large, redundant datasets; non-stationary distributions |
| **Mini-batch** | Small batch (16–512) per update | Standard modern practice; balances noise and stability |
| **Batch** | Full dataset per update | Small datasets; when second-order methods are tractable |

- SGD noise can escape shallow local minima → often finds better solutions than batch gradient descent
- Mini-batch is the standard in modern deep learning (PyTorch DataLoader default)
- (source: [[lecun_1998_efficient_backprop]])

## Input Normalisation

For fastest gradient descent convergence, inputs should be:
1. **Zero-mean**: subtract training set mean per feature; prevents biased gradient directions
2. **Unit variance**: divide by standard deviation (or percentile range); equalises learning speed across features
3. **Decorrelated**: PCA/whitening removes linear correlations between input features; reduces condition number of the Hessian

**In remote sensing practice**: Sentinel-2 time series are typically normalised per band using 2nd–95th percentile values before model training (source: [[hiebl_2025_pretraining]]); this directly implements the zero-mean / equal-variance recommendation

## Activation Functions

- **Sigmoid (logistic)**: f(x) = 1/(1+e⁻ˣ) — always positive outputs; slow convergence; prone to saturation; largely replaced
- **Tanh**: f(x) = tanh(x) — symmetric about zero; faster convergence than logistic
- **LeCun sigmoid** (1998 recommendation): f(x) = 1.7159 tanh(2x/3) — unit gain, targets at ±1 coincide with maximum curvature; still theoretically optimal for normalised inputs
- **ReLU / GELU / SiLU** (modern): f(x) = max(0,x) and variants — no saturation in positive regime; standard in modern architectures; partially circumvents vanishing gradient problem
- **Vanishing gradients**: when activations saturate (sigmoid/tanh extremes), gradients approach zero → deeper layers learn very slowly; addressed by residual connections, batch normalisation, or ReLU activations

## Weight Initialisation

**Goal**: keep pre-activation inputs in the sigmoid's linear region at network initialisation.

LeCun 1998 rule:
- σ_w = m^{−1/2} where m = fan-in (number of inputs to a node)
- Derived from requiring unit standard deviation at each neuron output when inputs are normalised

Modern extensions:
- **Xavier initialisation** (Glorot & Bengio 2010): σ_w = √(2/(fan-in + fan-out)) — accounts for both forward and backward pass variance
- **He initialisation** (He et al. 2015): σ_w = √(2/fan-in) — designed for ReLU activations; accounts for half-rectification variance reduction

## Learning Rate and the Hessian

The Hessian H = ∂²E/∂W² describes the curvature of the loss surface:
- **Optimal learning rate**: η_opt = 1/λ_max (largest eigenvalue of H); reaches minimum in one step for quadratic E
- **Maximum stable rate**: η_max = 2η_opt; η > η_max causes divergence
- **Condition number** κ = λ_max/λ_min: measures elongation of loss surface; high κ → slow convergence; decorrelating inputs minimises κ

Practical implications:
- Single global η: always a compromise between fast convergence in shallow directions and stability in steep directions
- **Per-weight learning rates** or adaptive optimizers resolve this

## Modern Optimizers

All extend basic gradient descent to address the learning-rate/curvature problem:

| Optimizer | Key idea | Notes |
|-----------|---------|-------|
| **SGD + momentum** | Accumulate velocity: Δw += μΔw + η∇E | Classic; requires careful lr tuning |
| **RMSProp** | Divide lr by running RMS of gradient | Adaptive per-weight; suited for non-stationary |
| **Adam** | Momentum + adaptive lr + bias correction | Default choice for most DL tasks |
| **AdamW** | Adam + weight decay decoupled from gradient | Better regularisation than L2 in Adam |
| **K-FAC** | Approximate full Hessian inverse using Kronecker factors | True second-order; expensive but fast convergence |

## Bias-Variance Tradeoff

- **Bias**: systematic deviation of model output from true function; large early in training
- **Variance**: sensitivity to which training examples were used; large late in training (overfitting)
- **Optimal model**: minimises total error = bias² + variance; requires held-out test set evaluation
- Early stopping: stop training when validation error stops improving → controls variance without explicit regularisation

## Regularisation Techniques

- **L2 weight decay**: add λ‖W‖² to loss → penalises large weights; improves generalisation
- **Dropout**: randomly zero activations during training → implicit ensemble of sub-networks
- **Batch normalisation**: normalise layer inputs to zero mean and unit variance during training → addresses internal covariate shift; also allows higher learning rates
- **Data augmentation**: artificially expand training set via transformations; crucial for small-data remote sensing problems

## Relation to Remote Sensing Deep Learning

All principles apply directly to deep learning models for remote sensing (e.g., InceptionTime, ResNet, Transformer):
- Input normalisation: per-band percentile scaling of spectral-temporal series
- Mini-batch SGD with Adam: standard in PyTorch-based RS models
- Spatial autocorrelation in train/test splits introduces effectively correlated inputs → inflates validation performance (analogous to correlated input problem described by LeCun et al.) — see [[transfer_learning_remote_sensing]]
- Small datasets: high variance problem → addressed by pretraining (transfer learning), regularisation, and spatial cross-validation

## Related pages

- [[transfer_learning_remote_sensing]]
- [[sentinel_2]]
- [[tree_species_mapping]]
