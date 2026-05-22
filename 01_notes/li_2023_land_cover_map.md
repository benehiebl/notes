---
title: "SinoLC-1: the first 1m resolution national-scale land-cover map of China created with a deep learning framework and open-access data"
authors:
  - Zhuohong Li
  - Wei He
  - Mofan Cheng
  - Jingxin Hu
  - Guangyi Yang
  - Hongyan Zhang
year: 2023
tags:
  - deep-learning
  - remote-sensing
  - machine-learning
keywords:
  - land cover mapping
  - very high resolution
  - VHR
  - weakly supervised
  - self-supervised
  - Google Earth
  - China
  - SinoLC-1
  - L2HNet
  - national scale
status: read
---

## 1. Title and Authors

**SinoLC-1: the first 1m resolution national-scale land-cover map of China created with a deep learning framework and open-access data**
Li et al. (2023), Earth System Science Data. Wuhan University.

## 2. Quick Overview

- **Why is it relevant?** Producing national-scale VHR land-cover maps without manual annotation is a fundamental methodological challenge with direct relevance to weakly supervised learning from coarser reference products.
- **What was done?** A weakly and self-supervised deep-learning framework (L2HNet) was trained on open-access data (three 10 m GLC products + OSM + 1 m Google Earth imagery) to produce a 1 m national land-cover map of China (SinoLC-1, 11 classes).
- **What is the main outcome?** SinoLC-1 achieves 73.61% overall accuracy and κ = 0.66 over ~9.6 million km², with 6.4% misestimation vs. official surveys, at the finest spatial resolution of any existing China-wide product.

## 3. Main Goal and Fundamental Concept

The study addresses the challenge of scaling VHR land-cover mapping to national extent without costly manual annotation. The core idea is to exploit the ensemble agreement of multiple coarse (10 m) GLC products as weak supervision, then refine predictions at 1 m resolution using self-supervised consistency losses — eliminating the resolution mismatch between coarse labels and fine imagery.

## 4. Technical Approach

- **Imagery:** 1 m Google Earth imagery tiles covering mainland China (~9.6 million km², 73.25 TB), divided into 7 geographic regions
- **Weak training labels:** Intersection of three 10 m GLC products (FROM-GLC10, ESA_GLC10, ESRI_GLC10) to identify high-confidence pixels; OSM road vectors added for traffic class
- **L2HNet architecture:**
  - Resolution-preserving (RP) backbone — extracts features without downsampling to preserve 1 m spatial detail
  - Confident Area Selection (CAS) module — weakly supervised; selects pixels where coarse label is reliable
  - Low-to-High (L2H) self-supervised loss — penalises inconsistency between coarse-label prediction and refined VHR prediction without manual annotation
  - Final loss: L = L(Y', Ŷ, G) + L_L2H
- **Classification scheme:** 11 classes (cropland, forest, grassland, shrubland, wetland, water, tundra, impervious surface, barren, snow/ice, traffic route)
- **Processing:** ~10 months on large-scale computing servers; parallel regional processing

## 5. Distinctive Features

- First 1 m national-scale land-cover map without any manual annotation — relies entirely on open-access labels and imagery
- Explicit resolution-mismatch handling via the L2H loss — conceptually similar to the soft-label problem in species mapping [[ball_2026_foundation_models]]
- OSM integration for a dedicated traffic route class — typically absent in satellite-only approaches
- Validated at provincial level (98 municipal-level areas) and compared against 5 GLC products and official survey statistics

## 6. Experimental Setup and Results

| Metric | Value |
|---|---|
| Overall accuracy | 73.61% |
| Cohen's κ | 0.6595 |
| Statistical misestimation vs. official surveys | 6.4% |

- Outperforms all compared 10–30 m GLC products in spatial detail and landscape representation
- Accuracy is lower in absolute terms than some 30 m products (e.g. FROM-GLC30: 83%), attributable to much finer resolution capturing genuine sub-pixel heterogeneity
- Highest commission error for spectrally similar classes (e.g. grassland vs. shrubland)

## 7. Advantages and Limitations

**Advantages:**
- Demonstrates that weakly supervised learning from coarse GLC label agreement is a viable path to VHR national mapping without field annotation
- Fully open-access data pipeline — Google Earth + OSM + public GLC products
- Resolution-preserving backbone design is transferable to other VHR mapping tasks

**Limitations:**
- 73.61% overall accuracy is moderate; inferior to manually annotated regional products
- Google Earth imagery is temporally inconsistent — different acquisition dates across China introduce spectral artefacts
- No temporal component — single-date snapshot, not a time series
- China-specific application; transferability to other continents requires re-training
- Coarse-label noise in weak supervision propagates to output where GLC products disagree
- Forest class not separately validated at species or functional type level — limited relevance for tree species mapping tasks

## 8. Conclusion

Li et al. (2023) demonstrate that combining coarse GLC ensemble agreement as weak labels with a self-supervised resolution-refinement loss enables national-scale 1 m land-cover mapping without manual annotation. The core methodological contribution — resolving the resolution mismatch between coarse labels and fine imagery through the L2H framework — is conceptually relevant to any task where training labels originate from a coarser source than the inference imagery, including the weakly supervised and soft-label approaches used in forest species mapping [[ball_2026_foundation_models]]. The specific application to China land cover is peripheral to this wiki's European forest focus, but the weak-supervision methodology is broadly applicable.

## Related pages

- [[ball_2026_foundation_models]]
- [[blickensdörfer_2024_tree_species]]
- [[weakly_supervised_learning]]
- [[land_cover_mapping]]
- [[deep_learning_remote_sensing]]
