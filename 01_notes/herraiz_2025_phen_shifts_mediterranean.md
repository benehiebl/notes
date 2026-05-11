---
title: Aridity-induced phenological shifts and greening trends in Mediterranean forest species — Insights from 28 years of Landsat data in southern Spain
authors:
  - Herraiz, Aurelio D.
  - Salazar-Zarzosa, Pablo
  - Acosta-Muñoz, Cristina
  - Hernández-Clemente, Rocío
  - Villar, Rafael
year: 2025
source: herraiz_2025_phen_shifts_mediterranean
tags:
  - remote-sensing
  - phenology
  - landsat
  - ndvi
  - mediterranean-ecosystems
  - forest-ecology
  - climate-change
keywords:
  - phenometrics
  - SOS
  - EOS
  - LOS
  - aridity
  - greening
  - Andalusia
  - Spanish-NFI
  - evergreen-forests
  - Pinus
  - Quercus
  - time-series-decomposition
status: summarized
---

## Title and Authors of the Paper

*Aridity-induced phenological shifts and greening trends in Mediterranean forest species: Insights from 28 years of Landsat data in southern Spain* — Aurelio D. Herraiz, Pablo Salazar-Zarzosa, Cristina Acosta-Muñoz, Rocío Hernández-Clemente, Rafael Villar (2025), Ecological Indicators, 171, 113115. DOI: 10.1016/j.ecolind.2025.113115.

## Quick Overview

- **Why is it relevant?** Mediterranean evergreen forests exhibit a phenological cycle that is fundamentally inverted relative to temperate deciduous forests — peak greenness occurs in winter, not summer — making standard phenological frameworks inappropriate and the effects of aridity distinct and poorly characterised across species.
- **What was done?** Maximum monthly NDVI from Landsat 5/7 was computed for 2,358 Spanish NFI plots in Andalusia (1994–2021) to characterise the full phenological cycle of 10 dominant Mediterranean forest species and quantify how aridity affects phenological metrics and NDVI trends.
- **What is the main outcome?** All species except *Eucalyptus camaldulensis* showed a significant positive NDVI trend (greening) over 28 years; aridity delays SOS and EOS for most pine and oak species and shortens the growing season of *P. halepensis* and *P. pinaster*, but NDVI magnitude declines with aridity for most species while timing metrics are less responsive to temporal trends.

## Main Goal and Fundamental Concept

Mediterranean evergreen forests experience **summer drought stress** as the primary growth-limiting factor, creating an annual NDVI cycle inverted relative to temperate forests: NDVI peaks in winter (December–February) when temperature is mild and moisture is available, and reaches a minimum in summer (June–August) when heat and aridity suppress photosynthetic activity. This means conventional phenological metrics (SOS, EOS, LOS) extracted from NDVI time series must be re-interpreted in a Mediterranean context.

Three objectives:
1. Characterise the phenological cycle and its metrics for 10 Mediterranean species (1 deciduous, 9 evergreen)
2. Quantify how aridity affects these phenological metrics across species distributions
3. Track temporal trends in NDVI and phenological metrics from 1994 to 2021

## Technical Approach

**Data:**
- Landsat 5 TM (1994–2000) and Landsat 7 ETM+ (2001–2021) via Google Earth Engine
- Maximum monthly NDVI per 30-m pixel per hydrometeorological year (September 1 – August 30)
- 2,358 permanent plots from the Spanish National Forest Inventory (SNFI/SFNI) in Andalusia, filtered for: aboveground biomass >90% from target species (allometric equations from DBH), forest density >150 trees ha⁻¹
- Single central pixel (30×30 m = 900 m²) strongly correlated with 9-pixel average (R²=0.93, p<0.001), validating single-pixel use

**Aridity index:**
- Modified Martonne index AI = 150 − MI, where MI = {[MAP+10] + {[12×DMP]/[DMT+10]/2}}
- MAP = mean annual precipitation, DMP = precipitation of driest month, DMT = temperature of driest month
- High AI = high aridity; derived from WorldClim 2.1 (20-year averages)
- Aridity-MAT correlation r = 0.31, Aridity-MAP correlation r = −0.67 (both significant)

**Phenological extraction:**
- Time-series decomposition: Rbeast package → seasonal + trend + residual components; trend used for temporal analysis
- Phenometrics extracted via Phenology R package (Garonna/García approach): Derivative + Spline smoothing technique
- Circular/angular statistics for cyclic metrics (SOS, EOS, POP, POT) using Directional and Circular R packages
- Phenometrics: SOS, EOS, LOS, POP (Position of Peak), POT (Position of Trough), PEAK (max NDVI), TROUGH (min NDVI), MSP (NDVI at SOS), MAU (NDVI at EOS)

**Analysis:**
- Monthly NDVI averages per species (252 values per species) for phenological cycle characterisation
- Linear regression of phenometrics vs aridity index
- Temporal trend of NDVI and phenometrics over 28 years (28 annual values per species/plot)
- Kruskal-Wallis + Dunn post-hoc tests for between-species comparisons

## Distinctive Features

- **Mediterranean inverted cycle**: explicitly demonstrates and characterises the inverted phenological cycle of evergreen Mediterranean species, rarely treated systematically across multiple species in a single study
- **NFI plot-level Landsat analysis**: links the national forest inventory plot network directly to Landsat pixel time series, enabling species-specific phenological profiles grounded in forest inventory data
- **Aridity as combined climate driver**: uses Martonne aridity index rather than temperature or precipitation alone, capturing their combined effect on Mediterranean plant physiology
- **Long 28-year record**: enables detection of slow phenological trends and disentangles NDVI magnitude trends from timing metric trends

## Experimental Setup and Results

**Species and study area:**
- Andalusia, southern Spain (36°–38.75°N, 7.37°–1.53°W); 26% forest area; high Mediterranean climatic variability
- 10 species (importance order): *P. halepensis* (24.8%), *Q. ilex* (18.9%), *P. nigra* (13.6%), *P. nigra* (12%), *P. pinaster* (11.5%), *Q. suber* (10.2%), *P. sylvestris* (4.1%), *O. europaea* (2.8%), *E. camaldulensis* (1.3%), *C. sativa* (0.9%)

**Phenological cycle characterisation:**
- *C. sativa* (deciduous): SOS DOY ~101 (spring), EOS DOY ~296 (autumn), LOS ~195 days, PEAK in summer — typical temperate pattern
- All 9 evergreen species: SOS in autumn (DOY ~250–290 for pines), EOS in spring (DOY ~50–110), PEAK in winter (December–February), TROUGH in summer — inverted Mediterranean cycle
- LOS varies by species: *C. sativa* ~210 days; *E. camaldulensis*, *O. europaea*, *P. pinea*, *Q. ilex*, *Q. suber* ~180 days; *P. halepensis*, *P. pinaster* ~170 days; *P. nigra*, *P. sylvestris* ~160 days (shortest; most erratic — related to altitude/snow)

**Aridity effects:**
- SOS: all Pinus and Quercus species show positive aridity → SOS relationship (delay in season start in more arid plots)
- EOS: *P. halepensis*, *P. nigra*, *P. pinaster*, *P. sylvestris*, *Q. suber* show positive aridity → EOS relationship (later EOS)
- LOS: significantly shortened by aridity in *P. halepensis* and *P. pinaster*; *P. nigra* and *P. sylvestris* also shortened; *Quercus* species LOS not significantly affected
- NDVI magnitude (PEAK, TROUGH, MSP, MAU): negatively correlated with aridity for most species (lower greenness in drier sites); exceptions: *C. sativa*, *P. nigra*, *P. pinaster*, *P. sylvestris* (mountain pines — different aridity exposure range)

**Temporal trends (1994–2021):**
- 9 of 10 species: significant positive NDVI trend (greening); exception: *E. camaldulensis* (stable)
- Two trajectory patterns:
  1. Stable until ~2005, then positive trend: *E. camaldulensis*, *O. europaea*, *Q. suber*, *P. pinaster*, *P. pinea*
  2. Positive throughout entire period: *C. sativa*, *Q. ilex*, *P. halepensis*, *P. nigra*
- NDVI-related metrics (PEAK, TROUGH, MSP, MAU): positive correlations with time for most species
- Timing metrics (SOS, EOS, LOS, POP, POT): **no significant temporal trends** — the phenological clock has not shifted despite NDVI increase
- Mountain pines (*P. nigra*, *P. sylvestris*): most erratic interannual variability, linked to altitude and snow cover effects

## Advantages and Limitations

**Advantages:**
- 28-year Landsat record provides statistical power to detect trends in slow-changing forest systems
- NFI plot-based approach links satellite data to known species composition, avoiding mixed-pixel ambiguity
- Circular statistics appropriate for cyclic phenometric variables (avoids artefacts from SOS/EOS crossing year boundaries for evergreens)
- Aridity index integrates temperature and precipitation, more ecologically relevant than either alone

**Limitations:**
- Single central pixel (30×30 m) captures only the immediate plot neighbourhood — not necessarily representative of the wider forest stand
- Landsat 7 SLC failure (post-2003) creates data gaps; mitigated by using maximum monthly NDVI and linear interpolation
- Shrub and herb understory NDVI contributions not fully separable from tree NDVI signal (partially addressed by tree cover density filter)
- Aridity index derived from 20-year WorldClim averages — does not capture inter-annual climate variability
- NFI plots may not be randomly distributed across the full aridity gradient (structured sampling design)

## Conclusion

Herraiz et al. (2025) demonstrate that Mediterranean evergreen forest species exhibit an inverted phenological cycle (peak in winter, trough in summer) driven by summer drought stress, with substantial species-level variation in growing season length, timing, and sensitivity to aridity. Despite general greening trends over 28 years (attributed to CO₂ fertilisation, reforestation, and climate resilience), aridity significantly delays the start of the growing season and shortens it for many pine species, with more arid plots consistently showing lower NDVI magnitudes. Critically, the timing of phenological events (SOS, EOS) has not shifted temporally even as NDVI values have increased — suggesting that Mediterranean forest species are increasing photosynthetic capacity without changing the fundamental timing of their annual cycles.

## Related Work & Obsidian Links

- [[phenology]]
- [[ndvi]]
- [[landsat]]
- [[vegetation_greenness_trends]]
- [[sampling_bias_remote_sensing]]
- [[national_forest_inventory]]

- [[bayle_2024_landsat_greening_inflated]] — Bayle et al. warn that increasing Landsat observation density over time inflates NDVImax greening trends; the greening trends found here should be interpreted with this caveat in mind, though monthly maximum compositing partially mitigates the bias
- [[bricca_2026_topo_diversity]] — both papers study Mediterranean forest ecology in Italy/Spain; Bricca et al. show diversity losses under projected warming, while Herraiz et al. document current greening resilience — a tension worth noting
- [[fady_2025_native_trees_mediterranean]] — both address Mediterranean tree species responses to climate; Fady et al. focus on conservation genetics while Herraiz et al. focus on RS-based phenological monitoring
- [[grabska_2024_tree_species_map]] — both use Landsat/Sentinel-2 time series for species-level forest monitoring; Grabska et al. exploit phenological timing differences for classification — Herraiz et al. quantify what those timing differences actually are for Mediterranean species

## Related pages

- [[landsat]]
- [[phenology]]
- [[ndvi]]
- [[vegetation_greenness_trends]]
- [[leaf_habit_latitudinal_gradient]]
- [[sampling_bias_remote_sensing]]
- [[national_forest_inventory]]
- [[bayle_2024_landsat_greening_inflated]]
- [[bricca_2026_topo_diversity]]
- [[fady_2025_native_trees_mediterranean]]
- [[grabska_2024_tree_species_map]]
