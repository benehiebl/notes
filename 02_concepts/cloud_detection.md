---
name: cloud_detection
description: Cloud and cloud shadow detection for optical satellite imagery — methods, features, validation, and impact on time series analysis
type: reference
tags:
  - remote-sensing
  - preprocessing
---

# Cloud and Cloud Shadow Detection

**Summary**: Cloud and cloud shadow (CCS) detection is an essential preprocessing step for optical satellite imagery; with global cloud fraction averaging 66%, unmasked clouds introduce systematic errors in all downstream products (land cover, LAI, phenology, time series analysis).

**Sources**: [[li_2022_cloud_detection]], [[qin_2026_forest_cover]], [[zhao_2022_forest_harvesting]], [[kollert_2021_tree_species]], [[blickensdörfer_2024_tree_species]]

**Last updated**: 2026-05-14

---

## Why Cloud Detection Matters

- Global average cloud fraction ≈ 66% — the majority of any satellite archive is cloud-affected (source: [[li_2022_cloud_detection]])
- Undetected clouds and shadows cause: commission errors in land cover maps; inflated NDVI in compositing; false change detection in time series; systematic gaps in spatial coverage
- [[sampling_bias_remote_sensing]]: non-uniform cloud frequency over time inflates apparent greening trends in long Landsat archives (source: [[bayle_2024_landsat_greening_inflated]])
- Cloud masks are a prerequisite for all Sentinel-2 and Landsat time series analysis

## Feature Taxonomy

Detection algorithms use features from one or more of these sources (source: [[li_2022_cloud_detection]]):

| Feature type | Examples |
|---|---|
| Spectral | Blue band (cloud bright), SWIR (cloud cold), cirrus band (1.38 μm) |
| Spectral-spatial | Texture, shape, spatial context |
| Spectral-temporal | Difference from cloud-free composite or prior scene |
| Spectral-spatial-temporal | Multi-temporal + spatial contextual models |
| Multi-source | Optical + SAR (cloud-penetrating radar reference) |

## Algorithm Types

- **Physical rule-based:** threshold tests on spectral properties (e.g., Landsat QA band, Sen2Cor SCL, Fmask); fast but miss thin clouds and misclassify bright surfaces (snow, sand)
- **Temporal-change based:** detect cloud-induced sudden reflectance changes in time series; effective for persistent cloud-free baseline comparisons
- **Machine learning:** RF, SVM classifiers on spectral/textural features
- **Deep learning (CNN/LSTM):** best current accuracy, especially for thin clouds and cloud shadows; combines spectral, spatial, and temporal features; growing dominant approach post-2017 (source: [[li_2022_cloud_detection]])

## Common Products

| Sensor | Cloud mask product |
|---|---|
| Landsat 8/9 | QA_PIXEL band (Fmask-derived); quality is variable for thin clouds |
| Sentinel-2 | Sen2Cor Scene Classification Layer (SCL); used in [[hiebl_2025_pretraining]], [[hiebl_2026_alphaearth]] |
| MODIS | MOD35 cloud mask; widely used but 500 m resolution |

## Thin Cloud and Bright Surface Challenges

- Thin/cirrus clouds: often transmissive; partially corrected by Sentinel-2 cirrus band (B10) but hard to fully detect
- Bright surfaces (snow, sand): spectrally similar to thick clouds; high false positive rate in rule-based methods
- Shadow detection: geometrically predicted from cloud position + solar angle, but requires accurate cloud height estimate

## Impact on Time Series Analysis

- Missing data from cloud masking creates irregular temporal sampling in Sentinel-2 SITS — a primary driver of the need for temporal interpolation (e.g., Whittaker smoother) and augmentation (e.g., interpolation resampling; source: [[yuan_2025_sits_augmentation]])
- High cloud frequency reduces effective observation density, especially in tropical and oceanic climates
- The CrossAttentionAlpha model in [[hiebl_2026_alphaearth]] is specifically designed to rely more on stable AEF embeddings when S2 cloud observation density is low

## Cloud-Prone Regions and Gap Filling

In persistently cloudy regions (subtropical / tropical monsoon zones, mountainous areas), cloud-free observations are scarce. Mitigation strategies (source: [[qin_2026_forest_cover]]):
- **Multi-sensor fusion** (Landsat + Sentinel-2 + MODIS) via DL reconstruction → seamless imagery and NDVI time series
- **Annual / multi-year compositing**: trade temporal resolution for completeness
- **STAARCH / HLS / Whittaker smoother**: classical gap-filling methods
- **DL-based reconstruction** outperforms classical methods for large gaps (>50%) but propagates reconstruction errors into downstream classifiers

For southern China (annual probability of valid Landsat-8 observation often 0–10%), DL reconstruction + RF classification produced annual 30 m forest cover maps with OA 0.904 (source: [[qin_2026_forest_cover]]).

### Multi-Temporal Cloud Removal (Image Reconstruction)

A related but distinct task from gap-filling time-series *metrics* (e.g. NDVI) is reconstructing full cloud-free *images* from short multi-temporal sequences (3 dates):
- **TSSMamba** (source: [[zhang_2026_statespacemodel]]): dual-branch state space model (Mamba) jointly modelling temporal-spectral and temporal-spatial dependencies across three cloud-contaminated Sentinel-2 acquisitions; outperforms CNN/Transformer/GAN baselines (PSNR up to 30.9 dB, SAM down to 4.98°) on three benchmarks (STGAN, Sen2_MTC, SEN12MS-CR-TS) with <1M parameters
- State space models (Mamba) offer linear-complexity sequence modelling vs. quadratic-cost Transformer self-attention — see [[transformers_time_series]] for architectural context
- Not yet validated for downstream forest/vegetation tasks (e.g. whether reconstructed pixels preserve phenological signal needed for SITS classification)

## Cloud-Independent Alternatives

Where optical sensors fail, **Sentinel-1 SAR** ([[sentinel_1_sar]]) provides cloud-independent imagery:
- Monthly S-1 composites + U-Net deep learning give mean F1 0.74–0.78 for monthly forest harvesting detection in California and Rondônia (source: [[zhao_2022_forest_harvesting]])
- S-1 backscatter complements optical phenology for tree species mapping in cloudy regions (source: [[blickensdörfer_2024_tree_species]])

## Mountain Forest Strategies

In Alpine regions where cloud-free single dates are rare across multi-orbit study areas (source: [[kollert_2021_tree_species]]):
- Three-monthly composites + Land Surface Phenology metrics outperform multitemporal classification (~85% vs 84.4% OA)
- Composites are more robust than relying on a small number of cloud-free single scenes
- Patch-stratified CV essential to prevent autocorrelation-inflated accuracy estimates (cf. [[spatial_proxies_random_forest]])

## Related pages

- [[landsat]]
- [[sentinel_2]]
- [[sentinel_1_sar]]
- [[phenology]]
- [[sampling_bias_remote_sensing]]
- [[vegetation_greenness_trends]]
- [[li_2022_cloud_detection]]
