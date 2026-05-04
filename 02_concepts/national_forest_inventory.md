---
name: national_forest_inventory
description: National Forest Inventories — purpose, sampling design principles, variables measured, and role as ground truth for remote sensing and forest policy
type: reference
---

# National Forest Inventory (NFI)

**Summary**: National Forest Inventories (NFIs) are systematic, large-scale sample surveys that provide authoritative statistics on the extent, structure, composition, and functions of a country's forests, serving as the primary ground truth for forest remote sensing and international reporting.

**Sources**: gasparini_2022_nfi_italy.pdf

**Last updated**: 2026-05-05

---

## Purpose

NFIs serve multiple simultaneous objectives:
- **Productive function**: estimate growing stock volume, biomass, annual increment, wood availability
- **Carbon accounting**: quantify forest carbon pools (biomass, deadwood, litter, soil) for UNFCCC/Kyoto compliance
- **Ecosystem characterisation**: biodiversity, forest health, structure, management, ownership, protective functions
- **Policy support**: national and international reporting (FAO-FRA, SoEF, CBD, SDGs)

## Sampling Design Principles

Modern NFIs (including Italy's INFC) use a **multi-phase systematic sampling** design:

- **Systematic grid**: points placed on a regular grid (e.g., 1 km × 1 km in INFC) over national territory
- **Phase 1**: photo/image interpretation — classify all grid points by land use/land cover; identify forest vs non-forest
- **Phase 2**: subset of forest points further classified (forest type, canopy cover, etc.)
- **Phase 3**: subset visited on the ground; plots measured in detail

This multi-phase approach is efficient: expensive field measurements are concentrated on confirmed forest points.

Plot designs use **concentric circular plots** of different radii for different tree size classes (e.g., large trees on a 13 m radius plot, small trees/understory on a 4 m radius plot).

## Key Variables Measured

| Domain | Examples |
|--------|---------|
| **Area** | Forest/OWL area by type, region, ownership |
| **Growing stock** | Volume by species, diameter class, forest type |
| **Biomass** | Aboveground biomass, carbon pools |
| **Deadwood** | Standing dead, lying deadwood, stumps |
| **Increment** | Annual volume and biomass increment |
| **Structure** | DBH distributions, height, age class, silvicultural system |
| **Biodiversity** | Species composition, deadwood, protected areas |
| **Health** | Damage agents, crown condition |
| **Carbon** | All five carbon pools (IPCC definition) |

## Italian NFI (INFC)

Three surveys completed:

| Inventory | Reference Year | Key Change |
|-----------|---------------|-----------|
| IFNI85 | 1985 | First Italian NFI; 3 km × 3 km grid |
| INFC2005 | 2005 | Three-phase design; FAO forest definition; carbon pools |
| INFC2015 | 2015 | Same methodology as INFC2005; +520,000 ha forest area |

INFC2015 headline results: 10,980,000 ha of forest (~37% of Italian territory); ongoing expansion into abandoned mountain/hilly agricultural land (source: gasparini_2022_nfi_italy.pdf).

## NFI and Remote Sensing

NFIs provide the ground truth that remote sensing products need to be calibrated and validated against:
- **Wall-to-wall mapping**: NFI plot data + satellite imagery used to produce spatially continuous forest attribute maps
- **Biomass estimation**: NFI-derived allometric models combined with satellite-derived canopy structure
- **Forest type mapping**: NFI species composition data used to train/validate remote sensing classifiers
- **Change detection**: NFI temporal comparisons validate satellite-derived forest loss/gain estimates

Key limitation: NFI plots are typically not publicly georeferenced — spatial linkage to satellite data requires statistical modelling rather than direct plot matching.

## International Reporting Standards

NFI data contribute to:
- **FAO Global Forest Resources Assessment (FRA)**: forest area, growing stock, biomass
- **State of Europe's Forests (SoEF)**: European-level forest monitoring
- **UNFCCC National Inventory Reports**: forest carbon accounting
- **CBD** (Convention on Biological Diversity): biodiversity indicators
- **SDGs**: Goal 15 (Life on Land)

## Related pages

- [[functional_diversity]]
- [[plant_functional_traits]]
- [[landsat]]
