---
name: tree_species_mapping
description: Methods, challenges, and best practices for mapping forest tree species from satellite remote sensing data at regional to national scales
type: reference
---

# Tree Species Mapping

**Summary**: Tree species mapping from satellite data involves classifying forest pixels into species or genus classes using spectral, temporal, and environmental predictors, enabling wall-to-wall coverage beyond what field inventory plot networks provide.

**Sources**: grabska_2024_tree_species_map.pdf, chabalala_2023_dl_s2_mediterranean_fruit_trees.pdf, koch_2025_intraspecies_variation_s2.pdf

**Last updated**: 2026-05-05

---

## Why Species Maps Matter

- Forest inventory (NFI) provides species composition at plot level but not spatially continuous
- Wall-to-wall species maps enable: biodiversity modelling, biomass estimation by species, disturbance monitoring, invasive species tracking, carbon accounting
- Fine-scale species maps at national scale are now achievable with Sentinel-2 (source: grabska_2024_tree_species_map.pdf)

## Key Predictor Types

| Predictor type | Examples | Contribution |
|---------------|---------|-------------|
| **Spectral (multi-season)** | Seasonal STMs from Sentinel-2; NDVI, red-edge indices | Primary species discrimination signal |
| **Temporal/phenological** | Seasonal composites (early spring, summer, autumn) | Captures species-specific phenological differences |
| **Topographic** | Elevation, slope, aspect | Explains species distribution along altitude gradients |
| **Climatic** | Temperature, precipitation (WorldClim, TerraClimate) | Explains biogeographic species limits |
| **Edaphic** | Soil type, moisture | Secondary discriminator |

In national-scale mapping for Poland, the most important variables were maximum temperature (autumn), elevation, and autumn/summer spectral bands — climate and topography dominated over soil (source: grabska_2024_tree_species_map.pdf).

## Reference Data Strategies

- **Forest inventory polygons** (e.g., Polish FDB, German NFI): management units with species share data; pure stands (≥90% species) most reliable
- **Field plots**: plot-based NFI data linked to satellite pixels
- **Photo-interpretation**: validation against very-high-resolution orthoimagery
- Sample size challenge: dominant species vastly outnumber rare species → class imbalance must be addressed

## Class Imbalance Problem

Tree species distributions are inherently imbalanced (e.g., pine covers ~59% of Polish forests). Two common strategies:
- **Proportional sampling**: sample size proportional to species area; maximises OA but rare species perform poorly
- **Disproportional sampling**: oversample rare species, undersample dominant species; improves minority class F1 at the cost of overall OA
- Poland study: proportional OA = 89.6%, disproportional OA = 84% — but disproportional better represents rare species (source: grabska_2024_tree_species_map.pdf)

## Classifiers

- **Random Forest (RF)**: most commonly used for tree species classification; robust to outliers, insensitive to overfitting, handles high-dimensional feature spaces; computationally lighter than SVM or deep learning
- **Support Vector Machine (SVM)**: competitive but computationally more intensive at scale
- **Deep learning (CNN, RNN, Transformer)**: increasingly used, especially for dense time series; requires large training datasets

## Accuracy Assessment

Best practices following Olofsson et al. (2014):
- **Area-adjusted accuracy**: accounts for class imbalance in accuracy reporting
- Report producer's accuracy (PA), user's accuracy (UA), F1, and overall accuracy (OA) per class
- Use stratified random sampling of test pixels, not just proportional
- Evaluate accuracy separately for different environmental strata (e.g., overlapping vs non-overlapping satellite orbits)

Typical OA for national-scale Sentinel-2 species mapping: 80–90%

## Key Challenges at Large Scale

- **Cloud cover**: more cloud images available from longer time series; mitigated by multi-annual seasonal STMs
- **Environmental heterogeneity**: optimal spectral windows differ by region and year (phenological gradients)
- **Reference data availability**: FDB/NFI data may not cover private forests; rare species underrepresented
- **Spectrally similar species**: broadleaved species (ash, hornbeam, lime, maple) are mutually confused; conifer confusion (Douglas fir ↔ pine)
- **Stand age effects**: young stands spectrally unlike mature stands of the same species
- **Observation frequency**: accuracy varies between areas with different Sentinel-2 revisit density

## Scale-Dependent Strategies

- At **regional scale** (single Landsat/Sentinel tile): single-date or single-year composite feasible; easier to tune acquisition dates
- At **national scale**: multi-annual STMs necessary to achieve adequate observations across the whole area; GEE essential for computational feasibility
- Subdividing into smaller regions may improve accuracy at national scale

## Spectral Diversity Approach (SVH-Based)

An alternative to classification: predict species diversity indices directly from spectral heterogeneity without classifying individual species:
- Based on the **Spectral Variability Hypothesis (SVH)**: spectral variance of an image area is positively related to species diversity
- Requires no labelled training data for individual species → scales to data-poor regions
- Rare species contribute proportionally to spectral heterogeneity — avoids the underestimation problem of classification methods
- Best metrics: Rao's Q and GLCM texture (source: liu_2023_spectral_spatial_resolution_effect.pdf); see [[spectral_diversity_biodiversity]]
- Optimal spatial resolution: 10–15m; sub-10m imagery introduces intra-crown noise that reduces inter-species separability
- Sentinel-2 at 10m with all spectral bands (esp. NIR + red-edge) achieves best accuracy (R²=0.477, RMSE=0.274 in Black Forest; source: liu_2023_spectral_spatial_resolution_effect.pdf)

**Sources**: grabska_2024_tree_species_map.pdf, chabalala_2023_dl_s2_mediterranean_fruit_trees.pdf, koch_2025_intraspecies_variation_s2.pdf, liu_2023_spectral_spatial_resolution_effect.pdf

## Related pages

- [[sentinel_2]]
- [[phenology]]
- [[national_forest_inventory]]
- [[functional_diversity]]
- [[plant_functional_traits]]
- [[spectral_diversity_biodiversity]]
