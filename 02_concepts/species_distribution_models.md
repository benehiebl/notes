---
name: species_distribution_models
description: Species distribution models (SDMs) — ecological niche modelling, response and predictor variables, remote sensing integration, and next-generation SDM concepts
type: reference
---

# Species Distribution Models (SDMs)

**Summary**: Species distribution models statistically relate species occurrence records to environmental predictor variables to estimate the spatial distribution of suitable habitat — a fundamental tool for biogeography, conservation planning, and forecasting range shifts under climate change.

**Sources**: he_2015_remote_sensing_sdm.pdf

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

**Remote sensing contributions** (source: he_2015_remote_sensing_sdm.pdf):
- Direct species detection for plants with unique spectral/phenological signatures (e.g., invasive species, dominant tree species)
- High-resolution imagery for large-bodied animal detection
- Provides presence AND absence data (unlike herbarium records) → reduces omission vs commission error trade-off
- Annually updatable — captures range dynamics

Key limitation: not all species are spectrally or structurally detectable; understory species and small animals remain challenging.

## Predictor Variables

**Abiotic (climate/environment):**
- Interpolated climate: WorldClim, CRU, CHELSA — temperature and precipitation surfaces; ubiquitous but spatially biased by weather station coverage
- Land surface temperature (LST): MODIS (1 km, 4× daily), Landsat (30 m); ecophysiologically more direct than air temperature
- Land cover: MODIS, Landsat — coarse habitat classification
- Topography: SRTM DEM (30–90 m), ASTER-DEM; slope, aspect, elevation routinely used
- Soil moisture: SMAP (1–3 km); not yet widely integrated as of 2015

**Biotic (vegetation/habitat):**
- [[ndvi]]: proxy for vegetation productivity, food availability, habitat quality; widely used but can create circularity if response also RS-derived
- Vegetation [[phenology]]: timing of green-up/senescence (MODIS, Landsat); growing season length as habitat proxy
- LAI, fPAR: light environment and plant productivity
- Canopy height / tree height: LiDAR and RADAR; improves bird and mammal SDMs substantially
- 3D habitat structural profile: LiDAR — vertical layering of vegetation
- Spectral heterogeneity: proxy for plant diversity and habitat complexity

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
