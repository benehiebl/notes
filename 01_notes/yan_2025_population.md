---
title: "High-precision population estimates by remote sensing big data and advanced transformer deep learning model"
authors:
  - Yan, Ziyun
  - Ma, Lei
  - Wang, Xuan
  - Kim, Yongil
  - Zhang, Liqiang
year: 2025
source: yan_2025_population
tags:
  - deep-learning
  - remote-sensing
  - machine-learning
keywords:
  - population mapping
  - Transformer
  - Sentinel-2
  - urban morphology
  - SHAP
  - explainability
  - CNN
  - random forest
status: read
---

# Yan et al. 2025 — High-precision Population Estimates with Transformer DL Model

## Title and Authors
**High-precision population estimates by remote sensing big data and advanced transformer deep learning model**
Ziyun Yan, Lei Ma, Xuan Wang, Yongil Kim, Liqiang Zhang — *Remote Sensing Applications: Society and Environment* 39: 101638 (2025).

## Quick Overview
- **Why is it relevant?** Demonstrates a SHAP-interpreted comparison of RF, CNN (ResNet 50), and Transformer for gridded population mapping — methodological reference for the Transformer advantage on RS-derived urban features, with parallels for vegetation regression tasks.
- **What was done?** Trained RF, ResNet 50, and a Transformer-based model on Sentinel-2 composite imagery + building height + sky view factor + building/pervious surface fraction in four Chinese megacities; quantified feature contributions via SHAP and permutation tests.
- **What is the main outcome?** Transformer best at population regression because it reads scene semantics from imagery (not just derived urban-morphology features); a CNN-Transformer hybrid produced the highest-precision population estimates.

## Main Goal and Fundamental Concept
Gridded population mapping relies heavily on derived urban-morphology features (building height/footprint, sky view factor, impervious surface) — which models depend most on which features, and is there an architecture that can "see" population directly from satellite imagery? Yan et al. systematically compare model classes with SHAP explanations to answer this.

## Technical Approach
- **Study areas**: Beijing, Shanghai, Chengdu, Guangzhou — four megacities (population >10 M each).
- **Input**: Sentinel-2 composite (Red, Green, Blue, NIR, SWIR1, SWIR2, 10 m resampled) + Baidu building contour data → derived BH, SVF, BS, PS.
- **Labels**: WorldPop 100 m weight + county-level census for ground truth.
- **Models**:
  1. Random Forest (classic baseline)
  2. ResNet 50 (CNN baseline)
  3. Proposed Transformer model (window-based self-attention, global context)
  4. CNN-Transformer hybrid
- **Interpretability**: SHAP for feature attribution + permutation importance.

## Distinctive Features
- **SHAP-based comparison across model classes** (RF / CNN / Transformer) for the same task.
- **First Transformer application to population regression** from RS imagery.
- Identifies that RF over-relies on derived urban morphology features (BH, SVF), while Transformer extracts population-related semantics directly from raw S2 spectral channels.
- Hybrid CNN-Transformer combines local (CNN) + global (Transformer) representations.

## Experimental Setup and Results

**Model performance**
- Transformer beats RF and ResNet 50 on population regression accuracy
- CNN-Transformer hybrid: best overall — combines local urban-pattern detection (CNN) with global scene-level reasoning (Transformer)

**SHAP findings**
- RF: ~70% of explanatory weight in derived urban morphology features; little use of spectral S2 channels
- CNN (ResNet 50): more balanced reliance on spectral + morphological features
- Transformer: dominated by spectral channels — can read population-relevant scene semantics (e.g. residential vs commercial) directly
- Building Height most important among urban morphology features

**Interpretability gain**
- SHAP made each model's decision pathway visible
- Permutation analysis confirmed: Transformer least sensitive to losing any single feature

## Advantages and Limitations
- **Advantages**: First Transformer application to population mapping; SHAP-based interpretability; clear architectural comparison; CNN-Transformer hybrid framework transferable to other regression-from-imagery tasks (vegetation cover, biomass).
- **Limitations**: Only 4 Chinese megacities — generalisability to less dense regions or western cities unclear; labels rely partly on WorldPop (label transfer biases); single year (2020); model interpretability via SHAP is post-hoc only; no spatial CV evaluation (cf. [[spatial_proxies_random_forest]]).

## Conclusion
**Transformer architectures, when combined with CNN local feature extraction, set a new precision benchmark for gridded population estimation from RS imagery** — and SHAP analysis explains why: Transformers extract population-relevant scene semantics from raw spectral data without depending on hand-crafted urban morphology. The methodological pattern (Transformer with global self-attention + interpretability via SHAP) is directly relevant to any vegetation regression task using RS imagery, including EVE cover mapping in the wiki workflow.

## Related pages
- [[transformer_sits]]
- [[vaswani_2023_attention_is_all]]
- [[transformers_time_series]]
- [[wen_2023_transformers_time_series]]
- [[hiebl_2026_alphaearth]]
- [[hamedianfar_2022_deep_learning]]
- [[nguyen_2022_forest_mapping_explainable]]
- [[transfer_learning_remote_sensing]]
