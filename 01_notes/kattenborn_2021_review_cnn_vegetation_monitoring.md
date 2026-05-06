---
title: "Review on Convolutional Neural Networks (CNN) in vegetation remote sensing"
authors:
  - Kattenborn, Teja
  - Leitloff, Jens
  - Schiefer, Felix
  - Hinz, Stefan
year: 2021
source: kattenborn_2021_review_cnn_vegetation_monitoring
tags:
  - deep-learning
  - remote-sensing
  - forest-ecology
status: read
---

# Kattenborn et al. 2021 — Review on CNNs in Vegetation Remote Sensing

## Title and Authors
**Review on Convolutional Neural Networks (CNN) in vegetation remote sensing**
Teja Kattenborn, Jens Leitloff, Felix Schiefer, Stefan Hinz — *ISPRS Journal of Photogrammetry and Remote Sensing*, 2021

## Quick Overview
- **Why is it relevant?** Comprehensive review of why CNNs are uniquely suited for vegetation remote sensing, covering all major application domains from individual plant detection to species mapping and trait estimation.
- **What was done?** Systematic literature review synthesizing CNN applications in vegetation RS, covering sensor types, spatial resolution, reference data, architectures, and application tasks, with meta-analysis of reported accuracies.
- **What is the main outcome?** CNNs consistently outperform traditional ML for vegetation tasks, particularly where spatial patterns matter; very high spatial resolution data gains the most from CNN's spatial feature extraction capability.

## Main Goal and Fundamental Concept
CNNs differ from pixel-wise classifiers by learning hierarchical spatial features (edges, textures, shapes, objects) end-to-end without manual feature engineering. This review explains why this matters specifically for vegetation: plant organs, canopy structure, and community patterns all exist at spatial scales that CNNs are designed to exploit.

## Technical Approach
Literature synthesis covering:
- **CNN architectures:** Standard CNN, FCN, U-Net, SegNet, Faster-RCNN, ResNet variants
- **Sensors/platforms:** UAV, airborne, satellite (Sentinel-2, Landsat), hyperspectral
- **Spatial grain:** Sub-cm (UAV) to 10 m (satellite)
- **Tasks:** Individual plant/organ detection, species/community classification, trait estimation, change detection
- **Reference data:** Field surveys, herbaria, citizen science, VHR imagery interpretation
- **Multi-modal and multi-temporal applications**

## Distinctive Features
- Bridges procedural knowledge (CNN architecture/operation) with declarative knowledge (vegetation science domain)
- Explains the alignment between CNN inductive biases (local connectivity, translation invariance) and vegetation spatial structure
- Discusses CNN interpretability methods (saliency maps, Grad-CAM) and their potential for improving ecological understanding
- Addresses challenges specific to vegetation RS: complex radiative transfer, phenology, reference data acquisition

## Key Findings
- CNNs outperform shallow ML in most vegetation tasks, especially where spatial context matters
- Very high resolution (VHR) data benefits most from CNN's spatial feature exploitation
- Multi-modal (spectral + structural) and multi-temporal architectures are particularly flexible and effective
- Reference data acquisition remains the primary bottleneck for vegetation-specific CNN applications
- Visualisation/interpretability tools are emerging and can help researchers understand what CNN learns from vegetation imagery

## Advantages and Limitations
- **Advantages:** End-to-end learning; exploits spatial context; flexible architecture; strong empirical evidence of accuracy gains
- **Limitations:** High data requirements; computational cost; limited interpretability; reference data acquisition challenges in vegetation science; spatial autocorrelation in train/test splits inflates reported accuracy

## Conclusion
CNNs are transformative for vegetation remote sensing, particularly leveraging spatial patterns from VHR data. The review serves as a foundation for understanding deep learning application strategies in forest and vegetation mapping. Key remaining challenges are reference data availability, interpretability, and spatial validation design.

## Related pages
- [[transfer_learning_remote_sensing]]
- [[neural_network_training]]
- [[tree_species_mapping]]
- [[sentinel_2]]
- [[spectral_diversity_biodiversity]]
