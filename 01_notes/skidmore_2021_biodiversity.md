---
title: "Priority list of biodiversity metrics to observe from space"
authors:
  - Skidmore, Andrew K.
  - Coops, Nicholas C.
  - Neinavaz, Elnaz
  - Schaepman, Michael E.
  - Paganini, Marc
  - Kissling, W. Daniel
  - Vihervaara, Petteri
  - Darvishzadeh, Roshanak
  - Feilhauer, Hannes
  - Fernandez, Miguel
  - Fernández, Néstor
  - Gorelick, Noel
  - Rocchini, Duccio
  - Wegmann, Martin
year: 2021
source: skidmore_2021_biodiversity
tags:
  - remote-sensing
  - forest-ecology
keywords:
  - essential biodiversity variables
  - EBV
  - GEO BON
  - ecosystem structure
  - ecosystem function
  - prioritisation
  - satellite remote sensing
  - biodiversity monitoring
status: read
---

# Skidmore et al. 2021 — Priority List of Biodiversity Metrics to Observe from Space

## Title and Authors
**Priority list of biodiversity metrics to observe from space**
Andrew K. Skidmore, Nicholas C. Coops, Elnaz Neinavaz et al. (large multi-institution expert team) — *Nature Ecology & Evolution* 5: 896–906 (2021).

## Quick Overview
- **Why is it relevant?** Authoritative prioritisation of Essential Biodiversity Variables (EBVs) that can realistically be measured from space — the operational framework underlying any RS-based forest biodiversity reporting (cf. [[vihervaara_2017_ebv_remote_sensing]], [[ebv_biodiversity_monitoring]]).
- **What was done?** Expert-review process across ecologists, RS scientists, space engineers, and policy experts ranked RS-derived biodiversity products against EBV classes using four criteria: relevance, feasibility, accuracy, maturity.
- **What is the main outcome?** **Ecosystem structure and ecosystem function** EBV classes are most relevant, feasible, accurate, and mature for direct satellite monitoring; **genetic composition** cannot be measured from space; **species traits** require finer resolution still under development.

## Main Goal and Fundamental Concept
GEO BON proposed Essential Biodiversity Variables (EBVs) as a unifying framework for global biodiversity monitoring (Pereira et al. 2013, Vihervaara et al. 2017). Translating EBVs into operational satellite products is non-trivial — many EBVs do not map cleanly to satellite-observable quantities. Skidmore et al. prioritise which EBVs to target now vs which need new sensor capabilities or are not satellite-amenable at all.

## Technical Approach
- **Expert review panel** spanning four communities: ecologists, RS scientists, space engineers, policy.
- **Six EBV classes** evaluated:
  1. Genetic composition (e.g. allelic diversity)
  2. Species populations (e.g. distribution, abundance)
  3. Species traits (e.g. morphology, phenology)
  4. Community composition (e.g. taxonomic / phylogenetic diversity)
  5. Ecosystem structure (e.g. live cover fraction, canopy height)
  6. Ecosystem function (e.g. NPP, fAPAR)
- **Prioritisation criteria**:
  - Relevance — biological meaningfulness
  - Feasibility — current sensor capabilities
  - Accuracy — measurement precision
  - Maturity — readiness for operational deployment
- **Scope**: satellite Earth observation only (UAV, airborne, in-situ excluded). Synoptic regional-to-global coverage prioritised.

## Distinctive Features
- Multi-stakeholder consensus across four expert communities.
- **Four-criterion prioritisation matrix** explicitly trades off relevance vs feasibility.
- Distinguishes between products **directly measurable now** vs **achievable with planned sensors** vs **not satellite-amenable**.
- Connects RS engineering specifications (signal-to-noise, resolution) to ecological priorities.

## Key Findings

**Highest priority (operational now)**
- **Ecosystem structure**: live cover fraction, canopy height (cf. [[lang_2024_canopy_height]]), vegetation cover types — directly mapped from current satellites
- **Ecosystem function**: NPP, fAPAR, gross primary productivity, evapotranspiration — derived from MODIS/Sentinel routinely

**Medium priority (achievable but needs work)**
- **Species populations**: tropical tree species distribution feasible at coarse resolution; finer scales need VHR (cf. [[lang_2024_canopy_height]], [[brown_2025_alphaearth]])
- **Community composition**: functional diversity of forests via spectral diversity (cf. [[spectral_diversity_biodiversity]], [[liu_2023_mapping_tree_species_diversity]])

**Low priority (requires future sensors)**
- **Species traits**: morphology, leaf chemistry — needs hyperspectral or VHR not yet operational

**Not feasible from space**
- **Genetic composition**: allelic diversity, genetic structure — fundamentally not observable from satellites

## Implementation Recommendations
- Align satellite missions to deliver EBV-relevant products (e.g. CHIME hyperspectral, BIOMASS)
- Adopt **FAIR data principles** for processing chains
- Build **globally coordinated, scientifically rigorous monitoring programme**
- Combine satellite RS with in-situ observations — the two are complementary, not substitutes

## Advantages and Limitations
- **Advantages**: Authoritative consensus across communities; explicit prioritisation matrix; identifies clear satellite gaps for forthcoming missions; serves both ecologists and engineers.
- **Limitations**: Excludes UAV/airborne RS (which fills many of the species-trait gaps); expert-judgement-based scoring; published 2021 — predates AlphaEarth-style foundation models that may change feasibility ratings; species-population monitoring still aspirational for most taxa.

## Conclusion
**Ecosystem structure and ecosystem function are the most ready EBVs for satellite biodiversity monitoring** — supporting the wiki's focus on canopy cover, tree species composition, forest type, and biophysical variables. Genetic composition is fundamentally beyond satellite reach. Skidmore et al. provides the canonical reference for *which* RS biodiversity products to prioritise and *why*, with direct implications for Italian forest monitoring deliverables.

## Related pages
- [[ebv_biodiversity_monitoring]]
- [[vihervaara_2017_ebv_remote_sensing]]
- [[spectral_diversity_biodiversity]]
- [[functional_diversity]]
- [[tree_species_mapping]]
- [[plant_functional_traits]]
- [[species_distribution_models]]
- [[grantham_2020_anthropogenic_modification]]
- [[lang_2024_canopy_height]]
- [[brown_2025_alphaearth]]
- [[liu_2023_mapping_tree_species_diversity]]
- [[atzberger_2020_monitoring_forests_eu]]
