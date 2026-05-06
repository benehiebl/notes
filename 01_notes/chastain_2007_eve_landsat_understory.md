---
title: Use of Landsat ETM and Topographic Data to Characterize Evergreen Understory Communities in Appalachian Deciduous Forests
authors:
  - Chastain, Robert A. Jr.
  - Townsend, Philip A.
year: 2007
tags:
  - remote-sensing
  - forest-ecology
  - land-cover-classification
  - "#machine-learning"
keywords:
  - landsat-ETM
  - evergreen-understory
  - rhododendron-maximum
  - kalmia-latifolia
  - appalachian-forests
  - topographic-indices
  - decision-tree-classification
  - maximum-likelihood
  - terrain-moisture-index
  - winter-leaf-off-imagery
status: unread
---

## Title and Authors of the Paper

*Use of Landsat ETM and Topographic Data to Characterize Evergreen Understory Communities in Appalachian Deciduous Forests* — Robert A. Chastain Jr. and Philip A. Townsend (2007), Photogrammetric Engineering & Remote Sensing, Vol. 73, No. 5. Affiliations: Fort Lewis Directorate of Public Works; University of Wisconsin-Madison, Department of Forest Ecology and Management.

## Quick Overview

- **Why is it relevant?** Evergreen understory shrubs (*Rhododendron maximum* and *Kalmia latifolia*) are ecologically important yet spatially poorly understood in Appalachian forests, and no automated remote-sensing-based mapping method existed at the time.
- **What was done?** Spring leaf-off Landsat ETM+ imagery combined with DEM-derived topographic indices were used to classify evergreen understory communities across two physiographic provinces using supervised maximum likelihood and decision tree classifiers.
- **What is the main outcome?** Overall classification accuracies above 80% were achieved in both study areas, with the best results using Landsat-only maximum likelihood (87.1%, Ridge and Valley) and a hybrid supervised-decision tree approach with topographic data (82.9%, Allegheny Plateau).

## Main Goal and Fundamental Concept

The study aims to produce the first automated, regional-scale maps of evergreen understory communities dominated by *R. maximum* and *K. latifolia* in central Appalachian deciduous forests. The core hypothesis is that spring leaf-off Landsat imagery — acquired when the deciduous overstory canopy is bare but evergreen shrubs remain visible — can spectrally distinguish these communities from other land cover types, and that topographic indices encoding moisture and exposure gradients can further disambiguate the two dominant species, which occupy distinct topoedaphic niches (*R. maximum* in mesic valley positions, *K. latifolia* on drier upper slopes).

## Technical Approach

A 31 March 2000 Landsat ETM+ image (path 16, rows 32/33) was geometrically corrected (RMSE = 0.57 pixels) and radiometrically normalised using a statistical cosine-i topographic illumination correction. Six reflective bands were transformed into principal components (PC1–PC3, explaining >98% of variance), tasseled-cap indices (Brightness, Greenness, Wetness), NDVI, and SAVI. Topographic indices were derived from the 30-m USGS NED DEM: slope, aspect (Beers transformation), elevation, relative slope position (RSP), topographic convergence index (TCI), terrain shape index (TSI), landform index (LFI), and terrain relative moisture index (TRMI). Six classification approaches were tested in a factorial design: three classifiers (maximum likelihood, minimum distance, decision tree) × two predictor sets (Landsat only; Landsat + topography). Field validation data consisted of 213 detailed vegetation plots collected 1999–2002 across Green Ridge, Savage River, Buchanan, Potomac, and Forbes State Forests, using the Bitterlich variable plot method and differential GPS. Training data were collected at 61 (Ridge and Valley) and 74 (Allegheny Plateau) additional sites. Map accuracy was assessed using overall accuracy, user's and producer's accuracy, K-hat statistics, and McNemar's chi-square test.

## Distinctive Features

The key methodological innovation is the integration of spectrally derived leaf-off imagery with landscape-scale topographic moisture and exposure indices to exploit the contrasting topoedaphic niches of the two dominant shrub species. Using spring leaf-off timing is particularly clever — it maximises the signal from evergreen understory species while minimising confusion from the deciduous overstory. The hybrid classification approach for the Allegheny Plateau (merging maximum likelihood results with a decision tree output specifically for understory hemlock) represents a pragmatic strategy for handling rare or structurally distinct classes that are poorly served by any single method.

## Experimental Setup and Results

Two study areas were chosen for their contrasting environments: the Ridge and Valley province (warmer, drier, oak-dominated, 39°29'–39°54'N, heavily logged history) and the Allegheny Plateau (cooler, wetter, mixed mesophytic, greater conifer component). Key results:

- **Ridge and Valley:** Best result — supervised parallelepiped/maximum likelihood, Landsat only: 87.1% overall accuracy (K-hat = 0.806). Evergreen understory covered 6.1% of forested area, 96% dominated by *K. latifolia*; *R. maximum* restricted to steep stream drainages.
- **Allegheny Plateau:** Best result — hybrid merged classification (supervised + decision tree for understory hemlock), Landsat + topography: 82.9% overall accuracy (K-hat = 0.755). Evergreen understory covered 26.6% of forested area; 43% included *R. maximum*. Mid-infrared bands (ETM5, ETM7) and SAVI/NDVI were most discriminative. Topographic variables TCI and RSP effectively separated *R. maximum* (low slope positions, high wetness) from *K. latifolia* (upper slopes, drier conditions).
- Minimum distance classifiers performed significantly worse in both study areas (McNemar's test, p < 0.05).
- A 30% cover threshold was identified as a practical minimum for reliable classification.

## Advantages and Limitations

**Advantages:** Uses widely available, low-cost Landsat and USGS DEM data. Leaf-off spring imagery provides a strong phenological signal for evergreen understory detection beneath a deciduous canopy. Topographic indices add ecological interpretability and improve species-level discrimination where land-use history does not confound relationships. The approach is scalable to regional assessments across the Appalachian range.

**Limitations:** Forest canopy closure inevitably obscures the understory, causing systematic underestimation of *R. maximum* and *K. latifolia* even under ideal conditions. Mixed pixels with <30% evergreen cover are unreliably classified. Land-use history (e.g., former agricultural fields) overrides topographic predictability in some areas, limiting the value of topographic data. Confusion between *R. maximum* and hemlock communities is structurally difficult to resolve. Decision tree classifiers were naively applied (no pruning or cross-validation), likely causing overfitting and degraded performance.

## Conclusion

Chastain and Townsend (2007) demonstrate that Landsat ETM+ leaf-off imagery, combined with topographic moisture and exposure indices, can map evergreen understory shrub communities across large Appalachian forest landscapes with acceptable accuracy (>80%). The study establishes proof of concept for an automated, regionally scalable method and provides baseline area estimates for *R. maximum* and *K. latifolia* dominance in two physiographic provinces. Key lessons — the primacy of spectral mid-IR bands, the value of topographic moisture indices, and the limitations imposed by canopy closure and land-use history — remain directly relevant to contemporary understory mapping efforts using higher-resolution imagery.

## Related pages

- [[landsat]]
- [[leaf_habit_latitudinal_gradient]]
- [[topographic_microclimate]]
- [[ndvi]]
- [[hiebl_2025_pretraining]]
- [[chabalala_2023_dl_s2_mediterranean_fruit_trees]]
- [[bell_2024_hindcasting_forest_structure]]
- [[amico_2025_nfi_italy]]
