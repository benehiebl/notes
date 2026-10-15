---
title: "Future expansion of upper forest-grassland ecotone under land-use and climate change in the Eastern Alps"
authors:
  - Sebastian Marzini
  - Erich Tasser
  - Camilla Wellstein
  - Katharina Albrich
  - Werner Rammer
  - Marco Mina
year: 2025
tags:
  - forest-ecology
  - climate-change
  - simulation-modelling
keywords:
  - forest-grassland ecotone
  - treeline
  - land-use abandonment
  - iLand
  - concave hull
  - Stubai Valley
  - species shift
status: read
---

## Title and Authors of the Paper

- "Future expansion of upper forest-grassland ecotone under land-use and climate change in the Eastern Alps"
- Sebastian Marzini, Erich Tasser, Camilla Wellstein, Katharina Albrich, Werner Rammer, Marco Mina
- *Landscape Ecology* 40: 55 (2025); doi: 10.1007/s10980-025-02070-8

## Quick Overview

- **Why is it relevant?** It is unclear how fast the upper forest-grassland ecotone will move when land-use abandonment and climate change act together, and which species will lead the shift.
- **What was done?** The forest landscape model iLand simulated 2020–2200 in the Stubai Valley (Tyrol) under grassland abandonment, historical and three-to-four future climate trajectories, natural disturbances (wind, bark beetle) and management; a concave hull algorithm extracted the upper ecotone from the model output.
- **What is the main outcome?** If grasslands are abandoned, forest is projected to expand quickly in the 21st century regardless of climate warming, because the current forest edge is mainly set by land use; climate mainly affects species composition and stocking at higher elevations and ecotone shifts are stronger on south-facing slopes.

## Main Goal and Fundamental Concept

- Goal: quantify future upward shift of the forest-grassland ecotone, species-specific elevational shifts and compositional change.
- Core idea: in the Alps, the present upper forest edge lies below its climatic potential because of past pasture use; releasing land use should therefore trigger expansion even without warming.
- Hypotheses: (H1) rapid upward shift even under historical climate, especially on south slopes; (H2) climate change influences shift velocity towards the end of the simulation, with hotter and drier climate slowing it; (H3) faster shift on south-facing slopes and species-composition differences that grow with scenario intensity.

## Technical Approach

- **Landscape**: Stubai Valley, central Alps, 4811 ha forest plus 1834 ha mountain pine shrubland (6646 ha forested in total) and grassland up to about 2400 m; forest edge currently around 2000 m a.s.l.; dominant species Norway spruce, European larch, Swiss stone pine; extended iLand landscape with managed and unmanaged grassland, mountain pine communities and soil data.
- **Model**: iLand (individual-based, process-based, daily climate), with wind and bark-beetle disturbance modules and current management implemented following Seidl et al. 2019.
- **Climate**: historical climatology (1961–2014 downscaled) and four future trajectories from GCM–RCM/RCP combinations, including a warm-and-wet scenario (+4.6 °C, +6.2 % precipitation) and a hot-and-dry scenario (+6.3 °C); simulation 2020–2100, extended to 2200 by resampling the last 20 years.
- **Ecotone delineation**: model output at 1 ha resolution converted to points, concave hull to delineate the upper edge following the Körner definition of the treeline, and analysis of the ecotone vs. forested area by species and aspect.

## Distinctive Features

- Couples a mechanistic landscape model with explicit land-use abandonment, climate scenarios, disturbances and management.
- Reports species-by-aspect elevational shifts and basal-area change in the ecotone, not only a single treeline shift.
- Uses the same landscape and model as [[albrich_2020_transitions_mountain_forests]], so results can be compared.

## Experimental Setup and Results

- Forest expanded upward under all scenarios including historical climate, with a general upward movement projected to stabilise before 2200.
- Within the ecotone, larch showed the highest shift of all species (+329 to +339 m by 2100 on south-facing slopes); stone pine showed a stronger shift in the ecotone (+321 m at 2100) than in the forested area (+161 m); on north slopes stone pine's shift in forest was +118 m.
- In forested areas differences between climate scenarios in elevational shift were almost negligible; spruce shifted moderately and stabilised after 2100; Scots pine had the highest overall shift (supplement).
- Basal area in the ecotone reached values similar to forested area by the end of the simulation; the hot-and-dry scenario showed higher basal-area increase at the ecotone; spruce declined strongly on north slopes and larch became the most represented species on north-exposed parts in the warm scenario.
- The authors attribute the stabilisation partly to low soil depth (0–20 cm extrapolated) above about 2400 m a.s.l. and harsh conditions there.

## Advantages and Limitations

**Advantages**
- Separates land-use effects from climate effects in a spatially explicit way, and includes disturbance and management.
- Long time horizon and aspect-resolved results.

**Limitations**
- Simulation only, with no validation of the projected ecotone shift against observed treeline change; the scenario assumes complete grassland abandonment, which is not a forecast of actual land use.
- Soil depth data above the current forest were uncertain (extrapolated), and the model has no dynamic soil formation or microclimate, which matter strongly at the treeline.
- 1 ha output resolution limits the ecotone delineation; the concave hull definition is a model-based proxy for the treeline.
- One valley; no snow, frost, browsing or seed-dispersal limitation beyond iLand's seed model, so the rate of upward shift may be over-estimated relative to treeline observations such as [[frei_2023_treeline_shift]] (about 10 m per decade) and the dispersal-limited expansion in [[dullinger_2004_climate_treeline_shifts]].
- The relative importance of land use vs. climate is a result of the chosen scenario design and not an estimate of the real attribution.

## Conclusion

- Land-use legacy, rather than climate, is the main trigger of expansion in this model, but climate decides species composition, particularly on south slopes and over longer time scales.
- It supports using land-use history as a covariate in treeline studies. Related: [[albrich_2019_climate_change_mountain_forests]], [[nicoud_2025_landuse_larch_expansion]], [[cudlin_2017_drivers_treeline_shift]].
