---
title: "Lightweight, Pre-trained Transformers for Remote Sensing Timeseries"
authors:
  - Tseng, Gabriel
  - Cartuyvels, Ruben
  - Zvonkov, Ivan
  - Purohit, Mirali
  - Rolnick, David
  - Kerner, Hannah
year: 2024
source: tseng_2024_presto
tags:
  - deep-learning
  - remote-sensing
  - machine-learning
keywords:
  - PRESTO
  - foundation model
  - Transformer
  - masked autoencoding
  - pixel-timeseries
  - multi-sensor
  - lightweight
  - self-supervised
status: read
---

# Tseng et al. 2024 — PRESTO: Lightweight Pre-trained Transformers for RS Time Series

## Title and Authors
**Lightweight, Pre-trained Transformers for Remote Sensing Timeseries**
Gabriel Tseng, Ruben Cartuyvels, Ivan Zvonkov, Mirali Purohit, David Rolnick, Hannah Kerner — arXiv:2304.14065v4 (Feb 2024).

## Quick Overview
- **Why is it relevant?** A pixel-time-series foundation model that handles multi-sensor RS inputs (S1+S2+ERA5+NDVI+Dynamic World+DEM+location) at scale; serves as a benchmark "lightweight" alternative to massive geospatial foundation models like [[brown_2025_alphaearth]] for vegetation regression tasks.
- **What was done?** Pre-trained a Transformer encoder–decoder via masked autoencoding on 21.5 M global pixel-timeseries × 12 months × 7 data products; evaluated on diverse downstream tasks (crop mapping, fuel moisture, land cover).
- **What is the main outcome?** Competitive with ViT/ResNet-based geospatial models using up to **1000× fewer parameters and orders-of-magnitude fewer FLOPs**; handles missing data and inputs of varying shape natively.

## Main Goal and Fundamental Concept
Geospatial foundation models (Prithvi, SatMAE, CROMA, AlphaEarth) treat RS data as image patches and require massive parameter counts. Tseng et al. argue that for many RS tasks the *temporal* and *multi-sensor* dimensions matter more than spatial context — and a *pixel-time-series* model can be far smaller while remaining competitive.

## Technical Approach
- **Architecture**: Transformer encoder–decoder, masked autoencoding (MAE-style); ~few million parameters.
- **Pre-training data**: 21.5 M pixels sampled globally; 12-month time series; resolution 10 m.
- **Per-pixel input**: 15 channels across:
  - Sentinel-2 multispectral
  - Sentinel-1 SAR (VV/VH)
  - ERA5 climate reanalysis
  - NDVI (derived from S2)
  - Dynamic World land cover
  - SRTM DEM (static)
  - Location coordinates (static)
- **Masking strategies** (4 types): random timestep, random channel, contiguous-time block, etc.
- **Token design**: per-timestep multi-band embedding; channel-aware tokens; encodes both static and dynamic inputs.
- **Downstream evaluation**: crop mapping, fuel moisture estimation, land cover segmentation, etc.

## Distinctive Features
- **Pixel-time-series approach**: drops spatial-context dependency that constrains ViT-based RS models.
- **Multi-sensor by design**: ingests heterogeneous sources natively.
- **Lightweight**: orders of magnitude smaller than ViT/ResNet foundation models.
- **Robust to missing data**: trained with masking → can handle real RS gaps without preprocessing.
- **Handles variable input shapes**: works with single timestep, multi-timestep, single sensor, multi-sensor downstream.
- **Open-source code + weights** released.

## Experimental Setup and Results

**Computational efficiency**
- Up to **1000× fewer trainable parameters** than competing geospatial foundation models
- Orders-of-magnitude fewer FLOPs at inference
- Trainable on CPUs (with some patience)

**Downstream performance**
- Competitive or superior to larger ViT/ResNet-based RS foundation models across diverse tasks
- Works well even on **image-based tasks where temporal information is absent** — suggests pixel-time-series representation transfers broadly
- Spatially coherent reconstructions even though inputs are single-pixel time series

**Why pixel-based works**
- Many RS tasks have small receptive-field needs
- Multi-modal + temporal signals carry the bulk of the discriminative information
- Brown et al. (2022) MOSAIKS already hinted at this; PRESTO formalises it

## Advantages and Limitations
- **Advantages**: Tiny model, broad applicability, multi-sensor + missing-data robust, easy deployment at scale; competitive with much larger models.
- **Limitations**: Pixel-level inputs miss fine-scale spatial context (texture, shape) that helps tall-canopy retrieval (cf. [[lang_2024_canopy_height]]) or harvest detection (cf. [[zhao_2022_forest_harvesting]]); monthly resolution may miss sub-monthly events; English-language documentation only.

## Conclusion
**PRESTO demonstrates that pre-trained Transformers for RS time series can be small, multi-sensor, and competitive with much larger foundation models** — the right benchmark for any vegetation regression task that depends on temporal + multi-sensor signals rather than spatial context. Position complement to [[brown_2025_alphaearth]] (much larger spatially-aware embedding) and direct alternative for SITS tasks where pixel-level reasoning suffices (e.g. EVE cover regression in the wiki). The 1000× efficiency gain makes it operationally relevant for Italian or pan-European forest mapping when compute is limited.

## Related pages
- [[transformer_sits]]
- [[transformers_time_series]]
- [[vaswani_2023_attention_is_all]]
- [[brown_2025_alphaearth]]
- [[transfer_learning_remote_sensing]]
- [[hiebl_2026_alphaearth]]
- [[hiebl_2025_pretraining]]
- [[yuan_2022_sitsformer]]
- [[yuan_2023_pretraining]]
- [[zerveas_2020_framework_transformer]]
- [[wen_2023_transformers_time_series]]
- [[reichstein_2019_deep_learning_earth_sciences]]
