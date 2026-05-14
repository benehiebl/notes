---
title: "Monthly mapping of forest harvesting using dense time series Sentinel-1 SAR imagery and deep learning"
authors:
  - Zhao, Feng
  - Sun, Rui
  - Zhong, Liheng
  - Meng, Ran
  - Huang, Chengquan
  - Zeng, Xiaoxi
  - Wang, Mengyu
  - Li, Yaxin
  - Wang, Ziyang
year: 2022
source: zhao_2022_forest_harvesting
tags:
  - remote-sensing
  - deep-learning
  - forest-ecology
keywords:
  - Sentinel-1
  - SAR
  - forest harvesting
  - U-Net
  - deep learning
  - transfer learning
  - clear-cuts
  - landscape pattern
  - tropical deforestation
status: read
---

# Zhao et al. 2022 — Monthly Forest Harvesting Mapping with Sentinel-1 SAR + U-Net

## Title and Authors
**Monthly mapping of forest harvesting using dense time series Sentinel-1 SAR imagery and deep learning**
Feng Zhao, Rui Sun, Liheng Zhong, Ran Meng, Chengquan Huang, Xiaoxi Zeng, Mengyu Wang, Yaxin Li, Ziyang Wang — *Remote Sensing of Environment* 269: 112822 (2022).

## Quick Overview
- **Why is it relevant?** Demonstrates that S1 SAR + U-Net can recover monthly-resolution forest harvesting maps from speckle-noisy radar data — relevant for any disturbance mapping work where optical observation is cloud-limited.
- **What was done?** Trained a U-Net on Sentinel-1 monthly composites in two contrasting harvesting hotspots (California, USA; Rondônia, Brazil), used multi-temporal SAR filtering, and tested transferability via local fine-tuning.
- **What is the main outcome?** Mean F1 0.74–0.78, IoU 0.59–0.65 vs object-based 0.38–0.43 — DL captures landscape pattern; multi-temporal filtering adds +0.04 F1 / +0.06 IoU; transferable with sparse local fine-tuning.

## Main Goal and Fundamental Concept
Annual forest-loss products (e.g. Hansen Global Forest Change) cannot distinguish salvage logging from slash-and-burn or routine harvest because they lack sub-annual resolution. Optical SAR fusion or pixelwise time-series approaches require intensive site-specific normalisation. Zhao et al. exploit the fact that the *landscape pattern* of a harvested patch (geometry, contrast with surrounding intact forest) is distinctive in SAR data and can be learned by a U-Net.

## Technical Approach
- Two study sites:
  - **Rondônia, Brazil** — tropical deforestation hotspot
  - **California, USA** — managed-forest harvest hotspot
- **Sentinel-1 SAR data**: VV/VH GRD, IW mode, 6–12 day revisit; monthly composites (median).
- **Multi-temporal SAR filtering** to reduce speckle while preserving boundaries.
- **U-Net** encoder–decoder CNN: input = S1 monthly composite + previous month + change; output = binary harvest mask per pixel.
- Training labels: harvested patches digitised from high-resolution imagery (cf. Hansen / Curtis et al. 2018) over multiple years.
- Comparison: object-based segmentation + RF classifier as traditional baseline.
- **Transferability**: fine-tune model trained in one site with small local sample from another (sparse 5–10% local samples → near-optimal performance).

## Distinctive Features
- **Landscape-pattern learning**: U-Net captures the *shape and context* of harvested patches rather than per-pixel reflectance — robust to speckle.
- **Pure SAR**: no optical fusion needed → operational in cloudy regions (Amazon, SE Asia).
- **Monthly temporal resolution**: enables distinction between salvage logging (post-fire), slash-and-burn (dry season + fire), and routine timber harvest.
- **Sparse fine-tuning transfer**: drops training-data requirement when moving between regions.
- **Perimeter-to-area ratio (PAR)**: explored as a proxy for harvest-shape complexity that affects model transferability.

## Experimental Setup and Results

**Performance vs baseline**
- U-Net: F1 0.74–0.78, IoU 0.59–0.65
- Object-based + RF baseline: IoU 0.38–0.43
- Multi-temporal SAR filtering: +0.04 F1, +0.06 IoU

**Transferability**
- Model trained in California, fine-tuned with sparse Rondônia samples → near optimal Rondônia performance
- Shape-complexity (PAR) of harvested patches affects transfer: complex shapes (more variable PAR) need more local fine-tuning

**Ecological insights from monthly maps**
- Rondônia: 70%+ of harvest in July/August (dry season); 14% followed by fire within months (slash-and-burn signature)
- California: stable monthly rates with spikes after large fires (salvage logging signal)

## Advantages and Limitations
- **Advantages**: Cloud-independent monthly resolution; landscape-pattern learning robust to speckle; transferable model; explicit social-economic differentiation of harvest types.
- **Limitations**: Training labels still hand-digitised — labour-intensive; 6–12-day revisit means very fast events may be missed; selective logging (lower-impact, no clearing) not detected; California + Rondônia may not generalise to mixed-forest plantations (cf. [[qin_2026_forest_cover]] in southern China); only forest *loss* mapped, not regrowth.

## Conclusion
**Dense Sentinel-1 SAR + U-Net produces operationally useful monthly forest harvesting maps where optical sensors fail, by learning landscape-level pattern rather than per-pixel reflectance.** Transferable with sparse fine-tuning. Connects to broader concepts of disturbance mapping ([[forest_disturbances]], [[wegler_2026_canopy_cover_loss]]) and deep-learning for forestry ([[hamedianfar_2022_deep_learning]], [[kattenborn_2021_review_cnn_vegetation_monitoring]]). Methodological precedent for monthly Alpine disturbance mapping where cloud cover and complex topography limit optical workflows.

## Related pages
- [[forest_disturbances]]
- [[tree_species_mapping]]
- [[cloud_detection]]
- [[hamedianfar_2022_deep_learning]]
- [[kattenborn_2021_review_cnn_vegetation_monitoring]]
- [[deluca_2022_s1_s2_lulc_mapping]]
- [[wegler_2026_canopy_cover_loss]]
- [[turubanove_2023_canopy_landsat]]
- [[transfer_learning_remote_sensing]]
- [[qin_2026_forest_cover]]
