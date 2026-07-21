---
title: "Multi-temporal forest monitoring in the Swiss Alps with knowledge-guided deep learning"
authors:
  - Nguyen, Thiên-Anh
  - Rußwurm, Marc
  - Lenczner, Gaston
  - Tuia, Devis
year: 2024
tags:
  - deep-learning
  - mountain-forests
keywords:
  - treeline
  - time series
  - convolutional neural network
  - gated recurrent unit
  - prior knowledge
  - temporal loss
  - historical aerial imagery
  - forest cover change
  - Swiss Alps
status: unread
---

## Title and Authors of the Paper
**Multi-temporal forest monitoring in the Swiss Alps with knowledge-guided deep learning**
Thiên-Anh Nguyen, Marc Rußwurm, Gaston Lenczner, Devis Tuia — *Remote Sensing of Environment* 305 (2024), 114109

## Quick Overview
- **Why is it relevant?** Shows how to monitor decades-long forest cover dynamics at the alpine treeline ecotone from heterogeneous historical aerial imagery, using only a single year of labels and domain-knowledge-guided temporal losses.
- **What was done?** Trained a U-Net + ConvGRU (irregular-time-gap variant) segmentation model on 1946–2020 SWISSIMAGE aerial time series over the Swiss Alps treeline, using segmentation labels only from 2020 and a custom loss encoding prior knowledge about forest cover dynamics (slow boundary change, abrupt loss only).
- **What is the main outcome?** The knowledge-guided multi-temporal model substantially improves forest boundary accuracy and temporal consistency over a mono-temporal baseline, and qualitatively reveals forest expansion at the upper treeline over 1946–2020.

## Main Goal and Fundamental Concept
- Goal: monitor forest cover change over a ~75-year historical time series of aerial imagery at the Swiss Alps treeline, where labels exist for only one (recent) acquisition year.
- Core idea: incorporate problem-specific prior knowledge (forest boundaries change slowly through time, except in case of abrupt loss from fire/windthrow/human intervention) directly into the training loss function, rather than requiring labels at every time step.
- Frames the problem as *sequence-to-sequence* / multi-temporal segmentation rather than independent mono-temporal classification, addressing large domain shifts across decades of different cameras/sensors/acquisition conditions.

## Technical Approach
- **Architecture:** U-Net (ResNet-18 encoder, ~19M params, stride reduced to 1 in first conv layer to preserve fine texture) as per-timestep image feature extractor, feeding a lightweight temporal module (~3,500 params): either a standard ConvGRU (Ballas et al. 2016) or an **IrregConvGRU** modified to weight update/reset gates by the time gap between irregular acquisitions.
- **Two-stage training:** (1) pretrain U-Net feature extractor mono-temporally on 2020 aerial imagery + DEM with SwissTLM3D forest labels (BCE loss); (2) jointly fine-tune feature extractor + temporal module on the full multi-temporal series, combining the segmentation loss (still only anchored on 2020 labels) with temporal losses.
- **Temporal losses tested:**
  - Generic: temporal MSE (tMSE) on predicted probabilities; temporal cross-entropy (tCE, after Saha et al. 2020) on predicted classes between consecutive time steps.
  - Domain-specific: **temporal Contour Alignment loss (tCA)**, a novel loss aligning the spatial gradients (Sobel, 7×7) of consecutive probability maps via cosine similarity, scaled by gradient norm — penalizes implausible abrupt/mixed boundary changes while tolerating slow gain and abrupt loss.
- **Data:** SWISSIMAGE HIST aerial photos 1946–2020 (12–20 acquisitions per 1 km² tile, avg. 14, harmonized to 1 m resolution; panchromatic pre-1998, RGB 1998–2020), SwissALTI3D DEM, SwissTLM3D forest polygons (2020 only) as training labels. Study area: 5,897 km² (Valais + Vaud), 2,660 tiles restricted to the 1,500–2,500 m a.s.l. subalpine–alpine transition. NIR excluded to avoid additional discontinuity in the historical series.
- **Evaluation:** 200 additional tiles manually annotated by the authors at random dates across 1946–2020 (100 val / 100 test), scored with IoU/F1 (segmentation) and a boundary-restricted F1c (within 25 m of contours).
- Data/statistics normalized per band and per acquisition year to reduce inter-sensor heterogeneity; time series processed in reverse chronological order (from 2020 back to 1946) so the model relies most on the best-quality, most recent imagery.

## Distinctive Features
- Novel domain-specific tCA loss explicitly encodes forest-dynamics prior knowledge (slow boundary change vs. permissible abrupt loss) as a differentiable term, rather than just generic temporal smoothness.
- IrregConvGRU handles genuinely irregular time gaps (1–34 years between acquisitions) via an explicit gap-scaling factor in the gate equations — most prior multi-temporal RS work assumes regular revisit intervals (e.g., Sentinel/Landsat).
- Trains a multi-temporal model with labels from a single time step and validates generalization across ~75 years of heterogeneous sensors (panchromatic film to digital RGB).
- Direct continuation of the group's treeline-ecotone forest mapping line — reuses the same Swiss Alps treeline study area and SwissTLM3D forest definition as [[nguyen_2022_forest_mapping_explainable]].

## Experimental Setup and Results
- Baseline (U-Net trained/pretrained only on 2020, applied mono-temporally, "U-Net2020"): All-years F1 = 85.6 ± 0.6, F1c = 66.7 ± 1.7 (much worse F1c on grayscale pre-1998 images, ~60%).
- Best multi-temporal model (U-Net + IrregConvGRU, tCE+tCA loss): All-years F1 = 88.1 ± 0.6, F1c = 80.9 ± 0.3 — F1c on grayscale images improved from ~60% to 81.0 ± 0.5.
- Ablations: tCE alone outperforms tMSE alone as the generic temporal loss; combining either with tCA further improves boundary accuracy (F1c), especially on older grayscale imagery; tCA alone underperforms without a generic consistency term.
- ConvGRU vs IrregConvGRU: similar overall performance, IrregConvGRU slightly better at boundaries and in qualitative examples with large/irregular time gaps (faster adaptation after long gaps).
- Trade-off: adding the temporal module slightly *decreases* performance on recent RGB (1998–2020) images while improving grayscale/historical performance substantially — attributed to reliance on prior (potentially wrong) predictions.
- Qualitative change-detection result (visual only, no quantitative trend validation): forest expansion detected at the upper treeline across 1946–2020, location-dependent rate; forest loss is rare in this dataset/time series.
- Documented failure cases: predictions not robust to shadows/clouds; rare acquisition patterns (snow/rock cover) especially in grayscale images; ambiguous shrub-forest vs. upright-forest boundary (a known difficulty for human annotators too, citing Rüetschi et al. 2021 and their own 2022 paper).

## Advantages and Limitations
- **Advantages:** requires labels for only one time step to train a model applicable across ~75 years of heterogeneous imagery; explicit encoding of forest-dynamics prior knowledge is interpretable and improves boundary accuracy where it matters ecologically (treeline); IrregConvGRU generalizes ConvGRU to irregular real-world time series; results reported over 5 seeded runs (variance quantified).
- **Limitations (critical read):**
  - The reported forest-expansion trend (Section 6.3, Fig. 13) is a purely **qualitative/visual** observation — no quantitative area statistics, uncertainty, or comparison against independent ground-truth trend data are given. This is a case study demonstration, not a validated ecological result.
  - Evaluation labels for historical years come from **manual, monocular photo-interpretation by the authors themselves** — inherently subjective, especially for the shrub-vs-upright-forest distinction the paper itself flags as difficult even for humans; no independent/blind annotation or inter-annotator agreement reported.
  - Train/val/test tiles are split spatially within a single, contiguous 5,897 km² region — no test of transfer to a different treeline / mountain range / country, so generalizability beyond the Swiss Alps and this specific aerial-photo archive is unverified.
  - The prior-knowledge assumption embedded in tCA (boundaries change slowly except abrupt loss) is domain-specific and hand-crafted; the authors explicitly note it would need to be redesigned for other land-cover types or dynamics (e.g., water, urban).
  - Binary forest/non-forest only — no species, structure, or canopy density information (contrast with the more detailed rule-based intermediate variables in [[nguyen_2022_forest_mapping_explainable]]).
  - Data not shared by the authors (Swisstopo licensing) — limits reproducibility/reuse outside Switzerland.
  - Adding the temporal module trades off a small performance loss on recent, high-quality RGB imagery for a large gain on old, low-quality imagery — a real generalization/architecture limitation acknowledged by the authors (Section 7.3), with proposed but untested fixes (stacked ConvGRU layers, Neural ODEs, temporal attention).

## Conclusion
- A U-Net + irregular-time-aware ConvGRU trained with a combination of generic (tCE) and domain-specific, prior-knowledge-guided (tCA) temporal losses can monitor forest cover across a ~75-year, irregularly-sampled, multi-sensor historical aerial image archive using labels from only one year.
- The approach meaningfully improves segmentation and especially boundary (contour) accuracy on old, low-quality (grayscale) imagery relative to a mono-temporal baseline trained only on recent labels.
- The demonstrated Swiss Alps treeline application shows qualitative upward/expanding forest cover trends consistent with known warming- and land-abandonment-driven treeline dynamics, but this specific trend claim is not quantitatively validated in the paper.
- The general recipe (architecture + problem-specific loss design) is presented as transferable to other long, sparsely-labeled Earth observation monitoring problems, though each new domain would require redesigning the domain-specific loss term.

## Related pages
- [[nguyen_2022_forest_mapping_explainable]]
- [[turubanova_2023_canopy_landsat]]
- [[wegler_2026_canopy_cover_loss]]
- [[noce_2023_altitude_shift_tree_italy]]
- [[transfer_learning_remote_sensing]]
- [[topographic_microclimate]]
- [[treeline_ecotone_theory]]
- [[treeline_remote_sensing_monitoring]]
