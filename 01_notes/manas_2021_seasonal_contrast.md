---
title: "Seasonal Contrast: Unsupervised Pre-Training from Uncurated Remote Sensing Data"
authors:
  - Mañas, Oscar
  - Lacoste, Alexandre
  - Giró-i-Nieto, Xavier
  - Vazquez, David
  - Rodriguez, Pau
year: 2021
source: manas_2021_seasonal_contrast
tags:
  - deep-learning
  - remote-sensing
  - machine-learning
keywords:
  - SeCo
  - seasonal contrast
  - temporal positive pairs
  - contrastive learning
  - self-supervised pretraining
  - Sentinel-2
  - land cover classification
  - multi-augmentation
  - time and position invariance
  - temporal invariance
status: read
---

# Mañas et al. 2021 — Seasonal Contrast: Unsupervised Pre-Training from Uncurated Remote Sensing Data

## Title and Authors
**Seasonal Contrast: Unsupervised Pre-Training from Uncurated Remote Sensing Data**
Oscar Mañas, Alexandre Lacoste, Xavier Giró-i-Nieto, David Vazquez, Pau Rodriguez (Element AI / Universitat Politècnica de Catalunya) — arXiv:2103.16607v2 (May 2021).

## Quick Overview
- **Why is it relevant?** Introduces **temporal positive pairs** for contrastive pre-training of RS representations — the canonical reference for the assumption that land cover / forest vegetation is ecologically stable enough across time to define valid contrastive positive pairs from the same location at different timestamps.
- **What was done?** SeCo (Seasonal Contrast) combines (1) an unsupervised Sentinel-2 dataset of 1M patches from ~200K global locations × 5 dates 3 months apart and (2) a multi-head contrastive learning algorithm that learns representations simultaneously invariant and variant to seasonal changes.
- **What is the main outcome?** SeCo outperforms ImageNet pre-training and MoCo-v2 on BigEarthNet land-cover classification (+4–6% mAP), EuroSAT (+6.7% accuracy), and OSCD change detection (+6.8% F1) — demonstrating that in-domain RS pre-training exploiting temporal structure is more effective than natural-image pre-training.

## Main Goal and Fundamental Concept

Remote sensing provides vast, mostly-unlabelled data with a unique structural property: **satellite revisit**. The same location on Earth is imaged repeatedly every few days. SeCo exploits this to create **natural augmentations** by treating images of the same location at different seasons as positive pairs in contrastive learning — instead of relying exclusively on synthetic augmentations (cropping, colour jitter) that cannot capture, for example, how a mountain looks after snowmelt.

The key inductive bias stated explicitly (p. 3):
> *"Encouraging the representation to be invariant to seasonal changes is a strong inductive bias. This property can be beneficial for certain downstream tasks where the prediction will not change with seasonal variations (e.g. **land-cover classification**, agricultural pattern segmentation, building detection)."*

This is the direct source for the assumption that **ecological (and therefore spectral) stability over time enables contrastive learning**.

## Technical Approach

**Dataset collection**
- ~200K global locations sampled around populated regions (to maximise scene diversity)
- 5 Sentinel-2 images per location, separated by ~3 months → captures full seasonal cycle
- Cloud cover < 10%; 1M patches total (2.65 × 2.65 km each, RGB + NIR)

**Multi-head contrastive architecture (Figure 2)**
- Shared ResNet backbone f(·) → common embedding V
- Three non-linear projection heads → three embedding sub-spaces Z₀, Z₁, Z₂:
  - **Z₀**: invariant to *all* transformations (seasonal + artificial)
  - **Z₁**: invariant to *seasonal* augmentations only; variant to artificial augmentations
  - **Z₂**: invariant to *artificial* augmentations only; variant to seasonal changes
- Transfer representation taken from V (the shared space) — doesn't assume a priori whether downstream task requires temporal invariance or variance

**Positive pair construction**
- Query: reference image at time t₀
- Key k₀ = T(x_{t₁}) — temporal augmentation + artificial augmentation
- Key k₁ = x_{t₂} — temporal augmentation only
- Key k₂ = T(x_{t₀}) — artificial augmentation only
- Contrastive loss (InfoNCE-style) summed across the three sub-spaces with appropriate positive/negative assignments

**Backbone**: MoCo-v2 (momentum contrast) with ResNet-18 or ResNet-50; separate queues of 16,384 negative embeddings per sub-space.

## Distinctive Features

- **First principled use of temporal positive pairs for RS contrastive pre-training** — images from same location at different seasons as natural augmentations
- **Multi-head design separates invariances**: representations encode both time-varying and time-invariant information, enabling transfer to both land-cover classification (needs invariance) and change detection (needs variance)
- **Fully unsupervised data collection**: no human curation or annotation
- **Domain-specific pre-training beats ImageNet**: confirms that the remote sensing domain gap is real and in-domain SSL is superior
- Compared with companion approach MoCo-v2+TP (temporal positive pairs only, no multi-head): SeCo outperforms by ~4% mAP on BigEarthNet — the multi-head architecture matters

## Experimental Setup and Results

**BigEarthNet land-cover classification (multi-label, Sentinel-2)**

| Pre-training | Linear 100% | Fine-tune 100% |
|---|---|---|
| Random init. | 45.95 | 79.80 |
| ImageNet (supervised) | 66.40 | 85.90 |
| MoCo-v2 (no temporal) | 70.90 | 85.17 |
| MoCo-v2+TP | 71.08 | 85.71 |
| **SeCo (1M, ResNet-18)** | **77.00** | **87.27** |
| **SeCo (1M, ResNet-50)** | **80.35** | **87.81** |

SeCo with 1% of labels matches ImageNet with 100% of labels (linear probing) → label-efficient.

**EuroSAT land-cover classification (10 class)**

| Pre-training | Fine-tune accuracy |
|---|---|
| ImageNet (supervised) | 86.44 |
| MoCo-v2+TP | 89.51 |
| **SeCo** | **93.14** |

**OSCD change detection** (where temporal *variance* matters):
- SeCo: F1 = 46.94 (best)
- MoCo-v2+TP: F1 = 40.12 (temporal positives forced full invariance → hurts change detection)
- Demonstrates the value of multi-head design: SeCo representations are both invariant AND variant to time in different sub-spaces

**Ablation on sampling strategy**: city-centric Gaussian sampling (74.67 mAP) > uniform continent sampling (71.63 mAP) on BigEarthNet — diverse scene coverage matters.

## Advantages and Limitations

- **Advantages**: Principled motivation for temporal positive pairs; multi-head design handles the invariance/variance trade-off; fully unsupervised; outperforms ImageNet on RS tasks; open code + dataset + models.
- **Limitations**: Uses only RGB (3 of 12 S-2 bands) in the experiments — full multispectral would likely improve further; temporal separation is 3 months (seasonal scale), not multi-year; urban-centric sampling may under-represent dense natural forest areas; change detection is relatively weak (low recall) even for SeCo; the temporal stability assumption is not formally tested — it is asserted as an inductive bias.

## The Temporal Stability Assumption — Scope and Limitations

SeCo establishes that the same location at **3-month intervals** constitutes a valid positive pair for land-cover classification. This assumption transfers to forest mapping with the following caveats:

1. **Seasonal vs multi-year windows**: SeCo tests 3-month separations; forest mapping workflows using multi-year (1–2 year) windows assume stability over a *longer* timescale. For mature forest stands this is ecologically justified (species composition changes on decadal, not annual, scales) — but disturbance events (windstorm, bark beetle, fire) can violate the assumption for any individual plot.
2. **Forest-specific support from wiki**: [[herraiz_2025_phen_shifts_mediterranean]] characterises forests as "slow-changing systems"; [[pflugmacher_2019_lulc_landsat]] and [[grabska_2024_tree_species_map]] show multi-year pooling stabilises STMs for forest classes — convergent evidence.
3. **The companion method MoCo-v2+TP**: SeCo's ablation directly isolates the temporal positive pair contribution, confirming it alone improves over no-temporal by +1.4 pp mAP — the multi-head refinement adds another +4 pp.

## Conclusion

**SeCo is the canonical methodological source for temporal contrastive positive pairs in RS.** It establishes both the conceptual argument — *"land cover does not change with the seasons, therefore same-location temporal pairs are semantically similar and valid positives"* — and the empirical evidence that this inductive bias substantially improves RS representation learning over standard SimCLR/MoCo and ImageNet pre-training. For the ls_mapping paper, SeCo supports line 49 (the temporal stability assumption) and is the direct methodological predecessor of the contrastive pre-training approach. The key qualifier is that SeCo validates seasonal (3-month) stability; multi-year stability is additionally supported by forest ecology literature but not directly by this paper.

## Related pages
- [[geospatial_foundation_models]]
- [[transfer_learning_remote_sensing]]
- [[transformer_sits]]
- [[chen_2020_contrastive_framework]]
- [[hiebl_2025_pretraining]]
- [[yuan_2023_pretraining]]
- [[tseng_2024_presto]]
- [[grabska_2024_tree_species_map]]
- [[pflugmacher_2019_lulc_landsat]]
- [[herraiz_2025_phen_shifts_mediterranean]]
- [[deep_ensemble_uncertainty]]
