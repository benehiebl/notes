---
title: "Deep learning for forest inventory and planning: a critical review on the remote sensing approaches so far and prospects for further applications"
authors:
  - Hamedianfar, Alireza
  - Mohamedou, Cheikh
  - Kangas, Annika
  - Vauhkonen, Jari
year: 2022
source: hamedianfar_2022_deep_learning
tags:
  - deep-learning
  - remote-sensing
  - machine-learning
keywords:
  - deep learning
  - forest inventory
  - convolutional neural network
  - CNN architecture
  - data requirements
  - overfitting
  - transfer learning
  - review
status: read
---

# Hamedianfar et al. 2022 — Deep Learning for Forest Inventory and Planning: A Critical Review

## Title and Authors
**Deep learning for forest inventory and planning: a critical review on the remote sensing approaches so far and prospects for further applications**
Alireza Hamedianfar, Cheikh Mohamedou, Annika Kangas, Jari Vauhkonen — *Forestry* 95: 451–465 (2022).

## Quick Overview
- **Why is it relevant?** Forestry-specific complement to the more vegetation-focused [[kattenborn_2021_review_cnn_vegetation_monitoring]]; identifies inventory-relevant DL pitfalls (training data, architecture choice, overfitting, generalisability) that matter for any wiki-related DL forest mapping work.
- **What was done?** Critical review of DL applications in forest inventory and planning, structured around CNN principles, identified challenges, and forestry-specific data considerations.
- **What is the main outcome?** DL applications in forestry are in their infancy and mostly limited to CNN-vs-shallow-ML comparisons on RS imagery; major challenges are (1) acquiring representative labelled data, (2) hyperparameter/architecture choice, (3) overfitting and generalisation; DL still lacks the causal reasoning of conventional forestry models.

## Main Goal and Fundamental Concept
DL has dominated remote-sensing image analysis since AlexNet (2012). Forestry adoption has been slower and more uneven than agricultural or general LULC use cases. The review asks: where are DL applications in forestry today, what works, what doesn't, and where should future effort go?

## Technical Approach
- Literature search across forestry + DL + RS, with focus on inventory-relevant tasks (species mapping, biomass, height, structural attributes).
- Structured by:
  1. Generic DL concepts (convolutions, fully-connected layers, pooling, RNN, autoencoders, RBM)
  2. Quantitative review: architectures + input data combinations
  3. Qualitative review: how DL principles are realised (or not) in current forestry studies
  4. Recommendations for ways forward

## Distinctive Features
- Forestry-specific framing (vs general RS / vegetation reviews).
- Explicit comparison with conventional forestry modelling, including causal-reasoning and physical-model traditions.
- Addresses inventory data types beyond imagery (plot data, LiDAR point clouds, structural attributes).
- Lists CNN architectures with practical pros/cons (depth/width, receptive field, training data requirements).

## Key Themes

**DL value proposition for forestry**
- Internal multi-scale feature learning replaces hand-crafted features (texture, GLCM, NDVI thresholds)
- Particularly valuable for 3D/multi-temporal/multi-source data where manual feature engineering is intractable
- High potential for time-series prediction via RNN/LSTM and now Transformer architectures

**Recurring challenges**
1. **Training data quantity and representativeness** — forestry tasks have small labelled datasets and uneven sampling along environmental gradients
2. **Architecture and hyperparameter selection** — many degrees of freedom, sparse forestry-specific best practices
3. **Overfitting / generalisability** — proper validation strategies critical (see [[spatial_proxies_random_forest]] for spatial CV pitfalls)
4. **Black-box concern** — DL models difficult to interrogate vs causal forestry models

**Recommended directions**
- Re-think forestry applications in DL-native terms (multi-source fusion, temporal sequences, end-to-end optimisation)
- Use Transfer Learning to reduce data requirements (see [[transfer_learning_remote_sensing]], [[hiebl_2025_pretraining]])
- Adopt RNN/Transformer architectures for time series (cf. [[transformers_time_series]])
- Build causal/process knowledge into DL via hybrid physics-informed models ([[reichstein_2019_deep_learning_earth_sciences]])

## Survey of Use Cases

- **Tree species classification**: CNNs dominate over shallow ML on imagery; gains depend on data quantity and inter-class similarity
- **Biomass / AGB**: regression CNNs help especially with VHR or multi-source data
- **Forest structure / height**: dense prediction CNNs increasingly common (cf. [[lang_2024_canopy_height]])
- **Disturbance / change detection**: encoder-decoder (U-Net-like) architectures (cf. [[zhao_2022_forest_harvesting]])
- **Forest type / LULC**: standard CNN/U-Net workflows

## Advantages and Limitations
- **Advantages**: Forestry-specific lens; pragmatic recommendations; covers data sources beyond imagery; pairs technical and operational considerations.
- **Limitations**: Pre-2022, so misses the foundation-model wave (Prithvi, AlphaEarth, PRESTO); does not cover Transformer architectures in depth; methodology review > empirical benchmarking.

## Conclusion
**DL is potentially transformative for forest inventory but currently underused beyond surface-level CNN-vs-shallow-ML comparisons.** Major progress requires forestry researchers to (1) engineer training datasets that span environmental gradients, (2) adopt validation strategies that test generalisability honestly, (3) move beyond pure-imagery DL to multi-source fusion and time-series architectures, and (4) integrate causal forestry knowledge with DL via hybrid models. The review remains a useful map of the territory but is now partly outdated by the foundation-model era.

## Related pages
- [[kattenborn_2021_review_cnn_vegetation_monitoring]]
- [[transfer_learning_remote_sensing]]
- [[neural_network_training]]
- [[safonova_2023_small_data]]
- [[tree_species_mapping]]
- [[reichstein_2019_deep_learning_earth_sciences]]
- [[hiebl_2025_pretraining]]
- [[brown_2025_alphaearth]]
- [[transformers_time_series]]
- [[spatial_proxies_random_forest]]
