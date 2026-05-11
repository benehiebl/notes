---
title: Drivers of the differentiation between broad-leaved trees and shrubs in the shift from evergreen to deciduous leaf habit in forests of eastern Asian subtropics
authors:
  - Jin, Yi
  - Qian, Hong
year: 2023
source: jin_2023_drivers_differentiation_evergreen
tags:
  - leaf-habit
  - deciduous
  - evergreen
  - latitudinal-gradient
  - plant-functional-traits
  - forest-ecology
  - canopy-microclimate
  - eastern-Asia
keywords:
  - leaf-phenology
  - growth-form
  - canopy-understory
  - MAT
  - annual-precipitation
  - forest-dynamics-plots
  - phylogenetic-conservatism
  - species-distribution-range
status: summarized
---

## Title and Authors of the Paper

*Drivers of the differentiation between broad-leaved trees and shrubs in the shift from evergreen to deciduous leaf habit in forests of eastern Asian subtropics* — Yi Jin, Hong Qian (2023), Plant Diversity, 45, 535–543. DOI: 10.1016/j.pld.2022.12.008

## Quick Overview

- **Why is it relevant?** In subtropical eastern Asian forests, leaf habit shifts from evergreen to deciduous toward higher latitudes, but whether canopy trees and understory shrubs respond differently to this climate gradient has been unknown.
- **What was done?** Modelled the proportion of deciduous broad-leaved species and species occurrence as a function of growth form (tree vs. shrub), climate (MAT, AP), and species geographical range across 10 large forest dynamics plots spanning the full subtropical latitudinal gradient in China.
- **What is the main outcome?** Trees shift leaf habit faster along the temperature gradient than shrubs, and this differentiation is strongest at low latitudes (warm climates), explained by canopy buffering of understory microclimate and species climatic niche breadth.

## Main Goal and Fundamental Concept

In the broad-leaved forests of subtropical eastern Asia, the dominance of deciduous angiosperm species increases and evergreen species decreases with latitude (temperature decrease, seasonality increase). This is driven by the advantage of deciduous leaf habit at higher latitudes where harsh winters make leaf retention costly.

**Two hypotheses tested:**
1. **H1 (canopy effect)**: Leaf habit shift is more pronounced in forest trees than in forest understory shrubs — because the forest canopy buffers the understory from climatic extremes, reducing the climate pressure on shrubs to shed leaves.
2. **H2 (latitudinal range effect)**: At higher latitudes, trees and shrubs converge in their leaf habit responses — because forest vertical structure simplifies at higher latitudes, reducing canopy buffering, and because species with wider latitudinal ranges have broader climate tolerance.

## Technical Approach

**Data:**
- 10 large-sized forest dynamics plots across subtropical eastern Asia (23°10'N–33°32'N; 108°22'E–121°47'E)
- 847 angiosperm woody species with stem diameter ≥ 1 cm at breast height; 468 trees, 379 shrubs
- Climate variables: mean annual temperature (MAT), annual precipitation (AP) — locally measured
- Species maximum distribution latitude (northern boundary of distribution range) as proxy for climatic niche breadth / cold tolerance
- Leaf habit (deciduous or evergreen broad-leaved) and growth form (tree or shrub) for each species

**Statistical models:**
- **GLS linear regression** (nlme package): proportion of deciduous broad-leaved species ~ growth form × MAT + growth form × AP + spatial autocorrelation; exponential spatial correlation structure to account for Moran's I
- **GLMM with MCMC** (MCMCglmm package; 210,000 iterations): species occurrence (binomial) ~ leaf habit × growth form × maximum distribution latitude × MAT (+ AP, plot size, interactions up to 4-way); random effects for species and plot
- Phylogenetic conservatism in leaf habit tested: Pagel's λ = 0.835 (p < 0.001) for leaf habit; λ = 0.947 for growth form; residuals of final GLMM not phylogenetically conserved (λ = 0.026) → phylogenetic control not required in final model
- Backward model selection using AICc (GLS) and DIC (GLMM)
- Variance inflation factor (VIF) screening excluded latitude and mean elevation (collinear with MAT)

## Distinctive Features

- **Growth-form-stratified analysis**: explicitly separates canopy trees from understory shrubs within the same forest plots — most macroecological leaf habit studies pool all growth forms
- **Species range as a predictor of climate sensitivity**: uses maximum distribution latitude (northern boundary) as a functional property capturing intrinsic cold tolerance — species with wide ranges are less sensitive to local MAT
- **10 large-sized forest dynamics plots**: each represents a substantial fraction of regional forest diversity, minimising sampling artefacts
- **Phylogenetic conservatism documented but not a confound**: high Pagel's λ shows leaf habit is phylogenetically structured, but model residuals are not — allowing standard mixed-model inference

## Experimental Setup and Results

**Study plots:**
- 8 plots on Eurasian continent, 2 on Taiwan; 5–50 ha each; mean plot size 24 ha
- Climate range: MAT 11.5–20.9°C, AP 908–4067 mm — covers the full subtropical deciduous/evergreen transition

**GLS results (proportion of deciduous species, plot-level):**

| Factor | Coefficient | Significance |
|--------|------------|-------------|
| Growth form (Tree) | +0.024 | — |
| MAT | −0.137 | ** |
| AP | −0.079 | * |
| Growth form (Tree) × MAT | −0.078 | *** |
| Growth form (Tree) × AP | not retained | — |

- Higher proportion of deciduous species at lower MAT (H1 confirmed: MAT effect stronger for trees than shrubs)
- Higher proportion of deciduous species at lower AP (but no tree-shrub differentiation in AP response)

**GLMM results (species occurrence, species-level):**
- Four-way interaction: leaf habit × growth form × maximum distribution latitude × MAT (retained in most supported model; Table 3)
- **Key interpretation**: at low maximum distribution latitudes (species restricted to warm subtropics), deciduous trees show much greater relative advantage over evergreen trees at low MAT compared to deciduous shrubs — i.e., tree-shrub differentiation in climate-driven leaf habit shift is largest among species with restricted southern ranges
- At high maximum distribution latitudes (species reaching northern temperate zone), the difference between trees and shrubs in leaf habit response to MAT narrows (H2 confirmed)
- Three-way interaction (leaf habit × maximum distribution latitude × AP): species at higher maximum distribution latitudes show stronger deciduous dominance with decreasing AP

**Mechanisms (Discussion):**
- **Canopy buffering**: forest canopy reduces light and moderates temperature extremes for understory shrubs → evergreen leaf habit remains viable for shrubs even under harsher regional climates (cost of evergreen leaves amortised in stable, low-resource understory)
- **Latitudinal convergence**: at higher latitudes, forest vertical structure simplifies (less foliated interior), canopy-understory environmental differences decrease → trees and shrubs experience more similar climates → leaf habit convergence
- **Climatic niche breadth**: species with wider geographic ranges (higher maximum distribution latitude) can tolerate harsher climates regardless of growth form → reduced tree-shrub differentiation
- **Precipitation mechanism**: deciduous leaf habit reduces water loss through transpiration in dry seasons, benefitting all growth forms equally; canopy does not intercept soil water, so understory shrubs experience similar soil moisture as trees

## Advantages and Limitations

**Advantages:**
- Explicitly tests growth-form stratification of climate responses in the same forest communities
- Species range as a functional predictor is ecologically motivated and novel in this context
- Large, well-documented forest dynamics plots provide high-quality floristic data across a wide climate gradient

**Limitations:**
- No direct measurements of understory microclimate — canopy buffering mechanism inferred, not measured
- Cross-sectional (spatial substitution for temporal): climate change inference requires caution
- Island plots (Taiwan) may be affected by geographic isolation altering species composition beyond climate effects
- No functional trait data (SLA, leaf longevity) to directly test the economic basis of evergreen vs. deciduous advantage

## Conclusion

Jin & Qian (2023) demonstrate that the latitudinal shift from evergreen to deciduous leaf habit in subtropical eastern Asian forests is significantly more pronounced in canopy trees than in understory shrubs. This is attributed to the forest canopy buffering the understory from climate extremes, making the evergreen leaf habit more viable for shrubs even under regionally harsher conditions. The differentiation between trees and shrubs decreases at higher latitudes as forest vertical structure simplifies and species distributions indicate broader climatic tolerance. These findings imply that global climate warming, by favouring evergreen species at higher latitudes, will differentially alter the distributions and growth form compositions of forest canopy and understory communities.

## Related Work & Obsidian Links

- [[plant_functional_traits]]
- [[leaf_habit_latitudinal_gradient]]
- [[topographic_microclimate]]
- [[phenology]]
- [[functional_diversity]]

- [[bricca_2026_topo_diversity]] — Bricca et al. (2026) demonstrate analogous canopy effects: tree guild is regulated more by solar radiation (canopy-level climate), shrub guild more by soil moisture (understory-level) in Italian forests — complementary evidence that canopy and understory experience different effective climates
- [[herraiz_2025_phen_shifts_mediterranean]] — the Mediterranean inverted phenological cycle (evergreen species maintaining greenness through winter) is precisely the leaf habit strategy Jin & Qian show is advantageous at lower latitudes / warmer climates
- [[hiebl_2025_pretraining]] — EVE (evergreen broad-leaved) species expansion documented at the Mediterranean-temperate transition in Italy; Jin & Qian provide the macroecological mechanism explaining why warming favours EVE species northward expansion

## Related pages

- [[leaf_habit_latitudinal_gradient]]
- [[topographic_microclimate]]
- [[phenology]]
- [[plant_functional_traits]]
- [[functional_diversity]]
- [[bricca_2026_topo_diversity]]
- [[herraiz_2025_phen_shifts_mediterranean]]
- [[hiebl_2025_pretraining]]
