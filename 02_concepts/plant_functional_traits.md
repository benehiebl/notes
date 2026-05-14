---
name: plant_functional_traits
description: Plant functional traits — the major axes of plant form and function, the TRY database, and their use in biodiversity and remote sensing research
type: reference
tags:
  - forest-ecology
  - biodiversity
---

# Plant Functional Traits

**Summary**: Plant functional traits are measurable characteristics of individual plants that affect performance — growth, survival, reproduction — and capture the major axes of plant life strategies, from leaf economics to root economics to reproductive strategies.

**Sources**: [[bricca_2026_topo_diversity]], [[jin_2023_drivers_differentiation_evergreen]], [[dyderski_2025_species_shift]]

**Last updated**: 2026-05-14

---

## The Major Trait Spectra

Plant traits cluster along a small number of independent axes (Díaz et al. 2016; Carmona et al. 2021):

| Spectrum | Key Traits | Captures |
|----------|-----------|---------|
| **Plant size spectrum** | Plant height, stem diameter | Competitive height, light acquisition strategy |
| **Leaf economic spectrum (LES)** | SLA (specific leaf area), leaf N, leaf P, leaf dry matter content | Fast (acquisitive) vs slow (conservative) resource use |
| **Root economic spectrum** | Specific root length (SRL) | Soil resource uptake strategy |
| **Reproductive spectrum** | Seed mass | Dispersal vs. establishment trade-off |
| **Woody economic spectrum** | Stem specific density (SSD/wood density) | Mechanical support, carbon storage, hydraulic safety |

Categorical traits commonly used alongside these:
- **Life-history habit**: annual, biennial, perennial, geophyte, woody
- **Leaf phenology**: evergreen vs. deciduous — see [[leaf_habit_latitudinal_gradient]] for the macroecological implications of this trait

**Leaf habit economics:**
- Evergreen: low SLA, high leaf dry matter content, long leaf lifespan → conservative resource strategy; advantageous in stable, low-light understory environments
- Deciduous: high SLA, faster return on leaf investment; shed leaves to avoid freeze damage and reduce winter respiration costs
- Leaf habit is strongly phylogenetically conserved (Pagel's λ ≈ 0.84 in subtropical angiosperm communities; source: [[jin_2023_drivers_differentiation_evergreen]])
- Community-level leaf habit composition shifts latitudinally: evergreen dominates at low latitudes and warm climates; deciduous dominates at high latitudes with cold, seasonal climates

## The TRY Database

- Global plant trait database aggregating millions of trait measurements across thousands of species
- Used in Bricca et al. (2026) for tree and shrub species in Italian forests (source: [[bricca_2026_topo_diversity]])
- Coverage is uneven — rare species and below-ground traits (e.g., specific root length) often have gaps
- **GRoOT database** (Global Root Traits) complements TRY for root economic traits

## Intraspecific Trait Variation (ITV)

- Trait values vary not just between species but within species across environmental gradients
- ITV is generally smaller in magnitude than between-species variation
- Most large-scale studies (including Bricca et al. 2026) use species-level mean trait values — a simplification that ignores population-level adaptation
- ITV may be particularly relevant in heterogeneous landscapes (e.g., elevation gradients) where populations adapt to local conditions

## Functional Traits and Remote Sensing

Several plant traits can be estimated from remote sensing data:
- **SLA / leaf area index**: related to canopy reflectance in red-edge and NIR bands (Sentinel-2, hyperspectral sensors)
- **Leaf chlorophyll content**: detectable from red-edge bands
- **Leaf water content**: sensitive NIR and SWIR reflectance
- **Wood density**: indirect proxies from canopy structure metrics (LiDAR)
- Spectral variation among individuals within species is a proxy for functional variation — see [[01_notes/koch_2025_intraspecies_variation_s2]]

## Related pages

- [[functional_diversity]]
- [[leaf_habit_latitudinal_gradient]]
- [[ndvi]]
