---
title: "Very-high resolution aerial imagery and deep learning uncover the fine-scale patterns of elevational treelines"
authors:
  - Erik Carrieri
  - Donato Morresi
  - Fabio Meloni
  - Nicolò Anselmetto
  - Emanuele Lingua
  - Raffaella Marzano
  - Carlo Urbinati
  - Alessandro Vitali
  - Matteo Garbarino
year: 2025
tags:
  - deep-learning
  - remote-sensing
  - forest-ecology
keywords:
  - treeline ecotone
  - UAV
  - Mask R-CNN
  - individual tree detection
  - instance segmentation
  - Italian Alps
status: read
---

## Title and Authors of the Paper

- "Very-high resolution aerial imagery and deep learning uncover the fine-scale patterns of elevational treelines"
- Erik Carrieri, Donato Morresi, Fabio Meloni, Nicolò Anselmetto, Emanuele Lingua, Raffaella Marzano, Carlo Urbinati, Alessandro Vitali, Matteo Garbarino
- *Biogeosciences* 22: 6393–6409 (2025); doi: 10.5194/bg-22-6393-2025

## Quick Overview

- **Why is it relevant?** Field plots resolve treeline patterns but are small, and satellites cover large areas but cannot resolve individual trees; UAV imagery plus deep learning is proposed as the bridge, and the paper gives an accuracy benchmark for treeline-specific tree mapping.
- **What was done?** A pre-trained Mask R-CNN (Detectron2) was fine-tuned on 5 cm RGB UAV orthomosaics from ten 9 ha treeline plots in the Italian Alps to detect, delineate, locate and measure the height of individual conifers.
- **What is the main outcome?** Detection rate was 70 % for conifers taller than 50 cm (F1 = 0.76) and 86 % for trees taller than 2 m; crown IoU was 0.76, and position and height RMSE were 59 cm and 92 cm.

## Main Goal and Fundamental Concept

- Goal: build and test a transferable workflow for stem-mapping treeline ecotones at the individual-tree scale over large extents.
- Idea: tree spatial patterns carry signatures of establishment, facilitation and competition, so accurate single-tree maps allow pattern-to-process inference (e.g. microsite effects on recruitment).
- Five hypotheses: (i) high detection performance, (ii) accurate tree attributes, (iii) generalisability across heterogeneous sites, (iv) good detection of tall trees and poorer detection of small ones without a critical drop in overall performance, (v) comparable performance across sites.

## Technical Approach

- **Sites**: ten treelines (2100–2400 m a.s.l.), each with a 300 × 300 m plot, spread over the western, central and eastern Italian Alps with at least 25 km between sites. Forestline was defined at 10 % canopy cover using the Copernicus Tree Cover Density layer. Dominant species are *Larix decidua* and *Pinus cembra*; edaphic treelines were avoided.
- **UAV data**: DJI Phantom 4 Pro V2 (RGB, 20 MP), three flight paths per set (two nadir, one 60° oblique), flights repeated for upper and lower plot halves, 80 % overlap, 12 GCPs with GNSS. Structure-from-Motion in Metashape produced 5 cm orthomosaics, DSMs, DTMs (ground points <10 cm above the DSM-derived surface) and canopy height models.
- **Field data**: 50 random trees per site (≥25 cm height) with GNSS position, height and species, giving 500 trees.
- **Deep learning**: Mask R-CNN, R101-FPN backbone, Adam (lr 0.00025), 512 × 512 px tiles, rotation/resize augmentation, early stopping on F1.
- **Training data**: 10 tiles per site (100 tiles, about 5 % of all tiles) annotated with help from Segment Anything, giving 1016 crowns (885 larch, 131 pine, labelled simply "tree"); split 70/20/10 into train/validation/test.
- **Transferability test**: leave-one-site-out spatial cross-validation (ten folds).
- **Evaluation**: precision, recall, F1, AP; detection rate and IoU after post-processing; position and height errors (RMSE, MAE, Euclidean distance); size classes small (≤130 cm), medium (130–200 cm), tall (>200 cm), compared with Wilcoxon tests.

## Distinctive Features

- Covers 90 ha across ten diverse treelines, which the authors say exceeds the extent of earlier treeline UAV studies (as far as they know).
- Needs very little training data (about 5 % of tiles) because it fine-tunes an off-the-shelf pre-trained model.
- AI-assisted annotation (Segment Anything) speeds up reference-data creation.
- Reports a leave-one-site-out transferability test rather than only a random tile split, and the authors state that the random split alone does not prove transferability.
- Delivers stem maps (position, crown, height) as a basis for later spatial-pattern analysis, which is the declared aim.

## Experimental Setup and Results

- **Test-split performance**: F1 0.76 for trees >50 cm; detection rate 70 % (52 % when including all small trees); IoU 0.76.
- **Size dependence**: detection rate 86 % and IoU 0.85 for tall trees; IoU for small and medium trees was significantly lower (about 0.70 for the lower classes).
- **Leave-one-site-out cross-validation**: F1 about 0.68, precision 0.90, recall 0.56, AP 0.36. Precision was high but recall low, so missed trees dominate the error (source: [[carrieri_2025_hr_imagery_treeline]]).
- **Attributes**: position RMSE 0.59 m; height RMSE 91.6 cm, MAE 71.8 cm, with a tendency to underestimate height. Position error was smaller for small trees than for tall ones.
- **Site effects**: best detection at Genevris (93 % for trees >50 cm); the Rion site, flown in late afternoon with long shadows, performed poorly in cross-validation, and the authors attribute this to illumination. Terrain characteristics showed no clear effect.

## Advantages and Limitations

**Advantages**
- Low-cost RGB UAV hardware and open-source software.
- Individual-tree outputs (position, crown, height) at plot-to-landscape scale.
- Tested over heterogeneous treelines with an explicit site-wise validation.

**Limitations**
- Small trees (<130 cm), the most relevant class for recruitment and treeline advance, are detected poorly; the authors state that these remain best covered by field surveys.
- No species classification: RGB imagery only, all crowns labelled "tree", only conifers considered, dwarf *P. mugo* excluded.
- The cross-validation recall (0.56) and AP (0.36) are clearly lower than the headline numbers, so the headline F1 of 0.76 reflects a within-site tile split; transfer to unseen sites is weaker.
- Illumination and phenology (shadows, season of flight) affect results and no standardised flight protocol was used across sites.
- Position error is partly due to GNSS inaccuracy and to stem base versus tree top offset.
- Single acquisition date per site (summer 2021, partly autumn), so no change detection yet; ground truth for IoU is semi-automatic annotation by a single operator.
- Heights are underestimated (DTM from SfM under crowns), and LiDAR would be more accurate but is costlier.

## Conclusion

- A fine-tuned Mask R-CNN on low-cost RGB UAV data maps individual conifers across Alpine treelines with useful accuracy for trees taller than about 50 cm, and well for trees taller than 2 m.
- It is a scale bridge between plots and satellites, but it is not a substitute for field data for seedlings and saplings, and transfer to new sites is weaker than the random-split numbers imply.
- For satellite-based treeline work this means that UAV stem maps can provide reference data at tree scale, but only for the taller size classes. See also [[garbarino_2023_treeline_remote_sensing]], [[nguyen_2024_treeline_monitoring]] and the treeline-monitoring concept page [[treeline_remote_sensing_monitoring]].
