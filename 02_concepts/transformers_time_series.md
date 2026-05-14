---
name: transformers_time_series
description: Transformer architecture for time series — self-attention, SITS adaptations, pre-training strategies, TST/InceptionTime for satellite image time series classification
type: reference
tags:
  - deep-learning
  - machine-learning
  - remote-sensing
---

# Transformers for Time Series

**Summary**: The Transformer architecture — based entirely on self-attention mechanisms — has become the dominant approach for sequence modelling, with growing applications to satellite image time series (SITS) classification and forecasting in remote sensing.

**Sources**: [[vaswani_2023_attention_is_all]], [[wen_2023_transformers_time_series]], [[hiebl_2025_pretraining]], [[hiebl_2026_alphaearth]], [[yuan_2025_sits_augmentation]], [[zerveas_2020_framework_transformer]], [[yuan_2022_sitsformer]], [[yuan_2023_pretraining]], [[tseng_2024_presto]], [[tan_2021_tser]]

**Last updated**: 2026-05-14

**Note**: For SITS-specific pretrained Transformer lineage (TST, SITS-BERT, SITS-Former, PRESTO), see the dedicated concept page [[transformer_sits]].

---

## The Original Transformer Architecture

The Transformer (source: [[vaswani_2023_attention_is_all]]) replaces recurrence entirely with self-attention:

**Core mechanism — scaled dot-product attention:**
- `Attention(Q,K,V) = softmax(QKᵀ/√d_k)V`
- Queries, keys, and values are linear projections of the input embeddings
- Output is a weighted sum of values where weights reflect query-key similarity

**Multi-head attention:**
- H parallel attention heads with different projection matrices
- Concatenated output → richer multi-scale representation
- Captures both local and global patterns simultaneously

**Architecture:**
- **Positional encoding:** sinusoidal or learnable encoding added to embeddings (no built-in sequence order in attention)
- **Encoder:** stacked self-attention + feed-forward blocks + residual connections + layer norm
- **Decoder:** adds cross-attention over encoder output (for seq2seq; encoder-only variants used for classification)
- Feed-forward network: `FFN(H') = ReLU(H'W₁ + b₁)W₂ + b₂`

**Key advantages over RNN/LSTM:**
- Full parallelisation during training (all positions processed simultaneously)
- O(1) sequential operations vs O(n) for RNNs
- O(1) path length between any positions → effective long-range dependency modelling
- Scales favourably with compute and data

## Transformer Adaptations for Time Series

Standard Transformer requires modifications for time series (source: [[wen_2023_transformers_time_series]]):

### Positional/Temporal Encoding
- **Fixed sinusoidal encoding:** Standard Transformer; works for regular sequences
- **Learnable temporal encoding:** Embeds absolute timestamps (year, month, day, hour) separately for each observation; essential for irregular SITS where cloud gaps create variable sampling intervals
- **Relative positional encoding:** Encodes pairwise position relationships rather than absolute positions

### Attention Modifications
- **Sparse attention (Informer):** Reduces quadratic O(n²) cost for long sequences by selecting top-k relevant pairs
- **LogSparse attention:** Reduces to O(n log n) for very long sequences
- **Multi-scale attention:** Separate attention at different temporal resolutions simultaneously

### Architecture-Level Modifications
- **Decomposition:** Explicit seasonal-trend decomposition before attention (Autoformer); particularly useful for vegetation SITS with strong annual phenological cycles
- **Patch-based tokenisation (PatchTST):** Divides time series into fixed-length patches treated as tokens; reduces effective sequence length and introduces local temporal context

## SITS-Specific Challenges and Solutions

Satellite image time series have unique properties (source: [[yuan_2025_sits_augmentation]]):
1. **Multivariate:** Multiple spectral bands processed simultaneously (cross-channel attention)
2. **Incompleteness:** Cloud contamination creates irregular/missing observations → interpolation resampling augmentation
3. **Spatio-temporal heterogeneity:** Same class shows different spectral signatures across years/regions due to phenology shifts

Key adaptations:
- **Irregular temporal encoding:** use actual acquisition timestamps, not index positions
- **Masking strategies:** handle missing observations; SSL via masked value prediction (MVP) uses the same mechanism as pre-training (source: [[hiebl_2025_pretraining]])
- **Data augmentation:** interpolation resampling, temporal shift, noise injection improve cross-year adaptation (source: [[yuan_2025_sits_augmentation]])

## Applications to Forest Mapping

SITS Transformers for tree species and forest type classification:
- **TST (Time Series Transformer):** Encoder-only Transformer for SITS classification; used in [[hiebl_2026_alphaearth]] as one of the architecture options for EVE cover mapping
- **InceptionTime:** 1D CNN-based time series classifier (not a Transformer, but often compared); primary architecture in Hiebl et al. 2025 due to strong performance on dense Sentinel-2 SITS (source: [[hiebl_2025_pretraining]])
- **CrossAttentionAlpha:** Cross-attention Transformer combining S-2 time series features with AlphaEarth foundation model embeddings — architecture in [[hiebl_2026_alphaearth]] for fusion

**Pre-training Transformers for SITS:**
- Masked value prediction (MVP) pretraining learns to reconstruct missing observations from context
- Forces the model to learn temporal continuity and phenological coherence
- Enables semi-supervised/SSL training on unlabelled satellite archives before fine-tuning on scarce labels

## Performance Characteristics

From empirical studies on SITS classification (source: [[wen_2023_transformers_time_series]], [[yuan_2025_sits_augmentation]]):
- Transformers competitive with or superior to LSTM for sequences >100 time steps
- Multi-layer CNNs (InceptionTime) often faster and comparably accurate for shorter, denser SITS
- Hybrid architectures (CA-TCN: channel attention + temporal CNN) combine efficiency of CNN with attention-based cross-channel modelling
- Pre-training on large archives substantially improves few-shot performance (1–10 labelled examples per class)

## Related pages

- [[transformer_sits]]
- [[neural_network_training]]
- [[transfer_learning_remote_sensing]]
- [[deep_ensemble_uncertainty]]
- [[hiebl_2025_pretraining]]
- [[hiebl_2026_alphaearth]]
- [[phenology]]
- [[sentinel_2]]
