---
title: "Ten deep learning techniques to address small data problems with remote sensing"
authors:
  - Safonova, Anastasiia
  - Ghazaryan, Gohar
  - Stiller, Stefan
  - Main-Knorn, Magdalena
  - Nendel, Claas
  - Ryo, Masahiro
year: 2023
source: safonova_2023_small_data
tags:
  - deep-learning
  - remote-sensing
  - machine-learning
status: read
---

# Safonova et al. 2023 — Ten Deep Learning Techniques for Small Data Problems in Remote Sensing

## Title and Authors
**Ten deep learning techniques to address small data problems with remote sensing**
Anastasiia Safonova, Gohar Ghazaryan, Stefan Stiller et al. — *International Journal of Applied Earth Observation and Geoinformation*, 2023

## Quick Overview
- **Why is it relevant?** Directly addresses the core challenge of the wiki's research context — mapping rare or fine-grained ecological variables (EVE cover, forest types) where ground truth is expensive and limited.
- **What was done?** Reviewed 10 DL techniques for small-data RS problems, provided a decision flowchart for technique selection, and discussed applicability conditions and limitations with RS examples.
- **What is the main outcome?** Small data is a universal challenge in RS; 10 techniques (transfer learning, SSL, semi-supervised, few-shot, zero-shot, active, weakly supervised, multitask, process-aware, ensemble learning) and spatial k-fold CV collectively address different facets of the problem.

## Main Goal and Fundamental Concept
RS data are abundant, but labelled ground truth for specific ecological tasks (biodiversity, rare events, ecosystem states) is severely limited. DL requires large labelled datasets, creating a "small data problem." This review provides a structured guide to DL techniques that reduce or circumvent this requirement, framing them in terms of specific RS problem contexts.

## Technical Approach
Review and synthesis of 10 DL techniques:
1. **Transfer learning** — pretrain on large dataset, fine-tune on small target domain
2. **Self-supervised learning (SSL)** — learn representations from unlabelled data (masked value prediction, contrastive)
3. **Semi-supervised learning** — combine small labelled + large unlabelled
4. **Few-shot learning** — generalise from few examples per class
5. **Zero-shot learning** — classify unseen classes via attribute/description transfer
6. **Active learning** — iteratively select most informative samples for labelling
7. **Weakly supervised learning** — learn from noisy, approximate, or incomplete labels
8. **Multitask learning** — share representations across related tasks
9. **Process-aware learning** — incorporate physical constraints/knowledge
10. **Ensemble learning** — combine multiple models for robustness
+ **Spatial k-fold cross-validation** as a validation technique for spatially correlated RS data

## Distinctive Features
- Practical decision flowchart guiding users to select the appropriate technique based on available data, labels, and task structure
- RS-specific framing: addresses satellite data characteristics (temporal, spectral, spatial), not just general ML
- Covers both supervised and unsupervised paradigms
- Discusses spatial k-fold CV as critical for avoiding inflated accuracy estimates from spatial autocorrelation

## Key Recommendations
- Transfer learning from large pretrained models (ImageNet, RS foundation models) is the most accessible and broadly effective first approach
- SSL (masked value prediction, contrastive learning) is increasingly competitive as a pretraining strategy for RS time series
- Ensemble learning provides uncertainty estimates alongside predictions — valuable for remote sensing applications
- Spatial k-fold is essential for honest accuracy assessment in spatially autocorrelated RS data

## Advantages and Limitations
- **Advantages:** Practical decision framework; comprehensive coverage; RS-specific examples; open flowchart
- **Limitations:** Review scope is broad — each technique could warrant its own review; technique interactions are not deeply explored; examples are illustrative rather than benchmarked

## Conclusion
The "small data problem" is pervasive in ecologically-focused RS. Transfer learning, SSL, and ensemble approaches are the most immediately applicable techniques for the wiki's research context (EVE mapping, tree species classification with limited ground truth). Spatial k-fold CV is non-negotiable for valid RS accuracy assessment.

## Related pages
- [[transfer_learning_remote_sensing]]
- [[neural_network_training]]
- [[hiebl_2025_pretraining]]
- [[sampling_bias_remote_sensing]]
