---
title: "Shifts in native tree species distributions in Europe under climate change"
authors:
  - Dyderski, Marcin K.
  - Paź-Dyderska, Sonia
  - Jagodziński, Andrzej M.
  - Puchałka, Radosław
year: 2025
source: dyderski_2025_species_shift
tags:
  - forest-ecology
  - machine-learning
keywords:
  - species distribution model
  - MaxEnt
  - climate change
  - SSP scenarios
  - functional traits
  - alternative stock species
  - range contraction
  - European forests
status: read
---

# Dyderski et al. 2025 — Shifts in Native Tree Species Distributions in Europe Under Climate Change

## Title and Authors
**Shifts in native tree species distributions in Europe under climate change**
Marcin K. Dyderski, Sonia Paź-Dyderska, Andrzej M. Jagodziński, Radosław Puchałka — *Journal of Environmental Management* 373: 123504 (2025).

## Quick Overview
- **Why is it relevant?** Updates pan-European SDMs to the CMIP6/IPCC AR6 SSP scenarios and explicitly evaluates alternative stock species (less commercial, ecologically important) — directly informs forest type prediction and management planning under climate scenarios.
- **What was done?** MaxEnt models for 20 native temperate tree species (10 standard stock + 10 alternative) under four SSP scenarios × two time horizons; range contraction linked to functional traits.
- **What is the main outcome?** Boreal/conifer species (*Abies alba*, *Larix decidua*, *Picea abies*, *Pinus sylvestris*) are most threatened, with major contraction by 2041–2060; broadleaved alternative-stock species (e.g. *Sorbus torminalis*, *Carpinus betulus*) are robust; "fast" trait species lose more range than "slow" ones — contrary to expectation.

## Main Goal and Fundamental Concept
Forestry planning needs species-by-species distribution projections under recent climate scenarios. Most prior studies used outdated AR5 scenarios and focused on economically dominant species. Dyderski et al. (a) update to AR6 SSPs, (b) add 10 alternative-stock species (less commercially important but ecologically suited to dominate stands), and (c) link projected contraction to functional traits to enable extrapolation to unmodelled species.

## Technical Approach
- 20 native European tree species, paired as standard stock (10) and alternative stock (10).
- Occurrence data: Caudullo et al. (2017), Mauri et al. (2017), GBIF (1970–2020, coordinate uncertainty <2.5 km), one point per 0.25° grid to reduce sampling bias.
- Climate: WorldClim 2.1, 19 bioclimatic variables, reduced to 7 less-correlated (|r|<0.7).
- SDM: MaxEnt; 30% random test split; AUC + TSS for evaluation.
- Future climate: 4 SSP scenarios (SSP1-2.6, SSP2-4.5, SSP3-7.0, SSP5-8.5) × 4 GCMs × 2 time horizons (2041–2060, 2061–2080).
- Trait analysis: link range contraction to height, leaf area, leaf N, SLA, seed mass, wood density (Paź-Dyderska & Jagodziński database).

## Distinctive Features
- AR6 SSP scenarios (newer than typical AR5 RCP studies).
- Includes alternative stock species rarely covered (*S. torminalis*, *U. minor*, *T. platyphyllos*, *A. pseudoplatanus*, *P. avium*, *C. betulus*, *U. laevis*, *A. platanoides*, *F. excelsior*, *U. glabra*).
- Trait-based generalisation enables predictions for species not directly modelled.
- Tests four hypotheses about transition (conifer → broadleaved), expansion of deciduous, contraction of boreal, and trait-dependence of contraction.

## Experimental Setup and Results

Three threat-level groups emerged:

**Non-threatened** (range stable or expanding): *Sorbus torminalis*, *Ulmus minor*, *Tilia platyphyllos*, *Acer pseudoplatanus*, *Prunus avium*, *Carpinus betulus*.

**Partially threatened**: *U. laevis*, *Betula pendula*, *Quercus robur*, *Q. petraea*, *A. platanoides*, *Fagus sylvatica*, *Fraxinus excelsior*, *T. cordata*, *Alnus glutinosa*, *U. glabra*.

**Most threatened** (largest contraction): *Abies alba*, *Larix decidua*, *Picea abies*, *Pinus sylvestris* — almost half of contraction occurring earlier (2041–2060) than previously predicted (2061–2080).

**Trait correlations with contraction**
- Range contraction *decreases* with:
  - Higher SLA
  - Larger leaf area
  - Higher leaf N
  - Larger seed mass
  - Higher specific stem density
- Range contraction *increases* with:
  - Greater tree height

This is contrary to the conventional "fast → fragile, slow → robust" expectation: many "fast" leaf-economic-spectrum traits associate with robustness here, suggesting that competitive broadleaved species with productive leaves outperform tall, slow boreal conifers under future climate.

**Pattern**: clear conifer → broadleaved transition; northward range shift; boreal pioneer species fail to migrate fast enough.

## Advantages and Limitations
- **Advantages**: Up-to-date SSP scenarios; explicit alternative-stock inclusion broadens management options; trait-based generalisation enables prediction for unmodelled species.
- **Limitations**: MaxEnt cannot capture biotic interactions, dispersal limitation, or land-use constraints; climate-only predictors (no soil); 2.5' grid resolution may smooth microclimatic variation; occurrence-data biases despite spatial thinning; functional trait values are species means without intraspecific variation.

## Conclusion
**Standard stock species in European forestry are under serious near-term threat**, with major boreal/conifer contractions arriving in 2041–2060 rather than 2061–2080. Forestry should diversify silvicultural risk across a wider range of species, **explicitly including underutilised native alternatives** (Sorbus, Tilia, Acer pseudoplatanus, Prunus avium, Carpinus betulus). The trait correlations open a path to extrapolate predictions to unmodelled species.

## Related pages
- [[species_distribution_models]]
- [[noce_2023_altitude_shift_tree_italy]]
- [[fady_2025_native_trees_mediterranean]]
- [[thom_2026_disturbance_suitability]]
- [[plant_functional_traits]]
- [[grünig_2026_climate_change_disturbances_forest]]
- [[albrich_2019_climate_change_mountain_forests]]
- [[schuldt_2020_drought_forest]]
- [[chelli_2017_climate]]
- [[babst_2019_redistribution]]
