---
title: Advancing forest mapping — Pretraining strategies and deep-ensemble based uncertainty for predicting evergreen broad-leaved cover from Sentinel-2 time series
authors:
  - Hiebl, Benedikt
  - Alessi, Nicola
  - Calvia, Giacomo
  - Bricca, Alessandro
  - Bonari, Gianmaria
  - Zangari, Giulio
  - Dorigo, Wouter
  - Zerbe, Stefan
  - Rutzinger, Martin
year: 2025
source: hiebl_2025_pretraining
tags:
  - deep-learning
  - remote-sensing
  - sentinel-2
  - transfer-learning
  - uncertainty-quantification
  - forest-ecology
  - Italy
  - evergreen-broadleaved
keywords:
  - InceptionTime
  - pretraining
  - masked-value-prediction
  - epistemic-uncertainty
  - aleatoric-uncertainty
  - EVE-cover
  - spectral-temporal-metrics
  - vegetation-plot-observations
  - out-of-distribution
  - probabilistic-CNN
  - forest-vegetation-database
status: summarized
---

## Title and Authors of the Paper

*Advancing forest mapping: Pretraining strategies and deep-ensemble based uncertainty for predicting evergreen broad-leaved cover from Sentinel-2 time series* — Benedikt Hiebl, Nicola Alessi, Giacomo Calvia, Alessandro Bricca, Gianmaria Bonari, Giulio Zangari, Wouter Dorigo, Stefan Zerbe, Martin Rutzinger (2025), International Journal of Applied Earth Observation and Geoinformation, 142, 104734. DOI: 10.1016/j.jag.2025.104734. Code: git.uibk.ac.at/c7161037/traceve_pretraining. Data: doi.org/10.5281/zenodo.15000771.

## Quick Overview

- **Why is it relevant?** Mapping evergreen broad-leaved (EVE) species cover in mixed temperate-Mediterranean forests is ecologically critical but challenged by limited field training data — pretraining deep learning models on larger, contextually similar datasets is a practical solution that has been underexplored for 1D spectral-temporal time series regression tasks.
- **What was done?** Three pretraining strategies (direct training, supervised contextual pretraining, self-supervised masked value prediction) were evaluated for a probabilistic InceptionTime CNN mapping EVE cover from Sentinel-2 annual time series across 5 Italian National Parks, with deep-ensemble uncertainty quantification to improve interpretability and detect out-of-distribution inputs.
- **What is the main outcome?** Supervised contextual pretraining on a large diverse forest vegetation database (mVDB_cover, mVDB_ftype) significantly outperforms direct training on small in-situ data; epistemic uncertainty effectively identifies unreliable predictions in OOD regions; taxonomic diversity of vegetation is the strongest driver of prediction error.

## Main Goal and Fundamental Concept

EVE species (*Quercus ilex*, *Olea europaea*, and related shrubs) are expanding at the transition zone between Mediterranean and temperate forests in Italy due to climate change and land abandonment. Monitoring these shifts requires spatially continuous cover maps from satellite data. The key problem: deep learning models for vegetation analysis require substantial labeled training data, but high-quality in-situ EVE plot observations are scarce (only 360 sites in this study, after careful spatial clustering to avoid autocorrelation).

Three strategies to address the **small data problem**:
1. **Direct training** (baseline): train only on available field data
2. **Supervised pretraining** (transfer learning): pretrain on a larger, structurally related dataset before fine-tuning on target data
3. **Self-supervised pretraining**: learn general spectral-temporal representations from unlabeled satellite data using Masked Value Prediction (MVP)

Additionally, **uncertainty quantification** addresses a second problem: how to distinguish confident predictions (reliable areas) from uncertain ones (OOD inputs, data gaps, rare forest types).

## Technical Approach

**Datasets:**
- **VPO2024** (target): 360 site-level vegetation plot observations, 5 Italian National Parks (SIB, GRA, GEN, CIL, NEB); each site = 4 systematic 100 m² plots; EVE cover estimated in 3 vertical layers (0–1 m, 1–10 m, 10–max); final 1440 plots. Spatially clustered into 20 k-means clusters (4 per park) to mitigate spatial autocorrelation
- **VDB** (pretraining): Italian Forest Vegetation Database — 16,908 plot observations from diverse studies across Italy (1972–2017); classified into forest types (EUNIS) and contains EVE cover estimates; 33,649 data points after annual splitting; represents diverse Italian forest spectral-temporal space
- **UPD** (self-supervised): 100,000 points randomly sampled across Italian forested areas (from Copernicus FTY forest mask), stratified by 30 k-means clusters on 2023 Sentinel-2 summer means and latitude

**Input features** (final set after VIF selection):
- 7 Sentinel-2 L2A bands: B02 (Blue), B03 (Green), B04 (Red), B05 (RE1), B07 (RE3), B11 (SWIR1), B12 (SWIR2)
- 4 vegetation indices: NDVI, NDMI (Normalized Difference Moisture Index), SAVI, NIRv (Near-Infrared Reflectance of Vegetation)
- Sentinel-2 time series 01.01.2017 – 31.12.2023; SCL-masked; aggregated to synthetic annual year; resampled to 3-day intervals; IQR outlier removal + Whittaker smoothing; normalised per band using 2nd and 95th percentiles
- Processed on Microsoft Planetary Computer Hub

**Model architecture (probabilistic InceptionTime CNN):**
- Modified InceptionTime: 4 convolutional inception blocks (CIB), 64 filters, 1D temporal convolutions applied independently per spectral band then jointly
- CIB applies temporal filters at multiple scales → learns spectral-temporal patterns at different temporal resolutions
- After shared backbone: ensemble of 15 independently initialized fully-connected heads
- **Aleatoric uncertainty (AU)**: separate CIB + head pair predicts per-pixel observation variance σ²(x) — captures label noise and inherent ambiguity
- **Epistemic uncertainty (EU)**: variance across 15 ensemble head predictions — captures model/data uncertainty (OOD detection)
- Loss: Gaussian Negative Log-Likelihood (NLL): ℒ_NLL = ½ log(σ²(x)) + (y − μ(x))² / (2σ²(x))
- Implemented in PyTorch

**Six models compared:**
| Model | Training strategy |
|-------|-----------------|
| mVPO2024 | Direct fine-tuning on VPO2024 (random split) |
| mVPO2024_r | Direct fine-tuning on VPO2024 (spatial/cluster split) |
| rfVPO2024 | Random Forest baseline (1D flattened features) |
| mVDB_ftype | Supervised pretraining on VDB for forest type classification → fine-tune on VPO2024 |
| mVDB_cover | Supervised pretraining on VDB for EVE cover regression → fine-tune on VPO2024 |
| mUPD | Self-supervised MVP pretraining on 100k unlabeled points → fine-tune on VPO2024 |

**Masked Value Prediction (MVP) for self-supervised pretraining:**
- Data corruption: set 16% of the year (mean window) and 25% total of STS to Nodata
- Model learns to reconstruct the full phenological curve from partially observed data
- Particularly useful for learning robust representations despite cloud/snow gaps
- MVP decoder: simple MLP outputting reconstructed time series
- CIB encoder frozen during fine-tuning to preserve learned features

**Cross-validation:**
- Spatial 5-fold leave-one-park-out CV: 4 parks training, 1 park testing
- Error metrics: MAE and RMSE of predicted vs true EVE cover
- OOD evaluation: 500 VDB samples per forest class (Mediterranean, submediterranean, temperate broadleaved, temperate needle-leaved, Mediterranean needle-leaved, boreal) tested on each model

## Distinctive Features

- **First study combining supervised TL, in-situ plot observations, and 1D TSER for EVE cover** in ecosystems where EVEs are non-dominant mixed species — previous TL studies used image patches or focused on simpler targets
- **Separated epistemic and aleatoric uncertainty**: most RS uncertainty studies conflate these; their disentanglement enables different interpretations (EU for OOD detection, AU for label noise)
- **Spatial cluster-based train/validation split**: counters spatial autocorrelation which inflates validation performance in standard random splits
- **Saliency maps via input × gradient**: reveals that pretrained model (mVDB_ftype) learns more temporally coherent phenological patterns than non-pretrained model — providing mechanistic insight into why pretraining works

## Experimental Setup and Results

**Study areas:**
- **SIB** (Sibillini, Central Apennines, 350–2912 m): temperate beech (*Fagus sylvatica*) dominant; low EVE
- **GRA** (Gran Sasso, Central Apennines): similar to SIB; low EVE
- **GEN** (Gennargentu, Sardinia, 0–1834 m): Mediterranean holm oak (*Quercus ilex*) dominant; high EVE
- **CIL** (Cilento, southern Apennines): most diverse — Mediterranean + sub-Mediterranean beech; highest errors across all models
- **NEB** (Nebrodi, Sicily): mixed Mediterranean/temperate at varying elevations; mixed EVE/deciduous

**Accuracy results (MAE, %_cover):**
| Model | Mean MAE | Rank |
|-------|---------|------|
| mVDB_cover | **12.80 ± 3.29** | 1 (best) |
| mVDB_ftype | 13.53 ± 3.11 | 2 |
| mUPD | 16.33 ± 2.68 | 4 |
| mVPO2024 | 15.46 ± 3.30 | 3 |
| mVPO2024_r | 18.55 ± 2.28 | 6 |
| rfVPO2024 | 18.32 ± 1.43 | 5 |

- Friedman test: p = 0.003 (statistically significant)
- Three performance groups (Wilcoxon + Holm): (mVDB_cover, mVDB_ftype) > (mUPD, mVPO2024) > (rfVPO2024, mVPO2024_r)
- mVPO2024_r higher RMSE than mVPO2024 despite being more generalisation-honest
- CIL consistently highest errors across all models (taxonomic diversity drives uncertainty)
- GEN, GRA: lower errors — more homogeneous, predictable spectral-temporal characteristics

**Error source analysis (Pearson correlation to RMSE):**
- γ-diversity (Shannon-Index): r = 0.88 (strongest)
- β-diversity (Jensen-Shannon Divergence): r = 0.91
- Feature space distance (PCA_all): r = 0.47
- Feature space distance (PCA_val): r = 0.36
- Topographic factors (slope, TRI): very low (< 0.20)

**Uncertainty results:**
- EU effectively flags: non-forested areas, shaded north-facing slopes, underrepresented forest types (coniferous stands)
- Coniferous stands show highest EU across all models — correctly flagged as OOD
- AU spatially non-coherent — captures label noise, not spatial patterns
- 92% of valid pixels: inter-model agreement within ±15% std; only 2% show std < 5%

**Saliency maps:**
- Both models attribute high importance to NDVI during leaf-off and senescence phases → EVE detection relies on evergreen winter signal
- Pretrained mVDB_ftype: cleaner, more pronounced seasonal patterns → better phenological feature learning from larger, diverse pretraining data
- NDMI: negative attribution during growing season → water stress signal discriminates EVE from non-EVE

## Advantages and Limitations

**Advantages:**
- Supervised contextual pretraining with task similarity provides the largest and most consistent accuracy improvement
- EU-guided sampling strategy (active learning) could substantially reduce future field data needs
- Disentangled uncertainty enables targeted map quality assessment
- Spatially clustered validation provides more realistic generalization estimates

**Limitations:**
- mUPD (self-supervised) did not learn features transferable to EVE cover prediction — possibly because feature masking during MVP does not align well with fine-tuning task; CIB freezing prevents adaptation
- All models overestimate EVE cover in coniferous OOD areas — EU flags this but does not correct it
- CIL region remains challenging for all models due to high within-park taxonomic diversity — a fundamental limit beyond model improvements
- Spatial k-means clustering mitigates but does not eliminate spatial autocorrelation in small sparse datasets
- mVDB_cover pretraining benefit assumed based on task similarity — further investigation of pretraining dataset composition needed

## Conclusion

Hiebl et al. (2025) demonstrate that supervised contextual pretraining on a large, diverse forest vegetation database substantially improves EVE cover prediction from Sentinel-2 1D time series in Italian mixed forests, particularly for generalisation to new regions. The key finding is that task similarity between pretraining and fine-tuning objectives matters: pretraining for EVE cover regression (mVDB_cover) outperforms pretraining for forest type classification (mVDB_ftype), which outperforms self-supervised MVP pretraining. Deep ensemble uncertainty quantification successfully identifies OOD forest types and data quality issues, providing spatially explicit prediction confidence that can guide both map interpretation and future field data collection. Taxonomic vegetation diversity is the dominant bottleneck for prediction accuracy — a challenge that pretraining alone cannot fully solve.

## Related Work & Obsidian Links

- [[transfer_learning_remote_sensing]]
- [[sentinel_2]]
- [[tree_species_mapping]]
- [[phenology]]
- [[national_forest_inventory]]

**Cross-paper links (same vault):**
- [[01_notes/bricca_2026_topo_diversity]] — Bricca et al. use the Italian Forest Database (IFD/VDB) for functional diversity analyses; Hiebl et al. use the same database (VDB) for pretraining — same ground truth infrastructure applied to different ecological questions
- [[01_notes/grabska_2024_tree_species_map]] — both address species-level forest classification from Sentinel-2 time series; Grabska et al. use Random Forest with seasonal STMs at national scale; Hiebl et al. use probabilistic 1D CNN with pretraining at regional scale with small data
- [[01_notes/chabalala_2023_dl_s2_mediterranean_fruit_trees]] — both apply DL to Sentinel-2 time series for vegetation species mapping; complementary approaches (Chabalala: classification; Hiebl et al.: continuous cover regression with uncertainty)
- [[01_notes/herraiz_2025_phen_shifts_mediterranean]] — the phenological dynamics of evergreen Mediterranean species described by Herraiz et al. explain *why* leaf-off and senescence windows are most important in the saliency maps found here
- [[01_notes/gasparini_2022_nfi_italy]] — Italian NFI (INFC) provides the forest area and species composition context within which EVE mapping is situated; the VDB used for pretraining draws on the same Italian forest plot infrastructure
