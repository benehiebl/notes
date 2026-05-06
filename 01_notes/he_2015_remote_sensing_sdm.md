---
title: Will remote sensing shape the next generation of species distribution models?
authors:
  - He, Kate S.
  - Bradley, Bethany A.
  - Cord, Anna F.
  - Rocchini, Duccio
  - Tuanmu, Mao-Ning
  - Schmidtlein, Sebastian
  - Turner, Woody
  - Wegmann, Martin
  - Pettorelli, Nathalie
year: 2015
source: he_2015_remote_sensing_sdm
tags:
  - remote-sensing
  - species-distribution-models
  - biodiversity
  - ndvi
  - phenology
  - lidar
  - hyperspectral
keywords:
  - SDM
  - NG-SDM
  - habitat-suitability
  - predictor-variables
  - biotic-predictors
  - abiotic-predictors
  - species-occurrence
  - vegetation-structure
  - WorldClim
  - ecological-niche
status: summarized
---

## Title and Authors of the Paper

*Will remote sensing shape the next generation of species distribution models?* — Kate S. He, Bethany A. Bradley, Anna F. Cord, Duccio Rocchini, Mao-Ning Tuanmu, Sebastian Schmidtlein, Woody Turner, Martin Wegmann, Nathalie Pettorelli (2015), Remote Sensing in Ecology and Conservation, 1(1), 4–18. DOI: 10.1002/rse2.7. Open Access.

## Quick Overview

- **Why is it relevant?** Classical species distribution models (SDMs) suffer from biased occurrence records and ecologically shallow predictor variables — remote sensing can address both limitations by providing spatially explicit, continuous, and temporally updatable data on both species occurrence and environmental conditions.
- **What was done?** A perspective review demonstrating how diverse remote sensing platforms and products can serve as either response variables (species occurrence) or predictor variables (environmental conditions) in SDMs, with a vision for next-generation SDMs (NG-SDMs).
- **What is the main outcome?** Remote sensing is moving from a supplementary to a central data source for SDMs, enabling more ecologically meaningful, spatially explicit, and dynamically updatable species distribution models — provided that RS and ecology communities collaborate and that circularity risks are managed.

## Main Goal and Fundamental Concept

The paper argues that two fundamental limitations of current SDMs can be overcome with remote sensing:
1. **Response variable bias**: species occurrence data from herbaria and atlases are spatially biased (under-sampled in remote areas), taxonomically incomplete, and static — RS can provide direct occurrence evidence or supplement field records
2. **Predictor variable shallowness**: most SDMs use interpolated climate variables (WorldClim, CRU) and categorical land cover — RS provides continuous, spatially explicit, ecologically relevant variables (NDVI, LST, phenology, canopy structure) at much higher resolution and temporal frequency

The paper proposes "Next-Generation SDMs" (NG-SDMs): integrative models along the correlative-to-process continuum that use ecophysiologically meaningful RS predictors, multi-level response variables, hierarchical spatial frameworks, and explicit biotic interactions.

## Technical Approach

This is a review/perspective paper — no new methodology is developed. Key contributions:

**Remote sensing as response variable (species occurrence):**
- Plant detection feasible when species have unique growth form, phenology, or spectral chemistry
- NDVI time series (MODIS/Landsat): species with distinct seasonal phenology (invasive grasses, understory bamboo, deciduous vs evergreen species)
- Hyperspectral (AVIRIS, HyMap): detect non-native trees by unique pigmentation and leaf water content; 76.5–93.2% accuracy for 8–11 tree species in the Alps using hyperspectral + LiDAR fusion
- High-resolution imagery (Worldview, Pleiades): large animal detection (zebra, polar bear, right whales) via brightness/thermal contrast
- LiDAR + multispectral: absolute population density estimates for tree species (not just presence/absence)

**Remote sensing as predictor variable:**

*Abiotic predictors:*
- Land cover (MODIS, Landsat ETM+): coarse habitat classification used ubiquitously but ecologically blunt
- Topographic features (SRTM, ASTER-DEM, LiDAR): elevation, slope, aspect; high-res LiDAR for micro-topography
- Land surface temperature / LST (Landsat-8, MODIS): 4× daily globally at 1 km; European 250 m product available; direct ecophysiological relevance as organisms respond to surface temperature
- Precipitation (TRMM at 4 km, GPM successor): satellite estimates are uninterpolated, unbiased by station coverage
- Soil moisture (SMAP, 1–3 km): not yet used in SDMs as of 2015

*Biotic predictors:*
- NDVI: proxy for vegetation productivity, food availability, habitat quality (widely used)
- Vegetation phenology (MODIS, Landsat): timing of green-up/senescence as habitat predictor; NDVI-based growing season length as proxy for summer length
- LAI (MODIS): used for habitat suitability modelling
- fPAR (MODIS, Landsat): indirect proxy for light competition and plant growth; LAI3g and fPAR3g as improved products
- Canopy/tree height (LiDAR, RADAR): structural habitat characterisation; improves bird and mammal SDMs
- 3D habitat structural profile (LiDAR/RADAR): vertical layering of vegetation; canopy moisture, roughness
- Spectral heterogeneity of vegetation (QuickBird, Landsat): proxy for plant diversity and habitat heterogeneity
- Spatial heterogeneity of vegetation (MODIS, Landsat): landscape-level diversity predictor

**NG-SDM framework** (proposed):
- Multi-scale hierarchical stack of RS predictor images (one layer per predictor, organized by scale and time)
- Ecophysiologically meaningful predictors (LST, MODIS phenology metrics)
- Demographic parameters from LiDAR (tree height, stem density at different life stages)
- Biotic interaction variables: plant functional types, fPAR, 3D habitat structure
- Multi-level response: presence/absence → fitness metrics → trait diversity → community assemblage abundance
- Model spatially explicit uncertainty quantification

## Distinctive Features

- **Comprehensive sensor catalogue** (Table 1): systematically covers passive multispectral (Worldview to AVHRR), hyperspectral (Hyperion, HyMap, AVIRIS, EnMAP), and active sensors (SAR: Sentinel-1, COSMO-Skymed; LiDAR: GEDI planned; passive microwave: SMAP, TRMM) with resolutions and revisit times
- **Predictor variable catalogue** (Table 2): the most systematic compilation (as of 2015) of RS-derived SDM predictors, organised by abiotic vs biotic and by sensor type
- **NG-SDM conceptual framework** (Figure 1): explicit visual model of how RS-derived responses and predictors stack into a multi-layer modelling framework with spatially explicit uncertainty
- **Circularity warning**: explicitly flags the risk of using RS-derived species distributions as model response AND RS predictors as model inputs — a methodological trap that undermines SDM validity

## Experimental Setup and Results

Not applicable — this is a perspective paper with case study examples drawn from the literature. Key empirical examples cited include:
- Invasive pepperweed (*Lepidium latifolium*) mapped with HyMap using unique white flower reflectance
- 8 tree species in the Southern Alps identified with LiDAR + hyperspectral + multispectral fusion (76.5–93.2% accuracy)
- Bamboo species mapped from early/late senescence phenology via Landsat NDVI time series
- Zebra and wildebeest populations estimated from GeoEye-1 (0.5 m) imagery
- NDVI from MODIS used as food availability proxy in vervet monkey SDM
- Multi-year NDVI projections under climate change used to forecast saiga distribution dynamics

## Advantages and Limitations

**Advantages of RS in SDMs:**
- Spatially continuous wall-to-wall coverage — no spatial sampling bias
- Annually updatable: track range shifts and habitat changes in near-real time
- RS response variables carry presence AND absence information (unlike museum records)
- Remote sensing is increasingly free and globally accessible (Landsat, MODIS, Sentinel)

**Limitations acknowledged:**
- Not all species are detectable by RS: understory species, small animals, species without distinctive spectral/structural signatures
- Spatial-temporal resolution trade-off: high temporal frequency (MODIS, daily) = low spatial resolution; high spatial resolution (Worldview) = infrequent coverage
- Short satellite archives (decades) limit projection of future distributions under century-scale climate change
- Circularity risk: if RS maps are used as response variable and RS metrics as predictors, model evaluation is circular
- Data management, processing expertise, and accessibility remain barriers

**Note on currency (2015 paper):**
Several developments since publication have changed the landscape — Sentinel-2 (here still "launch in 2015"), GEDI (launched 2019), Planet (daily 3 m imagery), and widespread cloud computing (GEE) have substantially increased RS accessibility and temporal density for SDM use.

## Conclusion

He et al. (2015) articulate the case for integrating remote sensing deeply into both the response and predictor sides of species distribution modelling. The key insight is that RS provides spatially explicit, temporally dynamic, and ecologically meaningful data that static interpolated climate datasets cannot — particularly vegetation structure (LiDAR), surface temperature, phenology, and spectral diversity. The proposed NG-SDM framework anticipates developments that have since materialised: dense Sentinel-2 time series enabling fine-grained phenological predictors, GEDI providing global forest height, and cloud computing enabling continental-scale ecological modelling. The circularity warning and the biotic predictor catalogue remain directly relevant to contemporary SDM development.

## Related Work & Obsidian Links

- [[species_distribution_models]]
- [[ndvi]]
- [[phenology]]
- [[landsat]]
- [[sentinel_2]]
- [[plant_functional_traits]]

- [[bricca_2026_topo_diversity]] — Bricca et al. use exactly the RS-derived predictor variables (temperature, solar radiation, soil moisture) advocated by He et al. for SDM-style analyses of forest diversity
- [[grabska_2024_tree_species_map]] — Grabska et al. implement the RS-based plant species detection vision of He et al. at national scale using Sentinel-2 (which was just launching when He et al. was written)
- [[bayle_2024_landsat_greening_inflated]] — He et al. recommend NDVI time series as SDM predictor; Bayle et al. demonstrate a key limitation of such time series (sampling bias), directly relevant to SDM reliability

## Related pages

- [[species_distribution_models]]
- [[sentinel_2]]
- [[ndvi]]
- [[phenology]]
- [[landsat]]
- [[plant_functional_traits]]
- [[bricca_2026_topo_diversity]]
- [[grabska_2024_tree_species_map]]
- [[bayle_2024_landsat_greening_inflated]]
