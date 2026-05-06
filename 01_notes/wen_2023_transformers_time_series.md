---
title: "Transformers in Time Series: A Survey"
authors:
  - Wen, Qingsong
  - Zhou, Tian
  - Zhang, Chaoli
  - Chen, Weiqi
  - Ma, Ziqing
  - Yan, Junchi
  - Sun, Liang
year: 2023
source: wen_2023_transformers_time_series
tags:
  - deep-learning
  - machine-learning
  - remote-sensing
status: read
---

# Wen et al. 2023 — Transformers in Time Series: A Survey

## Title and Authors
**Transformers in Time Series: A Survey**
Qingsong Wen, Tian Zhou, Chaoli Zhang et al. — *arXiv / IJCAI 2023*

## Quick Overview
- **Why is it relevant?** Comprehensive survey of Transformer architectures adapted for time series tasks, directly relevant to understanding SITS-former architectures used in satellite image time series classification for forest mapping.
- **What was done?** Systematically reviewed Transformer variants for time series from two perspectives: network structure modifications and application domains (forecasting, anomaly detection, classification), with empirical robustness and model size analyses.
- **What is the main outcome?** Transformers excel at long-range dependency modelling in time series; attention modifications (sparse, linear) are critical for efficiency with long sequences; seasonal-trend decomposition improves performance; classification applications are growing.

## Main Goal and Fundamental Concept
The Transformer's success in NLP and vision triggered extensive adaptation for time series. This survey provides the first systematic taxonomy of time series Transformer modifications and applications, identifying architectural patterns (positional encoding, attention modules, architecture level) and three main application domains (forecasting, anomaly detection, classification).

## Technical Approach
Survey taxonomy from two perspectives:
**Network structure modifications:**
- Positional encoding: vanilla sinusoidal, learnable timestamp/temporal encoding
- Attention modules: scaled dot-product, sparse attention, linear attention, multi-scale attention
- Architecture level: encoder-only, decoder-only, encoder-decoder; hierarchical and decomposed architectures

**Application domains:**
- Time series forecasting (most studied)
- Anomaly detection
- Classification (relevant for SITS)

Empirical analysis: robustness tests, model size scaling, seasonal-trend decomposition analysis

## Distinctive Features
- First comprehensive survey specifically for time series Transformers (vs. general DL time series reviews)
- Identifies key differences between general time series and satellite time series characteristics (multivariate, irregular sampling, missing data)
- Empirical comparison across multiple architectures on benchmark datasets
- Provides GitHub resource continuously updated with new papers

## Key Findings for Time Series Classification
- Self-attention captures global temporal dependencies without distance penalty (unlike LSTM)
- Multi-variate time series (multiple spectral bands) benefit from cross-channel attention
- Irregular sampling and missing data require special handling (interpolation resampling, masking)
- Pre-training Transformers on large unlabelled time series (SSL) improves classification with limited labels
- Seasonal-trend decomposition as preprocessing improves Transformer performance on periodic signals (e.g., vegetation phenology)

## Relevant Architectures for SITS
- **TST (Time Series Transformer):** Encoder-only, patch-based tokenisation; directly applied to SITS
- **PatchTST:** Uses patching to reduce sequence length while maintaining temporal context
- **SITS-Former variants:** Adaptations of Transformer for irregular, multivariate satellite time series

## Advantages and Limitations
- **Advantages:** Comprehensive coverage; empirical evaluation; connects to latest developments
- **Limitations:** Time series classification is less covered than forecasting; satellite-specific challenges (cloud contamination, irregular sampling) are acknowledged but not deeply addressed

## Conclusion
Transformers are increasingly competitive with or superior to LSTM/CNN for time series tasks, especially for long-range dependency modelling. For SITS classification applications, attention mechanisms that handle multivariate irregular series, pre-training on large archives (SSL), and seasonal-trend-aware architectures are the most relevant development directions.

## Related pages
- [[vaswani_2023_attention_is_all]]
- [[neural_network_training]]
- [[transfer_learning_remote_sensing]]
- [[hiebl_2025_pretraining]]
- [[phenology]]
