---
name: phenology
description: Vegetation phenology — seasonal timing of plant life-cycle events, remote sensing methods for extraction, and relevance to alpine and boreal ecosystems
type: reference
tags:
  - remote-sensing
  - forest-ecology
  - vegetation
---

# Phenology

**Summary**: Vegetation phenology describes the seasonal timing of plant life-cycle events (green-up, peak greenness, senescence, dormancy), which can be tracked remotely using time series of vegetation indices or surface reflectance.

**Sources**: [[bayle_2024_landsat_greening_inflated]], [[grabska_2024_tree_species_map]], [[he_2015_remote_sensing_sdm]], [[yel_2026_deciduous_forests]], [[schuldt_2020_drought_forest]], [[kempf_2023_greening]], [[yang_2020_modis_evergreen]], [[kollert_2021_tree_species]], [[herraiz_2025_phen_shifts_mediterranean]]

**Last updated**: 2026-05-14

---

## Key Phenological Metrics

- **Start of season (SOS / Onset)**: Date when NDVI exceeds a threshold (e.g., 50% of NDVImax)
- **End of season (EOS / Offset)**: Date when NDVI drops below the same threshold
- **Growing season length (GSL)**: EOS − SOS; a key driver of vegetation productivity and sampling bias magnitude
- **NDVImax**: Peak of the seasonal profile; highly sensitive to observation frequency — see [[sampling_bias_remote_sensing]]
- **Integrated NDVI (iNDVI)**: Season-cumulative NDVI; an alternative productivity metric less sensitive to single-observation timing

## Remote Sensing Platforms for Phenology

| Sensor | Resolution | Revisit | Strength |
|--------|-----------|---------|---------|
| MODIS (Terra/Aqua) | 250–500 m | Daily | High temporal density; phenological reference |
| Landsat (5/7/8/9) | 30 m | 16 days | High spatial resolution; long archive; observation-sparse |
| Sentinel-2 (A+B) | 10–20 m | ~5 days | Bridges spatial/temporal gap between MODIS and Landsat |

## Curve Fitting: Double-Logistic Model

A seven-parameter double-logistic function is the most widely used approach for modelling annual NDVI trajectories:
- Fits a smooth asymmetric curve encoding onset, offset, peak value, and transition rates
- Used in combination with preprocessing: BISE algorithm (noise reduction) + Savitzky-Golay filter (smoothing) → daily interpolated NDVI → double-logistic fit
- Enables phenological parameter extraction independent of observation timing
- Used in Bayle et al. (2024) to model true MODIS phenology and isolate the Landsat sampling bias (source: [[bayle_2024_landsat_greening_inflated]])

## Partitioning Around Medoids (PAM) Clustering

- Used to group pixels into discrete phenological clusters based on their NDVI seasonal profiles
- In Bayle et al. (2024), K = 3 clusters were identified for non-forested Alpine pixels: early, intermediate, and late snowmelt sites (source: [[bayle_2024_landsat_greening_inflated]])
- Each cluster has a different GSL and therefore different susceptibility to observational sampling bias

## Phenology in Alpine Ecosystems

- Growing season is compressed at high elevations and constrained by snow cover duration
- GSL ranges from ~200 days at 1500 m to ~110 days at 2800 m in the European Alps
- Late-snowmelt, high-elevation pixels have the shortest GSL → highest susceptibility to [[sampling_bias_remote_sensing]]
- Climate change is shifting phenological timing (earlier green-up, longer growing seasons), but this signal can be confounded by observational artefacts

## Mediterranean Phenology: The Inverted Cycle

Evergreen Mediterranean forest species exhibit a phenological cycle fundamentally different from temperate deciduous forests (source: [[herraiz_2025_phen_shifts_mediterranean]]):
- **NDVI peak**: winter (December–February) — mild temperatures and adequate soil moisture
- **NDVI trough**: summer (June–August) — heat and drought suppress photosynthesis
- **SOS**: autumn (DOY ~250–290 for pines); **EOS**: spring (DOY ~50–110)
- Growing season length (LOS) varies by species: 160–210 days; *Pinus nigra* and *P. sylvestris* shortest (~160 days); *Castanea sativa* (deciduous) longest (~210 days)
- Aridity delays SOS and EOS for most *Pinus* and *Quercus* species, and shortens LOS for *P. halepensis* and *P. pinaster*
- Timing metrics (SOS, EOS) have NOT shifted temporally over 28 years despite general greening — increasing photosynthetic capacity without changing phenological clock

## Evergreen Phenology and the FEVC Signal

For evergreen vs deciduous mapping, the **intra-annual NDVI minimum** is the most diagnostic phenological feature (source: [[yang_2020_modis_evergreen]]):
- Deciduous and crops drop to bare-soil NDVI in dormancy / fallow
- Evergreens retain photosynthetic activity year-round → high NDVI even at intra-annual minimum
- The **Coefficient of Variation** of an annual NDVI time series distinguishes evergreen (flat → low CV) from deciduous (large amplitude → high CV) and from continuous crops (multi-cycle)
- Combined with linear-mixing models (FEVC) this yields sub-pixel fractional evergreen cover at MODIS resolution (source: [[yang_2020_modis_evergreen]])

## Phenology under Climate Stress

Climate change is shifting phenological timing in temperate forests (source: [[yel_2026_deciduous_forests]]):
- SOS advancing ~1.5 days/decade in temperate regions
- Plant Phenology Index (PPI) in boreal forests: ~0.28 days/year advance
- EOS region-dependent (delays in wetter regions, no change in arid)
- Photoperiod controls dominate above 10 °C MAT; thermal forcing below
- fPAR products lag ground observations by 18–55 days during drought / hurricane events

The 2018 Central European drought triggered widespread **premature leaf senescence** in *Fagus sylvatica* (from late July) and **failed flushing in 2019** — phenological signals of drought legacy that propagate into satellite NDVI quantile ranks (source: [[schuldt_2020_drought_forest]]).

Pan-European NDVI trends 2001–2021 reveal **winter + early spring contributions** dominate greening signals in Northern Europe, consistent with longer GSL driven by warming (source: [[kempf_2023_greening]]).

## LSP for Mountain Tree Species Mapping

In Alpine terrain where cloud-free imagery is scarce, **Land Surface Phenology** metrics from a single year of Sentinel-2 + three-monthly composites give 85% OA — better than three-cloud-free-scene multitemporal classification (source: [[kollert_2021_tree_species]]). Larch's deciduous-conifer phenology is particularly diagnostic — strong contrast with evergreen spruce/fir.

## Phenology as SDM Predictor

Vegetation phenological metrics are valuable predictor variables in [[species_distribution_models]]:
- Growing season length as a proxy for the length of summer — shown to be a key predictor for moose body weight and habitat quality (source: [[he_2015_remote_sensing_sdm]])
- Multi-year MODIS phenology metrics reduce predictor collinearity and improve model transferability
- Early green-up / late senescence timing used to detect invasive annual grasses and discriminate native from non-native species
- Phenology timing from Sentinel-2 STMs is the primary discriminator between tree species in temperate forests — early spring and autumn windows are most informative (source: [[grabska_2024_tree_species_map]])

## Related pages

- [[ndvi]]
- [[landsat]]
- [[sentinel_2]]
- [[sampling_bias_remote_sensing]]
- [[vegetation_greenness_trends]]
- [[species_distribution_models]]
- [[tree_species_mapping]]