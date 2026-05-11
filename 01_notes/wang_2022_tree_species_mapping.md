---
title: "Assessing Landsat-8 and Sentinel-2 spectral-temporal features for mapping tree species of northern plantation forests in Heilongjiang Province, China"
authors:
  - Wang, Mengyu
  - Zheng, Yi
  - Huang, Chengquan
  - Meng, Ran
  - Zhao, Feng
year: 2022
source: wang_2022_tree_species_mapping
tags:
  - remote-sensing
  - machine-learning
  - forest-ecology
status: read
---

# Wang et al. 2022 — Landsat-8 and Sentinel-2 Spectral-Temporal Features for Tree Species Mapping in China

## Title and Authors
**Assessing Landsat-8 and Sentinel-2 spectral-temporal features for mapping tree species of northern plantation forests in Heilongjiang Province, China**
Mengyu Wang, Yi Zheng, Chengquan Huang et al. — *Forest Ecosystems*, 2022

## Quick Overview
- **Why is it relevant?** Quantifies the marginal contribution of red-edge bands, SAR, and temporal data density to plantation tree species classification accuracy — directly informing sensor and feature selection for time-series-based tree species mapping.
- **What was done?** Three classification experiment sets compared single-date, multi-date, and spectral-temporal features from Landsat-8 and Sentinel-2 (separately and fused) for mapping 4 keystone timber species in northern China plantation forests.
- **What is the main outcome?** Sentinel-2 consistently outperforms Landsat-8; NDTI and Tasseled Cap coefficients are most important features; increasing temporal density improves accuracy but saturates quickly (~2 key phenological images suffice).

## Main Goal and Fundamental Concept
For plantation forests with simpler species composition and regular stand structure, the study asks how much the red-edge capability and higher temporal resolution of Sentinel-2 improve species classification over Landsat-8, and whether fusing both sensors adds further gains beyond S2 alone.

## Technical Approach
- **Study area:** Heilongjiang Province, China (northern plantation forests: larch, Mongolian pine, Korean pine, Mongolian oak)
- **Sensors:** Landsat-8 (16-day) and Sentinel-2 (5-day), 7 image pairs from key growing stages
- **Experiment sets:**
  1. Single-date classification (7 dates separately)
  2. Multi-date classification (optimal season combinations)
  3. Spectral-temporal features (all available time series from each sensor + fusion)
- **Classifier:** Random Forest
- **Feature importance:** NDTI (SWIR1-SWIR2/SWIR1+SWIR2), Tasseled Cap, band-wise vegetation indices

## Distinctive Features
- Isolates red-edge contribution by comparing S2 with vs. without red-edge bands against L8
- Tests temporal saturation: when does adding more images no longer improve accuracy?
- Directly quantifies value of L8+S2 fusion vs. S2 alone — finds minimal additional gain

## Experimental Setup and Results
- **S2 outperforms L8:** 0.4–3.4% higher OA and 0.2–4.4% higher macro-F1 across all experiments
- **Red-edge contribution:** Provides some but not all of S2's advantage (SWIR features matter too)
- **Most important features:** NDTI and Tasseled Cap components; red-band vegetation indices important for time series
- **Temporal saturation:** OA improves from 90.1% (single-date) to 93.3% (S2 time series); similar with fusion (93.2%)
- **Two images suffice:** Results suggest ~2 images from key phenological stages capture most of the temporal signal

## Advantages and Limitations
- **Advantages:** Controlled experimental design isolating individual feature contributions; practical guidance for data acquisition planning
- **Limitations:** Only 4 species (plantation context is simpler than natural forests); temporal saturation finding may not generalise to more diverse natural forests; single study area

## Conclusion
Sentinel-2 consistently outperforms Landsat-8 for plantation tree species mapping, with improvement attributable to spectral richness (SWIR, red-edge) and temporal density. However, accuracy saturates after ~2 well-chosen phenological images — fusion with Landsat adds little over S2 alone. NDTI and Tasseled Cap are the most informative spectral features.

## Related pages
- [[sentinel_2]]
- [[landsat]]
- [[tree_species_mapping]]
- [[phenology]]
