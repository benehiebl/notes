---
title: "Drivers of broadleaved evergreen species spread into deciduous forests in the southern Swiss Alps"
authors:
  - Conedera, Marco
  - Wohlgemuth, Thomas
  - Tanadini, Matteo
  - Pezzatti, Gianni Boris
year: 2018
source: conedera_2018_drivers_evergreen
tags:
  - forest-ecology
keywords:
  - evergreen broad-leaved
  - laurophyllisation
  - propagule pressure
  - climate change
  - invasion ecology
  - Hedera helix
  - Ilex aquifolium
  - Prunus laurocerasus
  - Trachycarpus fortunei
  - tobit regression
status: read
---

# Conedera et al. 2018 — Drivers of Broadleaved Evergreen Spread in the Southern Swiss Alps

## Title and Authors
**Drivers of broadleaved evergreen species spread into deciduous forests in the southern Swiss Alps**
Marco Conedera, Thomas Wohlgemuth, Matteo Tanadini, Gianni Boris Pezzatti — *Regional Environmental Change* 18: 425–436 (2018).

## Quick Overview
- **Why is it relevant?** Tests the dominant Insubrian climate-change narrative quantitatively at a single regional climatic gradient, separating climate, propagule pressure, stand structure, and disturbance as drivers of EVE invasion.
- **What was done?** 200 forest plots on a 100 × 100 m systematic grid around Lago Maggiore, surveyed for four target EVE species (2 native, 2 exotic), with tobit regression on climatic and non-climatic covariates.
- **What is the main outcome?** Propagule pressure (distance to nearest garden) is the dominant driver for three of four species; meso-climate (winter temperature) plays a secondary role; the EVE spread is driven more by land-use change (abandoned coppices + planted gardens) than by climate warming.

## Main Goal and Fundamental Concept
The spread of EVE species into deciduous chestnut belt forests south of the Alps had been interpreted as a textbook ecological footprint of climate warming. Conedera et al. challenge this by asking: when you control for propagule pressure, stand structure, geomorphology, and disturbance, how much explanatory power does climate retain?

## Technical Approach
- Study area: ~100 km² around the Swiss part of Lago Maggiore, north- and south-facing slopes, 200–700 m a.s.l. (chestnut belt).
- 100 × 100 m systematic grid → 200 plots stratified across slope exposure and elevation.
- Target species: *Hedera helix* (native), *Ilex aquifolium* (native), *Prunus laurocerasus* (exotic), *Trachycarpus fortunei* (exotic).
- Response: averaged cover (herb + shrub + tree layer per species), arc-sin-sqrt transformed.
- Predictors: meso-climate (modelled average temperature of the coldest month), stand structure (tree/shrub cover and height), disturbance count, propagule pressure (distance to nearest garden in 6 ordinal classes), topographic aspect (northness/eastness).
- Tobit regression (handles censored zero-cover observations); stepwise variable selection via `regr0::step()`; collinearity checked via VIF.

## Distinctive Features
- Uses a regular sampling grid rather than EVE-rich targeted sites (contrasts with [[berger_2006_distribution_eve]]).
- Tobit regression appropriate for cover data with many zeros.
- Includes propagule pressure explicitly — usually omitted in invasion studies.
- Mechanistic interpretation tied to species life history (e.g. *Hedera* skototropic juvenile phase requires shade-providing host trees).

## Experimental Setup and Results

**Final tobit models (by absolute standardised coefficient)**

| Species | Top driver | Climate role |
|---|---|---|
| *Hedera helix* | Distance to garden (−) | Minor (+) |
| *Ilex aquifolium* | Coldest-month T (+) | Only retained predictor, weak model |
| *Prunus laurocerasus* | Distance to garden (−) | Secondary (+) |
| *Trachycarpus fortunei* | Distance to garden (−), coldest-month T (+) | Strong climate effect; also disturbances (+) and northness (+) |

Key mechanisms:
- *H. helix*: needs adult-phase climbing host trees near gardens; abandoned coppice canopies provide hosts. Climate is a weak modulator only.
- *I. aquifolium*: long-established, vegetative reproduction; weak overall model — climate retained but with low explanatory power.
- *P. laurocerasus*: large drupes poorly dispersed by birds → strong garden-distance dependence; low-temperature sensitivity.
- *T. fortunei*: ornamental garden boom since 1950s → first-generation escapees still close to mother trees; thermophilous; benefits from moist north-facing microsites.

**Cross-validation of the climate hypothesis**: 1975–1985 average coldest-month temperature ≈ 2.25 ± 1.29 °C, but 1915–1925 and 1950–1960 had comparable winter temperatures — yet no EVE expansion then because gardens with seed-producing evergreens did not exist and mature unmanaged forest stands were absent. **Climate enabled but did not trigger the invasion**; the trigger was land-use change.

## Advantages and Limitations
- **Advantages**: Regular grid + tobit handles zero inflation; explicit propagule term; mechanistic linking with species life histories; historical climate comparison decouples climate from invasion timing.
- **Limitations**: Single 100 km² window — generalisability limited; coldest-month T modelled rather than measured; frost-day extremes omitted; sample bias toward chestnut belt.

## Conclusion
EVE expansion into Insubrian deciduous forests is **primarily driven by propagule pressure from ornamental plantings combined with the abundance of mature, light-poor stands resulting from coppice abandonment**. Climate warming since the 1970s removed the temperature limitation, but the *trigger* of the invasion is land-use change. This recasts EVE expansion as an example of how multiple global-change drivers act in sequence: climate prepares the niche, propagule pressure colonises it, stand-structure change consolidates it. Has direct implications for RS-based EVE mapping — proximity to settlement should be a strong predictor independent of climate.

## Related pages
- [[evergreen_broadleaved_expansion]]
- [[berger_2006_distribution_eve]]
- [[chelli_2017_climate]]
- [[fady_2025_native_trees_mediterranean]]
- [[hiebl_2025_pretraining]]
- [[hiebl_2026_alphaearth]]
