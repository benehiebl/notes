---
name: vegetation_greenness_trends
description: Multi-decadal greening and browning trends from satellite vegetation indices — methods, drivers, caveats, and ecological interpretation
type: reference
tags:
  - remote-sensing
  - forest-ecology
  - vegetation
---

# Vegetation Greenness Trends

**Summary**: Vegetation greening (or browning) refers to long-term directional changes in satellite-derived vegetation indices, used as proxies for changes in plant productivity, biomass, and ecosystem functioning in response to climate and land use.

**Sources**: [[bayle_2024_landsat_greening_inflated]], [[herraiz_2025_phen_shifts_mediterranean]], [[midolo_2026_denser_vegetation]]

**Last updated**: 2026-05-05

---

## Definition

- **Greening**: positive multi-decadal trend in NDVI or EVI; widely interpreted as increasing plant productivity
- **Browning**: declining trend; associated with drought stress, permafrost thaw, or disturbance
- Both terms are used at scales from individual pixels to biome-level summaries

## Detection Methods

- **Annual maximum compositing (NDVImax)**: most common approach; sensitive to observation density — see [[sampling_bias_remote_sensing]]
- **Trend estimation**: Theil-Sen slope estimator preferred for robustness to outliers; Mann-Kendall test for significance
- **Integrated NDVI (iNDVI)**: seasonal sum; alternative metric less sensitive to single-observation timing but requires gap-filled data
- **Growing season mean NDVI**: averages over the phenologically defined season

## Eutrophication and Vegetation Densification as Greening Drivers

A major non-climatic driver of satellite-observed greening: nitrogen enrichment drives vegetation densification independently of temperature:
- Continent-wide nitrogen CM_EIV increase of +0.25 (1960–2020) across all European habitat types — the dominant driver of 60-year plant community change (source: [[midolo_2026_denser_vegetation]])
- Higher nitrogen → higher plant productivity → higher LAI → more biomass → positive NDVI trend
- Accompanied by CM_EIV light decline (-0.12) reflecting canopy closure and increasing shade-tolerant species dominance
- Management cessation (grazing, coppicing, mowing abandonment) amplifies both effects: biomass accumulates, canopy closes
- **Implication for RS**: NDVI greening reflects a combination of (1) temperature-driven growing season lengthening, (2) nitrogen-driven biomass increase, (3) CO₂ fertilization, and (4) observational bias (see [[sampling_bias_remote_sensing]]); disentangling these requires community-composition data alongside satellite signals

## Known Ecological Drivers of Greening

- CO₂ fertilisation and temperature increase (global greening signal)
- Longer growing seasons from reduced snow cover duration
- Land use change (reforestation, afforestation, agricultural intensification)
- Increased precipitation in formerly water-limited regions

## Caveats and Artefacts

- **Sampling bias**: Increasing Landsat observation density over time inflates NDVImax trends in cold, seasonally snow-covered ecosystems — in the European Alps, up to 50% of observed greening above 2400 m is artefactual (source: [[bayle_2024_landsat_greening_inflated]]) — see [[sampling_bias_remote_sensing]]
- **Sensor transitions**: Cross-sensor differences between Landsat generations (TM → ETM+ → OLI) require radiometric normalisation
- **Spatial heterogeneity**: Greening can reflect land cover change rather than productivity change; fine-scale patterns missed by coarse sensors
- **Temporal non-linearity**: Overall greening trends can mask alternating phases of greening, stability, and browning at shorter timescales

## Species-Level Greening Variation

Long-term Landsat NDVI time series (28 years) in Mediterranean forests reveal species-specific greening patterns (source: [[herraiz_2025_phen_shifts_mediterranean]]):
- 9 of 10 dominant Mediterranean species show significant positive NDVI trends; *Eucalyptus camaldulensis* stable
- Two trajectory types: (1) positive throughout 1994–2021 (*Q. ilex*, *P. halepensis*, *P. nigra*); (2) stable until ~2005 then increasing (*O. europaea*, *Q. suber*, *P. pinaster*)
- NDVI magnitude metrics (PEAK, TROUGH) increase over time; but phenological timing (SOS, EOS, LOS) shows no significant temporal shift
- Greening attributed to: CO₂ fertilisation, reforestation policies in Spain, species' physiological resilience to aridity

## Ecological Interpretation Caveats

- Greening does not automatically imply increased carbon uptake — ecosystem carbon balance depends on respiration, disturbance, and phenological shifts
- Greening at high elevations may signal thermophilisation (upward migration of warm-adapted species), but this interpretation is confounded by observational bias (source: [[bayle_2024_landsat_greening_inflated]])
- Arctic browning events (reversals of greening) have been documented despite global greening trends

## Related pages

- [[ndvi]]
- [[landsat]]
- [[phenology]]
- [[sampling_bias_remote_sensing]]
- [[vegetation_community_change]]