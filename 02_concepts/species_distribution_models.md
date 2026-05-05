---
name: species_distribution_models
description: Species distribution models (SDMs) — ecological niche modelling, response and predictor variables, remote sensing integration, and next-generation SDM concepts
type: reference
tags:
  - forest-ecology
  - machine-learning
  - remote-sensing
---

# Species Distribution Models (SDMs)

**Summary**: Species distribution models statistically relate species occurrence records to environmental predictor variables to estimate the spatial distribution of suitable habitat — a fundamental tool for biogeography, conservation planning, and forecasting range shifts under climate change.

**Sources**: [[he_2015_remote_sensing_sdm]], [[noce_2023_altitude_shift_tree_italy]], [[fady_2025_native_trees_mediterranean]]

**Last updated**: 2026-05-05

---

## Core Concept

SDMs (also called ecological niche models or habitat suitability models) learn the statistical relationship between where a species occurs and the environmental conditions at those locations, then project that relationship across space (and time) to predict where suitable habitat exists.

The two key model components:
- **Response variable**: species occurrence records (presence/absence or presence-only)
- **Predictor variables**: environmental layers describing climate, land cover, topography, vegetation

## Response Variables

**Classical sources** (biased):
- Herbarium and museum specimen records — spatially biased towards accessible areas
- National atlases, checklists — often outdated, coarse resolution
- Citizen science (iNaturalist, GBIF) — spatially and taxonomically uneven

**Remote sensing contributions** (source: [[he_2015_remote_sensing_sdm]]):
- Direct species detection for plants with unique spectral/phenological signatures (e.g., invasive species, dominant tree species)
- High-resolution imagery for large-bodied animal detection
- Provides presence AND absence data (unlike herbarium records) → reduces omission vs commission error trade-off
- Annually updatable — captures range dynamics

Key limitation: not all species are spectrally or structurally detectable; understory species and small animals remain challenging.

## Predictor Variables

**Abiotic (climate/environment)** (source: [[he_2015_remote_sensing_sdm]]):
- Interpolated climate: WorldClim, CRU, CHELSA — temperature and precipitation surfaces; ubiquitous but spatially biased by weather station coverage
- Land surface temperature (LST): MODIS (1 km, 4× daily), Landsat (30 m); ecophysiologically more direct than air temperature
- Land cover: MODIS, Landsat — coarse habitat classification
- Topography: SRTM DEM (30–90 m), ASTER-DEM; slope, aspect, elevation routinely used; EU-DEM 25m used for Italian SDMs (source: [[noce_2023_altitude_shift_tree_italy]])
- Soil moisture: SMAP (1–3 km); not yet widely integrated as of 2015

**Biotic (vegetation/habitat)** (source: [[he_2015_remote_sensing_sdm]]):
- [[ndvi]]: proxy for vegetation productivity, food availability, habitat quality; widely used but can create circularity if response also RS-derived (source: [[he_2015_remote_sensing_sdm]])
- Vegetation [[phenology]]: timing of green-up/senescence (MODIS, Landsat); growing season length as habitat proxy (source: [[he_2015_remote_sensing_sdm]])
- LAI, fPAR: light environment and plant productivity
- Canopy height / tree height: LiDAR and RADAR; improves bird and mammal SDMs substantially
- 3D habitat structural profile: LiDAR — vertical layering of vegetation
- Spectral heterogeneity: proxy for plant diversity and habitat complexity

## Mediterranean Tree Species Diversity as SDM Context

The Mediterranean basin holds 496 native tree species and 147 subspecies — the richest tree flora in Europe/Western Asia (source: [[fady_2025_native_trees_mediterranean]]):
- Species richness is positively correlated with botanical territory area and habitat heterogeneity; richness hotspots are concentrated in the Balkans, Turkey, and North African mountain zones
- ~38% of species lack IUCN extinction risk assessments; genetic diversity data absent for ~2/3 of species — critical knowledge gaps for SDM-informed conservation
- Endemism is highest in islands and southern mountain ranges — exactly the zones with fewest occurrence records, making SDMs most uncertain where they are most needed
- This floristic richness and data paucity are the primary motivation for NG-SDMs that can leverage RS data to fill spatial gaps in occurrence records (source: [[he_2015_remote_sensing_sdm]])

## Correlative vs Process-Based Continuum

SDMs range across a modelling continuum:
- **Fully correlative (MaxEnt, BioClim, GLM)**: fit statistical relationship between occurrence and environment; extrapolation uncertain; no mechanism
- **Hybrid**: incorporate mechanistic constraints (thermal tolerance, phenological limits) within statistical framework
- **Fully process-based**: simulate population dynamics, dispersal, biotic interactions from first principles

Most operational SDMs fall at the correlative end. Remote sensing can improve both ends by providing ecophysiologically meaningful predictors.

## Next-Generation SDMs (NG-SDMs)

Proposed framework (He et al. 2015) for integrating RS more deeply:
1. **Ecophysiologically meaningful predictors**: LST, MODIS phenological metrics, fPAR — directly relevant to organism physiology rather than indirect climate surrogates
2. **Demographic parameters from LiDAR**: tree height and stem density at multiple life stages → link to population dynamics
3. **Biotic interaction variables**: plant functional types, 3D habitat structure — capture competition, shelter, food
4. **Multi-level response variables**: presence/absence → fitness metrics → trait diversity → community assemblages
5. **Hierarchical spatial framework**: multiple scales simultaneously; spatially explicit uncertainty quantification
6. **Explicitly process-oriented component**: dispersal kernels, demographic rates — not purely correlative

## MaxEnt for Altitudinal Range Shift Projections

Italian mountain forest case study (Noce et al. 2023) demonstrates operational MaxEnt SDM workflow for forest management:
- **Occurrence data**: NFI systematic grid (INFC 2005) provides systematic, unbiased presence records across national territory — stronger spatial design than opportunistic herbarium data (source: [[noce_2023_altitude_shift_tree_italy]])
- **High-resolution climate**: VHR-REA_IT (2.2 km, ERA5 downscaled via COSMO-CLM) outperforms standard WorldClim for mountain topographic heterogeneity
- **Altitudinal band analysis**: zonal statistics in 150m elevation bands directly translates to spatial management prescriptions (which altitudes to prioritise for each species)
- **Key results**: Silver fir most vulnerable (loss across all 5 Italian mountain sections); European larch gains in Alps (+33 to +40%); Turkey oak gains in Apennines; tree line expected to shift upward; Northern Apennines most impacted
- **RCP scenario bracketing**: using both RCP 4.5 and 8.5 provides upper/lower uncertainty bounds; some species show divergent projections between scenarios

**Limitations specific to NFI-based SDMs:**
- Occurrence data from older NFI cycle (INFC 2005) creates temporal mismatch with modern climate baseline
- NFI grid coordinates systematically offset (SW corner of 1km cell) — introduces positional uncertainty
- NFI presence-only data: no confirmed absences → MaxEnt required (cannot use presence-absence methods)

## Key Limitations and Caveats

- **Circularity risk**: if response variable is derived from RS (e.g., species map from RS classification) AND predictors are also RS-derived metrics, the model is circular — avoid or explicitly test independence
- **Spatial-temporal resolution trade-off**: high temporal resolution (MODIS daily) → low spatial resolution; unavoidable given physics of satellite sensors
- **Short satellite archives** (decades): limit projection of range shifts under century-scale climate scenarios
- **Not all species detectable by RS**: understory plants, small animals, species without distinctive spectral signatures require field surveys

## Remote Sensing Sensors Relevant to SDMs

| Data type | Key sensors | SDM application |
|-----------|------------|----------------|
| Multispectral time series | Landsat, Sentinel-2, MODIS | NDVI, phenology, land cover predictors |
| Hyperspectral | AVIRIS, HyMap, EnMAP | Species-level plant detection; trait predictors |
| LiDAR | GEDI, airborne | Canopy height, 3D habitat structure; tree species detection |
| SAR | Sentinel-1, ALOS | Forest structure, biomass proxy |
| Thermal | MODIS, Landsat-8 | LST as ecophysiological predictor |
| Passive microwave | SMAP | Soil moisture predictor |

## Related pages

- [[ndvi]]
- [[phenology]]
- [[landsat]]
- [[sentinel_2]]
- [[plant_functional_traits]]
- [[topographic_microclimate]]
- [[tree_species_mapping]]
