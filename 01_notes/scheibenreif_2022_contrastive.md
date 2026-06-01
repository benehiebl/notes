---
title: "Contrastive Self-Supervised Data Fusion for Satellite Imagery"
authors:
  - Linus Scheibenreif
  - Michael Mommert
  - Damian Borth
year: 2022
tags:
  - deep-learning
  - remote-sensing
keywords:
  - contrastive learning
  - self-supervised learning
  - data fusion
  - Sentinel-1
  - Sentinel-2
  - multimodal
  - SEN12MS
  - land cover classification
  - augmentation-free
  - SSL pretraining
status: read
---

## 1. Title and Authors

**Contrastive Self-Supervised Data Fusion for Satellite Imagery**
Scheibenreif, Mommert, Borth (2022), *ISPRS Annals* V-3-2022:705–711. DOI: 10.5194/isprs-annals-V-3-2022-705-2022

## 2. Quick Overview

- **Why is it relevant?** Establishes the principle that spatially co-registered multi-modal RS observations (S1/S2) provide **natural positive pairs for augmentation-free contrastive SSL** — a cleaner alternative to synthetic augmentations that don't transfer to non-RGB RS data.
- **What was done?** Two contrastive SSL methods using unlabelled SEN12MS (S1/S2 pairs) for pretraining: D-SimCLR (dual-encoder SimCLR) and MMA (Multi-Modal Alignment with spatial correlation maps); evaluated on DFC2020 land cover classification.
- **What is the main outcome?** D-SimCLR with 10% of labels outperforms the best supervised fusion model trained on 100% of labels; linear probing on par with fully supervised approaches — cross-modal SSL is a powerful pretraining strategy.

## 3. Main Goal and Fundamental Concept

Standard contrastive SSL (SimCLR, MoCo) relies on strong random augmentations (colour jitter, crop, blur) to create positive pairs. These are poorly suited to multi-spectral RS data: changing hue or saturation alters spectral band semantics; standard RGB augmentations lose information from NIR/SWIR bands. The key insight: **two spatially aligned images of the same scene from different sensors (S1 SAR + S2 multispectral) are natural positive pairs** — semantically identical, perceptually different. This removes augmentation design entirely.

## 4. Technical Approach

**D-SimCLR** (Dual SimCLR):
- Separate ResNet18 encoders for S1 (2-channel VV/VH) and S2 (13-band multispectral)
- Separate projection MLPs (2 FC + ReLU → 128-dim)
- NT-Xent contrastive loss: latent vector of S1 image of scene *i* pushed toward S2 of same scene, away from all other scenes in batch
- For downstream: concatenate f_s1(x) and f_s2(x) before linear classifier

**MMA** (Multi-Modal Alignment):
- Two VGG-style spatial feature encoder branches (retains 2D spatial maps)
- Cross-modal similarity via 2D correlation map: C_{i,j} = z_i ★ z_j (feature map cross-correlation)
- Contrastive loss uses max of correlation map as scalar similarity
- No projection heads — preserves spatial feature structure (intended for dense tasks)

**Training**: SEN12MS (180,662 co-located S1/S2 pairs, 10 m); evaluated on DFC2020 (5,128 scenes, 8 land cover classes). Oversample rare classes during fine-tuning.

## 5. Distinctive Features

- **Augmentation-free by design**: avoids the difficult question of which augmentations preserve semantic meaning in multispectral RS data
- **Implicit data fusion**: the model jointly learns S1 and S2 representations without any labels — the pretraining task itself IS the fusion objective
- **Cross-dataset transfer**: models pretrained on SEN12MS transfer to EuroSAT (10 different land cover classes, 27k images), outperforming supervised OnlySen-2 baseline after only 20 fine-tuning epochs

## 6. Experimental Setup and Results

| Method | Single-label OA (%) | Multi-label O-F1 (%) | Linear probe single (%) |
|--------|---------------------|----------------------|--------------------------|
| OnlySen-1 (supervised) | 62 | 62 | — |
| OnlySen-2 (supervised) | 62 | 63 | — |
| EarlyFusion (supervised) | 66 | 62 | — |
| LateFusion (supervised) | 65 | 61 | — |
| SimCLR (RGB only) | 58 | 49 | — |
| **D-SimCLR** | **70** | **69** | **59** |
| MMA | 69 | 66 | 57 |

- D-SimCLR with **10% labels** → 67% OA, outperforming best supervised model at 100% labels (66%)
- EuroSAT transfer: D-SimCLR 95%, MMA 97%, vs supervised OnlySen-2 91% (after 20 epochs each)
- t-SNE: D-SimCLR and MMA structure latent space by land-cover class as well as supervised methods

## 7. Advantages and Limitations

**Strengths**
- Elegantly solves the RS augmentation problem by exploiting sensor co-registration
- Strong few-label performance: dramatically reduces labelling requirements
- Clean ablation: SimCLR (RGB only) vs D-SimCLR vs supervised shows modal contrast is the key contributor, not architecture

**Critical Limitations**
- **Scene-level classification only**: both encoders operate on entire 128×128 patches; not directly applicable to pixel-level or time-series tasks
- **No temporal dimension**: positive pairs are near-in-time but not explicitly temporal; does not exploit phenological signal
- **Short paper (7 pages)**: limited ablation, no per-class breakdown of where S1 adds value
- **ResNet18 backbone**: modest capacity; unclear how scaling affects the multi-modal SSL advantage
- **SEN12MS single-season pairs**: does not exploit multi-temporal variation (unlike SeCo)

## 8. Conclusion

Scheibenreif et al. (2022) make a clear and reusable contribution: **geo-registered S1/S2 pairs are natural positive pairs for augmentation-free contrastive SSL**, producing representations that outperform supervised fusion baselines at a fraction of labelling cost. This is the cross-modal analogue of SeCo's temporal positive pairs [[manas_2021_seasonal_contrast]]. The approach is directly relevant whenever S1 and S2 data are co-available (as in most forest RS workflows) and labels are scarce. For the wiki's TRACEVE context: S1 + S2 cross-modal SSL pretraining is an alternative to temporal contrastive learning that could further reduce label requirements for forest type mapping.

## Related Pages

- [[transfer_learning_remote_sensing]]
- [[manas_2021_seasonal_contrast]]
- [[sentinel_1_sar]]
- [[sentinel_2]]
- [[chen_2020_contrastive_framework]]
- [[geospatial_foundation_models]]
