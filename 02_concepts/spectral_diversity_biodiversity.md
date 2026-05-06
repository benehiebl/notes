---
name: spectral_diversity_biodiversity
description: Spectral Variability Hypothesis (SVH) — predicting species diversity from spectral heterogeneity metrics; optimal spatial resolution; Rao's Q and GLCM texture
type: reference
tags:
  - remote-sensing
  - forest-ecology
  - biodiversity
---

# Spectral Diversity and Biodiversity

**Summary**: The Spectral Variability Hypothesis (SVH) posits that the spectral heterogeneity of a satellite image is positively related to plant species diversity, enabling direct biodiversity estimation from remote sensing without species classification.

**Sources**: [[liu_2023_spectral_spatial_resolution_effect]], [[bricca_2026_topo_diversity]], [[liu_2023_mapping_tree_species_diversity]]

**Last updated**: 2026-05-06

---

## The Spectral Variability Hypothesis (SVH)

The SVH (Palmer et al. 2002) states that spectral heterogeneity of an area — the variation in reflectance across pixels — is positively related to plant species diversity:
- More diverse plant communities produce more diverse spectral signals (different leaf chemistries, canopy structures, phenological dynamics)
- Spectral heterogeneity can therefore serve as a proxy for species diversity without requiring explicit species classification
- Confirmed for multiple ecosystems and sensors, including temperate montane forests (source: [[liu_2023_spectral_spatial_resolution_effect]])

**Caution**: the relationship is imperfect — background effects (bare soil, understory litter, rock) can inflate spectral heterogeneity without reflecting canopy diversity; Rao's Q accounts for this better than CV by weighting pairwise distances.

## SVH vs. Classification-Based Diversity Mapping

| Approach | Description | Strengths | Weaknesses |
|----------|-------------|----------|-----------|
| **Classification-based** | Map individual species → compute diversity index from species map | Provides species identity; high accuracy with sufficient training data | Requires large labelled training datasets; rare species underrepresented |
| **SVH / spectral diversity** | Predict diversity index directly from spectral heterogeneity metrics | No species labels needed; rare species contribute proportionally; scalable | Species identity unknown; sensitive to background effects; generally lower R² |

Both approaches are complementary — see [[tree_species_mapping]] for the classification paradigm.

## Spectral Heterogeneity Metrics

Seven common metrics for quantifying spectral heterogeneity in a pixel neighbourhood:

| Metric | Key property | Typical performance for TSD |
|--------|-------------|---------------------------|
| **Rao's Q** | Weighted pairwise spectral distances × pixel abundances; accounts for both abundance and dissimilarity | High; robust across sensors (r ≈ 0.46–0.53 with Shannon H') |
| **Texture (GLCM)** | 8 co-occurrence statistics (mean, variance, homogeneity, contrast, dissimilarity, entropy, 2nd moment, correlation) | High; captures spatial structure of canopy heterogeneity |
| **Coefficient of variation (CV)** | Standard deviation / mean; simple spread metric | Moderate; sensitive to outliers and background |
| **Convex hull area (CHA)** | 2D spectral space coverage area | Moderate; collapses multi-band information |
| **Convex hull volume (CHV)** | Multi-dimensional spectral volume (PCA-based) | Moderate; variable across sensors |
| **Spectral angle mapper (SAM)** | Mean angle between pixel spectra | Consistently worst; assigns equal weight to all bands including uninformative ones |
| **Spectral species diversity (SSD)** | Clustering-based; counts spectral types | Moderate; requires classification decision (cluster number) |

**Best metrics**: Rao's Q and GLCM texture — use both to avoid underestimating sensor capability (source: [[liu_2023_spectral_spatial_resolution_effect]]).

## Rao's Q as a Remote Sensing Biodiversity Metric

Rao's Quadratic Entropy applied to spectral data:
- RQ = Σᵢ Σⱼ dᵢⱼ · pᵢ · pⱼ where dᵢⱼ = spectral distance between pixels i and j; pᵢ, pⱼ = relative pixel counts
- Considers both the abundance distribution and the pairwise spectral distances between pixels in a window
- Less sensitive to outliers and background effects than CV or CHA because extreme pairs are not given disproportionate weight
- Applied as a direct biodiversity indicator at the landscape scale (Rocchini et al. 2017)
- Note: **not the same as functional Rao's QE** (which uses species traits and abundances) — but both are mathematically equivalent in structure; see [[functional_diversity]]

## Optimal Spatial Resolution for SVH-Based Mapping

A key finding from Liu et al. (2023) with broad implications:
- **Too fine resolution** (< 10m for most forest sensors): individual pixels within a single tree crown vary spectrally (sunlit/shaded foliage, bark, understory gaps) → intra-species spectral variance inflates spectral heterogeneity → overestimates diversity in homogeneous stands
- **Optimal range**: 10–15m for temperate montane forests; matches stand-level rather than individual crown variation
- **Too coarse** (30m for Landsat): pixel mixing reduces inter-species spectral variation → underestimates spectral heterogeneity
- This forms a unimodal relationship between spatial resolution and TSD prediction accuracy

**Practical implication**: Sentinel-2 at native 10m is near-optimal for SVH-based TSD mapping in temperate forests. Resampling PlanetScope (3m) to ~15m can improve rather than reduce accuracy.

## Most Important Spectral Bands for TSD

From sensor comparisons in Liu et al. (2023):
- **NIR**: consistently the most important band across all sensors; captures structural variation in canopy architecture
- **Red-edge**: critical for Sentinel-2 and RapidEye; narrow red-edge bands detect subtle chlorophyll and leaf structure differences between species
- **SWIR**: contributes to Landsat-8 and RapidEye models; less so for Sentinel-2
- **Red**: consistently low importance for TSD prediction
- **Blue, Green**: lowest importance

The advantage of Sentinel-2 over other sensors is dual: (1) three additional red-edge bands capturing inter-species biochemical variation; (2) broader NIR band and narrower visible bands providing more specific spectral sensitivity (source: [[liu_2023_spectral_spatial_resolution_effect]]).

## Phenological Timing

- October (leaf senescence) is the optimal acquisition period for temperate forest TSD mapping
- At senescence, inter-species differences in browning rate, colouration, and canopy structure are maximised
- Peak growing season (summer): high LAI and full canopy closure — canopy signatures become more homogeneous → lower inter-species separability
- Multi-temporal approach (adding multiple seasons) expected to further improve accuracy beyond single-date

## Related pages

- [[sentinel_2]]
- [[functional_diversity]]
- [[tree_species_mapping]]
- [[ndvi]]
- [[phenology]]
- [[species_distribution_models]]
