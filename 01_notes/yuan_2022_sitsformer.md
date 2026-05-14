---
title: "SITS-Former: A pre-trained spatio-spectral-temporal representation model for Sentinel-2 time series classification"
authors:
  - Yuan, Yuan
  - Lin, Lei
  - Liu, Qingshan
  - Hang, Renlong
  - Zhou, Zeng-Guang
year: 2022
source: yuan_2022_sitsformer
tags:
  - deep-learning
  - remote-sensing
keywords:
  - SITS-Former
  - Transformer
  - self-supervised learning
  - Sentinel-2
  - patch-based classification
  - missing-data imputation
  - pretraining
  - 3D-CNN
status: read
---

# Yuan et al. 2022 — SITS-Former: Pre-trained Spatio-Spectral-Temporal Model for S2 Time Series

## Title and Authors
**SITS-Former: A pre-trained spatio-spectral-temporal representation model for Sentinel-2 time series classification**
Yuan Yuan, Lei Lin, Qingshan Liu, Renlong Hang, Zeng-Guang Zhou — *Int J Appl Earth Obs Geoinformation* 106: 102651 (2022).

## Quick Overview
- **Why is it relevant?** Combines a patch-based Transformer + 3D-CNN with self-supervised pretraining on Sentinel-2 time series — captures spectral, spatial, and temporal dependencies simultaneously; methodological precedent for spatial-context-aware SITS modelling.
- **What was done?** Pre-trained a Transformer on Sentinel-2 patch time series via a missing-data imputation proxy task; fine-tuned on crop classification benchmarks.
- **What is the main outcome?** Outperforms pure supervised SITS classifiers by 2.64–3.30 pp in overall accuracy; first SSL approach for patch-based SITS analysis.

## Main Goal and Fundamental Concept
SITS-BERT (Yuan & Lin 2021, see [[yuan_2023_pretraining]]) was pixel-based and ignored spatial context. Yuan et al. extend it to **patch-based** SITS-Former that learns spatial + spectral + temporal features jointly. Pretraining proxy: given a time series of image patches with some patches masked, regress the **central pixels** of the masked patches from the surviving ones — forces the model to learn both phenology and local spatial structure.

## Technical Approach
- **Inputs**: time series of 5×5 image patches, each tensor (10 bands × 5 × 5).
- **Image patch embedding module**: two Conv3D layers (32 filters 5×3×3 → 64 filters 3×3×3) + FC + BN+ReLU → 256-dim **Spatio-Spectral Embedding Vector (SSEV)** per patch.
- **Positional Encoding Vector**: sinusoidal encoding of Day-of-Year (DOY) — handles irregular sampling and cross-year alignment.
- **Sum**: token embedding = SSEV + PEV.
- **Transformer encoder**: standard multi-head self-attention on the sequence of patch tokens.
- **Pretraining proxy**: randomly mask patches; regress masked-patch central pixel reflectance from the rest of the sequence.
- **Fine-tuning**: discard reconstruction head, add classification head, train on labelled data.
- Tested on crop classification benchmarks (two large-scale datasets).

## Distinctive Features
- **Patch-based instead of pixel-based** — captures local spatial structure (texture, regular spacing of fruit trees, etc.).
- **3D convolution** in patch embedding exploits both **inter-band correlation** and **local spatial structure** simultaneously.
- **Self-supervised pretraining** with central-pixel regression — forces semantic representation rather than trivial copy-and-paste reconstruction.
- **DOY-based sinusoidal positional encoding** handles irregular SITS sampling without explicit interpolation.
- First SSL approach to patch-based SITS analysis (cf. [[chen_2020_contrastive_framework]] for image-based SSL).

## Experimental Setup and Results

**Crop classification accuracy gains over supervised baselines**
- Improvements: **+2.64% to +3.30%** in overall accuracy
- Outperforms LSTM, Bi-LSTM, TempCNN, plain Transformer (no pretraining) baselines

**Sample-efficiency**
- Gains larger when labelled data are scarce — characteristic SSL behaviour
- Saturates when labelled data are abundant

**Ablations**
- Conv3D embedding > Conv2D embedding (spatial + spectral correlation)
- Patch-based > pixel-based for crops with regular spatial pattern (orchards)
- Pretraining + fine-tuning consistently > fully supervised

## Advantages and Limitations
- **Advantages**: Spatial + spectral + temporal in one model; SSL leverages unlabelled SITS at scale; sinusoidal DOY encoding handles irregularity; modular (encoder reusable for any downstream task).
- **Limitations**: 5×5 patches limit spatial receptive field; pretraining cost not negligible vs lightweight models like PRESTO ([[tseng_2024_presto]]); evaluated only on crop classification (not yet on forest tasks); single-sensor (S2 only).

## Conclusion
**SITS-Former demonstrates that patch-based Transformer + self-supervised pretraining lifts SITS classification accuracy by ~3 pp** over fully supervised baselines and earlier pixel-based pretrained models. Methodologically the closest existing precedent for spatial-context-aware Italian forest type classification from S2 time series — a natural complement to the pixel-based SITS-BERT ([[yuan_2023_pretraining]]) and the multi-sensor PRESTO ([[tseng_2024_presto]]). Connects to [[transformer_sits]] concept.

## Related pages
- [[transformer_sits]]
- [[transformers_time_series]]
- [[vaswani_2023_attention_is_all]]
- [[wen_2023_transformers_time_series]]
- [[yuan_2023_pretraining]]
- [[tseng_2024_presto]]
- [[zerveas_2020_framework_transformer]]
- [[transfer_learning_remote_sensing]]
- [[chen_2020_contrastive_framework]]
- [[hiebl_2025_pretraining]]
- [[hiebl_2026_alphaearth]]
- [[brown_2025_alphaearth]]
