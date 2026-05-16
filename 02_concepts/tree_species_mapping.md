---
name: tree_species_mapping
description: Methods, challenges, and best practices for mapping forest tree species from satellite remote sensing data at regional to national scales
type: reference
tags:
  - remote-sensing
  - forest-ecology
  - machine-learning
  - deep-learning
---

# Tree Species Mapping

**Summary**: Tree species mapping from satellite data involves classifying forest pixels into species or genus classes using spectral, temporal, and environmental predictors, enabling wall-to-wall coverage beyond what field inventory plot networks provide.

**Sources**: [[grabska_2024_tree_species_map]], [[chabalala_2023_dl_s2_mediterranean_fruit_trees]], [[koch_2025_intraspecies_variation_s2]], [[hemmerling_2021_forest_mapping_s2]], [[bolyn_2022_tree_species_mapping]], [[astola_2019_s2_l8_comparison]], [[pu_2021_tree_species_mapping_review]], [[wang_2022_tree_species_mapping]], [[wegler_2025_tree_species_germany]], [[wegler_2026_canopy_cover_loss]], [[adagbasa_2022_deep_learning_s2]], [[liu_2023_mapping_tree_species_diversity]], [[nguyen_2022_forest_mapping_explainable]], [[blickensdörfer_2024_tree_species]], [[kollert_2021_tree_species]], [[klehr_2025_synthetic_data]], [[yang_2020_modis_evergreen]], [[wang_2026_foundation]], [[tan_2025_deep_tree_species]]

**Last updated**: 2026-05-16

**Last updated**: 2026-05-14

---

## Why Species Maps Matter

- Forest inventory (NFI) provides species composition at plot level but not spatially continuous
- Wall-to-wall species maps enable: biodiversity modelling, biomass estimation by species, disturbance monitoring, invasive species tracking, carbon accounting
- Fine-scale species maps at national scale are now achievable with Sentinel-2 (source: [[grabska_2024_tree_species_map]])

## Key Predictor Types

| Predictor type | Examples | Contribution |
|---------------|---------|-------------|
| **Spectral (multi-season)** | Seasonal STMs from Sentinel-2; NDVI, red-edge indices | Primary species discrimination signal |
| **Temporal/phenological** | Seasonal composites (early spring, summer, autumn) | Captures species-specific phenological differences |
| **Topographic** | Elevation, slope, aspect | Explains species distribution along altitude gradients |
| **Climatic** | Temperature, precipitation (WorldClim, TerraClimate) | Explains biogeographic species limits |
| **Edaphic** | Soil type, moisture | Secondary discriminator |

In national-scale mapping for Poland, the most important variables were maximum temperature (autumn), elevation, and autumn/summer spectral bands — climate and topography dominated over soil (source: [[grabska_2024_tree_species_map]]).

## Reference Data Strategies

- **Forest inventory polygons** (e.g., Polish FDB, German NFI): management units with species share data; pure stands (≥90% species) most reliable
- **Field plots**: plot-based NFI data linked to satellite pixels
- **Photo-interpretation**: validation against very-high-resolution orthoimagery
- Sample size challenge: dominant species vastly outnumber rare species → class imbalance must be addressed

## Class Imbalance Problem

Tree species distributions are inherently imbalanced (e.g., pine covers ~59% of Polish forests). Two common strategies:
- **Proportional sampling**: sample size proportional to species area; maximises OA but rare species perform poorly
- **Disproportional sampling**: oversample rare species, undersample dominant species; improves minority class F1 at the cost of overall OA
- Poland study: proportional OA = 89.6%, disproportional OA = 84% — but disproportional better represents rare species (source: [[grabska_2024_tree_species_map]])

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
- Best metrics: Rao's Q and GLCM texture (source: [[liu_2023_spectral_spatial_resolution_effect]]); see [[spectral_diversity_biodiversity]]
- Optimal spatial resolution: 10–15m; sub-10m imagery introduces intra-crown noise that reduces inter-species separability
- Sentinel-2 at 10m with all spectral bands (esp. NIR + red-edge) achieves best accuracy (R²=0.477, RMSE=0.274 in Black Forest; source: [[liu_2023_spectral_spatial_resolution_effect]])

## Deep Learning CNN Approach (Sub-meter Airborne)

CNN super-ensemble from aerial orthophotos + lidar CHM (Sylvain et al. 2024; Quebec boreal/mixed forest, 10,000 km²):
- **Input**: 30cm RGBI aerial photos + lidar canopy height model (CHM) stacked as 5th channel; 0.9m output resolution
- **Architecture ensemble**: VGG16, ResNet50-v2, DenseNet-121 × 3 training datasets = 9 models → modal vote = super-ensemble prediction
- **Uncertainty**: inter-model agreement % per pixel — validated as reliable performance indicator against 1,311 NFI plots; higher agreement → higher F1-score
- **CHM benefit**: +5pp accuracy across all classes; reduces variance between architectures; most useful for ground/low vegetation and broadleaf species separation
- **Super-ensemble F1=0.90** (12 classes including 9 tree species + 4 land cover); individual architectures 0.84–0.86 (source: [[sylvain_2024_tree_species_uncertainty]])
- Black spruce and white birch most accurately predicted (precision > 0.90); red maple, larch, white spruce weakest (precision 0.19–0.42)
- Broadleaf mixed stands have lower agreement (more heterogeneous) than pure coniferous stands

**Sources**: [[grabska_2024_tree_species_map]], [[chabalala_2023_dl_s2_mediterranean_fruit_trees]], [[koch_2025_intraspecies_variation_s2]], [[liu_2023_spectral_spatial_resolution_effect]], [[sylvain_2024_tree_species_uncertainty]]

## National-Scale Approaches

Recent studies have achieved national-scale tree species mapping using Sentinel-2 time series:

- **Germany (Wegler et al. 2025):** 10 dominant species groups, 10 m, F1=0.89 using S2+S1+DEM; reference collected from city registers + Google Earth Pro — no restricted NFI needed (source: [[wegler_2025_tree_species_germany]])
- **Poland (Grabska 2024):** 5 species, 10 m, OA=89.6% using seasonal STMs + RF; first national product for Poland (source: [[grabska_2024_tree_species_map]])
- **Germany (Wegler et al. 2026):** Species-specific canopy cover loss 2018–2024; spruce dominated losses (51.3% of total); shows monitoring value of combining species map with disturbance product (source: [[wegler_2026_canopy_cover_loss]])

## Soft Classification for Mixed Forest Stands

When pixels contain multiple species (mixed stands), hard classification fails. Approaches:
- **Proportion mapping (UNet++):** Predict per-pixel basal area proportions summing to 1; OA_maj=0.73, R²=0.50 in Wallonia using Sentinel-2 (source: [[bolyn_2022_tree_species_mapping]])
- Training data can include mixed stands (not just pure stands) when reference is a forest parcel polygon database with species proportions

## Sensor Comparison: Sentinel-2 vs Landsat 8

For forest variable prediction in boreal Finland (source: [[astola_2019_s2_l8_comparison]]):
- Sentinel-2 outperforms Landsat 8 across all variables (stem volume, diameter, height, basal area)
- Best single predictor: red-edge band B05_RE1
- S2 advantage persists even when downsampled to 30 m — spectral richness (red-edge, SWIR) matters beyond spatial resolution

For plantation forests in northern China (source: [[wang_2022_tree_species_mapping]]):
- S2 outperforms L8 by 0.4–3.4% OA; NDTI and Tasseled Cap are most important features
- Temporal saturation: ~2 key phenological images captures most temporal signal; S2+L8 fusion adds minimal gain over S2 alone

## Dense Time Series Approach

Dense Sentinel-2 time series (5-day, gap-filled via radial basis filters) for mapping 17 species in Brandenburg, Germany (source: [[hemmerling_2021_forest_mapping_s2]]):
- Spectral time series is the **primary** explanatory source — adding environmental data or texture metrics provides minimal additional improvement
- Main species accuracy: 98.9% to 66.8%; minor species (<0.5% area) most affected by errors
- Key finding: maximising temporal coverage/density is the most impactful lever

## Explainable Deep Learning for Forest Mapping

Rule-informed CNNs that explicitly encode forest definition criteria (tree height + canopy density thresholds) match black-box CNN accuracy while providing interpretable decisions (source: [[nguyen_2022_forest_mapping_explainable]]):
- Predicts intermediate variables (tree height, canopy density) explicitly
- Correction pathway reveals annotator label inconsistencies
- Particularly valuable at alpine treeline where definition-sensitive boundaries are complex

## Mixed Forest and Rare Species Challenges

National-scale species mapping is honest only when **mixed-stand validation** is performed (source: [[blickensdörfer_2024_tree_species]]):
- Pure-stand F1 scores typically overestimate real map accuracy by 4–14 percentage points
- Pseudo-labelling extends NFI training to mixed plots while preserving label confidence
- Variable-radius NFI plots need careful pixel-plot linking via species count proportions

**DL pseudo-labeling for mixed stands** — train binary/multi-class DL on pure stands, score unlabeled mixed plots, accept labels above confidence threshold (e.g. 0.9) (source: [[tan_2025_deep_tree_species]]):
- Focuses on species pairs with large phenological contrast (evergreen vs deciduous) for reliable scores
- Pretraining (SSL via masked reconstruction on unlabeled forest pixels) + pseudo-labeling: OA 0.847, macro-F1 0.836 vs OA 0.764 without pretraining
- **Red-edge indices** (NDre1-2, NDVIre1-3) most discriminative; **January–April and October–December** (leaf-off) most diagnostic periods
- Time series length matters: accuracy grows from OA 0.496 (6–7 months) to OA 0.847 (24 months); second year adds meaningful gain before plateauing
- Validates the temporal contrastive learning assumption ([[manas_2021_seasonal_contrast]]): multi-year SITS improves species representations

**Synthetically mixed training data + ANN regression** turns the mixing problem on its head (source: [[klehr_2025_synthetic_data]]):
- Linear-mixing of pure-pixel endmembers generates a synthetic spectral library with controlled mixture fractions as labels
- Allows 9 species + "other species" with as few as **30 pure pixels per class**
- ANN regression outputs continuous per-pixel species fractions (MAE 2.76–16.05%, R² up to 0.92)
- Particularly powerful for **rare species** that NFI databases under-represent

## Mountain Forests and Cloud Cover

In Alpine terrain where cloud-free single dates are rare (source: [[kollert_2021_tree_species]]):
- Three-monthly Sentinel-2 composites + LSP metrics give 85% OA — better than 3-cloud-free-scene baseline (84.4%)
- Single-year of S2 imagery sufficient when composited well
- Patch-stratified CV essential to avoid spatial autocorrelation between train and test pixels (cf. [[spatial_proxies_random_forest]])

## Fractional Evergreen Cover

For fractional evergreen-vs-deciduous cover, classical NDVI time-series statistics deliver interpretable sub-pixel maps:
- **FEVC model**: dimidiate pixel model on intra-annual NDVI minimum (when only evergreen + soil remain)
- **CV filter**: discriminates evergreen (flat NDVI curve, low CV) from deciduous and crops
- OA > 90%, RMSE ~10% in subtropical China (source: [[yang_2020_modis_evergreen]])

## Foundation Models for Forest Mapping

AlphaEarth Foundation embeddings (source: [[brown_2025_alphaearth]]) and their integration with VHR change detection enable annual 3D forest change estimates (source: [[wang_2026_foundation]]):
- AlphaEarth + S1/S2 + GEDI → 10 m annual canopy height
- VHR Siamese change detection → annual loss masks
- Combination → forest carbon stock loss
- Hiebl et al. 2026 ([[hiebl_2026_alphaearth]]) uses TST_AEF,S2 cross-attention fusion of AEF + S2 for Italian forest type and EVE cover — 10–24× faster than S2-only with matching accuracy

## Related pages

- [[sentinel_2]]
- [[phenology]]
- [[national_forest_inventory]]
- [[functional_diversity]]
- [[plant_functional_traits]]
- [[spectral_diversity_biodiversity]]
- [[evergreen_broadleaved_expansion]]
- [[transformer_sits]]
- [[transfer_learning_remote_sensing]]
- [[deep_ensemble_uncertainty]]
