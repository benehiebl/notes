---
title: Climate change will increase forest disturbances in Europe throughout the 21st century
authors:
  - Grünig, Marc
  - Rammer, Werner
  - Senf, Cornelius
  - et al.
year: 2026
source: grünig_2026_climate_change_disturbances_forest
tags:
  - forest-ecology
  - climate-change
  - forest-disturbances
  - deep-learning
  - remote-sensing
  - Europe
keywords:
  - wildfire
  - bark-beetle
  - windthrow
  - SVD-framework
  - disturbance-interactions
  - vegetation-feedback
  - forest-demography
  - RCP-scenarios
  - Landsat-disturbance-map
  - state-and-transition-model
status: summarized
---

## Title and Authors of the Paper

*Climate change will increase forest disturbances in Europe throughout the 21st century* — Marc Grünig, Werner Rammer, Cornelius Senf, and 35+ co-authors (2026), Science, 391, eadx6329. DOI: 10.1126/science.adx6329. Code: github.com/magruen/disturbance_scenarios_europe; SVD model: github.com/edfm-tum/SVD.

## Quick Overview

- **Why is it relevant?** Future forest disturbance regimes under climate change are poorly constrained because disturbance agents interact with each other and with vegetation dynamics — existing projections that ignore these feedbacks likely misestimate future disturbance risk.
- **What was done?** A continental-scale, 100-m resolution deep learning simulation framework (SVD) was developed to project wildfire, bark beetle, and windthrow disturbances across 187 million ha of European forests under three climate scenarios, explicitly accounting for disturbance interactions and vegetation feedbacks.
- **What is the main outcome?** Disturbed forest area will more than double under unabated climate change (+122% under RCP8.5) by the end of the century; wildfire is the dominant driver; vegetation feedbacks substantially dampen but cannot eliminate disturbance increases; young forests will increase and old forests decline across Europe.

## Main Goal and Fundamental Concept

The study projects 21st-century forest disturbance trajectories at high spatial resolution and continental scale, accounting for two key mechanisms typically omitted from prior projections:
1. **Disturbance interactions**: windthrow creates habitat and conditions for bark beetle outbreaks (31% of all bark beetle disturbed area traced to prior wind events)
2. **Vegetation feedbacks**: disturbance changes forest structure and composition, which in turn changes susceptibility to future disturbances (dampening factor of 2.6–3.9× without feedbacks)

The framework is relevant both as an ecological forecast for European forest policy and as a methodological template combining process models, remote sensing calibration, and deep learning at continental scale.

## Technical Approach

**SVD (Scaling Vegetation Dynamics) framework** — a state-and-transition metamodel integrating:

**Forest state representation:**
- Each 100 m × 100 m cell described by 3 dimensions: tree species composition, canopy height (0–50 m binned to 2 m resolution), leaf area index (LAI, 3 classes)
- 5,445 unique discrete forest states used in the model
- Initialized from satellite-derived products (2020): canopy height from Sentinel-2/GEDI fusion, LAI from MODIS, species composition from tree species distribution models

**Slow transitions (forest development DNN):**
- Feedforward neural network: 22 layers, 3 blocks with residual connections, 6.6M parameters (TensorFlow/Keras)
- Trained on 1.1 million harmonized simulations from 17 locally validated process models across 13,600 locations in Europe (135 million simulation years)
- Predicts: (1) target forest state after transition; (2) time until transition occurs (10-year forecasting window)
- Drivers: current forest state + residence time, soil conditions (WHC, texture, depth, N), climate (temperature, precipitation, radiation, VPD)
- Validation: 86.9% accuracy for target state; 61.1% for exact timing; true state in top 2 predictions 79.3% of cases

**Fast transitions — three disturbance modules:**
- **Wildfire**: statistical fire frequency model (negative binomial; VPD, topography, population density, lightning as predictors) + probabilistic cellular automaton for fire spread (fuel availability from vegetation state, wind, topography as spread controls)
- **Bark beetle** (*Ips typographus*): mechanistic phenology (PHENIPS model; temperature/radiation → generation number → dispersal pressure); spread via generation-dependent dispersal kernels; constrained to Norway spruce; interactions with wind events modelled explicitly
- **Wind**: statistical storm frequency (GAM; wind speed return intervals as predictors) + neighbourhood-based spread (species composition and tree height determine susceptibility)
- All calibrated against Landsat-derived European forest disturbance map (1986–2020; annual disturbance rates from time series analysis)

**Climate and management:**
- Three RCP scenarios (RCP2.6, RCP4.5, RCP8.5) × 3 GCMs (MPI-M-MPI-ESM-LR, ICHEC-EC-EARTH, NCC-NorESM1-M) downscaled with SMHI-RCA4 → 9 climate trajectories
- 10 replicate simulations per trajectory → 120 total future trajectories
- Business-as-usual forest management: stand-level harvesting based on growth-and-yield principles; final harvest at height growth threshold (~30 m); no management composition changes

## Distinctive Features

- **First continental-scale, 100-m resolution disturbance projection**: previous projections were either coarser spatial resolution or smaller spatial extent
- **Explicit disturbance interactions**: windthrow → bark beetle feedback is modelled mechanistically, not assumed
- **Vegetation feedbacks as emergent property**: changing forest structure in response to disturbance feeds back into future disturbance susceptibility — not parameterised but emerging from SVD dynamics
- **Deep learning metamodel of forest development**: replaces computationally prohibitive process model simulations at scale, trained on 135 million simulation years
- **Remote sensing calibration**: Landsat-derived disturbance map used for both training disturbance modules and model validation (simulation r = 0.95 for fire events, r = 0.71 for burned area; bark beetle median 33,871 ha vs observed 29,046 ha)

## Experimental Setup and Results

**Disturbance rate projections (RCP8.5 vs. historical 1986–2020):**
- Overall disturbed area: +122% by 2081–2100 (RCP8.5); +61% (RCP4.5); +31% (RCP2.6)
- Disturbance rotation: historical 1485 ± 756 years → 510 ± 36 years (RCP8.5), 869 ± 51 years (RCP2.6)
- Disturbance rates increase in 76% of forested hexagons (RCP8.5)

**By disturbance agent:**
- **Fire**: historical 82,016 ha/yr → 232,061 ± 9,924 ha/yr (RCP8.5) = +183%; extreme fire years occur every year by end of century
- **Bark beetles**: 32,251 ha/yr → 58,923 ± 1,599 ha/yr (RCP8.5) = +83%; extreme years every year under RCP8.5 by 2081–2100
- **Wind**: 68,537 ha/yr → 76,920 ± 2,843 ha/yr (RCP8.5) = +12%; relatively stable as extreme wind events don't change directionally but forest structure changes

**Spatial patterns:**
- Hotspots (>0.3% yr⁻¹): coastlines of Mediterranean Sea, western France, British Isles, Carpathians, southern Finland–Germany corridor
- Mediterranean biome: 89% of area shows increasing disturbance under RCP8.5
- Mediterranean warming most strongly driven by VPD and temperature increases

**Vegetation feedbacks and interactions:**
- Without vegetation feedbacks: disturbance rates would be 2.6× (RCP2.6) to 3.9× (RCP8.5) higher
- Wind–bark beetle interaction: 31% of bark beetle disturbed area attributable to preceding wind events

**Forest demography (year 2100):**
- Young forests (<10 years): +0.4% (RCP2.6) to +14.2% (RCP8.5) relative to baseline
- Old forests (>80 years, undisturbed): −0.8% (RCP2.6) to −2.9% (RCP8.5)
- Strongest effect in Mediterranean and temperate biomes

## Advantages and Limitations

**Advantages:**
- Continental coverage at 100 m resolution captures local disturbance dynamics and spatial contagion
- Disturbance interactions and vegetation feedbacks are mechanistically represented, not assumed
- 120 future trajectories (9 climate × 10 replicates) provide robust uncertainty quantification
- Open-source code and data enable reproducibility and extension

**Limitations:**
- Business-as-usual management assumption; adaptive management strategies (e.g., mixed forests, compositional shifts) are not evaluated
- Wind disturbance projections assume unchanged wind climatology — only forest structure changes drive wind disturbance change
- Only high-severity (stand-replacing) disturbances modelled; low-severity disturbances (ecologically important) are not included
- Bark beetle module focuses exclusively on *Ips typographus* in Norway spruce; other bark beetle species and hosts not considered
- Disturbance refugia identified spatially but transition dynamics (migration, colonisation) within refugia are not modelled
- Future growing season length changes (which affect disturbance susceptibility) are modelled implicitly through climate drivers but not as explicit phenological shifts

## Conclusion

Grünig et al. (2026) provide the most spatially explicit and mechanistically comprehensive projection of future European forest disturbances to date. Forest disturbances will increase under all climate scenarios, with disturbed area more than doubling under unabated warming. Wildfire is the dominant agent of future disturbance change, particularly in the Mediterranean and expanding into temperate and boreal biomes. Vegetation feedbacks substantially moderate but cannot prevent disturbance increases. The resulting demographic shift — towards younger, more open forests at the expense of old-growth — has profound consequences for carbon storage, biodiversity, and timber markets. The study represents a compelling case for integrating disturbance interactions, vegetation feedbacks, and deep learning into continental-scale forest projections, and for treating mitigating climate change as the primary lever for forest risk management.

## Related Work & Obsidian Links

- [[forest_disturbances]]
- [[landsat]]
- [[vegetation_greenness_trends]]

**Cross-paper links (same vault):**
- [[01_notes/albrich_2019_climate_change_mountain_forests]] — Albrich et al. use iLand process model for Alpine forest dynamics; Grünig et al. use SVD (trained partly on iLand-like simulations) for continental-scale disturbance projections; complementary scales and approaches
- [[01_notes/bayle_2024_landsat_greening_inflated]] — Grünig et al. use Landsat-derived disturbance time series for calibration; the observation density bias described by Bayle et al. is a potential source of calibration uncertainty in the disturbance rates used here
- [[01_notes/bricca_2026_topo_diversity]] — both papers address climate change impacts on European forests; Bricca et al. focus on biodiversity changes via temperature-diversity relationships, Grünig et al. focus on disturbance regime changes; disturbance is a key mechanism through which diversity changes occur
