---
title: "An Empirical Study on Data Augmentation for Pixelwise Satellite Image Time-Series Classification and Cross-Year Adaptation"
authors:
  - Yuan, Yuan
  - Lin, Lei
  - Xin, Qi
  - Zhou, Zeng-Guang
  - Liu, Qingshan
year: 2025
source: yuan_2025_sits_augmentation
tags:
  - deep-learning
  - remote-sensing
  - machine-learning
status: read
---

# Yuan et al. 2025 — Data Augmentation for Pixel-Wise SITS Classification and Cross-Year Adaptation

## Title and Authors
**An Empirical Study on Data Augmentation for Pixelwise Satellite Image Time-Series Classification and Cross-Year Adaptation**
Yuan Yuan, Lei Lin, Qi Xin, Zeng-Guang Zhou, Qingshan Liu — *IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing*, 2025

## Quick Overview
- **Why is it relevant?** Provides the most systematic empirical evaluation of data augmentation for pixel-wise SITS classification, directly relevant for improving classification models when labelled RS time series data is limited.
- **What was done?** Evaluated 11 augmentation techniques and their combinations for pixel-wise satellite time series (Sentinel-2) classification using four DL architectures (CNN, RNN, Transformer, hybrid), including cross-year adaptation experiments.
- **What is the main outcome?** Interpolation resampling is particularly effective for irregular/incomplete SITS; augmentation benefits depend heavily on architecture, sequence length, and sample size; no single technique dominates across all conditions.

## Main Goal and Fundamental Concept
Supervised DL for SITS classification requires large labelled datasets, but annotation is expensive in RS. Data augmentation generates synthetic training samples through label-preserving transformations, effectively enlarging training sets. However, general time series augmentation techniques require adaptation for satellite time series' unique properties: multivariate spectral bands, irregular/incomplete sampling (cloud gaps), and spatio-temporal heterogeneity across years.

## Technical Approach
- **Dataset:** Sentinel-2 SITS, pixelwise classification task (land cover)
- **Architectures evaluated:** CNN, LSTM/RNN, Transformer, CA-TCN (hybrid)
- **11 augmentation techniques:**
  - Spectral domain: noise injection, scaling, mixup, DBA (dynamic time warping barycentric averaging)
  - Temporal domain: temporal dropout, window slicing, temporal shift, time warping
  - Mixed domain: interpolation resampling (new), amplitude jittering, phase jittering
- **Experiments:** Same-year and cross-year test sets; varying sequence length, sample size, time period, parameter sensitivity
- **Novel contribution:** Interpolation resampling — handles irregular/incomplete SITS by resampling temporal positions to simulate different observation intervals

## Distinctive Features
- First study to specifically test augmentation for **pixelwise** (not object-based) SITS classification
- Introduces interpolation resampling designed for SITS's inherent irregular sampling and missing data
- Explicitly tests cross-year adaptation — does augmentation improve generalisation across years?
- Evaluates on modern architectures including Transformer and hybrid CA-TCN

## Experimental Setup and Results
- **Interpolation resampling:** Best performance when missing data is severe; significantly improves cross-year adaptation
- **Noise injection + scaling:** Broadly effective across architectures; simple and fast
- **Temporal shift:** Useful for cross-regional phenology simulation; improves year-to-year robustness
- **DBA and time warping:** More computationally expensive; context-dependent benefits
- **Cross-year adaptation:** Augmentation reduces accuracy degradation when applying models to a different year; interpolation resampling provides the largest cross-year benefit
- **No universal best technique:** Best choice depends on architecture, sample size, and sequence length

## Advantages and Limitations
- **Advantages:** Comprehensive systematic evaluation; SITS-specific techniques; cross-year evaluation is novel and practically important; code open-source on GitHub
- **Limitations:** Evaluated on one primary dataset/region; effect of augmentation may vary with geographic context; deep generative augmentation (GANs) not included

## Conclusion
Data augmentation substantially improves SITS classification under limited labelled data, but the best technique depends on context. Interpolation resampling is the most important novel contribution for SITS, directly addressing cloud contamination and irregular sampling. Cross-year adaptation benefits confirm that augmentation helps generalise models across years — particularly valuable for operational monitoring applications.

## Related pages
- [[transfer_learning_remote_sensing]]
- [[neural_network_training]]
- [[sentinel_2]]
- [[phenology]]
- [[sampling_bias_remote_sensing]]
