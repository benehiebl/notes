---
title: "Self-Supervised Pre-Training of Transformers for Satellite Image Time Series Classification (SITS-BERT)"
authors:
  - Yuan, Yuan
  - Lin, Lei
year: 2022
source: yuan_2023_pretraining
tags:
  - deep-learning
  - remote-sensing
keywords:
  - SITS-BERT
  - Transformer
  - self-supervised pretraining
  - SITS classification
  - BERT
  - pixel-based
  - label scarcity
status: read
---

# Yuan & Lin 2022 — SITS-BERT: Self-Supervised Pre-Training of Transformers for SITS Classification

## Title and Authors
**Self-Supervised Pre-Training of Transformers for Satellite Image Time Series Classification**
Yuan Yuan, Lei Lin — *IEEE JSTARS* (2020/2022; preprint posted as TechRxiv 13025039.v3, Nov 2020). File on disk: `yuan_2023_pretraining.pdf`.

## Quick Overview
- **Why is it relevant?** First BERT-style self-supervised pretraining for SITS — pixel-based predecessor of [[yuan_2022_sitsformer]] and conceptual ancestor of [[tseng_2024_presto]]; the foundational reference for "BERT for SITS".
- **What was done?** Pretrained a Transformer (SITS-BERT) on massive unlabelled annual pixel time series via a denoising proxy task: given a time series of (observation, DOY) pairs with some noise injected, predict the clean values.
- **What is the main outcome?** Accuracy gains of 1.91–6.69 pp on three SITS classification benchmarks; first demonstration that self-supervised pretraining works for SITS.

## Main Goal and Fundamental Concept
Direct adaptation of the **BERT idea** (Devlin et al. 2018, Masked Language Modelling) to SITS. Just as masked-word prediction lets a model learn linguistic structure from unlabelled text, **predicting corrupted satellite observations from their temporal context** lets a model learn spectral-temporal structure from unlabelled SITS. The pre-trained encoder then transfers to any downstream SITS classification task with limited labels.

## Technical Approach
- **Architecture**: Transformer encoder operating on a sequence of (observation, day-of-year) tokens.
- **Tokens**: per timestep, an embedding of the spectral observation summed with a sinusoidal positional encoding of DOY.
- **Pretraining proxy**: randomly contaminate observations with Gaussian noise; train the model to regress the original clean values from the full (corrupted) sequence.
- **Pre-training data**: large unlabelled pixel time series (annual, multispectral).
- **Fine-tuning**: discard regression head, attach classification head, train on small labelled set.
- **Evaluation**: three benchmark SITS classification datasets (large study areas).

## Distinctive Features
- **First SSL for SITS** — predates SITS-Former, CROMA, PRESTO.
- **BERT-style pretext task** explicitly adapted to time-series structure rather than language tokens.
- **Sinusoidal DOY positional encoding** — handles irregular sampling and cross-year alignment without interpolation.
- **Pixel-based**: ignores spatial context but scales easily; later extended to patch-based in [[yuan_2022_sitsformer]].
- **End-to-end deep learning architecture** as an alternative to RNN/LSTM/TempCNN.

## Experimental Setup and Results

**Accuracy improvements over fully supervised baselines**
- **+1.91% to +6.69%** in overall accuracy across three benchmarks
- Larger gains in label-scarce regimes
- Outperforms supervised LSTM, GRU, and plain Transformer (no pretraining)

**Architectural finding**
- Transformer encoder + DOY encoding outperforms RNNs / TempCNNs on raw SITS
- Bidirectional context (BERT-style) helps more than left-to-right alone

## Advantages and Limitations
- **Advantages**: Simple, effective SSL adaptation; foundational template for downstream patched and multi-sensor approaches; handles irregular SITS sampling natively.
- **Limitations**: Pixel-based — misses spatial context; single-sensor (S2 only as evaluated); pretraining requires large unlabelled corpus; gains plateau when labelled data abundant; predates more recent foundation-model approaches (PRESTO, AlphaEarth) that ingest multi-sensor inputs.

## Conclusion
**SITS-BERT is the foundational reference for self-supervised pretraining of Transformers on SITS.** Its descendants — SITS-Former ([[yuan_2022_sitsformer]]), PRESTO ([[tseng_2024_presto]]), AlphaEarth ([[brown_2025_alphaearth]]) — all build on the basic insight that **predicting corrupted parts of a satellite time series from the rest learns transferable spectral-temporal representations**. For the wiki, this is the key reference for choosing between SSL pretraining strategies (masked-value prediction in [[hiebl_2025_pretraining]] follows the same template).

## Related pages
- [[transformer_sits]]
- [[transformers_time_series]]
- [[transfer_learning_remote_sensing]]
- [[vaswani_2023_attention_is_all]]
- [[yuan_2022_sitsformer]]
- [[tseng_2024_presto]]
- [[zerveas_2020_framework_transformer]]
- [[brown_2025_alphaearth]]
- [[hiebl_2025_pretraining]]
- [[chen_2020_contrastive_framework]]
- [[wen_2023_transformers_time_series]]
