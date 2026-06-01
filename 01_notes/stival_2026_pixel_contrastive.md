---
title: "Pixel-Wise Multimodal Contrastive Learning for Remote Sensing Images (PIMC)"
authors:
  - Leandro Stival
  - Ricardo da Silva Torres
  - Helio Pedrini
year: 2026
tags:
  - deep-learning
  - remote-sensing
keywords:
  - contrastive learning
  - self-supervised learning
  - pixel time series
  - recurrence plots
  - 2D representations
  - SITS
  - vegetation indices
  - NDVI
  - multimodal
  - PASTIS
  - EuroSAT
status: read
---

## 1. Title and Authors

**Pixel-Wise Multimodal Contrastive Learning for Remote Sensing Images**
Stival, Torres, Pedrini (2026), arXiv preprint 2601.04127. *(Preprint — not yet peer-reviewed.)*

## 2. Quick Overview

- **Why is it relevant?** Proposes using **recurrence plots (2D representations) of pixel-level vegetation index time series** as one modality in a multimodal contrastive framework — a novel way to leverage temporal pixel patterns that 1D approaches cannot capture, and relevant to SITS-based forest monitoring.
- **What was done?** PIMC (Pixel-wise Image Multimodal Contrastive) trains two independent encoders — one for 2D recurrence plots of NDVI/EVI/SAVI pixel time series, one for RSI patches — using contrastive alignment between co-located instances; evaluated on PASTIS (classification, forecasting) and EuroSAT (land cover).
- **What is the main outcome?** 2D representations consistently outperform 1D representations; PIMC encoders match or exceed SeCo and DINO-MC for forecasting; comparable to ViT-32 after fine-tuning on EuroSAT.

## 3. Main Goal and Fundamental Concept

Most SITS-based SSL approaches treat pixels as 1D sequences of band values at each timestamp. This discards **autocorrelation structure within the time series** — temporal recurrences that encode phenological cycles, drought signatures, and change events. Recurrence plots (RPs) transform a 1D time series into a 2D binary/fuzzy matrix R_{ij} = Θ(ε - ||x_i - x_j||) where entry (i,j) = 1 if x_i ≈ x_j (similar states at times i and j). RPs make temporal self-similarity patterns explicit and enable standard 2D CNNs to process them.

PIMC's multimodal approach: the same ground location contributes both a 2D RP (from pixel vegetation indices over time) and an RSI patch (image encoder). Contrastive alignment between the two modalities creates a shared feature space encoding both spatial and temporal vegetation properties.

## 4. Technical Approach

**Recurrence Plot construction**:
1. For each SITS patch, select pixels using Hilbert curve sampling (space-filling curve ensures spatial coverage)
2. Compute NDVI/EVI/SAVI for each selected pixel at each timestamp
3. For each pixel's 1D time series → 2D recurrence plot R (threshold ε tuned per dataset)
4. Result: 2D image of size T×T where T = number of timestamps

**Two separate encoders**:
- RSI encoder: standard CNN (ResNet variant) trained on image patches
- Time series encoder: CNN trained on recurrence plot images (RP → 2D → CNN)

**Contrastive alignment (CLIP-style)**:
- Co-located RSI patch and RP from same location = positive pair
- Cross-location pairs = negatives
- InfoNCE / NT-Xent loss aligns RSI and RP embeddings

**Training data**: PASTIS (T=61 timestamps of S2 SITS patches for crop classification/segmentation)

**Downstream evaluation**:
- PASTIS pixel classification: classify land cover type per pixel
- PASTIS forecasting: predict next 10 vegetation index values from 32-observation series
- EuroSAT land cover classification

## 5. Distinctive Features

- **First SITS SSL method using recurrence plots as a modality**: RP captures temporal autocorrelation patterns invisible to 1D representations
- **Pixel-level focus**: avoids patch-aggregation artifacts; directly relevant to per-pixel forest mapping tasks
- **Independent encoders after training**: each modality encoder works standalone at inference — no requirement for both modalities at test time (unlike CLIP-style architectures that need both)
- **2D enables standard CV backbone reuse**: ResNets/ViTs pre-designed for 2D images can process RPs without architecture modification

## 6. Experimental Setup and Results

**Time Series Forecasting (PASTIS, predict next 10 VI values, 3 vegetation indices)**:

| Method | Rep | NDVI RMSE | EVI RMSE | SAVI RMSE |
|--------|-----|-----------|----------|-----------|
| MOMENT | 1D | 0.5829 | 0.5900 | 0.6052 |
| 1D CNN | 1D | 0.6808 | 0.6392 | 0.6467 |
| SeCo FT | 2D | 0.8552 | 0.7439 | 0.7788 |
| DINO MC FT | 2D | 0.5147 | 0.5067 | 0.4907 |
| **PIMC FT** | 2D | **0.4849** | **0.5464** | **0.5387** |

- PIMC best on NDVI; DINO-MC-FT best on EVI/SAVI; 2D consistently beats 1D raw representations
- **EuroSAT land cover** (10 classes): PIMC FT on par with ViT-32 (ACC ~88%), slightly below SeCo FT

## 7. Advantages and Limitations

**Strengths**
- Recurrence plot: principled way to capture temporal autocorrelation structure; proven in other time-series domains
- Independent encoders: flexible deployment — RP encoder can be used for SITS-only inference, RSI encoder for image-only
- Pixel-level design is directly compatible with per-pixel forest mapping workflows

**Critical Limitations**
- **Preprint only**: not peer-reviewed; results should be treated cautiously
- **Limited benchmarks**: only PASTIS and EuroSAT; no tree species or fractional cover task
- **Recurrence plot construction is expensive**: O(T²) memory/computation per pixel; PASTIS T=61 → 61×61 RP; for annual Landsat T=30 it is manageable, but for dense S2 T=100+ becomes costly
- **ε (recurrence threshold) sensitivity**: results may depend on threshold tuning per dataset/VI; not analysed
- **Forecasting task**: predicting vegetation index values is a proxy task; accuracy on classification/mapping tasks more relevant for the wiki's use case
- **Comparison gap**: not compared to TST, SITS-BERT, PRESTO — the main SITS SSL/transformer baselines in this wiki

## 8. Conclusion

Stival et al. (2026) introduce a creative use of recurrence plots as a SITS modality for contrastive SSL. The core insight — that 2D temporal autocorrelation representations contain information invisible to 1D pixel sequences — is theoretically sound and empirically supported on forecasting. For the wiki's forest mapping context, PIMC offers a complementary approach to standard SITS SSL: it operates at pixel level (compatible with forest type regression), leverages temporal structure explicitly, and produces independent encoders usable at inference. However, as an unreviewed preprint with limited task coverage, its claims should be verified against PRESTO/SITS-BERT baselines before adoption.

## Related Pages

- [[transfer_learning_remote_sensing]]
- [[transformer_sits]]
- [[manas_2021_seasonal_contrast]]
- [[stival_2025_contrastive_msi]]
- [[sentinel_2]]
- [[tseng_2024_presto]]
