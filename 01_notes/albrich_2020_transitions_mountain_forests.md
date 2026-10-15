---
title: "Climate change causes critical transitions and irreversible alterations of mountain forests"
authors:
  - Katharina Albrich
  - Werner Rammer
  - Rupert Seidl
year: 2020
tags:
  - forest-ecology
  - climate-change
  - simulation-modelling
keywords:
  - tipping points
  - hysteresis
  - resilience
  - iLand
  - topographic buffering
  - Norway spruce
  - Eastern Alps
status: read
---

## Title and Authors of the Paper

- "Climate change causes critical transitions and irreversible alterations of mountain forests"
- Katharina Albrich, Werner Rammer, Rupert Seidl
- *Global Change Biology* 26(7): 4013–4027 (2020); doi: 10.1111/gcb.15118

## Quick Overview

- **Why is it relevant?** It asks whether Alpine forests respond gradually or abruptly to warming, and whether the change is reversible, a question that bears on any forest-type or species-cover map that is meant to remain valid under climate change.
- **What was done?** The individual-based landscape model iLand was run for the Stubai Valley (Tyrol) under stepwise warming (+0 to +6 °C) and then cooling, combined with 0 to −30 % precipitation and three topography scenarios, each step simulated for 1000 years.
- **What is the main outcome?** Above about +2 °C the simulated landscape tipped from a spruce-dominated state with many large trees to a state of smaller, mostly broadleaved trees, and it did not return along the same path when the climate was cooled (hysteresis).

## Main Goal and Fundamental Concept

- Goal: test (a) whether forest composition and size structure show threshold responses to climate forcing, (b) how topographic complexity changes that response, and (c) whether the changes are reversible.
- Core idea: ecological resilience is the amount of perturbation a system absorbs before it moves to an alternative stable state; a hysteretic system does not return to its initial state along the same path when the driver is reversed.
- Hypothesis: complex topography decouples local from regional conditions and creates refugia, so it should reduce threshold behaviour.
- The analysis uses equilibrium states, which deliberately removes land-use legacies and transient dynamics.

## Technical Approach

- **Model**: iLand, a spatially explicit individual-based forest landscape model. It has daily water-cycle dynamics on 1 ha cells, monthly productivity via resource-use efficiency, annual carbon allocation, and regeneration on 4 m² cells with seed dispersal and climate-dependent establishment.
- **Landscape**: 4811 ha of forested Stubai Valley, Central Alps, 900 m to the timber line at ~2000 m a.s.l. Present species are Norway spruce, European larch and Swiss stone pine; mean annual temperature (1961–2014) is 4.1 °C.
- **Topography scenarios**:
  - Complex: real valley, climate and soils vary at 100 m.
  - Uniform: one homogeneous climate and soil, seed influx from all sides.
  - Intermediate: rescaled heterogeneity, run with a small and a large external seed area.
- **Climate forcing**: statistically downscaled HadGEM2-ES / CLMcom-CCLM4-8-17 RCP 8.5 data. Temperature rose stepwise by 1 °C up to +6 °C, then fell symmetrically. Precipitation was held at baseline, −10 %, −20 % or −30 %. Each step lasted 1000 simulated years, with 10 replicates per combination.
- **Indicators**: Norway spruce share of basal area (composition) and number of trees >30 cm dbh per hectare (size structure).
- **Analysis**: visual detection of nonlinear change (tipping point) and of differing warming/cooling paths (hysteresis). Bray–Curtis dissimilarity between warming and cooling trajectories was tested with PERMANOVA.

## Distinctive Features

- Claims to be the first documentation of hysteresis in the response of forests to climate warming, and the first assessment of critical transitions for Central European forests (source: [[albrich_2020_transitions_mountain_forests]]).
- Explicitly manipulates topographic complexity instead of treating the landscape as a single climate cell.
- Joint attractor-space analysis of structure and composition, showing two basins of attraction.
- Equilibrium simulations of 1000 years per step (a doubled duration gave no significant difference), so the result is about attractors, not about transient timing.

## Experimental Setup and Results

- **Tipping points**:
  - Uniform topography: abrupt change in large-tree numbers between +1 and +2 °C; spruce share dropped by 75 % at +2 °C and was almost extirpated at +4 °C.
  - Complex topography: gradual decline in large trees (about 175 to about 50 trees/ha >30 cm at +6 °C) and gradual spruce decline.
  - Beyond +2 to +3 °C a critical transition occurred in all scenarios; lower precipitation lowered the threshold.
- **Species sequence**: spruce was replaced by beech, then by oak and Scots pine at higher warming. *Pinus cembra*, the current timber-line species, was lost completely above +2 °C.
- **No forest loss**: at most 2 % of the forest area lost tree cover even at +6 °C, so the transition is a change of forest type, not a collapse to non-forest.
- **Hysteresis**: under uniform topography the system returned to its start state when cooled; under complex topography, especially with reduced precipitation, size structure and composition differed from the starting state even at +0 °C. Founder effects of warm-adapted generalists and dispersal limitation behind mountain barriers ("legacy lock") are given as the mechanism.
- **Refugia**: spruce persisted at high elevations and on north-facing slopes in the complex scenario.

## Advantages and Limitations

**Advantages**
- Process-based and spatially explicit; can reach conditions with no historic analogue.
- Systematically separates temperature, precipitation and topography effects.
- Replicated (10 runs) and statistically tested.

**Limitations**
- Model-based only; no empirical validation of the *transition* itself, only of the baseline behaviour of iLand in the focal landscape (per the authors' supplement).
- Excludes disturbances (wind, bark beetle, fire) and management, which in the authors' own words may alter resilience in either direction.
- Soil properties are time-invariant, there is no soil-vegetation nutrient feedback and no ground-vegetation competition; the authors argue these omissions make the estimates conservative.
- CO₂ fertilisation is not simulated; its persistence is uncertain.
- Single climate-model pair under RCP 8.5, one landscape, and equilibrium results over 1000-year steps are not predictions of the timing of change in this century.
- Only two indicators were used; the topography scenarios are constructed, not observed.
- Relevance to treeline work: the timber line is represented only as the upper edge of a forested valley (*P. cembra* loss), not as an ecotone with its own mechanisms (e.g. snow, frost, land-use legacy).

## Conclusion

- Even moderate warming (~+2 °C) can push a simulated Alpine forest landscape across a tipping point from spruce-dominated, large-tree stands to smaller broadleaved ones.
- Topographic complexity delays and smooths the change and provides refugia, but it also strengthens irreversibility through dispersal limitation.
- For mapping work: static species-cover or forest-type maps and training labels reflect a transient state, and the species mix at a given site may shift on decadal-to-century scales; the paper gives no timing for this.
- Complements the earlier landscape study [[albrich_2019_climate_change_mountain_forests]].
