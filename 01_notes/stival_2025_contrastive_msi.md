---
title: "Semantically-Aware Contrastive Learning for multispectral remote sensing images (SACo+)"
authors:
  - Leandro Stival
  - Ricardo da Silva Torres
  - Helio Pedrini
year: 2025
tags:
  - deep-learning
  - remote-sensing
keywords:
  - contrastive learning
  - self-supervised learning
  - multispectral
  - Sentinel-2
  - semantic band combinations
  - texture features
  - LBP
  - SeCo
  - EuroSAT
  - land cover classification
  - change detection
  - semantic segmentation
status: read
---

## 1. Title and Authors

**Semantically-Aware Contrastive Learning for multispectral remote sensing images**
Stival, Torres, Pedrini (2025), *ISPRS Journal of Photogrammetry and Remote Sensing* 223:173–187.

## 2. Quick Overview

- **Why is it relevant?** Directly extends SeCo [[manas_2021_seasonal_contrast]] by incorporating **spectral band semantics** (known vegetation/water/urban band combinations) and **texture (LBP)** as categorical contrastive anchors — addressing the problem that standard augmentations ignore the semantic meaning of individual spectral bands in MSRSI.
- **What was done?** SACo+ trains ResNet encoders using a two-stage contrastive loss: first categorical (band group means as anchors), then instance-level + temporal (SeCo-style), using CACo + SeCo training datasets (100k + 1M S2 images).
- **What is the main outcome?** SACo+ (ResNet-18) reaches 94.72% on EuroSAT land cover classification vs SeCo's 90.05%, narrowing the gap with SpectralGPT (99.15%) despite being 10× smaller.

## 3. Main Goal and Fundamental Concept

Standard contrastive SSL for MSRSI (MoCo, SeCo, CACo) treats the image as an opaque input and designs positive pairs around augmentations or temporal repetition. This ignores a unique property of multispectral data: **specific band combinations encode physically meaningful ground properties** (vegetation indices from NIR/Red, water from SWIR, urban from SWIR2/NIR). The hypothesis: making the contrastive objective explicitly aware of these semantic groups yields a richer, domain-appropriate feature space.

SACo+ introduces three positive pair sources simultaneously:
1. **Augmentation pairs** (MoCo-style): original + random crop/flip/zoom
2. **Temporal pairs** (SeCo-style): same location, different timestamp
3. **Categorical/semantic pairs**: image views defined by band group (vegetation group, urban group, water group) + LBP texture map

## 4. Technical Approach

**Semantic band groups** (manually defined from spectral knowledge):
- Vegetation: NIR, red-edge, red bands → vegetation indices sensitive to chlorophyll and LAI
- Urban: SWIR2, NIR, red bands → urban/built-up discrimination
- Water: NIR, SWIR1, blue → water body discrimination
- (Groups drawn from prior spectral index literature)

**LBP texture**: Local Binary Pattern computed for each semantic group channel — encodes local contrast/edge texture patterns; 8 neighbours, radius 1 or 2.

**Two-stage contrastive loss**:
- Stage 1 (categorical): pull image embedding toward mean of its semantic group embeddings (̂x = mean over all images in group); positive = same group, negatives from memory bank (65,536 negatives following SeCo/CACo)
- Stage 2 (instance): standard momentum contrastive (MoCo-style) with augmented + temporal positives

**Backbone**: ResNet-18 (main) and ResNet-50 (comparison); **Training**: Adam, lr=1e-4, 100 epochs, batch=64, schedule at epochs 60/80; **Data**: CACo 100k S2 + SeCo 1M dataset.

## 5. Distinctive Features

- **First integration of spectral semantic groups into contrastive RS pretraining**: prior work (SeCo, CACo, D-SimCLR) does not exploit known spectral physics
- **Complementary to temporal pairs**: semantic groups add categorical-level structure, temporal adds invariance to seasonal change, augmentations add instance-level invariance
- **Band-aware augmentation policy**: deliberately excludes colour jitter (which would destroy spectral semantics); uses geometric augmentations only

## 6. Experimental Setup and Results

**EuroSAT land cover classification** (10 classes, 27k S2 patches):

| Method | Backbone | Accuracy (%) |
|--------|----------|-------------|
| MoCo V2 | ResNet-18 | 83.72 |
| SeCo | ResNet-18 | 90.05 |
| CACo | ResNet-18 | 93.08 |
| **SACo+ (ours)** | ResNet-18 | **94.72** |
| SeCo | ResNet-50 | 93.12 |
| CACo | ResNet-50 | 94.48 |
| DINO-MC | ResNet-50 | 95.70 |
| SpectralGPT | ViT (10× larger) | 99.15 |
| **SACo+ (ours)** | ResNet-50 | **95.77** |

- Ablation (SACo = without texture): 85.79% (ResNet-18) → adding texture gives +8.93pp
- **Change detection (OSCD)**: SACo+ outperforms MoCo V2, SeCo on precision/recall/F1 for pixel-level change
- **Semantic segmentation (PASTIS, GID)**: competitive with SeCo/CACo

## 7. Advantages and Limitations

**Strengths**
- Semantically grounded design: band group construction draws on decades of spectral index research
- Multi-task validation (classification, change detection, segmentation) — more comprehensive than most SSL papers
- Ablation (SACo vs SACo+) isolates texture contribution cleanly

**Critical Limitations**
- **Manually designed semantic groups**: band groupings are heuristic — no learned optimisation of which bands to group; may not be optimal for all vegetation types
- **LBP texture**: a simple hand-crafted texture descriptor; not learned; potentially superseded by learned texture representations
- **SpectralGPT gap**: at ResNet-50, SACo+ (95.77%) still trails SpectralGPT (99.15%) by 3.38pp — a large ViT backbone likely dominates semantic group design
- **EuroSAT bias**: EuroSAT is a relatively easy, well-balanced, RGB-interpretable dataset; improvements on spectrally complex tasks (tree species, fractional cover) may differ
- **No time series architecture**: SACo+ treats images as spatially independent snapshots; no explicit SITS/temporal modelling

## 8. Conclusion

SACo+ makes a principled extension of SeCo by incorporating spectral band semantics as categorical contrastive anchors. The +4.67pp gain over SeCo on EuroSAT (ResNet-18) is meaningful and traces specifically to the semantic band group module. For the wiki's vegetation RS context, the key insight is: **standard RS augmentations should not alter spectral bands semantically, and contrastive positives can be constructed from known band combination groups** — this is applicable to SITS pretraining for forest cover mapping where vegetation/SWIR/NIR groupings are ecologically meaningful. However, at larger ViT scales (SpectralGPT), architectural capacity may subsume the need for explicit spectral supervision.

## Related Pages

- [[transfer_learning_remote_sensing]]
- [[manas_2021_seasonal_contrast]]
- [[scheibenreif_2022_contrastive]]
- [[sentinel_2]]
- [[chen_2020_contrastive_framework]]
- [[geospatial_foundation_models]]
