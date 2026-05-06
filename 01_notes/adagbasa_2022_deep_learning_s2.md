---
title: "Application of deep learning with stratified K-fold for vegetation species discrimination in a protected mountainous region using Sentinel-2 image"
authors:
  - Adagbasa, Efosa G.
  - Adelabu, Samuel A.
  - Okello, Tom W.
year: 2022
source: adagbasa_2022_deep_learning_s2
tags:
  - deep-learning
  - remote-sensing
  - sentinel-2
  - vegetation-mapping
status: read
---

# Adagbasa et al. 2022 — Deep Learning with Stratified K-Fold for Vegetation Species Discrimination

## Title and Authors
**Application of deep learning with stratified K-fold for vegetation species discrimination in a protected mountainous region using Sentinel-2 image**
Efosa G. Adagbasa, Samuel A. Adelabu & Tom W. Okello — *Geocarto International*, 2022

## Quick Overview
- **Why is it relevant?** Demonstrates MLP deep learning for plant species-level classification using Sentinel-2 in a montane ecosystem, directly relevant to fine-scale vegetation mapping tasks.
- **What was done?** A multi-layer perceptron (MLP) deep neural network combined Sentinel-2 multispectral bands with Sentinel-1 SAR, vegetation indices, and ASTER DEM to discriminate grass species at Golden Gate Highlands National Park, South Africa.
- **What is the main outcome?** MLP with combined Sentinel-2 + ASTER DEM achieved the highest overall F1 score of 92%, outperforming Random Forest, SVM, and other conventional classifiers.

## Main Goal and Fundamental Concept
The study aims to discriminate multiple grass species at species level in a mountainous protected area using freely available satellite imagery and deep learning. The core hypothesis is that an MLP exploiting multi-source data (optical, SAR, DEM, vegetation indices) outperforms conventional machine learning classifiers for this fine-grained vegetation task.

## Technical Approach
- **Sensor combination:** Sentinel-2 reflectance bands + Sentinel-1 SAR + ASTER DEM + multiple vegetation indices as input features
- **Classifier:** Multi-layer perceptron (MLP) deep neural network
- **Cross-validation:** Stratified K-fold to ensure balanced class representation in training/test splits
- **Comparison:** Against Random Forest, SVM, Classification and Regression Trees (CART), LDA, KNN
- **Temporal focus:** Rainy-season imagery over two periods to capture intra-annual change in species distribution

## Distinctive Features
- First application of deep learning to satellite-based grass species discrimination at species level in a montane protected area
- Uses stratified K-fold cross-validation specifically to address class imbalance in species distribution data
- Assesses change in species distribution over 4 years, linking classification results to ecological succession patterns

## Experimental Setup and Results
- **Study area:** Golden Gate Highlands National Park, Free State, South Africa (~340 km², up to 2,829 m elevation)
- **Accuracy:** MLP + Sentinel-2 + ASTER DEM: F1 = 92%; outperformed all ML baselines
- **Adding SAR:** Sentinel-1 added modest improvement; DEM combination proved more impactful
- **Ecological finding:** Increased abundance of increaser-II species (e.g., *Eragrostis curvula*), decreased decreaser species (e.g., *Phragmites australis*) over 4 years

## Advantages and Limitations
- **Advantages:** MLP learns complex non-linear feature interactions; free Sentinel data; stratified K-fold reduces class imbalance bias
- **Limitations:** Mountainous terrain introduces topographic effects and shadows; no temporal time series used, only single-date composites; limited transferability to other regions without retraining; small study area

## Conclusion
This study confirms that MLP deep learning on combined Sentinel-2, Sentinel-1, vegetation indices and DEM outperforms conventional ML for grass species discrimination at species level. The stratified K-fold approach effectively handles class imbalance. Results demonstrate remote sensing can track ecological succession (increaser/decreaser species dynamics) at protected area scale.

## Related pages
- [[sentinel_2]]
- [[tree_species_mapping]]
- [[neural_network_training]]
- [[transfer_learning_remote_sensing]]
