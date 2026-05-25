---
title: "The European Forest Disturbance Atlas: a forest disturbance monitoring system using the Landsat archive"
authors:
  - Alba Viana-Soto
  - Cornelius Senf
year: 2025
tags:
  - remote-sensing
  - forest-ecology
  - machine-learning
keywords:
  - forest disturbance
  - Landsat
  - European Forest Disturbance Atlas
  - EFDA
  - annual mapping
  - disturbance agent
  - harvest
  - windstorm
  - bark beetle
  - fire
  - random forest
status: read
---

## 1. Title and Authors

**The European Forest Disturbance Atlas: a forest disturbance monitoring system using the Landsat archive**
Viana-Soto & Senf (2025), Earth System Science Data. Technical University of Munich.

## 2. Quick Overview

- **Why is it relevant?** Europe's forests are undergoing accelerating disturbance regime shifts; no prior product mapped disturbances annually, multi-event, and with agent attribution continent-wide.
- **What was done?** A Landsat-based classification framework was developed to map annual forest disturbances across continental Europe (1985–2023) at 30 m, with agent attribution (wind/bark beetle, fire, harvest).
- **What is the main outcome?** EFDA maps 439,000 km² of disturbed forest area (22% of EU forest) with overall F1 = 0.89 and quantifies harvest as the dominant agent (79.2%), available openly on Zenodo.

## 3. Main Goal and Fundamental Concept

EFDA provides the first operational, annually-updatable, wall-to-wall forest disturbance monitoring system for continental Europe, going beyond prior single-event-per-pixel approaches to capture multiple disturbance events per time series, disturbance severity, and the most likely causal agent.

## 4. Technical Approach

- **Landsat data cube:** 115,663 Landsat 4–9 images (1984–2023), growing-season summer composites (June–September), processed with FORCE including atmospheric correction, topographic normalisation (C-correction), BRDF correction, and cloud/shadow masking (Fmask); best-available-pixel compositing with 10.1% → 4.9% gap-filling
- **Forest land use mask:** Random Forest trained on 20,084 manually interpreted forest pixels + 46,651 LUCAS non-forest reference pixels; applied across full time series stacked composites (FAO definition, MMU = 0.54 ha)
- **Annual disturbance detection:** Annual Random Forest classifier using spectral change features from target year (t₀) vs. prior year (t₋₁): NDVI, NBR, tasseled-cap brightness/greenness/wetness, Disturbance Index; SMOTE balancing for 3% disturbance prevalence; MMU = 3 pixels (0.27 ha); collapsing step to remove illogical consecutive detections within 4-year windows
- **Agent attribution:** Patch-level Random Forest with 18 predictors (spectral change, patch size/shape, landscape context) classifying into wind/bark beetle, fire, and harvest; background sample for harvest
- **Reference data:** 20,084 manually segmented Landsat pixels for 35 countries (Senf et al. 2018, 2021) + 12,571 agent reference points [[zhao_2022_forest_harvesting]]

## 5. Distinctive Features

- First European disturbance product capturing **multiple disturbance events per pixel** (predecessor Senf & Seidl 2021 limited to greatest event)
- Designed for operational annual updating — new composites trigger re-classification without recalibration
- Separates stand-replacing from non-stand-replacing disturbances in reference design
- Harvest is treated as a disturbance agent class (via background sampling), not excluded
- Wind and bark beetle merged into one class — ecologically justified as a disturbance complex, and practical given sparse pre-2017 bark beetle reference data

## 6. Experimental Setup and Results

**Land use mask accuracy:** Overall F1 = 0.92 (forest F1 = 0.91, non-forest F1 = 0.93); forest area vs. FAOSTAT: R² = 0.98, MAE = 6,019 km²

**Disturbance map accuracy:**

| Class | F1 | Commission | Omission |
|---|---|---|---|
| Overall | 0.89 | — | — |
| Undisturbed | 0.99 | <1% | <1% |
| Disturbed | 0.80 | 17.3% | 22.5% |

- Commission error decreases after 2000 (19.5% → 10.6%); pre-1990 noise drives early errors
- Omission driven by low-intensity/non-stand-replacing disturbances (omission drops to 14.2% for stand-replacing only)
- Disturbance year MAE = 1.91 years (R² = 0.73)

**Disturbance totals (1985–2023):**
- 439,000 km² total disturbed area (22% of EU forest)
- 610,000 km² counting multiple events (28% of pixels disturbed >1×)
- Harvest: 79.2%, wind/bark beetle: 12.0%, fire: 8.8%

**Agent model (spatial cross-validation, not map accuracy):**
- Overall error: 14.1%
- Wind/bark beetle: commission 10.5%, omission 19.1%
- Fire: commission 5.7%, omission 25.5%
- Harvest: commission 17.4%, omission 8.7%

## 7. Advantages and Limitations

**Advantages:**
- Longest consistent pan-European time series (1985–2023), 30 m, annually updatable
- Multiple disturbance events per pixel — important for reburns, short-rotation plantations
- Open-access product with full processing code for reproducibility [[schloegl_2026_reproducibility]]
- Captures disturbance severity (NBR change) as a continuous layer

**Limitations:**
- No independent map accuracy for agent attribution — only spatial cross-validation accuracy reported
- Low-severity and non-stand-replacing disturbances are systematically under-detected (high omission)
- 30 m resolution limits detection of fine-scale disturbances (MMU ≈ 0.27 ha)
- Wind and bark beetle cannot be separated — ecologically relevant distinction is lost pre-2017
- Commission error elevated pre-1990 due to limited Landsat image availability
- Italy-specific methods not independently validated; comparison to [[turubanove_2023_canopy_landsat]] shows divergence in absolute estimates

## 8. Conclusion

EFDA provides the most comprehensive and temporally consistent Landsat-based forest disturbance record for Europe, covering 1985–2023 with annual temporal resolution, multiple-event tracking, severity layers, and agent attribution. It demonstrates that classification-based approaches outperform trajectory segmentation for multi-event detection and commission error control. The product directly supports disturbance-ecology research and forest monitoring policy, and it is relevant context for canopy cover and tree cover change analyses [[wegler_2026_canopy_cover_loss]], [[thom_2026_disturbance_suitability]], [[grünig_2026_climate_change_disturbances_forest]].

## Related pages

- [[thom_2026_disturbance_suitability]]
- [[grünig_2026_climate_change_disturbances_forest]]
- [[wegler_2026_canopy_cover_loss]]
- [[turubanove_2023_canopy_landsat]]
- [[zhao_2022_forest_harvesting]]
- [[schloegl_2026_reproducibility]]
- [[forest_disturbance]]
- [[landsat_time_series]]
