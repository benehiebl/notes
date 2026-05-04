---
title: Topography and Soil Moisture Regulate the Temperature-Biodiversity Relationship of Forests
authors:
  - Bricca, Alessandro
  - Zerbe, Stefan
  - Sabatini, Francesco Maria
  - Hiebl, Benedikt
  - Rutzinger, Martin
  - di Musciano, Michele
  - Calvia, Giacomo
  - Chiarucci, Alessandro
  - Poschlod, Peter
  - Rossi, Christian
  - Alessi, Nicola
  - Bonari, Gianmaria
year: 2026
source: bricca_2026_topo_diversity
tags:
  - forest-ecology
  - biodiversity
  - functional-diversity
  - plant-functional-traits
  - climate-change
  - topographic-microclimate
  - Italy
keywords:
  - taxonomic-diversity
  - functional-diversity
  - Rao-quadratic-entropy
  - TRY-database
  - species-richness
  - temperature-biodiversity
  - solar-radiation
  - soil-water-capacity
  - EUNIS-forest-habitats
  - thermophilisation
  - space-for-time-substitution
status: summarized
---

## Title and Authors of the Paper

*Topography and Soil Moisture Regulate the Temperature-Biodiversity Relationship of Forests* — Alessandro Bricca, Stefan Zerbe, Francesco Maria Sabatini, Benedikt Hiebl, Martin Rutzinger, Michele di Musciano, Giacomo Calvia, Alessandro Chiarucci, Peter Poschlod, Christian Rossi, Nicola Alessi, Gianmaria Bonari (2026), Global Ecology and Biogeography, 35: e70186.

## Quick Overview

- **Why is it relevant?** Climate change effects on forest biodiversity are typically assessed at broad biome scales, ignoring that local topographic and soil conditions regulate how temperature affects diversity within and among distinct forest habitat types.
- **What was done?** Regression models were fitted to >5000 Italian forest vegetation plots to quantify the individual and combined effects of temperature, solar radiation (proxy for topography), and soil moisture on taxonomic and functional diversity of tree and shrub guilds across four forest habitat types.
- **What is the main outcome?** Temperature is a strong biodiversity driver but its effect is consistently modulated by solar radiation and soil moisture; warm Mediterranean forest habitats are projected to lose diversity under climate change while cold temperate coniferous forests are projected to gain it.

## Main Goal and Fundamental Concept

The study investigates how climate change will affect the taxonomic and functional diversity of forest plant communities, explicitly accounting for the regulatory role of local topographic and soil conditions.

The core insight is that lumping different forest habitat types into a single broad biome category (e.g., "European temperate forest") masks divergent responses — a forest near its warm physiological limit and a forest at its cold limit respond to warming in opposite directions. Topographic solar radiation modulates local heat exchange and microclimate; soil moisture modulates drought stress. Both mediate the actual climate signal experienced by plants.

Three research questions:
1. Do current climatic conditions differentially influence taxonomic and functional diversity across forest habitat types?
2. Do topographic solar radiation and soil moisture regulate the temperature-diversity relationship?
3. Are these effects consistent across tree and shrub guilds?

## Technical Approach

- **Data**: Italian Forest Database (IFD) — 16,259 vegetation plots; final dataset: 5,450 tree plots (94 tree species) and 5,940 shrub plots (359 shrub species) after quality filtering.
- **Forest habitat types** (EUNIS classification):
  - T1: Broadleaved-deciduous forests
  - T2: Broadleaved-evergreen forests
  - T3m: Mediterranean coniferous forests
  - T3t: Temperate coniferous forests
- **Diversity metrics**:
  - Taxonomic diversity (TD): species richness
  - Functional diversity (FD): Rao's Quadratic Entropy (multi-FD) based on 7 traits — plant height, seed mass, SLA, specific root length, stem specific density (from TRY/GRoOT databases), plus life-history habit and leaf phenology as categorical traits; Gower's distance handles mixed trait types and missing data
- **Climate and local variables**: Mean annual temperature (MAT, °C) from CHELSA downscaled to 250 m; Direct Normal Irradiation (DNI, kWh/m²) from Global Solar Atlas as proxy for topographic effects; soil water capacity (SWC, θ) from SoilGrids 2.0
- **Statistical models**: Linear and quadratic regression with interaction terms (temperature × solar radiation, temperature × soil moisture); model selection via chi-squared test on residual sums of squares; PCA used to check predictor collinearity
- **Future projections**: Space-for-time substitution applied to three IPCC scenarios (+1.4°C mild/SSP1-1.9, +2.7°C intermediate/SSP2-4.5, +4.4°C worst-case/SSP5-8.5 by 2100); delta = diversity 2100 − diversity 1980–2010

## Distinctive Features

- **Vertical stratification of plant guilds**: Separate analysis of tree and shrub guilds reveals that different local modulators operate at canopy vs. understory level — solar radiation is the dominant regulator for trees; soil moisture dominates for shrubs.
- **Habitat-type specificity**: Four distinct forest habitat types are analysed separately, revealing contrasting — sometimes opposite — responses within the same broad biome.
- **Two facets of diversity**: Simultaneous assessment of taxonomic richness and functional diversity allows distinction between adding more species vs. adding more functionally distinct species.
- **Italian gradient**: Italy spans Mediterranean, Continental, and Alpine biogeographical regions, providing strong environmental gradients in one national-scale study.

## Experimental Setup and Results

**Tree guild:**
- MAT had significant effects on TD and FD in all four habitat types.
- Inverted U-shaped (unimodal) temperature-TD relationship in broadleaved-deciduous, broadleaved-evergreen, and Mediterranean coniferous forests (diversity peaks at intermediate temperatures).
- Linear positive temperature-TD in temperate coniferous forests (frost-limited — warmer = more species).
- Solar radiation regulated the temperature-diversity relationship: where DNI is high, temperature effects were steeper.
- Adjusted R²: 9–27% for TD; 3–41% for FD (Mediterranean coniferous highest).

**Shrub guild:**
- Similar general patterns as tree guild but weaker (adjusted R² 2–19% TD; 2–13% FD).
- Soil moisture (SWC) was the primary local regulator for shrubs (vs. solar radiation for trees) — consistent with shrubs being closer to the ground and more sensitive to soil microenvironment.
- Unimodal FD-temperature for broadleaved-deciduous; negative for broadleaved-evergreen; no significant FD response in temperate coniferous.

**Projections (worst-case +4.4°C scenario):**
- Temperate coniferous forests (Alps): gain in TD for both tree and shrub guilds — thermophilisation
- Broadleaved-deciduous forests: gain TD inland (Alps, Apennines) but lose TD along coastlines
- Mediterranean coniferous and broadleaved-evergreen forests: loss of TD and FD, especially along the coasts of central Italy — intensified drought stress
- Spatially explicit maps produced for each habitat type and diversity facet

## Advantages and Limitations

**Advantages:**
- Large, quality-controlled national dataset (>5000 plots) spanning strong environmental gradients.
- Explicit separation of tree and shrub guilds reveals mechanistic differences between vertical forest strata.
- Climate variables downscaled to 250 m better capture topoclimatic variation than coarse gridded products.
- Spatially explicit projections are actionable for habitat-specific conservation planning.

**Limitations:**
- Space-for-time substitution assumes climate-diversity relationships observed spatially hold over time — migration lags and dispersal limitations mean real changes lag behind predictions.
- Species-level trait values from TRY ignore intraspecific trait variation (ITV); though ITV is generally smaller than between-species variation, it may bias community-level results.
- Forest management practices are spatially heterogeneous and not included — land use history can override climatic predictors.
- Analysis does not distinguish biodiversity gain from immigration vs. biodiversity loss from local extinction — processes operating at different timescales.

## Conclusion

Bricca et al. (2026) show that temperature is a primary driver of forest diversity in Italy, but its effects vary by habitat type and are consistently regulated by topographic solar radiation (for trees) and soil moisture (for shrubs). Mediterranean forests near physiological heat and drought tolerance limits are predicted to lose diversity under warming, while frost-limited temperate coniferous forests are predicted to gain diversity through thermophilisation. These opposite projections within the same country underscore the need for habitat-specific rather than biome-wide management strategies and highlight the critical role of topographic and edaphic heterogeneity in buffering or amplifying climate change impacts on forest biodiversity.

## Related Work & Obsidian Links

- [[functional_diversity]]
- [[plant_functional_traits]]
- [[topographic_microclimate]]

**Cross-paper links (same vault):**
- [[01_notes/albrich_2019_climate_change_mountain_forests]] — both address climate-driven changes in European mountain forest composition; Albrich et al. use process-based simulation while Bricca et al. use observational plot data; complementary mechanistic and statistical perspectives
- [[01_notes/fady_2025_native_trees_mediterranean]] — both address climate threats to Mediterranean forest trees; Fady et al. focus on species-level conservation while Bricca et al. address community-level diversity patterns
- [[01_notes/koch_2025_intraspecies_variation_s2]] — Koch et al. address intraspecific spectral variation, paralleling the ITV limitation acknowledged in Bricca et al.
