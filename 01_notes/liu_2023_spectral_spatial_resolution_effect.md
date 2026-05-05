---
title: Tree species diversity mapping from spaceborne optical images — The effects of spectral and spatial resolution
authors:
  - Liu, Xiang
  - Frey, Julian
  - Munteanu, Catalina
  - Denter, Martin
  - Koch, Barbara
year: 2023
source: liu_2023_spectral_spatial_resolution_effect
tags:
  - tree-species-diversity
  - spectral-variability-hypothesis
  - sentinel-2
  - landsat
  - spatial-resolution
  - spectral-heterogeneity
  - random-forest
  - Germany
  - Black-Forest
keywords:
  - Shannon-Wiener-diversity
  - Rao's-Q
  - texture-metrics
  - GLCM
  - sensor-comparison
  - PlanetScope
  - RapidEye
  - spectral-species-diversity
  - biodiversity-remote-sensing
status: summarized
---

## Title and Authors of the Paper

*Tree species diversity mapping from spaceborne optical images: The effects of spectral and spatial resolution* — Xiang Liu, Julian Frey, Catalina Munteanu, Martin Denter, Barbara Koch (2023/2024), Remote Sensing in Ecology and Conservation, 10(4), 463–479. DOI: 10.1002/rse2.383. Part of the ConFoBi project (Conservation of Forest Biodiversity in Multiple-Use Landscapes of Central Europe).

## Quick Overview

- **Why is it relevant?** The choice of satellite sensor (spectral and spatial resolution) significantly affects tree species diversity (TSD) mapping accuracy, but direct sensor comparisons under equal conditions were lacking, particularly for temperate montane forests.
- **What was done?** Compared Random Forest regression for Shannon-Wiener diversity across four spaceborne sensors (PlanetScope 3m, RapidEye 5m, Sentinel-2 10m, Landsat-8 30m) at multiple spatial resolutions (3–30m) using seven spectral heterogeneity metrics in the Black Forest, Germany (130 one-ha plots).
- **What is the main outcome?** Sentinel-2 at 10m achieves the highest accuracy (R²=0.477, RMSE=0.274); 10–15m is the optimal spatial resolution range; NIR and Red-edge bands are the most important spectral features; Rao's Q and texture (GLCM) metrics outperform other spectral heterogeneity metrics.

## Main Goal and Fundamental Concept

Tree species diversity is a fundamental indicator of forest ecosystem health. Two broad approaches exist for mapping TSD from satellite data:
1. **Classification-based**: classify tree species → compute diversity indices from the map (two-step; requires large labelled training data)
2. **Spectral diversity-based** (this study): directly predict TSD from spectral heterogeneity metrics, using the **Spectral Variability Hypothesis (SVH)** — spectral variance of a pixel neighbourhood is positively related to species diversity, without explicit species classification

This study uses the SVH approach because:
- No species classification training data required
- Directly scalable to large areas
- Avoids systematic underestimation of rare species

**Research questions:**
1. Which sensor provides the best TSD prediction accuracy?
2. What is the optimal spatial resolution for TSD mapping?
3. Which spectral bands are most important for TSD?
4. How do different spectral heterogeneity metrics compare?

## Technical Approach

**Study area:**
- Southern Black Forest of Baden-Württemberg, Germany; ~4000 km²; elevation 208–1493 m
- Dominant species: Norway spruce (*Picea abies*), silver fir (*Abies alba*), European beech (*Fagus sylvatica*) — coniferous and mixed forests
- 130 one-ha sample plots (100×100m) from ConFoBi project; DBH ≥ 7 cm trees inventoried; stratified by forest cover and structure

**Response variable:**
- Shannon-Wiener diversity: H' = −Σ pᵢ ln(pᵢ) where pᵢ = basal area proportion of species i

**Satellite sensors and preprocessing:**

| Sensor | Native res. | Bands | Acquisition |
|--------|------------|-------|------------|
| PlanetScope | 3 m | Blue, Green, Red, NIR | Oct 14–15, 2018 |
| RapidEye | 5 m | Blue, Green, Red, Red-edge, NIR | Oct 14–15, 2018 |
| Sentinel-2 | 10–20 m | 13 bands (B2–B12, B8A) | Oct 12, 2018 (L2A via Sen2Cor) |
| Landsat-8 | 15–30 m | 9 bands (B1–B9, excl. Cirrus) | Oct 10, 2019 (OLI Collection 2 L2) |

- October imagery chosen for leaf senescence: phenological differences between species are most pronounced at this time
- All sensors resampled to 3, 5, 10, 15, 20, 25, 30 m using nearest neighbour to isolate spatial resolution effects
- 4-band datasets (Blue, Green, Red, NIR only) created for all sensors to isolate spectral resolution effect

**Spectral heterogeneity metrics (7 types):**

| Metric | Abbreviation | Based on | Captures |
|--------|-------------|---------|---------|
| Rao's Q | RQ | All bands and VIs | Weighted pairwise spectral distances |
| Coefficient of variation | CV | Each band and VI | Spectral spread within window |
| Convex hull area | CHA | All bands | 2D spectral space coverage |
| Convex hull volume | CHV | First 3 PCs | Multi-dimensional spectral volume |
| Spectral angle mapper | SAM | All bands | Spectral angle between pixels |
| Spectral species diversity | SSD | First 3 PCs | Clustering-based spectral types |
| Texture (GLCM) | Tex1–Tex8 | Each band and VI | Spatial textural pattern (mean, var, homogeneity, contrast, dissimilarity, entropy, 2nd moment, correlation) |

Plus average (AVG) of bands and VIs as non-heterogeneity baseline.

**Modelling:**
- Random Forest regression (ntree=500, mtry 1–8 grid search)
- Feature selection: Pearson VIF pruning (r ≥ 0.8) → RF-based recursive feature elimination (RF-RFE) with 10-fold CV (3 repeats)
- Accuracy assessment: 5-fold CV repeated 10 times (R² and RMSE)
- Statistical comparison: one-way ANOVA + Tukey multiple comparison test

## Distinctive Features

- **Fairest sensor comparison to date**: all sensors resampled to identical spatial grids; 4-band versions isolate spectral resolution from spatial resolution effects; same acquisition period
- **Most comprehensive spectral heterogeneity metric comparison**: 7 metric types compared simultaneously under the same modelling framework
- **Two-way resolution analysis**: spatial resolution effect tested for each sensor independently (fine → coarse resampling); spectral resolution effect isolated via 4-band datasets
- **Autumn acquisition**: phenologically optimal — leaf senescence maximises inter-species spectral differences (confirmed by prior literature)

## Experimental Setup and Results

**Overall model performance:**

| Sensor | Best resolution | Best R² | Best RMSE |
|--------|----------------|---------|----------|
| Sentinel-2 | 10 m (all-band) | 0.477 | 0.274 |
| RapidEye | 10 m (all-band) | 0.346 | 0.303 |
| PlanetScope | 15 m (all-band) | 0.337 | 0.304 |
| Landsat-8 | 30 m (all-band) | 0.316 | 0.309 |

Best individual CV run for Sentinel-2 at 10m: R²=0.490, RMSE=0.272 (Fig. 7C).

**Spatial resolution effect:**
- Very fine resolution (3–5m for PlanetScope, 5m for RapidEye) performs worse than 10–15m
- Mechanism: at too-fine resolution, individual pixels within a single tree crown vary spectrally (sunlit vs. shaded foliage, understory, bark) → intra-species spectral variance inflates spectral heterogeneity → overestimates diversity in homogeneous stands
- Optimal: 10m for Sentinel-2 and RapidEye; 15m for PlanetScope; 30m is already too coarse for Landsat-8
- Resampling from fine to coarser resolution improved PlanetScope accuracy up to ~15m, then declined

**Spectral resolution (band number) effect:**
- Sentinel-2 all-band dataset significantly outperforms 4-band Sentinel-2 at 10m (p < 0.05)
- Sentinel-2 4-band dataset still outperforms PlanetScope and Landsat-8 at most resolutions → Sentinel-2's broader NIR and narrower RGB band widths also contribute beyond just red-edge bands
- For RapidEye and Landsat-8: all-band only marginally better than 4-band (p > 0.05) → these sensors' additional bands add less value

**Most important spectral bands:**
- **NIR**: consistently the most important across all sensors; NIR-derived texture and Rao's Q dominate best models
- **Red-edge (RE1, RNDVI)**: important for RapidEye and especially Sentinel-2; RNDVI important in RapidEye best model
- **SWIR**: contributes to Landsat-8 and RapidEye best models; less so for Sentinel-2
- **Red**: consistently low importance
- **Green, Blue**: very low importance

**Spectral heterogeneity metric performance:**
- **Texture (GLCM)** and **Rao's Q**: highest and most consistent correlation with H' across all sensors and resolutions (r ≈ 0.48–0.55 for Sentinel-2)
- **CV**: moderate; fluctuates across sensors (r ≈ 0.15–0.39)
- **CHA, CHV**: moderate for some sensors, poor for Landsat-8
- **SAM**: consistently worst (r ≈ 0.01–0.24); assigns equal weight to all bands, many non-informative bands dilute signal
- **SSD**: moderate to good
- **AVG (non-heterogeneity baseline)**: r ≈ 0.30–0.35 — confirms spectral heterogeneity adds value beyond band means

**Landscape patterns:**
- All sensors agree: low TSD in central high-altitude areas and high diversity in surrounding lowlands; higher diversity in broad-leaved and mixed forests vs. coniferous
- Systematic bias: all models overestimate low TSD and underestimate high TSD (regression dilution toward the mean)
- Predictions consistent across sensors: CV of predicted values < 10% in most areas; largest differences in central high-altitude and SW mixed forest zones

## Advantages and Limitations

**Advantages:**
- SVH approach avoids classification training data requirements → applicable to data-poor regions
- Spectral diversity approach better captures rare species contributions than classification (which understimates rare species due to training data imbalance)
- Sentinel-2 at 10m is already freely available globally → directly operational for large-scale TSD monitoring

**Limitations:**
- Single-date imagery: multi-temporal approach could improve accuracy (multi-season phenological variation distinguishes species better)
- Background effects (bare soil, understory) can inflate spectral heterogeneity without reflecting tree species diversity → particularly problematic for very high spatial resolution imagery
- No elevation/topographic predictors included — forest type and altitude influence TSD and might improve models
- Sample plots (130) relatively small for modelling high-TSD forests; model saturates for very high TSD values
- Shannon diversity is one of several diversity metrics; results may differ for richness (species count) or evenness separately

## Conclusion

Liu et al. (2023) demonstrate that Sentinel-2 at 10m resolution, using all spectral bands including red-edge, achieves the highest accuracy for TSD mapping in temperate montane forests using the Spectral Variability Hypothesis approach. The finding that an intermediate spatial resolution (10–15m) is optimal — rather than the finest available — is key: sub-10m imagery introduces intra-crown spectral noise that dilutes inter-species spectral differences. Among spectral heterogeneity metrics, Rao's Q and texture (GLCM) are the most robust predictors of Shannon diversity, confirming the SVH across multiple sensors. The study provides strong operational evidence that spaceborne optical imagery, particularly free Sentinel-2 data, can support continuous, large-scale TSD monitoring.

## Related Work & Obsidian Links

- [[spectral_diversity_biodiversity]]
- [[sentinel_2]]
- [[tree_species_mapping]]
- [[functional_diversity]]
- [[ndvi]]

**Cross-paper links (same vault):**
- [[01_notes/grabska_2024_tree_species_map]] — complementary approach: Grabska et al. use classification-based (RF + seasonal STMs) approach to map individual species at national scale; Liu et al. use the SVH approach (no species classification needed); together they cover both major paradigms for tree diversity RS
- [[01_notes/bricca_2026_topo_diversity]] — both study TSD/FD in temperate forest; Bricca et al. use field-measured trait data; Liu et al. use spectral heterogeneity as a proxy; the spectral-functional diversity link is the bridge between these approaches
- [[01_notes/hiebl_2025_pretraining]] — both evaluate Sentinel-2 for forest vegetation mapping; Hiebl et al. use 1D time series regression; Liu et al. use single-date spatial heterogeneity; together they show two complementary Sentinel-2 strategies
- [[01_notes/koch_2025_intraspecies_variation_s2]] — Koch et al. document intraspecific spectral variation in Sentinel-2, which is the source of noise at very high spatial resolution identified by Liu et al. as inflating intra-species variance and reducing TSD prediction accuracy
