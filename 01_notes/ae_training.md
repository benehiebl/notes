---
title: "ae_training — TRACEVE + AlphaEarth Cross-Attention Fusion (code repository)"
authors:
  - Hiebl, Benedikt
year: 2026
source: ae_training
tags:
  - deep-learning
  - remote-sensing
  - sentinel-2
  - forest-ecology
status: read
---

# Title and Authors of the Codebase

**ae_training — TRACEVE + AlphaEarth Cross-Attention Fusion Framework**
Benedikt Hiebl (University of Innsbruck / UIBK)
Repository: `00_literature/ae_training/`
Related publication: Hiebl et al. 2026 — "Combining specialized Sentinel-2 time series features with AlphaEarth Foundations for forest type mapping" (ISPRS Annals)

---

## Quick Overview

- **Why is the code relevant in the context of the vault?** This repository implements the multi-modal fusion experiments combining Sentinel-2 time series with [[brown_2025_alphaearth]] foundation model embeddings for forest type mapping, extending [[hiebl_2025_pretraining]] to the AlphaEarth paradigm.
- **What does it do?** Provides three competing architectures (MLPAlpha, TST, CrossAttentionAlpha) for TSC and TSER on Sentinel-2 + AlphaEarth inputs, with a config-driven framework to ablate the contribution of each modality.
- **What is the main outcome?** A training framework enabling systematic comparison of AE-only, S2-only, and cross-attention fusion approaches for EVE cover regression and forest type classification.

---

## Main Goal and Fundamental Concept

AlphaEarth Foundations ([[brown_2025_alphaearth]]) provide 64-dimensional embeddings encoding multi-modal Earth observation information (spectral, structural, climatic) at 10 m globally. This repository tests whether these dense foundation model representations complement sparse Sentinel-2 time series for forest mapping — and designs a cross-attention mechanism that allows the model to selectively attend over time steps in the S2 time series, guided by the AE embedding query. The core hypothesis is that AE embeddings encode complementary contextual information (e.g., canopy structure, climate context) that improves upon spectral-temporal features alone.

---

## Technical Approach

**Three competing architectures:**

1. **MLPAlpha** (`graphs/models/MLPAlpha.py`):
   - Simple MLP applied to AlphaEarth 64-dim embeddings only
   - No time series component
   - Baseline for AE-only prediction performance

2. **TST** (`graphs/models/TST.py`):
   - Custom Time Series Transformer (encoder-only) on sparse Sentinel-2 time series
   - **Time encoding:** sinusoidal positional encoding using actual acquisition timestamps in days (`time_encoding` → `pe[..., 0::2] = sin(t·ω); pe[..., 1::2] = cos(t·ω)`); masked for missing observations (padded with -1)
   - Per-channel input projection (`W_P`), optional sensor-type projection (`W_S`)
   - Key-padding mask propagated through multi-head self-attention to handle irregular/missing observations
   - Optional attention pooling (`attn_pool=1`) before prediction head
   - Baseline for S2-only performance

3. **CrossAttentionAlpha** (`graphs/models/CrossAttentionAlpha.py`):
   - **Primary novel architecture:** fuses AE embedding and S2 time series via cross-attention
   - Forward pass: `q = proj_e(embd).unsqueeze(1)` → AE embedding as single-token query `[B,1,d_model]`; `kv = proj_x(x) + time_embedding` → S2 time steps as key-value sequence `[B,T,d_model]`
   - N stacked `AttentionBlock(q, kv)` layers: multi-head cross-attention (AE query attends over S2 time steps) + GELU feed-forward + residual + LayerNorm
   - Skip connection: `out = head(q) + skip_connection(embd)` preserves AE information if attention adds nothing
   - Small init for head weights (`gain=0.1`) ensures AE baseline is preserved early in training

**Training agents:**
- `tser_base.py` (TSERAlphaAgent): handles dual-input (S2 tensor + AE embedding CSV) for regression
- `tsc_base.py`: classification variant

**Data flow:**
- S2 time series: loaded from `.nc` files (bands: B02–B12, NDVI, precipitation, temperature vars)
- AE embeddings: loaded from `.csv` files (`vpo2025_alphaearth.csv`) — pre-extracted 64-dim vectors per plot
- `TSRobustStandardize`: robust z-score via quantile winsorisation (q=[0.02, 0.98]), per-band

**Config structure:**
Six config files covering combinations of: architecture (TST/MLPAlpha/CrossAttentionAlpha) × task (TSC/TSER) × seed. Experiment naming: `tst_eve_ae_0`, `mlp_class_alpha_0`, etc. Enables direct ablation comparison across same seed.

---

## Distinctive Features

- **Cross-attention as modality fusion:** rather than concatenating AE embeddings with temporal features, the AE embedding serves as a single-token query that attends over all S2 time steps — the model learns which acquisition dates are most informative given the local foundation model context
- **Skip connection with small head init:** ensures the model starts close to the AE-only baseline (`MLPAlpha`) and only improves over it — prevents the cross-attention pathway from degrading early training
- **Sinusoidal timestamp encoding:** both TST and CrossAttentionAlpha use actual acquisition day-of-year timestamps (not indices) for positional encoding, correctly handling irregular S2 observations with variable cloud gaps
- **Direct ablation design:** three architectures share the same config structure and agents, enabling clean modality ablation (AE-only vs S2-only vs fusion) under identical training conditions

---

## Experimental Setup and Results

Experiment configs define the full setup:
- **Task — TSER (EVE regression):** target `cover_woody_eve` (0–1 after rescaling)
- **Task — TSC (classification):** target `class_v3` (forest type classes)
- **Input bands:** 14 features = B02, B03, B04, B05, B06, B07, B08, B11, B12, NDVI + climate (pr, tas, tasmi, tasma)
- **Spatial CV:** `test_cluster = ("test_values", seed)` — seed-indexed spatial test cluster
- **Model selection:** RMSE-based best-checkpoint selection

Results are documented in [[hiebl_2026_alphaearth]]:
- **TST_AEF,S2 (CrossAttentionAlpha)** consistently outperforms all stand-alone models: ETC RMSE=0.161, R²=0.724; FVT Acc=0.757, F1w=0.747
- **MLP_AEF and TST_S2** achieve similar accuracy to each other, despite radically different input processing; MLP_AEF trains in 30 s vs ~12 min for TST_S2
- AEF attribution ~3× higher than S2/CHELSA in Integrated Gradients; S2 adds phenological detail; CA attends less to S2 when cloud observation density is low

---

## Advantages and Limitations

**Advantages:**
- Minimal changes from `traceve_pretraining` base: leverages same config-driven infrastructure, adding only AE embedding dataloader support and the three model architectures
- Skip connection prevents training instability when AE embeddings are noisy or uninformative
- Time encoding handles irregular S2 acquisitions correctly — no assumption of fixed temporal grid
- Direct model comparison enabled by shared training infrastructure and identical config naming conventions

**Limitations:**
- Requires access to pre-extracted AlphaEarth embedding files (`vpo2025_alphaearth.csv`) — not open-source; limits reproducibility for external users
- No deep ensemble uncertainty (unlike `traceve_pretraining`) — single prediction head without calibrated uncertainty estimates
- TST architecture is custom (not tsai-based), so lacks the validation history of InceptionTime
- CrossAttentionAlpha uses a single AE query token, which may limit expressiveness for heterogeneous plots with multiple vegetation types

---

## Conclusion

`ae_training` extends the TRACEVE framework to multi-modal fusion, implementing a principled cross-attention architecture (CrossAttentionAlpha) that uses AlphaEarth foundation model embeddings as a global context query attending over Sentinel-2 time series observations. The repository is structured for clean ablation: MLPAlpha isolates AE contribution, TST isolates S2 contribution, and CrossAttentionAlpha tests fusion benefit. The skip connection and small-init design ensure training stability. This codebase represents the current frontier of the TRACEVE research line, combining task-specific spectral-temporal features with multi-modal foundation model representations.

## Related pages
- [[hiebl_2025_pretraining]]
- [[brown_2025_alphaearth]]
- [[transfer_learning_remote_sensing]]
- [[transformers_time_series]]
- [[traceve_pretraining]]
- [[ls_mapping]]
- [[sentinel_2]]
