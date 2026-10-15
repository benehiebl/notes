---
title: "Evidence for 40 Years of Treeline Shift in a Central Alpine Valley"
authors:
  - Esther R. Frei
  - Ignacio Barbeito
  - Lisa M. Erdle
  - Elisabeth Leibold
  - Peter Bebi
year: 2023
tags:
  - forest-ecology
  - climate-change
keywords:
  - treeline advance
  - infilling
  - land-use change
  - resurvey
  - dendrochronology
  - Dischma valley
  - Larix decidua
  - Pinus cembra
status: read
---

## Title and Authors of the Paper

- "Evidence for 40 Years of Treeline Shift in a Central Alpine Valley"
- Esther R. Frei, Ignacio Barbeito, Lisa M. Erdle, Elisabeth Leibold, Peter Bebi
- *Forests* 14(2): 412 (2023); doi: 10.3390/f14020412

## Quick Overview

- **Why is it relevant?** It gives rare tree-by-tree ground evidence of treeline change over 40 years and separates real upslope advance from infilling below the old treeline, which satellite products struggle to do.
- **What was done?** A 1972/73 survey of all treeline trees and tree groups (>0.5 m) in the Dischma valley (Davos, Switzerland) was repeated in 2012 and combined with GIS moving-window analysis, tree-ring dating and decision-tree analysis of site factors.
- **What is the main outcome?** The treeline advanced on average by about 10 m per decade (maximum local advance 42 m per decade), but most new trees (79 % of cells) were infilling, and advance depended on aspect, species, microsite and land use in 1900.

## Main Goal and Fundamental Concept

- Goal: quantify treeline advance versus infilling over 40 years and identify which climatic, topographic, biotic and land-use factors control the advance.
- Concept: temperature governs treelines at large scales, but wind, snow, soil, disturbance, browsing and historic land use modify the response locally, so the treeline does not simply track a shifting isotherm.
- Research questions: (i) change on north and south slopes, (ii) share of advance vs. infilling by species and site, (iii) influence of land use relative to other drivers.

## Technical Approach

- **Study area**: Dischma valley, about 10 km², 1600–2800 m a.s.l., avalanches are the main disturbance; Norway spruce, larch and Swiss stone pine; mean annual temperature in Davos 3.5 °C (1981–2022 reference).
- **Surveys**: positions of all trees and groups >0.5 m recorded in 1972/73 on topographic maps with a barometric altimeter and in 2012 with GPS; tree species, browsing and snow-fungus (*Phacidium infestans*) infection recorded.
- **Spatial analysis**: data rasterised to a 50 m grid (1972 mapping errors mostly <25 m); a moving-window algorithm (adapted from Gehrig-Fasel et al.) with a 150 × 150 m window classified newly established cells as treeline advance, infilling or downward shift.
- **Age**: increment cores/discs of trees above and below the old treeline, to date establishment.
- **Drivers**: conditional decision trees (R package *party*) on 164 advance and 164 non-advance cells with 13 site variables (climate, topography, vegetation, land use in 1900 and 1982, avalanche risk).

## Distinctive Features

- A complete resurvey of the same area after 40 years, which is rare for treelines.
- Distinguishes advance from infilling explicitly and uses tree-ring ages to confirm establishment dates.
- Includes historical land-use maps (1900, 1982) as predictors alongside climate and topography.
- Species-specific analysis, because larch, pine and spruce behave differently.

## Experimental Setup and Results

- In 2012, 740 tree groups and 321 single trees (>0.5 m) were recorded in the ecotone; tree density increased strongly on both slopes.
- Of 765 cells with newly established trees, 21 % (164 cells) were advance and 79 % (601 cells) were infilling; 18 cells were downward shifts, mostly in avalanche paths. Above 2250 m a.s.l., 34 % of new cells were advance.
- Advanced trees stood on average 25 m (north-facing slope) and 40 m (south-facing slope) higher than the closest 1972 trees; treeline moved about 40 m in 40 years on average (10 m per decade).
- Larch advanced more on south-facing slopes, pine more on north-facing slopes; spruce mostly infilled. Larch was a steady early colonizer; pine advanced mainly in specific habitats.
- Decision tree: above about 2330 m a.s.l. advance occurred on favourable microsites without competing dwarf-shrub vegetation (ridges, no current land use); at lower elevations advance mainly took place where land use was present in 1900. Current land use had no significant effect.
- Browsing damage affected 26 % (north) and 22 % (south) of larch, far more than pine (7 %, 4 %) and spruce (5 %, 4 %); snow fungus infected 62 % (south) and 32 % (north) of pines.
- The authors argue that warming was likely the more important driver for the uppermost trees, whereas land-use legacy explained advance at slightly lower elevations.

## Advantages and Limitations

**Advantages**
- Direct field evidence over four decades, with individual-tree resolution.
- Multiple lines of evidence (resurvey, tree rings, decision trees).

**Limitations**
- Single valley; the generality of the advance rate (10 m per decade) is unknown.
- 1972 positions were hand-mapped with a barometric altimeter (error mostly <25 m), so a 50 m grid and a coarse treeline definition are needed; a change of about 40 m is of the same order as 1–2 grid cells.
- Moving-window classification depends on window size (150 m chosen after testing); classification may overestimate advance in gullies when windows are large.
- Land-use maps (1900, 1982) are coarse, and land-use factors are partly collinear with terrain suitability.
- Establishment dates of trees that died or were not sampled are missing; trees below 0.5 m are not recorded.
- Data only on request.

## Conclusion

- The treeline ecotone has densified strongly in 40 years, mostly by infilling and to a smaller extent by upslope advance of about 10 m per decade.
- Species, aspect, microsite and historical land use control where trees establish, so it is inadequate to model treeline shift as tracking temperature alone.
- Useful as ground-truth and as a counter-check for RS-based treeline shift rates: [[garbarino_2023_treeline_remote_sensing]], [[menegaldo_2025_landsat_treeline_dynamics]], [[carrieri_2025_hr_imagery_treeline]], [[cudlin_2017_drivers_treeline_shift]].
