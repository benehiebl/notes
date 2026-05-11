---
name: functional_diversity
description: Functional diversity metrics measuring the range and dissimilarity of plant functional traits within a community — Rao's QE, multi-FD, and distinction from taxonomic diversity
type: reference
tags:
  - forest-ecology
  - biodiversity
  - remote-sensing
---

# Functional Diversity

**Summary**: Functional diversity quantifies the range, divergence, and dissimilarity of plant functional traits within a community, capturing how ecosystems function beyond simple species counts.

**Sources**: [[bricca_2026_topo_diversity]], [[liu_2023_spectral_spatial_resolution_effect]], [[francioni_2026_canopy_closure]]

**Last updated**: 2026-05-05

---

## Taxonomic vs Functional Diversity

Two core facets of biodiversity:
- **Taxonomic diversity (TD)**: number of species (species richness); measures *who is there*
- **Functional diversity (FD)**: dissimilarity of traits among co-occurring species; measures *what they do*

These facets can be independent: adding species with similar traits increases TD without changing FD, reflecting functional redundancy. A positive TD-FD relationship (more species = more functionally distinct species) reflects low functional redundancy and high niche partitioning.

## Rao's Quadratic Entropy (QE)

The most common FD metric for community-level analyses:

FD (multi-FD) = Σᵢ Σⱼ dᵢⱼ · pᵢ · pⱼ

Where dᵢⱼ is the functional distance between species i and j (typically Gower's distance), and pᵢ, pⱼ are their relative abundances. Higher values indicate communities with more functionally dissimilar species.

**Gower's distance** is preferred because:
- Handles mixed data types (quantitative + categorical traits)
- Tolerates missing trait values
- Gives balanced weight to quantitative and categorical traits when using the updated formulation (de Bello et al. 2021)

## Functional Redundancy

- **High functional redundancy**: many species share similar traits → community function is buffered against species loss
- **Low functional redundancy**: species are functionally distinct → species loss has larger functional consequences
- Distinguishing functional redundancy from functional diversity is important for ecosystem resilience assessments

## Application in Forest Ecology

In Bricca et al. (2026), multi-FD was computed from 5 quantitative traits (plant height, SLA, seed mass, specific root length, stem specific density) + 2 categorical traits (life-history, leaf phenology) using Gower's distance at the plot level (source: [[bricca_2026_topo_diversity]]). Key findings:
- FD responses to temperature were habitat-type-specific and sometimes opposite in direction to TD responses
- Mediterranean coniferous forests showed the strongest FD response to temperature (adj. R² = 41% for trees)
- Solar radiation modulated FD in trees; soil moisture modulated FD in shrubs (source: [[bricca_2026_topo_diversity]])

Long-term forest monitoring shows that canopy closure following management abandonment reduces understory species richness — a direct link between structural functional diversity (canopy openness) and taxonomic diversity. In 31 Italian ICP Forests Level II plots over 25 years, boreal and nemoral beech/oak forests showed significant species richness declines driven primarily by increasing tree cover (source: [[francioni_2026_canopy_closure]]).

## Relationship to Remote Sensing

- Direct mapping of functional diversity from satellite data is an active research area (e.g., using hyperspectral data or multispectral proxies like [[ndvi]])
- Spectrally detectable traits (e.g., leaf chlorophyll, SLA, water content) allow partial FD estimation from EO data
- Linking ground-measured FD to spectral variation is relevant for upscaling plot-level assessments to landscape scale
- **Spectral Rao's Q** uses the same mathematical structure as functional Rao's QE but with pixel spectral distances instead of species trait distances → bridges spectral heterogeneity and functional diversity as related biodiversity facets — see [[spectral_diversity_biodiversity]]
- Confirmed in montane forests: NIR-based Rao's Q and texture metrics are the best spectral predictors of Shannon-Wiener tree species diversity (source: [[liu_2023_spectral_spatial_resolution_effect]])

**Sources**: [[bricca_2026_topo_diversity]], [[liu_2023_spectral_spatial_resolution_effect]]

## Related pages

- [[plant_functional_traits]]
- [[ndvi]]
- [[spectral_diversity_biodiversity]]
