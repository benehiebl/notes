---
name: drought_mortality
description: Hotter droughts and tree mortality in temperate forests — physiological mechanisms, redistribution of climatic drivers, and remote sensing detection
type: reference
tags:
  - forest-ecology
  - remote-sensing
---

# Drought-Induced Tree Mortality in Temperate Forests

**Summary**: "Hotter droughts" — droughts at temperatures elevated above historical norms — drive widespread tree mortality through xylem hydraulic failure and carbon starvation, with strong drought-legacy effects (delayed mortality and secondary pest/pathogen vulnerability). The 20th century has redistributed the climatic drivers of global tree growth from energy- to water-limitation, and the 2018 Central European drought set new severity records.

**Sources**: [[schuldt_2020_drought_forest]], [[babst_2019_redistribution]], [[chelli_2017_climate]], [[dyderski_2025_species_shift]], [[grünig_2026_climate_change_disturbances_forest]]

**Last updated**: 2026-05-14

---

## Hotter Droughts vs Normal Droughts

A **hotter drought** is one that combines low precipitation with abnormally high temperature and high vapour pressure deficit (VPD). The combination amplifies physiological stress beyond what either factor would cause alone (source: [[schuldt_2020_drought_forest]]).

Mechanisms:
- High VPD → high evaporative demand → faster water loss through stomata
- Low soil moisture → reduced water supply
- Crossing **xylem hydraulic failure threshold** → embolism → cavitation cascade → death
- Carbon starvation in long-duration events as stomatal closure halts photosynthesis

## The 2018 Central European Drought

(source: [[schuldt_2020_drought_forest]])

**Climatic severity** (DACH region April–October 2018):
- Mean growing-season air temperature **+3.3 °C** above 1961–1990 baseline; **+1.2 °C above 2003**
- Mean VPD: highest on record
- Climatic water balance: −238 mm (second worst after 1976)

**Forest impacts**:
- *Fagus sylvatica* (European beech): widespread premature leaf senescence from late July 2018; many individuals failed to flush in 2019 → defoliation → mortality
- *Picea abies* (Norway spruce): needle discoloration → bark-beetle vulnerability
- *Pinus sylvestris* (Scots pine): similar pattern
- Foliar water potentials below xylem hydraulic failure thresholds for many species

**MODIS NDVI evidence**: area of deciduous forest in lowest NDVI quantiles ≈ **2 × that of 2003** (~11,200 vs ~5,600 km²); spatially more uniform than 2003.

**Drought legacy**: 2019 surveys showed many surviving beech trees failed to flush — **physiological recovery impaired**, leaving trees vulnerable to secondary stressors (bark beetles, fungal pathogens). Mortality continues for years post-event.

## Global Redistribution of Climatic Drivers

(source: [[babst_2019_redistribution]])

20th-century warming has shifted the climatic *limitation* of tree growth across vast areas:
- **Energy (T)-limited area**: shrank by **−8.7 ± 0.6 Mio km² (−10.8%)** between 1930–1960 and 1960–1990
- **VPD-limited area**: grew by the same amount (+8.7 Mio km²)
- **P-limited and SPEI-limited areas**: stable

Spatial pattern:
- Cold-humid regions (southern Alaska, NE Canada, coastal Scandinavia, Alps, Tibet, NE Siberia) — was energy-limited, becoming less so
- Hot-dry, temperate, cold-humid: increasingly summer-VPD limited
- Strongest signal in cold-humid where warming has been largest

**Implication**: continued warming will accelerate this redistribution; the future global forest is **increasingly water-limited**, even in historically energy-limited regions.

## Pan-Italian Context

Italian climatic-zone synthesis (source: [[chelli_2017_climate]]):
- **Drought overrides warming benefits** even in non-Mediterranean zones (temperate, sub-Mediterranean)
- Mediterranean and sub-Mediterranean zones: increasing drought + heat → reduced productivity, mortality
- Alpine: snowmelt advance + summer drought increasingly important
- *Abies alba* particularly vulnerable in southern Alps (drought-limited)
- *Picea abies* growth declines in dry years across Italy

## Species Vulnerability Ranking

From combined SDM + functional trait analyses (source: [[dyderski_2025_species_shift]]):
- **Most threatened** under climate change: *Abies alba*, *Larix decidua*, *Picea abies*, *Pinus sylvestris* — major contractions by 2041–2060
- **Partially threatened**: *Fagus sylvatica*, *Quercus robur/petraea*, *Fraxinus excelsior*
- **Robust / expanding**: many alternative broadleaved species — *Sorbus torminalis*, *Tilia platyphyllos*, *Acer pseudoplatanus*, *Prunus avium*, *Carpinus betulus*

## Climate × Disturbance Feedbacks

Drought-stressed trees become vulnerable to:
- **Bark beetles** (especially *Ips typographus* on spruce) — populations grow during droughts, attack weakened hosts
- **Fungal pathogens** — opportunistic colonisation of compromised xylem
- **Wildfire** — increased fuel load + drier biomass

These secondary stressors drive much of the actual mortality after the initial physiological event (source: [[schuldt_2020_drought_forest]], [[grünig_2026_climate_change_disturbances_forest]]).

## Remote Sensing Detection

**Optical indices for drought stress**:
- NDVI quantiles vs historical baseline → severity ranking (source: [[schuldt_2020_drought_forest]])
- NDWI / NDMI → canopy water content, drought tracking
- SIF → true photosynthetic activity (catches greenness-vs-photosynthesis decoupling that NDVI misses)
- PRI → photosynthetic efficiency, xanthophyll cycle

**Time series approaches**:
- Anomaly detection vs multi-year baseline (Buras et al. 2020, Kempf 2023; cf. [[kempf_2023_greening]])
- Drought-legacy detection: continued NDWI/NDVI decline in subsequent years (Sturm et al. 2022)

**Limitations**:
- 250 m–500 m MODIS resolution coarse for stand-level inferences
- Species attribution requires combining with tree species maps (cf. [[blickensdörfer_2024_tree_species]], [[wegler_2026_canopy_cover_loss]])
- Canopy greenness can mask early-stage physiological decline (LAI–GPP decoupling)

## Implications for Forest Management

- **Diversify species portfolios** — broadleaved alternatives are more climate-robust (cf. [[dyderski_2025_species_shift]])
- **Monitor drought legacy** — multi-year follow-up post-event
- **Pan-European ground monitoring + RS** as advocated by Schuldt et al. — bridge gap between ICP Forests sparse plot network and continuous RS
- **Integrate climate, species, and disturbance** in projections (cf. [[grünig_2026_climate_change_disturbances_forest]], [[albrich_2019_climate_change_mountain_forests]])

## Related concepts
- [[forest_disturbances]]
- [[vegetation_greenness_trends]]
- [[species_distribution_models]]
- [[phenology]]
- [[ndvi]]
- [[sampling_bias_remote_sensing]]
