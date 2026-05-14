---
name: transformer_sits
description: Transformer architectures and self-supervised pretraining for satellite image time series (SITS) — masked-value prediction, multi-sensor fusion, and lightweight pixel-time-series models
type: reference
tags:
  - deep-learning
  - remote-sensing
---

# Transformers for Satellite Image Time Series (SITS)

**Summary**: Transformer encoders adapted to satellite image time series (SITS) — pixel-based (SITS-BERT, Time Series Transformer), patch-based (SITS-Former), and multi-sensor lightweight (PRESTO) — are the dominant architectural family for time-series RS classification and regression. **Self-supervised pretraining via masked-value prediction** (BERT-style adapted to continuous-valued time series) is the standard transfer-learning paradigm, leveraging massive unlabelled SITS archives to overcome label scarcity.

**Sources**: [[zerveas_2020_framework_transformer]], [[yuan_2022_sitsformer]], [[yuan_2023_pretraining]], [[tseng_2024_presto]], [[vaswani_2023_attention_is_all]], [[wen_2023_transformers_time_series]], [[tan_2021_tser]], [[hiebl_2025_pretraining]], [[hiebl_2026_alphaearth]]

**Last updated**: 2026-05-14

---

## Why Transformers for SITS

SITS has three structural properties that fit Transformer architectures well:
1. **Sequential**: monthly or per-acquisition observations form a sequence
2. **Long-range dependencies**: phenology spans the full growing season (~5–12 months)
3. **Irregular sampling**: cloud cover and orbit overlap produce non-uniform intervals

Compared to RNNs/LSTMs:
- **Parallelisable training** (no sequential recurrence)
- **O(1) path length** between any two timesteps → effective long-range modelling
- **Multi-head attention** captures multi-scale temporal patterns (seasonal, phenological, event-scale)
- Outperforms TempCNN, LSTM, GRU on raw SITS with noisy observations (source: [[yuan_2023_pretraining]])

(source: [[vaswani_2023_attention_is_all]], [[wen_2023_transformers_time_series]], [[transformers_time_series]])

## Architectural Lineage

**TST — Time Series Transformer (Zerveas et al. 2020)**
- First Transformer encoder dedicated to multivariate time series representation learning
- Unsupervised pretraining via input-denoising / masked-value reconstruction
- Outperforms supervised SOTA (TS-CHIEF, HIVE-COTE, ROCKET, InceptionTime) on UEA/Monash benchmarks
- Architecture template behind TRACEVE pipelines (source: [[zerveas_2020_framework_transformer]], [[traceve_pretraining]], [[ae_training]], [[ls_mapping]])

**SITS-BERT (Yuan & Lin 2020/2022)**
- First BERT-style SSL pretraining adapted to SITS
- Pixel-based: per-timestep (observation, DOY) tokens
- Sinusoidal DOY positional encoding handles irregular sampling
- Pretraining: regress randomly contaminated observations from the rest of the time series
- +1.91% to +6.69% accuracy over supervised baselines on three SITS classification benchmarks
- (source: [[yuan_2023_pretraining]])

**SITS-Former (Yuan et al. 2022)**
- Extension of SITS-BERT to **patch-based** input (5 × 5 image patches)
- 3D-CNN patch embedding + Transformer encoder
- Pretraining: regress masked-patch central pixels from the rest
- +2.64% to +3.30% OA over fully supervised
- Captures spatial + spectral + temporal jointly (source: [[yuan_2022_sitsformer]])

**PRESTO (Tseng et al. 2024)**
- Lightweight (< few M parameters), **multi-sensor**, pixel-time-series Transformer
- Pretrained on 21.5 M global pixels × 12 months × 7 data products (S1+S2+ERA5+NDVI+Dynamic World+DEM+location)
- Masked-autoencoding with 4 masking strategies (timestep, channel, contiguous-block, etc.)
- Up to **1000× fewer parameters** than ViT-based foundation models with competitive performance
- Robust to missing data and inputs of varying shape (source: [[tseng_2024_presto]])

**TST_AEF,S2 (Hiebl et al. 2026)**
- Cross-attention fusion of AlphaEarth Foundation embeddings + Sentinel-2 SITS via Transformer
- Best Italian forest type + EVE cover performance (RMSE 0.161, Acc 0.757)
- AEF embeddings reduce S2 compute requirement by 10–24× (source: [[hiebl_2026_alphaearth]])

## Self-Supervised Pretraining Paradigm

**Masked-Value Prediction (MVP)** — the BERT idea for SITS:

```
1. Take an unlabelled pixel-time-series x = {x_t}
2. Randomly mask some entries: x̃ with ~25% values masked
3. Train Transformer to reconstruct masked values from surviving context
4. After pretraining, discard reconstruction head
5. Attach task-specific head, fine-tune on labelled target data
```

Variants:
- **Random timestep masking** (Zerveas, Yuan, PRESTO)
- **Random channel masking** (PRESTO)
- **Contiguous-block masking** (Hiebl 2025 — 16% mean window length, 25% total; source: [[hiebl_2025_pretraining]])
- **Central-pixel regression** (SITS-Former)
- **Adversarial denoising** (Yuan SITS-BERT)

## Positional Encoding for Irregular SITS

Two standard approaches:
- **Sinusoidal DOY encoding**: vector assigned per Day-of-Year, allows cross-year alignment (Yuan SITS-BERT, SITS-Former)
- **Learnable positional embedding**: indexed by timestep position (TST, PRESTO)

DOY encoding usually wins on irregularly-sampled SITS because it preserves seasonal semantics (source: [[yuan_2022_sitsformer]], [[yuan_2023_pretraining]]).

## Pixel-Based vs Patch-Based

| Property | Pixel-based (TST, SITS-BERT, PRESTO) | Patch-based (SITS-Former, TST_AEF,S2) |
|---|---|---|
| Spatial context | None | Local 5×5 to multi-scale |
| Compute | Light | Heavier |
| Memory | Small | Larger |
| Best for | Pure temporal phenology, scarce labels, scale | Texture-rich problems (orchards, plantations), VHR |
| Examples | Crop classification, EVE cover regression | Tree species classification with regular spacing |

Pixel-based often surprises with strong performance — many RS tasks need small receptive fields and benefit more from time + multi-sensor than from spatial context (source: [[tseng_2024_presto]]).

## Comparison with Foundation Models

| Property | SITS Transformer (PRESTO/SITS-Former) | Foundation model (AlphaEarth) |
|---|---|---|
| Pretraining scale | 10⁷ pixel-time-series | 10⁹ multi-modal observations |
| Parameter count | < 10 M | ~500 M |
| Spatial context | Local (patch) or none (pixel) | Multi-scale, spatially aware |
| Multi-sensor | Yes (PRESTO) | Native |
| Frozen embedding use | Possible | Designed for this |
| Best when | Modest compute, time-rich problems | Frozen embeddings + scarce labels, large-scale mapping |

For Italian forest mapping, the wiki research uses both: SITS Transformer fine-tuning ([[hiebl_2025_pretraining]]) and AlphaEarth-based cross-attention fusion ([[hiebl_2026_alphaearth]]).

## Time Series Extrinsic Regression Context

Many SITS tasks (canopy cover, EVE fraction, biomass) are **scalar regression from a time series** — TSER (source: [[tan_2021_tser]]). Transformer + pretraining is the dominant method; the Rocket baseline ([[tan_2021_tser]]) is the simplest non-DL benchmark.

## Practical Recommendations

- **Pretrain whenever possible** — gains of 2–7 pp accuracy or RMSE are typical
- **DOY-based positional encoding** for irregular SITS
- **Pixel-based for scarce labels + pure phenology**; patch-based for texture-dependent tasks
- **PRESTO** as a lightweight starting point when compute is limited; **AlphaEarth + Transformer** as a heavy alternative
- **β-NLL deep ensembles** (see [[deep_ensemble_uncertainty]]) layered on top for uncertainty
- **Spatial CV** to validate honestly (see [[spatial_proxies_random_forest]])

## Related concepts
- [[transformers_time_series]]
- [[transfer_learning_remote_sensing]]
- [[deep_ensemble_uncertainty]]
- [[neural_network_training]]
- [[tree_species_mapping]]
- [[spatial_proxies_random_forest]]
