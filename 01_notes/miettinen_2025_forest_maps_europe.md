---
title: Pan-European forest maps produced with a combination of earth observation data and national forest inventory plots
authors:
  - Miettinen, Jukka
  - Breidenbach, Johannes
  - Adame, Patricia
  - Adolt, Radim
  - Alberdi, Iciar
  - Chirici, Gherardo
  - Corona, Piermaria
  - D'Amico, Giovanni
  - Fischer, Christoph
  - et al.
year: 2025
source: miettinen_2025_forest_maps_europe
tags:
  - forest-structure-mapping
  - biomass
  - timber-volume
  - sentinel-2
  - national-forest-inventory
  - kNN
  - Europe
  - model-assisted-estimation
  - forest-ecology
keywords:
  - above-ground-biomass
  - AGB
  - timber-volume
  - deciduous-coniferous-proportion
  - kNN
  - Copernicus-FTY
  - Copernicus-TCD
  - PathFinder
  - pan-European
  - wall-to-wall
status: summarized
---

## Title and Authors of the Paper

*Pan-European forest maps produced with a combination of earth observation data and national forest inventory plots* — Jukka Miettinen, Johannes Breidenbach, Patricia Adame et al. (2025), Data in Brief, 60, 111613. DOI: 10.1016/j.dib.2025.111613. Part of the EU PathFinder project (GA101056907).

**Note**: This is a Data in Brief paper describing a publicly available dataset, not a primary research article. Dataset at Zenodo: doi.org/10.5281/zenodo.13143235

## Quick Overview

- **Why is it relevant?** No previous pan-European forest structure map combined harmonized NFI plot data with high-resolution Sentinel-2 imagery at 10m resolution across 40 countries simultaneously.
- **What was done?** Produced wall-to-wall maps of timber volume (Vol), above-ground biomass (AGB), and deciduous-coniferous proportion (DCP) at 10m resolution for reference year 2020 using kNN with ~151,000 NFI field plots from 14 countries and Sentinel-2 spectral composites.
- **What is the main outcome?** Maps are nearly unbiased at the European level (AGB bias: 1.0 t/ha, 1% of mean) but show systematic overestimation at low biomass and underestimation at high biomass; intended as auxiliary data for model-assisted estimation rather than direct area statistics.

## Main Goal and Fundamental Concept

**Three target variables:**
| Variable | Unit | Description |
|----------|------|-------------|
| Timber Volume (Vol) | m³/ha | Growing stock volume |
| Above-Ground Biomass (AGB) | t/ha | Total aboveground tree biomass |
| Deciduous-Coniferous Proportion (DCP) | % | Percentage of conifer species in AGB; deciduous = 100-DCP |

These maps fill a European-scale data gap for forest carbon accounting, habitat monitoring, and model-assisted NFI estimation. They are the first products of the **PathFinder** system — a European forest monitoring and policy assessment framework aiming to integrate RS and NFI for consistent European LULUCF (land use, land-use change, and forestry) monitoring.

## Technical Approach

**NFI field data (Table 4):**
- 14 national NFIs: Austria, Belgium, Switzerland, Czechia, Germany, Spain, Finland, France, Ireland, Italy, Norway, Poland, Sweden, Slovenia
- Total: 100,797 plots used for mapping; 50,393 for validation (1/3 hold-out)
- Measurement years: mostly 2019-2021 (some 2017-2022) to minimise temporal mismatch with 2020 Sentinel-2 composite
- Plot density varies strongly: Germany 0.36 plots/km² forest; Italy 0.05 plots/km² (sparse)

**Remote sensing inputs:**
- **Sentinel-2 mosaic (2020)**: 7 spectral bands (B2, B3, B4, B5, B8, B11, B12); 10m resolution; cloud-free composite; cloud screening using image quality band (>4000 threshold)
- **Copernicus HRL Forest Type (FTY; 2018)**: coniferous/broadleaved/non-forest; 10m
- **Copernicus HRL Tree Cover Density (TCD; 2018)**: 0-100%; 10m
- **Global Forest Change (GFC v1.9)**: used to screen out plots with canopy change 2018-2021 (before field measurement)

**kNN modelling:**
- k=7, Euclidean distance, inverse-distance weighting: ŷ_p = Σ wᵢ yᵢ
- Feature space: 7 S2 bands + TCD (continuous) + FTY (categorical, weighted mode) + geographic location (northing, easting from INSPIRE 1km grid) when NFI plots available
- **Uncertainty per pixel**: standard deviation of k neighbors: ŝ_p = √(Σ(yᵢ − ŷ_p)²/k)
- Multivariate: same kNN model predicts all three variables simultaneously
- 13 processing areas covering all 40 European countries
- For areas without NFI plots (7 of 13 areas): training data from ecologically similar neighboring regions; INSPIRE coordinates NOT used as features (would be uninformative without local plots)
- Processing on Forestry TEP platform; 745 Sentinel-2 tiles processed

**Output format:**
- 500×500 km tiles; EPSG:3035 ETRS89-extended/LAEA Europe projection; 10m GeoTiff (UInt16)
- Masked with Copernicus FTY forest extent (2018); non-forest = NoData
- Layers per variable: attribute map + standard deviation (uncertainty)

## Key Results

**AGB overall accuracy:**
- European-level bias: 1.0 t/ha (1% of mean AGB 137 t/ha) — nearly unbiased on average
- RMSE range across 13 areas: 53% (Nordic) to 73% (South-Eastern area)
- R² range: 0.24–0.54 across areas

**Systematic biomass class bias (Table 3):**
| AGB class (t/ha) | Bias (t/ha) | Bias% |
|-----------------|------------|------|
| 0–124 | **+38.3** | **+66.3%** (overestimate) |
| 125–249 | −3.5 | −1.9% |
| 250–374 | −87.1 | −29.1% |
| 375–499 | −174.0 | −42.6% |
| 500+ | **−351.1** | **−58.7%** (underestimate) |

This regression-to-the-mean pattern is inherent to kNN/imputation methods: predictions cluster around the training mean rather than capturing extreme values.

**Value of national NFI plots:**
- Including local NFI plot locations as features substantially reduces RMSE vs using only ecologically similar plots from other countries (Table 5):
  - Czechia: RMSE% 53.8% (with CZ plots) vs 62.2% (no CZ plots)
  - Poland: RMSE% 54.6% (with PL plots) vs 65.8% (no PL plots)
- Bias can be highly erratic without local NFI data → maps for areas without NFI plots require extra caution

**DCP (Deciduous-Coniferous Proportion):**
- RMSE%: 30-65% across areas; R² 0.52-0.73
- Useful for broad-scale forest composition mapping but too uncertain for local-scale species composition

## Advantages and Limitations

**Advantages:**
- First 10m pan-European forest structure map integrating harmonised multi-country NFI data
- Uncertainty layer (pixel-level standard deviation) enables spatially explicit confidence assessment
- Freely available on Zenodo; compatible with PathFinder model-assisted estimation framework
- DCP enables separation of broadleaved vs. coniferous forest AGB without separate classification
- Processing scripts publicly available (GitLab nFIESTA)

**Limitations:**
- **Regression to mean**: systematic overestimation of low AGB and underestimation of high AGB — maps must NOT be summarised by pixel counting for area statistics
- Areas without local NFI plots (7 of 13 processing areas) have unknown and potentially high biases
- NFI temporal mismatch: some plots measured 2017-2022; effects on map consistency not quantified
- Temporal mismatch between Copernicus FTY/TCD (2018) and Sentinel-2 composite (2020)
- 10m resolution is high for volume/biomass mapping — spatial detail reflects Sentinel-2 spectral variation rather than verified local structural variation

## Implications for Remote Sensing Ground Truth

- Maps designed as **auxiliary data for model-assisted estimation** — where they shine is in providing spatial structure and gradients, not absolute values for summarization
- NFI plot density (plots/km² forest) is the key driver of local map quality; Italy (0.05 plots/km²) much sparser than Germany (0.36 plots/km²)
- Geographic coordinates as kNN features: effective way to leverage large multinational NFI datasets while preserving local calibration — key design insight
- Standard deviation uncertainty layer: directly usable for identifying where map predictions are unreliable (high ŝ_p → high uncertainty)

## Conclusion

Miettinen et al. (2025) present the first pan-European 10m forest structure maps integrating harmonised NFI data from 14 countries with Sentinel-2 imagery via kNN modelling. The maps provide spatially continuous estimates of timber volume, AGB, and deciduous-coniferous proportion for 40 European countries, nearly unbiased at the continental scale. Their primary use is as auxiliary information for model-assisted NFI estimation and forest monitoring within the PathFinder framework — not for direct pixel-counting statistics. The systematic regression-to-the-mean bias at the biomass class level is an inherent limitation of the kNN approach.

## Related Work & Obsidian Links

- [[national_forest_inventory]]
- [[sentinel_2]]
- [[tree_species_mapping]]
- [[transfer_learning_remote_sensing]]

**Cross-paper links (same vault):**
- [[01_notes/gasparini_2022_nfi_italy]] — Italian NFI (INFC) provides the Italian field plots (2,813 plots, 2018-2019) used in this pan-European mapping; map accuracy in Italy partly reflects INFC plot density (0.05 plots/km²)
- [[01_notes/mattioli_2025_carta_forestale]] — CFI2020 provides the forest mask and type information for Italy; Copernicus FTY (used here) and CFI2020 serve similar masking purposes; CFI2020 is at higher thematic detail
- [[01_notes/hiebl_2025_pretraining]] — both use Copernicus FTY as forest mask; Miettinen et al. provide the continental AGB and DCP context within which EVE cover mapping in Italian National Parks is situated
- [[01_notes/grabska_2024_tree_species_map]] — both use Sentinel-2 + NFI data for national/continental forest mapping; Grabska et al. map species identity (classification); Miettinen et al. map structure attributes (regression); complementary products
