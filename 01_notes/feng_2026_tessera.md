---
title: "TESSERA: Temporal Embeddings of Surface Spectra for Earth Representation and Analysis"
authors:
  - Zhengpeng Feng
  - Clement Atzberger
  - Sadiq Jaffer
  - Jovana Knezevic
  - Silja Sormunen
  - Robin Young
  - Madeline C. Lisaius
  - Markus Immitzer
  - Toby Jackson
  - James Ball
  - David A. Coomes
  - Anil Madhavapeddy
  - Andrew Blake
  - Srinivasan Keshav
year: 2026
tags:
  - deep-learning
  - remote-sensing
  - foundation-models
keywords:
  - geospatial foundation model
  - Tessera
  - Barlow Twins
  - Sentinel-1
  - Sentinel-2
  - pixel-wise embeddings
  - temporal sampling invariance
  - cloud robustness
  - label efficiency
  - tree species classification
  - self-supervised learning
status: read
---

## 1. Title and Authors

**TESSERA: Temporal Embeddings of Surface Spectra for Earth Representation and Analysis**
Feng et al. (2026), arXiv preprint. University of Cambridge, dClimateLabs, Aalto University, University of Bristol.

## 2. Quick Overview

- **Why is it relevant?** Most geospatial foundation models assume cloud-filtered or composited inputs, discarding partly-cloudy observations that carry phenological information critical for vegetation monitoring.
- **What was done?** A pixel-wise, multi-modal (Sentinel-1/2) foundation model was pretrained on ~800M d-pixels from 3,012 global MGRS tiles via Barlow Twins with temporal sampling invariance, global shuffling, and mix-based regularization — learning embeddings robust to irregular EO time series.
- **What is the main outcome?** TESSERA achieves state-of-the-art accuracy across classification, segmentation, and regression benchmarks with strong label efficiency, while releasing open-source global 10 m annual int8 embeddings and model weights under FAIR principles.

## 3. Main Goal and Fundamental Concept

TESSERA addresses a fundamental gap in geospatial foundation models: rather than filtering imperfect observations, it forces embeddings to be invariant to *which* cloud-free observations are selected from a time series. The core hypothesis is that a pixel-wise embedding that is robust to temporal sampling variability will better capture phenological dynamics than composite-based representations, and will transfer more effectively to downstream tasks with minimal labels.

## 4. Technical Approach

- **Input:** Multi-temporal Sentinel-1 (VV/VH) + Sentinel-2 sequences stacked as *d-pixels* — all channel values at a single (i,j) location across time; padded to fixed length L=40 via random resampling
- **Architecture:**
  - Dual-branch encoder: separate 4-block Transformer (self-attention + positional encoding via sine DoY) for S2, and 4-block Transformer + GRU pooling for S1; branches fused via 2-layer MLP → 128-dim embedding
  - Encoder: **45.7M parameters** (vs AlphaEarth's 480M)
  - Quantization-Aware Training (QAT) → int8 storage (4× compression, negligible accuracy loss)
- **Self-supervised objective:** Barlow Twins — invariance term encourages similar embeddings from two random temporal subsets; redundancy-reduction term minimises cross-dimension correlation
- **Two key regularizers:**
  - *Global shuffling:* d-pixels randomised across all geographic tiles before batching — breaks spatial autocorrelation, preventing the model from exploiting local neighbourhood context
  - *Mix-based regularization (MIX):* blends observations across time and samples to stabilise learning under extreme sparsity; mixed inputs from two augmented views M_A and M_S with coefficient α ~ Uniform(0,1)
- **Pretraining:** ~800M d-pixels, 3,012 global MGRS tiles (2017–2024), 16 AMD MI300X GPUs; AdamW optimiser
- **Inference:** Fixed encoder (projector discarded) → global 10 m annual 128-dim embeddings → lightweight heads (2-layer MLP for pixel tasks, compact 30M-parameter UNet for segmentation)
- **Releases:** Open weights + code at https://github.com/ucam-eo/tessera; global annual int8 embedding maps; GeoTessera Python library

## 5. Distinctive Features

- **Pixel-wise, not patch-wise:** captures per-pixel spectral-temporal trajectories without spatial context — temporal phenological signal is the primary discriminant, not spatial texture
- **Temporal sampling invariance:** explicit training objective to be robust to which subset of cloud-free observations is used — unlike all prior RSFMs that assume clean composited inputs
- **FAIR from the start:** global, annual, 10 m int8 embeddings released openly alongside weights and code — democratises access (AlphaEarth weights are closed)
- **Multi-modal (S1+S2) at pixel level:** first pixel-wise RSFM combining optical and radar, unlike most prior models that are single-modal or patch-based
- **Global shuffling as a key design choice:** removes spatial autocorrelation during training — prevents the model from using geographic proximity as a shortcut; empirically the most important regulariser (−9.2 F1 when removed)

## 6. Experimental Setup and Results

Six benchmarks spanning classification, segmentation, and regression:

**Classification:**

| Benchmark | TESSERA (1%) | AlphaEarth (1%) | TESSERA (full) | AlphaEarth (full) |
|---|---|---|---|---|
| TreeSatAI-TS (tree species, Germany) | **60.58** | 52.79 | **79.23** | 76.90 |
| Austrian Crop (classification) | — | — | **82.09** | — |

- At 1% labels, TESSERA outperforms AlphaEarth by +7.8 F1 on tree species classification

**Segmentation:**

| Benchmark | TESSERA (1%) | AlphaEarth (1%) | TESSERA (full) | AlphaEarth (full) |
|---|---|---|---|---|
| PASTIS-R (crop parcels, France) | **27.54** | 27.12 | 50.68 | **51.08** |
| Austrian Crop (segmentation) | **28.20** | 14.64 | **53.12** | 25.70 |

**Regression:**

| Benchmark | TESSERA | AlphaEarth | Presto | Best fine-tuned RSFM |
|---|---|---|---|---|
| Biomassters AGB (RMSE t/ha ↓) | **27.43** | 29.59 | — | 30.78 (Skysense) |
| Borneo CHM (RMSE m ↓) | **13.1** | 16.1 | 17.9 | 15.6 (Skysense) |

**Ablation (Austrian Crop):**

| Variant | F1 | ΔF1 |
|---|---|---|
| Full model | 77.3 | — |
| w/o Global shuffling | 68.1 | −9.2 |
| w/o Mix-based regularization | 66.2 | −11.1 |
| w/o Pretraining | 43.8 | −33.5 |
| w/o Quantization | 77.9 | +0.6 |

**Cloud robustness:** performance stable until fewer than ~20 valid S2 observations/year; degrades markedly below this threshold.

## 7. Advantages and Limitations

**Advantages:**
- Best-in-class label efficiency — especially at 1% labels, relevant for forest inventory settings with scarce annotations [[hiebl_2025_pretraining]]
- Cloud-robust by design — handles operational EO time series without preprocessing
- Open weights + global embeddings — FAIR, reproducible, no proprietary barrier
- Multi-modal fusion: SAR adds cloud-independent signal relevant for forest structure [[sentinel_1_sar]]
- Small encoder (45.7M params) makes fine-tuning and inference affordable vs AlphaEarth (480M)
- Strong on vegetation/forest tasks: SOTA on TreeSatAI-TS tree species classification and Borneo canopy height regression

**Limitations:**
- Annual embedding cadence — sub-annual phenological tasks require accessing raw time series + re-encoding
- Pixel-wise (no spatial context) — spatial texture tasks (e.g. road/building segmentation) may benefit from patch-based models; segmentation results on PASTIS-R are marginally weaker than AlphaEarth at full labels
- int8 quantization introduces minor information loss (negligible in ablation but may matter for edge cases)
- Global shuffling removes spatial autocorrelation as a training signal — intentional but means spatial structure tasks require spatial heads (UNet)
- Pretraining tiles (2017–2024): performance on pre-2017 archives untested
- ArXiv preprint — not yet peer-reviewed at time of this note

## 8. Conclusion

TESSERA is the key companion foundation model to AlphaEarth ([[brown_2025_alphaearth]]) in this wiki's context. Its pixel-wise, multi-modal (S1+S2) design with temporal sampling invariance directly addresses the cloud-contamination problem in operational EO time series. TESSERA achieves SOTA across diverse tasks with high label efficiency, and is directly evaluated for tree species mapping in [[ball_2026_foundation_models]] — where it outperforms AlphaEarth on minority-species discrimination and parcel compositional fidelity, while AlphaEarth has marginally higher weighted F1. The fully open release (weights, embeddings, GeoTessera library) removes the main practical barrier to adoption that limits AlphaEarth's use.

## Related pages

- [[brown_2025_alphaearth]]
- [[hiebl_2026_alphaearth]]
- [[ball_2026_foundation_models]]
- [[hiebl_2025_pretraining]]
- [[manas_2021_seasonal_contrast]]
- [[tseng_2024_presto]]
- [[geospatial_foundation_models]]
- [[transformer_sits]]
- [[sentinel_1_sar]]
- [[sentinel_2]]
- [[tree_species_mapping]]
