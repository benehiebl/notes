---
title: "Fractional evergreen forest cover mapping by MODIS time-series FEVC-CV methods at sub-pixel scales"
authors:
  - Yang, Yingying
  - Wu, Taixia
  - Wang, Shudong
  - Li, Hao
year: 2020
source: yang_2020_modis_evergreen
tags:
  - remote-sensing
keywords:
  - evergreen forest
  - fractional cover
  - MODIS
  - NDVI time series
  - coefficient of variation
  - dimidiate pixel model
  - sub-pixel mapping
status: read
---

# Yang et al. 2020 — Fractional Evergreen Forest Cover Mapping with MODIS Time Series

## Title and Authors
**Fractional evergreen forest cover mapping by MODIS time-series FEVC-CV methods at sub-pixel scales**
Yingying Yang, Taixia Wu, Shudong Wang, Hao Li — *ISPRS J Photogramm Remote Sens* 163: 272–283 (2020).

## Quick Overview
- **Why is it relevant?** Sub-pixel fractional evergreen cover mapping using only MODIS NDVI time-series statistics — a classical, interpretable benchmark against which DL-based EVE mapping (e.g. [[hiebl_2025_pretraining]]) should be compared.
- **What was done?** Combined the Fractional Evergreen Forest Cover (FEVC) model (a dimidiate pixel linear mixing model using intra-annual NDVI minimum) with the Coefficient of Variation (CV) of the NDVI time series to discriminate evergreen from deciduous and crops; verified against 2 m Gaofen-1 imagery.
- **What is the main outcome?** Overall accuracy >90%, RMSE ≈10% on fractional cover, with better performance in non-urban areas than urban areas.

## Main Goal and Fundamental Concept
Evergreen forests are a key class for biodiversity and carbon studies but are hard to map at sub-pixel scale in fragmented landscapes (e.g. southern China). Existing approaches either ignore the mixed-pixel problem (pure pixel-based classification) or work only at small scales (high-resolution fusion). Yang et al. propose a two-step method: (1) extract fractional evergreen cover via a linear-mixing model using **the intra-annual NDVI minimum** as the dominant signal (only evergreen + soil remain when other vegetation senesces); (2) discriminate evergreen from deciduous and crops via the **Coefficient of Variation** of the time-series NDVI (evergreen is flatter through the year).

## Technical Approach
- Study area: Jiangsu + Anhui + Zhejiang + Shanghai, 359,000 km², subtropical China.
- MODIS MOD13Q1 NDVI (16-day, 250 m), 2017, 23 scenes per pixel.
- Preprocessing: MNSPI cloud replacement + Savitzky-Golay smoothing.
- **FEVC model** (Eq. 2):
  - `fc_ever = (NDVI_annmin − NDVI_soil_annmin) / (NDVI_veg_annmin − NDVI_soil_annmin)`
  - Uses intra-annual NDVI minimum (when only evergreen remains photosynthetically active).
- **CV decomposition**:
  - `CV_ai` (intra-annual): low for evergreen (stable NDVI), higher for deciduous (large amplitude)
  - `CV_kp` (continuous-crop key phenology period): used to discriminate evergreen from continuous crops that also have low annual CV
- Spatial heterogeneity handled by gridded threshold estimation (urban vs non-urban; grid units).
- Validation: 2 m Gaofen-1 PMS imagery; RMSE + MRE on fractional cover.
- Comparison with 30 m GLC 2015 and 500 m MODIS MCD12Q1.

## Distinctive Features
- **Pure NDVI-based, interpretable**: no DL, no auxiliary data — relies entirely on linear-mixing assumption + statistics of one NDVI year.
- **Fractional output**: sub-pixel cover rather than binary classification.
- **CV filter** explicitly separates evergreen from continuous crops, which often confound NDVI-only approaches.
- **Grid-based threshold adaptation** to spatial heterogeneity.

## Experimental Setup and Results

**Quantitative accuracy**
- Overall accuracy: >90%
- RMSE of fractional cover: ~10%
- Mean Relative Error (MRE): lower in non-urban than urban areas

**Comparative**
- Outperforms 500 m MCD12Q1 and 30 m GLC 2015 at the fractional cover task in this region
- Handles urban evergreen trees better than coarse classifications

## Advantages and Limitations
- **Advantages**: Conceptually clear (linear mixing on NDVI minimum); computationally light; physically interpretable; produces fractional rather than binary maps; explicit handling of crop confusion.
- **Limitations**: 250 m MODIS resolution coarse for stand-level analysis; depends on stable seasonal contrast (works well in subtropical China; less so where evergreen niches blur with deciduous in mild winters, e.g. Mediterranean); urban accuracy lower; cannot distinguish evergreen species; linear-mixing assumption fragile in highly heterogeneous pixels.

## Conclusion
**The FEVC-CV method demonstrates that careful use of NDVI time-series statistics can yield fractional evergreen-cover maps at sub-pixel scales without DL or auxiliary data.** Important methodological precedent for benchmarking DL-based EVE cover regression workflows ([[hiebl_2025_pretraining]], [[hiebl_2026_alphaearth]]) — the FEVC + CV pair establishes the interpretable baseline. The principle (use intra-annual NDVI minimum to isolate persistently green vegetation) generalises beyond subtropical China and is worth keeping in the methodological toolkit.

## Related pages
- [[ndvi]]
- [[phenology]]
- [[tree_species_mapping]]
- [[evergreen_broadleaved_expansion]]
- [[hiebl_2025_pretraining]]
- [[hiebl_2026_alphaearth]]
- [[chastain_2007_eve_landsat_understory]]
- [[kang_2021_lai_landsat]]
- [[sampling_bias_remote_sensing]]
