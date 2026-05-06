---
title: Mapping pan-European land cover using Landsat spectral-temporal metrics and the European LUCAS survey
authors:
  - Pflugmacher, Dirk
  - Rabe, Andreas
  - Peters, Mathias
  - Hostert, Patrick
year: 2019
source: pflugmacher_2019_lulc_landsat
tags:
  - land-cover-mapping
  - landsat
  - spectral-temporal-metrics
  - random-forest
  - LUCAS
  - Europe
  - LULC
  - remote-sensing
  - machine-learning
keywords:
  - land-cover-classification
  - CORINE
  - LUCAS
  - spectral-temporal-metrics
  - observation-density
  - auxiliary-features
  - pan-European
  - cloud-gap-filling
status: summarized
---

## Title and Authors of the Paper

*Mapping pan-European land cover using Landsat spectral-temporal metrics and the European LUCAS survey* — Dirk Pflugmacher, Andreas Rabe, Mathias Peters, Patrick Hostert (2019), Remote Sensing of Environment, 221, 583–595. DOI: 10.1016/j.rse.2018.12.001. Pan-European LC map for 2015 available at PANGAEA: doi.org/10.1594/PANGAEA.896282.

## Quick Overview

- **Why is it relevant?** CORINE, the existing pan-European land cover product, relies on semi-automated visual interpretation and has known biases (overestimates croplands by 63%, underestimates grasslands by 37%); an automated approach using Landsat spectral-temporal metrics and the publicly available LUCAS survey had not been tested at pan-European scale.
- **What was done?** Mapped 12 land cover classes across Europe (35°N–71°N) by training Random Forest classifiers on 221,110 LUCAS reference samples using Landsat-8 spectral-temporal metrics (seasonal + annual) and environmental auxiliary features over a 3-year observation period (2014–2016).
- **What is the main outcome?** The best model achieves 75.1% overall accuracy; area proportions strongly correlate with LUCAS estimates (r=0.98 vs r=0.84 for CORINE); auxiliary environmental features (climate, location) are the single most impactful component; 3-year multi-year pooling substantially reduces cloud gaps.

## Main Goal and Fundamental Concept

**Spectral-temporal metrics (STMs)** are per-pixel statistical summaries of all cloud-free reflectance observations within a defined time window. Rather than selecting the single best observation (compositing), STMs describe the distribution and seasonal variation of a pixel's spectral signal:
- Simple and computationally efficient to calculate at continental scale
- Capture seasonal phenological dynamics through seasonal windows (spring, summer, fall)
- Capture spectral variability through annual percentiles and variance statistics
- Reduce cloud shadow impacts by averaging over many observations
- Enable pooling of multi-year data without requiring temporal alignment

**LUCAS** (Land Use/Cover Area frame Survey) is Eurostat's harmonised in-situ European land cover survey — the largest and most consistent European-wide reference dataset (221,110 samples; 2 km × 2 km systematic grid; 2015 reference year), collected via photo-interpretation + field visits. First used here for pan-European automated classification training.

## Technical Approach

**Landsat-8 data:**
- 18,675 images across 476 WRS-2 footprints; January 2014 – December 2016
- Cloud/shadow masking with FMask; cloud cover threshold <75% for download
- Surface reflectance (USGS Level-1T + LEDAPS); 6 spectral bands (Blue, Green, Red, NIR, SWIR1, SWIR2)
- Derived indices: NDVI, NBR, MSAVI2, Tasseled Cap Brightness (TCB), Tasseled Cap Greenness (TCG), Tasseled Cap Wetness (TCW) → 12 bands total

**Observation density:**
- 1-year (2015): average 12.7 clear observations; spring/fall lowest (3.2 and 3.1); 6.7–6.8% area unobserved in spring/fall
- 3-year (2014–2016): tripled observations → <0.2% area unobserved in all seasons
- Strong latitudinal gradient: Scandinavia minimum 16 clear observations/year; Mediterranean maximum 66

**Spectral-temporal metrics computed (Table 2):**
- **Annual interval (1 window)**: min, max, mean, standard deviation, 5th, 25th, 50th, 75th, 95th percentile per band/index (108 features for Full3)
- **Seasonal intervals (4 windows)**: spring (Mar–May), summer (Jun–Aug), fall (Sep–Nov), core growing season (May–Sep); median per band/index (48 features)
- Winter (Dec–Feb) excluded: low sun angles limit quality

**Auxiliary features (22):**
- Elevation (GTOPO30 30 arc-second)
- Geographic latitude and longitude (WGS-84)
- 19 WorldClim bioclimatic variables (1970–2000; 1 km²)

**Four classification models tested (Table 3):**

| Model | Data | Seasonal | Annual | Aux | Total features |
|-------|------|---------|--------|-----|---------------|
| Medians1 | 2015 | Medians (48) | Medians (12) | All (22) | 82 |
| Medians3 | 2014–2016 | Medians (48) | Medians (12) | All (22) | 82 |
| NoAux3 | 2014–2016 | Medians (48) | Medians (12) | None | 60 |
| Full3 | 2014–2016 | Medians (48) | Variance metrics (108) | All (22) | **178** |

**Random Forest**: n=500 trees; √p variables sampled per node; cross-validation on entire LUCAS dataset (OOB predictions); post-stratified accuracy estimator following Olofsson et al. (2013)

**LUCAS reference data:**
- 12 land cover classes (Table 1): artificial land, seasonal cropland, perennial cropland, broadleaved forest, coniferous forest, mixed forest, shrubland, grassland, barren, wetland, water, snow/ice
- 221,110 training/validation samples (only EU countries — Norway, Switzerland, non-EU Balkans excluded)
- Strict selection criteria: land cover area >50%, field GPS <30m from LUCAS point; for perennial cropland/artificial land, relaxed to 25%/any (otherwise too few samples)

## Key Results

**Overall accuracy (cross-validated):**
| Model | OA (%) |
|-------|--------|
| Medians1 | 73.2 |
| Medians3 | 74.6 |
| NoAux3 | 70.4 |
| **Full3** | **75.1** |

- **Multi-year pooling (Medians3 vs Medians1)**: +1.4pp OA; larger gains for temporally dynamic classes (seasonal cropland, grassland) and small/spectrally ambiguous classes
- **Annual variance metrics (Full3 vs Medians3)**: +0.5pp OA overall; +3pp for seasonal cropland PA (captures within-season variability of crops vs. grasslands)
- **Auxiliary features (Medians3 vs NoAux3)**: **+4.7pp OA** — largest single contributor; especially critical for perennial croplands (−10pp), shrubland (−9pp), artificial land (−7pp) — geographically restricted classes that need biogeographic context

**Class-specific accuracy (Full3):**
| Class | PA (%) | UA (%) |
|-------|--------|--------|
| Seasonal cropland | 89.4 | 89.9 |
| Grassland | 81.3 | 74.3 |
| Broadleaved forest | 79.8 | 73.7 |
| Coniferous forest | 75.7 | 73.2 |
| Water | 90.5 | 91.5 |
| Barren | 74.1 | 81.7 |
| Mixed forest | **50.2** | **60.8** |

- Mixed forest: hardest class; confused with both pure forest types
- Mediterranean grassland: lowest UA (62.5%) due to spectral similarity with shrubland and barren in dry climates
- Total combined forest accuracy: UA=91.7%, PA=91.8% (balanced omission and commission)

**Comparison with CORINE (2012):**
- This study vs LUCAS proportions: r=0.98, country-by-country std=0.02
- CORINE vs LUCAS proportions: r=0.84, country-by-country std=0.14
- CORINE overestimates seasonal cropland area by 63%, underestimates grassland by 37%
- Mapped broadleaved forest 9% higher than LUCAS estimate (likely real difference given LUCAS sampling unit vs min mapping unit)

**Feature importance:**
- Geographic location (latitude, longitude) > elevation > WorldClim bioclimatic variables
- Spectral bands: seasonal medians capture phenological dynamics that discriminate cropland/grassland/forest
- Seasonal cropland vs grassland confusion remains the dominant classification challenge

## Advantages and Limitations

**Advantages:**
- First fully automated pan-European land cover map from Landsat + harmonised in-situ data
- 30m minimum mapping unit vs CORINE's 25ha → fundamentally higher spatial detail
- Reproducible and updatable: same pipeline applicable to future years as Landsat archive grows
- STM approach handles cloud gaps by statistical pooling — no single clear observation required per pixel
- LUCAS as training data: large, publicly available, harmonised across EU countries

**Limitations:**
- LUCAS excludes non-EU countries (Norway, Switzerland, Balkans) → accuracy unknown for these areas
- Mixed forest systematically poor: spectrally indeterminate without additional data (e.g., texture, high-resolution, phenology)
- Mediterranean grassland/shrubland/barren confusion: phenological similarity limits discrimination with STMs alone
- 3-year pooling ignores inter-annual land cover changes (e.g., crop rotations) → some samples misrepresent actual 2015 conditions
- No winter season metrics (low sun angle) → loss of potential discriminating features for evergreen species

## Conclusion

Pflugmacher et al. (2019) demonstrate that the combination of Landsat spectral-temporal metrics (seasonal medians + annual variance statistics over three years) and the large LUCAS reference dataset produces a pan-European land cover map substantially better than CORINE in terms of area proportion accuracy. Auxiliary environmental features (location, climate) are the most impactful single contributor to classification accuracy — more than additional observation density or variance metrics. The multi-year pooling approach is essential for cloud-affected regions. The framework is directly transferable to Sentinel-2 (higher resolution, more frequent revisit), which is expected to further improve accuracy for spectrally dynamic classes.

## Related Work & Obsidian Links

- [[landsat]]
- [[tree_species_mapping]]
- [[sampling_bias_remote_sensing]]
- [[sentinel_2]]
- [[phenology]]

- [[grabska_2024_tree_species_map]] — Grabska et al. apply the same STM paradigm to Sentinel-2 for tree species mapping at national scale in Poland; the seasonal composite approach and RF classifier are directly analogous; Sentinel-2 replaces Landsat with higher resolution and more spectral bands
- [[bayle_2024_landsat_greening_inflated]] — Pflugmacher et al. show that 3-year pooling reduces cloud gaps from 6.7% to <0.2% in spring; Bayle et al. show that the non-uniform increase in cloud-free observations over the Landsat archive creates false greening trends — both papers illuminate the same observation density problem from different angles
- [[hiebl_2025_pretraining]] — Hiebl et al. use Copernicus FTY forest mask (derived from similar STM-based Landsat/S2 classification) as a forest extent layer; this paper is the conceptual predecessor of that product at the continental scale

## Related pages

- [[landsat]]
- [[sentinel_2]]
- [[sampling_bias_remote_sensing]]
- [[tree_species_mapping]]
- [[phenology]]
- [[grabska_2024_tree_species_map]]
- [[bayle_2024_landsat_greening_inflated]]
- [[hiebl_2025_pretraining]]
