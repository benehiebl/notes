---
title: "Detection and Modeling of Drought-induced Forest Dieback in Mediterranean Ecosystems"
authors:
  - Gabriele Giuseppe Antonio Satta
  - Francesca Giannetti
  - Antonio Deidda
  - Andrea Brandano
  - Andrea Lentini
  - Giovanni Piras
  - Pino Angelo Ruiu
  - Salvatore Seddaiu
  - Bruno Scanu
year: 2025
tags:
  - remote-sensing
  - machine-learning
  - forest-ecology
keywords:
  - Sentinel-2
  - vegetation indices
  - NGRDI
  - change detection
  - LogitBoost
  - random forest
  - SPI
  - Sardinia
  - holm oak dieback
status: read
---

## Title and Authors of the Paper

- "Detection and Modeling of Drought-induced Forest Dieback in Mediterranean Ecosystems"
- Satta GGA, Giannetti F, Deidda A, Brandano A, Lentini A, Piras G, Ruiu PA, Seddaiu S, Scanu B
- **SSRN preprint, not peer reviewed** (ssrn.com/abstract=5761729). The file is named `seddaiu_2025_mediterranean_dieback` but the first author is Satta; cite as Satta et al. 2025 (preprint) and check whether a journal version exists.

## Quick Overview

- **Why is it relevant?** It is a worked example of mapping an abrupt drought-induced canopy dieback event with Sentinel-2 and then modelling where it happened with climate, terrain and canopy predictors and spatial cross-validation, closely matching the methods needed for forest-stress work.
- **What was done?** Six Sentinel-2 indices were compared in an August 2023 vs August 2024 change detection over Sardinia (validated by photo-interpretation of PlanetScope), and the best index's dieback map was then used as label for Random Forest and LogitBoost models with topographic, soil, climate and vegetation predictors.
- **What is the main outcome?** NGRDI was the best single detector (Acc 0.95, κ 0.71, F1 0.74), about 110,400 ha of dieback were mapped, and the 12-month Standardised Precipitation Index was the most important predictor in the best LogitBoost model (AUC 0.95).

## Main Goal and Fundamental Concept

- Goals: (i) map dieback during an extreme climatic event, (ii) quantify the influence of environmental drivers, (iii) predict the spatial distribution of drought-induced dieback.
- Concept: spectral change between two Augusts (ΔIndex) captures sudden browning, and whether a pixel "died back" is then explained by long-term drought anomalies plus site conditions (water redistribution by terrain, canopy density).
- Separating a model with climate from a model without climate yields an "actual event" map vs an "environmental vulnerability" map.

## Technical Approach

- **Study event**: extreme dry and warm period summer 2023 to summer 2024 in Sardinia; holm oak (~255,000 ha) and cork oak (~153,000 ha) dominate forests (NFI).
- **Step 1, detection (Google Earth Engine)**: Sentinel-2 L2A harmonised, cloud-masked monthly composites for August 2023 and August 2024; 20 m bands resampled to 10 m; forest/shrub mask from Dynamic World (classes tree, shrub/scrub); burned areas of 2024 removed.
- **Indices**: NGRDI, NDVI, GNDVI, NBR, EVI, NDWI; ΔIndex = VI₂₀₂₄ − VI₂₀₂₃; dieback = ΔIndex < −0.1 (threshold taken from [[puletti_2019_drought_forest_health]] and related studies, not tuned); only patches > 1 ha kept.
- **Validation**: 3 km regular grid of points on 3 m PlanetScope, labelled affected/unaffected by expert visual interpretation; confusion-matrix metrics (accuracy, κ, sensitivity, specificity, precision, F1, balanced accuracy, McNemar).
- **Step 2, modelling (R)**: predictors at 50 m: slope, aspect, TPI, TRI, TWI from a 10 m DEM; SPI-3/6/12 from ERA5-Land (June–August 2024); SoilGrids properties (250 m); Copernicus tree cover density (TCD); collinearity filter (|r| < 0.7, VIF).
- **Samples**: 1 point/100 ha in dieback areas and 0.2 points/100 ha in unaffected areas (1,055 vs 4,597 points); Moran's I and Geary's C computed.
- **Models**: ranger Random Forest and LogitBoost with grid tuning, ROSE class balancing, spatial block cross-validation (blockCV, hexagonal blocks, five folds), predictor-group combinations (topography, soil, climate, vegetation).

## Distinctive Features

- Direct, quantitative comparison of six indices for abrupt drought dieback, including an RGB-only index (NGRDI) that outperforms NIR/SWIR indices.
- Explicit, spatially blocked validation and a climate-excluded counterfactual model to separate vulnerability from the realised event.
- Publicly available GEE application for the change detection, and region-wide coverage (Sardinia).

## Experimental Setup and Results

- **Index validation**: accuracy 0.87 (NBR) to 0.95 (NGRDI); κ 0.71 for NGRDI, 0.68 for NDVI and EVI, 0.17 for GNDVI; sensitivity highest for NBR and NDWI (0.83) and NDVI (0.81), NGRDI 0.69; precision 0.50 (NBR) to 0.80 (NGRDI); dieback prevalence in the reference points ~11–13 %; NBR and NDWI over-predicted dieback; McNemar showed no significant bias only for NGRDI and EVI.
- **Spatial pattern**: ~110,400 ha affected, clustered in eastern and southern Sardinia (Moran's I = 0.568, Geary's C = 0.463).
- **Models**: best overall LogitBoost with topography + climate + vegetation (AUC 0.95, prAUC 0.83, accuracy 0.91, κ 0.75, sensitivity 0.90, specificity 0.96); the competing model (apparently Random Forest, text partly garbled in extraction) had similar or higher AUC (≈0.97) and prAUC (0.92) but lower threshold metrics; models without climate dropped to sensitivity ≤ 0.62 and balanced accuracy ≤ 0.78; climate-only LogitBoost still reached AUC 0.87.
- **Importance**: SPI-12 (June 2024) highest (100), TCD 86, TRI 84, SPI-3 58–64; elevation ≤ 10; TPI and aspect < 5; soil variables low.
- **Maps**: ~16 % of forest and shrub area with predicted dieback probability > 60 % under the full model, ~39 % when climate was excluded.

## Advantages and Limitations

- **Advantages**: transparent workflow, open data only, spatial CV, scalable in GEE, and a useful negative result (GNDVI fails, NBR over-predicts).
- **Limitations** (critical reading):
  - Not peer reviewed; some values in the extracted text are inconsistent or garbled (e.g. F1 values for the model, block size), so numbers must be checked in the PDF before citing.
  - **Label circularity**: the model labels are the ΔNGRDI mask, not independent field data; the models therefore explain the index-derived mask (precision 0.80, sensitivity 0.69), and validation of the mask is only a 3 km grid of photo-interpreted points (dieback prevalence ~12 %, so few positive points).
  - Threshold −0.1 is borrowed, not calibrated; one pair of Augusts only, no phenological/atmospheric normalisation, burn and forest masks come from third-party products (Dynamic World, regional fire perimeters).
  - SPI-12 is a smooth ERA5-Land field (~9 km) from a single date, so its dominant importance may partly capture a regional gradient and spatial confounding rather than a process; with one event, the climate effect cannot be tested across years.
  - Class imbalance is handled with different sampling intensities and ROSE, so PPV (≥ 0.95) and "probability > 60 %" are not calibrated probabilities; threshold-based metrics such as the chosen "best" model depend on this design (AUC would favour the other model).
  - No biotic variables (*Phytophthora*), no management data, SoilGrids too coarse; the authors admit this and expect under-estimation of risk where pathogens are present.
  - NGRDI is an RGB index that captures visible browning; the authors note it likely misses early-stage stress, so results apply to late, visible dieback of this event.
- Transferability to other events, species or the Alps is untested.

## Conclusion

- Sentinel-2 ΔNGRDI is a reliable, cheap detector of abrupt Mediterranean canopy browning, and long-term drought (SPI-12) plus canopy density and terrain roughness explain where the 2024 dieback occurred in Sardinia.
- Good methodological template (index comparison, spatial CV, climate-excluded counterfactual) but the preprint status, pseudo-label design and single-event setting limit the strength of the driver conclusions.
- Relevant for: [[mediterranean_holm_oak_dieback]], [[drought_mortality]], [[sentinel_2]], [[ndvi]], [[area_of_applicability]], [[spatial_proxies_random_forest]]; companion overview: [[seddaiu_2025_quercus_dieback]].
