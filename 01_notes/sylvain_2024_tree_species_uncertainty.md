---
title: High-resolution mapping of tree species and associated uncertainty by combining aerial remote sensing data and convolutional neural networks ensemble
authors:
  - Sylvain, Jean-Daniel
  - Drolet, Guillaume
  - Thiffault, Evelyne
  - Anctil, François
year: 2024
source: sylvain_2024_tree_species_uncertainty
tags:
  - tree-species-mapping
  - deep-learning
  - CNN
  - ensemble-modelling
  - uncertainty-assessment
  - LiDAR
  - Canada
  - boreal-forest
  - remote-sensing
keywords:
  - VGG16
  - ResNet50-v2
  - DenseNet-121
  - super-ensemble
  - canopy-height-model
  - agreement-map
  - forest-inventory
  - boreal-tree-species
  - aerial-photography
  - sub-meter-resolution
status: summarized
---

## Title and Authors of the Paper

*High-resolution mapping of tree species and associated uncertainty by combining aerial remote sensing data and convolutional neural networks ensemble* — Jean-Daniel Sylvain, Guillaume Drolet, Évelyne Thiffault, François Anctil (2024), International Journal of Applied Earth Observation and Geoinformation, 131, 103960. DOI: 10.1016/j.jag.2024.103960.

## Quick Overview

- **Why is it relevant?** Operational-scale sub-meter tree species mapping from airborne data at regional extent (10,000 km²) was lacking, and spatially explicit uncertainty maps — essential for operational use — had not been reliably produced from CNN ensembles for this application.
- **What was done?** Trained a super-ensemble of 9 CNN models (3 architectures × 3 training datasets) on RGBI aerial orthophotos + lidar-derived canopy height model to map 9 tree species and 4 land cover types at 0.9m resolution across 10,000 km² in Quebec; used inter-model agreement as uncertainty proxy; validated against 1,311 independent NFI plots.
- **What is the main outcome?** Super-ensemble achieves F1=0.90; CHM adds +5pp over RGBI alone; inter-model agreement is a reliable spatially explicit indicator of model performance; broadleaf species and mixed stands have higher uncertainty than coniferous and land cover classes.

## Main Goal and Fundamental Concept

Ecoforestry maps — the operational standard for forest management in Quebec — are produced by photointerpretation of 1:20,000 scale imagery. They describe dominant species per polygon but cannot resolve fine-scale spatial variation within stands, smaller features (wetlands, fire scars, edge effects), or provide uncertainty estimates. This study demonstrates an automated CNN pipeline as an alternative.

**Key innovations:**
1. **Super-ensemble of 9 CNNs** (3 architectures × 3 training datasets): model-level diversity provides free uncertainty estimates without explicit Bayesian inference
2. **Agreement map** as spatially explicit uncertainty indicator — a pixel has high uncertainty when the 9 models disagree on its class
3. **CHM integration**: lidar canopy height model stacked as a 5th channel alongside RGBI orthophotos
4. **External validation** via 1,311 independent NFI (forest inventory) plots

## Technical Approach

**Study area:**
- Western Quebec, ecological sub-region 5B (white birch fir forest); mixed and boreal forest transition; 10,000 km²
- 9 tree species: black spruce, white spruce, balsam fir, jack pine, larch (*Larix laricina*), trembling aspen, white birch, yellow birch, red maple
- 4 land cover classes: ground/low vegetation, road, water body, wetland/swamp

**Input data:**
- **RGBI orthophotos**: 2,994 digital aerial photos (Vexcel UltraCam X and Xp); 4 spectral bands (R, G, B, NIR) at 30cm → pansharpened to 30cm; panophotography June–September 2017; geometric and radiometric correction; mosaicked into 5,443 tiles (5000×5000 pixels each)
- **Canopy Height Model (CHM)**: Airborne LiDAR (Leica ALS70-HP; 1064nm; 0.5–4 pts/m²; 2017); ground/non-ground classified with lasclassify (LAStools); CHM generated at 0.3m resolution (0.1m vertical resolution)

**Training data (3 sampling approaches):**
1. **Stem database**: individual trees ≥7m, photointerpreted in 3D stereo; 1-ha polygons; 9 main species + defoliation level assessed; GPS-corrected; 30m patch per tree crown centre
2. **Stand database**: homogeneous species stands; 3m internal buffer; random sampling within buffered polygons; 30m patch
3. **Land cover database**: automatically generated from ecoforestry maps + road network (GIS); 4 additional non-tree classes
- Training: max 5,000 images/class (data augmentation to balance); total ~50,000 training, 550 validation, 550 test images per dataset
- Spatial constraint: validation/test images ≥7m from training images

**CNN architectures (3):**
- **VGG16**: simple sequential 3×3 conv + maxpool; 28.4M trainable parameters; baseline; loses high-frequency spatial detail due to pooling
- **ResNet50-V2**: residual connections (skip connections) prevent vanishing gradient in deep networks; 23.6M trainable + 45K non-trainable
- **DenseNet-121**: dense connections (each layer connected to ALL subsequent layers); maximises feature reuse; 6.97M trainable + 83.6K non-trainable; best single-architecture performance

**Super-ensemble (9 models = 3 datasets × 3 architectures):**
- Inference: sliding 31×31 pixel window (9.3m) → upsampled to 71×71 for DenseNet/ResNet; mapped at every 3rd pixel (0.9m resolution output)
- Modal vote aggregation per pixel across 9 model predictions
- Uncertainty = proportion of models predicting the minority class = 1 − (agreement %/100)

**Training details:**
- Adam optimizer; up to 150 epochs; batch size 256
- Hyperparameters optimised with Hyperband (Li et al. 2018)
- Loss: sparse categorical cross-entropy weighted by inverse class frequency (handles imbalance)
- He uniform variance weight initialisation
- Data augmentation: horizontal/vertical shift, rotation, brightness, contrast, shear
- Early stopping: validation loss decrease < 0.01 for 5 consecutive epochs

**External validation:**
- 1,311 Quebec government forest inventory plots (400 m², radius 11.28m)
- Species-specific proportion of plot basal area compared to species proportion of pixels from super-ensemble within the plot radius
- Metrics: Spearman ρ, regression slope α (y = αx + β where y=basal area proportion, x=pixel proportion)

## Key Results

**Classification accuracy (test dataset, 12-class scheme, RGBI-CHM):**

| Model | Precision | Recall | F1 |
|-------|----------|--------|-----|
| **Super-ensemble** | **0.90** | **0.90** | **0.90** |
| DenseNet-121 ensemble | 0.86 | 0.86 | 0.86 |
| VGG16 ensemble | 0.85 | 0.85 | 0.85 |
| ResNet50-v2 ensemble | 0.85 | 0.84 | 0.84 |

- Super-ensemble outperforms all individual architectures
- RGBI only (no CHM): super-ensemble F1=0.85 → **CHM adds +5pp** across all architectures
- Yellow birch merged into white birch (12→11 classes): F1 improves 0.87→0.90 for the merger classes

**Species-specific performance (RGBI-CHM super-ensemble, external validation):**
| Species | n plots | Mean cover | Slope α | Spearman ρ | Precision |
|---------|---------|-----------|---------|-----------|----------|
| Black spruce | 776 | 61% | 0.55 | 0.62 | **0.95** |
| White birch | 762 | 25% | 0.47 | 0.61 | 0.92 |
| Trembling aspen | 135 | 19% | 0.53 | 0.64 | 0.62 |
| White spruce | 653 | 6% | 0.25 | 0.31 | **0.42** |
| Jack pine | 615 | 25% | 0.81 | 0.64 | 0.55 |
| Red maple | 163 | 5% | 0.21 | 0.25 | 0.35 |
| Larch | 643 | 3% | 0.14 | 0.26 | 0.19 |

- Regression slopes < 1 for most species → super-ensemble overestimates species occurrence (compared to basal area from ground plots); expected given nadir-view vs individual tree detection
- Slope ≈ 1 for jack pine (best quantitative agreement)

**CHM effect:**
- +5–6pp across all classes uniformly when CHM is added
- Largest improvement in ground/low vegetation and balsam fir, white birch, yellow birch, red maple
- CHM reduces variance in performance across architectures — stabilises learning across diverse stand conditions
- Especially useful for differentiating low vegetation (shrubs, ericaceous plants, grasses) from trees

**Uncertainty (agreement) reliability:**
- Positive relationship between agreement % and F1-score in external validation plots (Fig. 8d)
- Plots with 10% of pixels having agreement ≤30% → F1 ≈ 0.75
- Plots with 70% of pixels having agreement ≤45% → F1 ≈ 0.68
- Geographically: higher agreement in homogeneous pure stands (large water bodies, pure conifer stands, roads); lower agreement at forest edges, mixed stands, transition zones
- Broadleaf species consistently lower agreement than coniferous — reflects real heterogeneity of mixed stands

## Comparison with Ecoforestry Map (Fig. 11)

| Aspect | Super-ensemble raster | Ecoforestry polygon map |
|--------|----------------------|------------------------|
| Resolution | 0.9m pixel | 1:20,000 polygon (min 25% BA) |
| Species detection | Per-pixel occurrence probability | Dominant species only |
| Small features | Detected (fire scars, wetlands, roads) | Often missed |
| Inside-stand variation | Captured | Not captured |
| Uncertainty | Spatially explicit agreement map | Unknown |
| Production cost | Automated; months | Manual; 10+ years for 550,000 km² |

## Advantages and Limitations

**Advantages:**
- 0.9m resolution — sub-tree-crown detail; captures heterogeneity within stands
- Spatially explicit uncertainty map (agreement) validated against independent NFI plots
- Mapping 9 species + 4 land cover types simultaneously — not just dominant species
- CHM integration provides structural context that pure spectral classification lacks
- Ensemble approach yields uncertainty estimates for free (no explicit probabilistic model needed)
- Scalable: mapping 90,000 km² (3 model architectures × 3 datasets × 10,000 km²) demonstrated operationally

**Limitations:**
- Airborne data: expensive acquisition; not freely available at national scale unlike Sentinel-2/Landsat
- Training data acquired in specific years/conditions — temporal mismatch and acquisition condition variability affects generalisation
- Nadir-view: understory trees and small-diameter stems not detectable; model detects dominant canopy species only
- Class imbalance: yellow birch, red maple poorly represented → oversampling + class weighting does not fully resolve
- ReLU activations → overconfident softmax probabilities (known issue) → agreement map used as proxy rather than direct probability
- External validation assumes basal area ≈ crown cover proportion (not strictly true)
- Limited generalisability to other regions/sensors without retraining

## Conclusion

Sylvain et al. (2024) demonstrate that a super-ensemble of 9 CNNs trained on RGBI aerial orthophotos and a lidar canopy height model achieves F1=0.90 for sub-meter tree species mapping across 10,000 km² of boreal/mixed forest in Quebec. The CHM adds +5pp improvement over spectral imagery alone by providing structural context for stand discrimination. Inter-model agreement is validated as a reliable spatially explicit uncertainty indicator — plots with higher agreement within them show systematically better F1-scores. The framework is directly applicable for operational ecoforestry mapping, with the agreement map identifying where to prioritize additional field data collection.

## Related Work & Obsidian Links

- [[tree_species_mapping]]
- [[transfer_learning_remote_sensing]]
- [[neural_network_training]]
- [[national_forest_inventory]]

**Cross-paper links (same vault):**
- [[01_notes/hiebl_2025_pretraining]] — both use deep ensemble uncertainty: Hiebl et al. use 15-head deep ensemble with epistemic/aleatoric separation on 1D Sentinel-2 time series; Sylvain et al. use 9-model super-ensemble agreement on 2D aerial image patches — complementary uncertainty approaches for different data modalities and spatial scales
- [[01_notes/grabska_2024_tree_species_map]] — both address tree species mapping from RS but at opposite ends of the scale/resolution spectrum: Grabska et al. use free 10m Sentinel-2 at national scale with RF; Sylvain et al. use 30cm airborne data at regional scale with CNN — operational trade-offs between coverage and detail
- [[01_notes/liu_2023_spectral_spatial_resolution_effect]] — Liu et al. show that too-fine spatial resolution (< 10m) degrades tree diversity mapping via spectral heterogeneity; Sylvain et al. show that sub-meter resolution (0.9m) is viable and beneficial for tree species identity mapping when combined with structural data (CHM) — the information content of very high resolution becomes usable when structural separation is added
