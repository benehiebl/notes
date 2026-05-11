---
title: "Attention Is All You Need"
authors:
  - Vaswani, Ashish
  - Shazeer, Noam
  - Parmar, Niki
  - Uszkoreit, Jakob
  - Jones, Llion
  - Gomez, Aidan N.
  - Kaiser, Łukasz
  - Polosukhin, Illia
year: 2017
source: vaswani_2023_attention_is_all
tags:
  - deep-learning
  - machine-learning
status: read
---

# Vaswani et al. 2017 — Attention Is All You Need

## Title and Authors
**Attention Is All You Need**
Ashish Vaswani, Noam Shazeer, Niki Parmar et al. — *NeurIPS 2017* (arXiv 2023 version)

## Quick Overview
- **Why is it relevant?** Foundational paper introducing the Transformer architecture — the basis for nearly all modern large-scale sequence models, including time series transformers used for satellite image time series classification in forest mapping.
- **What was done?** Proposed a new sequence transduction architecture (the Transformer) based entirely on attention mechanisms, dispensing with recurrence and convolutions, and evaluated on machine translation benchmarks.
- **What is the main outcome?** Transformer achieves 28.4 BLEU (WMT 2014 En-De) and 41.8 BLEU (WMT 2014 En-Fr), outperforming all prior models including ensembles, while requiring significantly less training time due to full parallelisation.

## Main Goal and Fundamental Concept
Standard sequence models (RNNs, LSTMs) process sequences element-by-element, limiting parallelisation and making it hard to model long-range dependencies (information decay over many time steps). The Transformer replaces sequential processing with a **self-attention** mechanism that directly computes relationships between all positions in a sequence in parallel, enabling both long-range dependency modelling and full GPU parallelisation.

## Technical Approach
**Core components:**
- **Scaled dot-product attention:** `Attention(Q,K,V) = softmax(QKᵀ/√d_k)V` — computes weighted sum of values based on query-key similarity
- **Multi-head attention:** H parallel attention heads with different projections, concatenated → richer feature representations
- **Positional encoding:** Fixed sinusoidal or learnable encoding added to input embeddings to inject sequence order information (absent in attention mechanism)
- **Encoder-decoder structure:** Stacked (N=6) encoder blocks (self-attention + FFN); stacked decoder blocks (self-attention + cross-attention + FFN)
- **Residual connections + layer normalisation** around each sub-layer
- **Feed-forward networks:** Position-wise, applied to each token independently

## Distinctive Features
- First architecture to rely **entirely** on attention — no recurrence or convolution
- O(1) sequential operations (vs. O(n) for RNNs) enables full parallelisation during training
- O(1) path length between any two positions (vs. O(n) for RNNs) for long-range dependency modelling
- Highly modular and generalizable — the architecture has since been adapted to images (ViT), audio, time series, and more

## Experimental Setup and Results
- **WMT 2014 English-German:** 28.4 BLEU — +2 BLEU over best prior ensembles
- **WMT 2014 English-French:** 41.8 BLEU (new single-model state-of-the-art)
- **Training time:** 3.5 days on 8 P100 GPUs — fraction of cost of prior SOTA models
- **Generalisation:** Successfully applied to English constituency parsing (large and limited data)

## Advantages and Limitations
- **Advantages:** Fully parallelisable; models long-range dependencies effectively; serves as foundation for BERT, GPT, ViT, and time series transformers (TST, PatchTST, SITS-Former)
- **Limitations:** Quadratic attention complexity O(n²) for long sequences — problematic for very long time series; requires positional encoding to inject order information; large training data requirements

## Conclusion
The Transformer architecture is the most influential DNN contribution of the past decade, enabling modern large language models and foundation models. In the RS/forest mapping context, it directly underlies time series Transformer architectures (TST, PatchTST, SITS-Former) used for satellite image time series classification. Understanding the Transformer's attention mechanism is essential for applying and extending these models to forest type mapping from Sentinel-2 time series.

## Related pages
- [[neural_network_training]]
- [[transfer_learning_remote_sensing]]
- [[hiebl_2025_pretraining]]
