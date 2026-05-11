---
title: "Mapping Tree Species Using Advanced Remote Sensing Technologies: A State-of-the-Art Review and Perspective"
authors:
  - Pu, Ruiliang
year: 2021
source: pu_2021_tree_species_mapping_review
tags:
  - remote-sensing
  - machine-learning
  - forest-ecology
status: read
---

# Pu 2021 — Tree Species Mapping with Advanced Remote Sensing: State-of-the-Art Review

## Title and Authors
**Mapping Tree Species Using Advanced Remote Sensing Technologies: A State-of-the-Art Review and Perspective**
Ruiliang Pu — *Journal of Remote Sensing*, 2021

## Quick Overview
- **Why is it relevant?** Comprehensive review covering four decades of tree species mapping with all major sensor types (satellite, airborne, UAV, LiDAR), synthesising trends and identifying future directions relevant to the wiki's core research focus.
- **What was done?** Reviewed 231 peer-reviewed papers on tree species classification using RS data, assessing sensor types, data fusion methods, classification techniques (including deep learning), and accuracy assessment practices.
- **What is the main outcome?** Three "multiple" method development trends dominate: multi-source data fusion, multi-season/temporal feature extraction, and multi-scale methods; deep learning is significantly improving accuracy.

## Main Goal and Fundamental Concept
Accurate tree species information is essential for forest management, biodiversity monitoring, carbon accounting, and invasive species tracking. This review assesses how 40 years of RS advances have addressed the challenge of species-level classification across increasing geographic scales, sensor capabilities, and algorithmic sophistication.

## Technical Approach
Literature synthesis of 231 papers (primarily post-2015) covering:
- **Sensors:** VHR satellite MS (IKONOS, WorldView), airborne HS (AVIRIS), airborne LiDAR, UAV-based sensors
- **Methods:** SVM, RF, MLP, CNN, LSTM; data fusion (optical+LiDAR, optical+SAR)
- **Feature selection:** Spectral, temporal, textural, structural features
- **Accuracy assessment:** OA, PA, UA, kappa; training/validation design issues

## Distinctive Features
- Reviews six earlier review papers to position its own contribution
- Identifies the "multiple method" development trend as the defining characteristic of recent progress
- Explicitly addresses limitations of satellite-based species mapping at moderate resolution
- Recommends three future directions: refining "multiple" methods, novel data fusion algorithms, spectral unmixing from satellite hyperspectral data

## Key Findings from Literature
- VHR satellite + airborne hyperspectral dominate the literature; UAV growing rapidly since 2015
- "Multiple" method trend: combining multiple sensors, seasons, and scales
- Machine learning (RF, SVM) remains widespread; deep learning (CNN) increasingly adopted post-2017
- LiDAR adds structural information that substantially improves species accuracy when combined with optical
- Class imbalance and small training sample sizes remain persistent challenges
- Spatial autocorrelation in train/test splits inflates reported accuracy (noted as a key concern)
- Moderate-resolution satellites (Sentinel-2, Landsat) increasingly viable for regional mapping via time series

## Advantages and Limitations
- **Advantages:** Broad scope; historical perspective; practical future directions
- **Limitations:** Review criteria may miss some studies; diversity of accuracy metrics prevents direct cross-study comparison; future directions are general rather than prescriptive

## Conclusion
Tree species mapping has advanced substantially through multi-source data fusion, multi-temporal feature extraction, and deep learning. Satellite hyperspectral (e.g., EnMap) and UAVs are identified as emerging frontiers. Remaining challenges are minority species, accurate accuracy assessment, and scaling from local test sites to national mapping.

## Related pages
- [[tree_species_mapping]]
- [[sentinel_2]]
- [[landsat]]
- [[transfer_learning_remote_sensing]]
- [[national_forest_inventory]]
