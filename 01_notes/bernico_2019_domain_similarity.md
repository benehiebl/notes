---
title: "Investigating the Impact of Data Volume and Domain Similarity on Transfer Learning Applications"
authors:
  - Bernico, Michael
  - Li, Yuntao
  - Zhang, Dingchao
year: 2019
source: bernico_2019_domain_similarity
tags:
  - deep-learning
  - machine-learning
keywords:
  - transfer learning
  - domain similarity
  - data volume
  - fine-tuning
  - feature extraction
  - convolutional networks
status: read
---

# Bernico et al. 2019 — Impact of Data Volume and Domain Similarity on Transfer Learning

## Title and Authors
**Investigating the Impact of Data Volume and Domain Similarity on Transfer Learning Applications**
Michael Bernico, Yuntao Li, Dingchao Zhang (State Farm Insurance) — *FTC 2018* / AISC 881: 53–62 (Springer, 2019).

## Quick Overview
- **Why is it relevant?** Quantifies — empirically and simply — how transfer-learning performance scales with target dataset size and source-target similarity; foundational reference for the "small data + pretraining" approach used in [[hiebl_2025_pretraining]], [[safonova_2023_small_data]], [[transfer_learning_remote_sensing]].
- **What was done?** Trained ConvNets (Inception V3, VGG16, VGG-Face) with feature-extraction vs fine-tuning on target datasets of growing size (10k–100k) under three regimes of source-target similarity (Dogs/Cats, MiniPlaces, IMDB-WIKI).
- **What is the main outcome?** Model accuracy improves **log-linearly** with target data size in every regime; for similar source-target domains, feature extraction = fine-tuning at small data, fine-tuning pulls ahead with more data; for dissimilar domains, fine-tuning is always required and more data is needed.

## Main Goal and Fundamental Concept
Transfer learning is widely used to compensate for scarce labels in target domains. Bernico et al. ask: how *much* target data is enough, and how does the answer depend on source-target similarity? They control for everything except data size and similarity to isolate the two factors.

## Technical Approach
- Three target datasets: Dogs/Cats (Kaggle), MiniPlaces (100 scene categories), IMDB-WIKI (~1 M face age labels).
- Three source models:
  - **Inception V3 (ImageNet)** → Dogs/Cats (exploratory)
  - **VGG-Face (face images)** → IMDB-WIKI (highly similar source/target)
  - **VGG16 (ImageNet)** → MiniPlaces (moderately different)
  - **VGG-Face** → MiniPlaces (highly different)
- Two strategies:
  - **Feature extraction**: freeze backbone, train new output layer
  - **Fine-tuning**: same as feature extraction, then unfreeze and continue training all layers
- Target data sizes: 10k → 100k in 10k steps; 10 epochs each; ADAM; 10k holdout.
- Metrics: categorical accuracy (classification) and MAE (regression).

## Distinctive Features
- Systematic factorial design: data-size × similarity × strategy.
- Reveals scaling laws (log-linear improvement with data).
- Practical business orientation (small-data regime typical in industry).
- Three concrete regimes of similarity covering most practical situations.

## Experimental Setup and Results

**Universal finding: accuracy grows log-linearly with target data size** (consistent with Sun et al. 2017 "Revisiting Unreasonable Effectiveness").

**Highly similar source/target (VGG-Face → IMDB-WIKI)**
- Feature extraction ≈ fine-tuning at small data sizes
- Fine-tuning pulls ahead as data grows beyond ~50k
- Very efficient transfer overall

**Moderately different (VGG16 → MiniPlaces)**
- Fine-tuning consistently > feature extraction
- Performance improves with data but plateaus more quickly
- Source features partially useful but require adaptation

**Highly different (VGG-Face → MiniPlaces)**
- Fine-tuning massively > feature extraction (frozen face features cannot describe scenes)
- More target data required for any acceptable performance
- Beyond a threshold, transfer benefit shrinks vs random-init training

## Practical Implications

| Source-target | Small data (~10k) | Larger data (~100k) |
|---|---|---|
| Similar | Feature extraction OK | Fine-tune for last gains |
| Moderate | Fine-tune | Fine-tune; needs more data |
| Different | Fine-tune full network | Consider training from scratch |

## Advantages and Limitations
- **Advantages**: Clean factorial design; log-linear scaling is operationally actionable; clear contrast of strategies vs similarity regimes.
- **Limitations**: Pre-2019, predates foundation models; ImageNet/face/scene similarity proxies may not generalise to all domains; no spatially-explicit RS use case; ConvNet architectures only (no transformers).

## Conclusion
**More target data always helps**, but how much you need depends on source-target similarity. Use **feature extraction** when domains are highly similar and data is scarce; **fine-tune** in all other cases; **train from scratch** only when source and target are so different that fine-tuning offers no benefit. Directly applicable to choosing pretraining strategies in [[hiebl_2025_pretraining]], [[hiebl_2026_alphaearth]], and the broader [[transfer_learning_remote_sensing]] workflow.

## Related pages
- [[transfer_learning_remote_sensing]]
- [[safonova_2023_small_data]]
- [[hiebl_2025_pretraining]]
- [[hiebl_2026_alphaearth]]
- [[chen_2020_contrastive_framework]]
- [[brown_2025_alphaearth]]
- [[hamedianfar_2022_deep_learning]]
- [[neural_network_training]]
- [[kattenborn_2021_review_cnn_vegetation_monitoring]]
