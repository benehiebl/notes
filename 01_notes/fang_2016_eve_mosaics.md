---
title: "Habitat heterogeneity explains mosaics of evergreen and deciduous trees at local-scales in a subtropical evergreen broad-leaved forest"
authors:
  - Fang, Xiaofeng
  - Shen, Guochun
  - Yang, Qingsong
  - Liu, Heming
  - Ma, Zunping
  - Deane, David C.
  - Wang, Xihua
year: 2016
source: fang_2016_eve_mosaics
tags:
  - forest-ecology
keywords:
  - evergreen-deciduous mosaic
  - habitat heterogeneity
  - soil phosphorus
  - evergreen broad-leaved forest
  - EBLF
  - spatial point-pattern analysis
  - multivariate regression tree
  - spatial scale
  - subtropical China
status: read
---

# Fang et al. 2016 — Habitat Heterogeneity Explains Mosaics of Evergreen and Deciduous Trees

## Title and Authors
**Habitat heterogeneity explains mosaics of evergreen and deciduous trees at local-scales in a subtropical evergreen broad-leaved forest**
Xiaofeng Fang, Guochun Shen, Qingsong Yang, Heming Liu, Zunping Ma, David C. Deane, Xihua Wang — *Journal of Vegetation Science* (2016). DOI: 10.1111/jvs.12496.

## Quick Overview
- **Why is it relevant?** Provides mechanistic evidence for the edaphic and topographic drivers of evergreen-deciduous spatial patterns within forest stands — informs why EVE cover is spatially heterogeneous and what microhabitat features predict it, beyond the mesoscale climate factors.
- **What was done?** Used a 20-ha stem-mapped evergreen broad-leaved forest (EBLF) in subtropical China to test whether environmental heterogeneity explains the observed evergreen-deciduous mosaic, via spatial point-pattern analysis and multivariate regression trees at three scales (10, 20, 50 m).
- **What is the main outcome?** Habitat heterogeneity fully accounts for the mosaic: **soil phosphorus (>0.27–0.30 g/kg) is the dominant driver** of deciduous species dominance at all scales; removing environmental heterogeneity eliminates spatial segregation.

## Main Goal and Fundamental Concept
Subtropical EBLF characteristically show a patchy mosaic of evergreen and deciduous trees. Two competing explanations exist: (1) biotic interactions (competition, trait-based niche differentiation) or (2) habitat heterogeneity (abiotic filtering). Disentangling them requires controlling for the environment while testing spatial patterns. The paper tests: does evergreen-deciduous segregation disappear once environmental variation is removed?

The underlying theory: deciduous trees have higher photosynthetic rates requiring high-nutrient soils (especially P), while evergreens tolerate nutrient-poor soils via leaf trait economics (longer leaf lifespan, low SLA, high sclerophylly).

## Technical Approach
- **Site**: 20-ha stem-mapped Tiantong plot, Zhejiang, China; subtropical monsoon climate (MAT 16.2°C, MAP 1374.7 mm); mean elevation 447 m; slope 14°–50°
- **Data**: 94,605 living individuals; 79 deciduous + 73 evergreen species; EVE importance value 79.9 vs deciduous 20.1
- **Environmental variables**: 4 topographic (elevation, slope, aspect, convexity) + 3 soil (pH, total N, total P) measured at 10, 20, 50 m grid cells; 1,310 soil sampling points
- **Methods**:
  1. **Univariate point-pattern analysis**: pair correlation functions ge(r) and gd(r) with CSR null model (199 Monte Carlo simulations, α=0.01)
  2. **Spatial association analysis**: cross-pair correlation g12(r) and bivariate L-function with independence null model; then heterogeneous Poisson process (HPP) model removing environmental heterogeneity effects
  3. **Multivariate regression trees (MRT)**: at 10, 20, 50 m scales using importance value as response and all 7 environmental variables as predictors

## Distinctive Features
- **Scale-explicit analysis**: tests the same hypotheses at 10, 20, and 50 m simultaneously — reveals hierarchical operation of different environmental drivers
- **HPP model**: explicitly removes environmental heterogeneity effects to test whether residual spatial segregation remains
- **Importance value** (relative dominance + relative abundance) as continuous response variable — more informative than binary presence/absence

## Experimental Setup and Results

**Point-pattern analysis:**
- Evergreen trees aggregated at scales < 125 m; deciduous trees aggregated at scales < 60 m
- Mutual spatial exclusion between life forms at scales < 120 m
- **After HPP control for environmental heterogeneity: all segregation disappears at all scales** → habitat heterogeneity is sufficient to explain the mosaic

**Multivariate regression trees:**

| Scale | Key driver | Threshold | Pattern |
|---|---|---|---|
| 50 m | Soil total P | >0.27–0.30 g/kg | Deciduous dominated at high P |
| 20 m | P + elevation + slope | Various | More differentiation |
| 10 m | P + slope + N | Various | N excluded deciduous at low N |

**Soil P at all scales**: deciduous trees preferred sites with P > 0.27–0.30 g/kg — explains ~31% of importance value variance. This reflects deciduous trees' high photosynthetic rates requiring high-P soils during the growing season to maximize leaf N-use efficiency.

**Soil N and slope**: at fine scales (10m), deciduous favoured low slope (moist) + high P; evergreen favoured steeper slopes (drier, less fertile) + lower P

**Hierarchy of controls:**
- Coarse scales: temperature/elevation (as in Song et al. 2014 on latitudinal gradient)
- Intermediate scales (~20m): soil P
- Fine scales (<20m): microhabitat — slope, P, N jointly

## Advantages and Limitations
- **Advantages**: Most comprehensive multi-scale study of EBLF mosaic mechanism; HPP model directly tests habitat heterogeneity hypothesis; 20-ha provides rare statistical power; soil measurements at 1310 points.
- **Limitations**: Single 20-ha site in subtropical China — not directly transferable to other regions (Appalachians, Italian forests, Mediterranean); soil P mechanism may not be universal (Song et al. 2014 found thermal + water factors more important at biogeographic scales); correlative approach — cannot fully exclude biotic interactions (experimental test needed).

## Conclusion
**Habitat heterogeneity, primarily mediated by soil phosphorus availability, generates the observed mosaic of evergreen and deciduous trees in EBLF.** Deciduous species dominate nutrient-richer (high-P), moderate-moisture sites; evergreens dominate nutrient-poorer (low-P), drier, steeper sites. Environmental controls operate hierarchically — temperature and elevation at landscape scales, soil properties at stand scales, micro-topography at stand and fine scales. For RS mapping: the evergreen-deciduous pattern has an edaphic-topographic signal that may complement spectral-temporal signatures.

## Related pages
- [[evergreen_broadleaved_expansion]]
- [[plant_functional_traits]]
- [[leaf_habit_latitudinal_gradient]]
- [[topographic_microclimate]]
- [[functional_diversity]]
- [[jin_2023_drivers_differentiation_evergreen]]
- [[fady_2025_native_trees_mediterranean]]
- [[chelli_2017_climate]]
- [[berger_2006_distribution_eve]]
