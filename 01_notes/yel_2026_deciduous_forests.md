---
title: "Remote sensing applications for assessing climate change impacts on deciduous forests — A systematic review"
authors:
  - Yel, Sude Gül
  - Özmen, Hasan Burak
  - Birol, Siğnem Öney
  - Görmüş, Esra Tunç
  - Kaplan, Gordana
year: 2026
source: yel_2026_deciduous_forests
tags:
  - remote-sensing
  - forest-ecology
keywords:
  - deciduous forests
  - climate change
  - NDVI
  - EVI
  - SIF
  - phenology
  - MODIS
  - Landsat
  - Sentinel-2
  - PhenoCam
  - systematic review
status: read
---

# Yel et al. 2026 — RS for Climate Change Impacts on Deciduous Forests

## Title and Authors
**Remote sensing applications for assessing climate change impacts on deciduous forests — A systematic review**
Sude Gül Yel, Hasan Burak Özmen, Siğnem Öney Birol, Esra Tunç Görmüş, Gordana Kaplan — *Physics and Chemistry of the Earth* 143: 104321 (2026).

## Quick Overview
- **Why is it relevant?** Maps the current methodological landscape for monitoring deciduous-forest responses to climate change with optical RS — directly informs sensor + index + algorithm choices for any Italian/European deciduous mapping work.
- **What was done?** Systematic review of 70 peer-reviewed RS studies covering phenology, productivity, and resilience of deciduous forests under climate change.
- **What is the main outcome?** NDVI/EVI/LAI dominate; multi-sensor fusion (MODIS + Landsat + Sentinel-2 + PhenoCam) is becoming standard; persistent gaps in biological interpretation of indices and in fine-scale resilience assessment.

## Main Goal and Fundamental Concept
Deciduous forests are highly responsive to climate change through phenological shifts (advancing SoS, variable EoS, shortened GSL), productivity changes, and resilience differentials. RS provides the only practical means to track these at landscape-to-continental scales. The review asks: which sensors, indices, and analytical methods have been used; what consistent findings emerge; and what gaps need closing.

## Technical Approach
- Web of Science search on RS × deciduous forest × climate change terms; 70 articles retained.
- VOSviewer + CiteSpace keyword co-occurrence analyses.
- Categorisation by sensor, index, analytical approach, and topic (phenology / productivity / resilience).
- Index inventory: NDVI, kNDVI, EVI/EVI2, LAI, NDWI, NDMI, NBR, SAVI, PRI, SIF, PPI (Plant Phenology Index).
- Analytical taxonomy: time-series + regression (TIMESAT, Savitzky-Golay, double-logistic), Linear Mixed-Effects Models (LMEM), Random Forest classification, hierarchical Bayesian models (e.g. Continuous Development Spring Onset Model).

## Distinctive Features
- Side-by-side equations + use-cases for ~12 spectral indices with strengths/weaknesses (Table 1 in paper).
- Explicit treatment of biological interpretation gap — indices correlate with structure but lack mechanistic mapping to leaf-level physiology.
- Highlights complementary near-surface RS (PhenoCam) as validation for satellite phenology.
- Distinguishes phenological shifts by climate zone (temperate vs subtropical vs tropical dry forests).

## Key Findings

**Sensors**
- MODIS dominates phenology (daily revisit, since 2000)
- Landsat for long archives (pre-2000)
- Sentinel-2 (since 2015) increasingly used for regional/fine-scale work
- PhenoCam: indispensable for cross-validation; coverage gaps in tropical/subtropical regions

**Phenology**
- SoS advancing ~1.5 days/decade in temperate regions (PPI ≈ 0.28 days/year advance in boreal forests)
- EoS trends region-dependent (delays in wetter regions, no change in arid)
- Photoperiod controls dominate above 10 °C MAT threshold; thermal forcing below
- fPAR products lag ground observations by 18–55 days during stress events (drought, hurricane)
- High-elevation forests show heterogeneous, sometimes delayed responses

**Productivity & Carbon**
- Boreal: short-term gains from longer GSL; long-term losses from heat + drought
- Tropical: persistent carbon-sink role but high drought sensitivity (Amazon NEP drops linked to El Niño)
- LAI–photosynthesis decoupling under stress: optical greenness can mask actual GPP losses — SIF needed for true productivity assessment

**Deforestation & Resilience**
- LST inversely correlated with NDVI in deforested tropics (Malaysia: 16% Perak, 9% Kedah forest loss → measurable LST rise)
- 2018 Central European drought: 4.3% of Swiss forest area NDWI decline; 2.7% still declining the following year (delayed/legacy mortality)
- Mature forests > young forests in drought resistance; arid-region forests least resilient

## Indices Selection Guide (extracted)

| Index | Best for | Caveats |
|---|---|---|
| NDVI | General greenness, SoS/EoS | Saturates in dense canopies |
| kNDVI | High biomass | σ choice not standardised |
| EVI/EVI2 | Dense canopies | EVI2 sensor-dependent |
| NDWI / NDMI | Canopy water, drought | Soil background contamination |
| NBR | Burn severity | Limited relevance to phenology |
| PRI | Photosynthetic efficiency | Noisy, short archives |
| LAI | Canopy structure | Saturates at LAI > 5 (see [[lai_estimation]]) |
| SIF | True photosynthesis | Low spatial resolution; limited archive |

## Advantages and Limitations
- **Advantages**: comprehensive index inventory; explicit method taxonomy; highlights physiology-RS gap.
- **Limitations**: review only — no original data; "deciduous" includes both temperate and tropical dry, sometimes conflating contexts; 70 papers is a small sample for global synthesis; methodological recommendations remain mostly qualitative.

## Conclusion
RS for climate-change monitoring of deciduous forests has matured around NDVI/EVI/LAI time series, multi-sensor fusion, and ML methods. The next frontier is **biological grounding of indices** (linking spectral metrics to leaf physiology, especially via SIF and PRI) and **fine-scale resilience metrics** capable of detecting drought legacy and species-specific recovery. The review is a useful reference for sensor-index selection in any deciduous-forest mapping effort but does not supply quantitative benchmarks.

## Related pages
- [[ndvi]]
- [[phenology]]
- [[lai_estimation]]
- [[sentinel_2]]
- [[landsat]]
- [[sampling_bias_remote_sensing]]
- [[vegetation_greenness_trends]]
- [[schuldt_2020_drought_forest]]
- [[kempf_2023_greening]]
- [[bayle_2024_landsat_greening_inflated]]
- [[herraiz_2025_phen_shifts_mediterranean]]
