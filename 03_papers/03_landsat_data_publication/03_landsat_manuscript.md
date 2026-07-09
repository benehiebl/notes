---
title: "A 40-year annual time series of forest type and leaf type cover for Italy derived from Landsat using deep learning"
author:
  - name: Benedikt Hiebl
    affiliation: "University of Innsbruck"
    email: "Benedikt.Hiebl@uibk.ac.at"
date: "2026"
abstract: |
  Consistent long-term maps of forest functional type and dominant tree species cover at high spatial resolution are currently unavailable for Italy. We present an annual 30 m resolution map time series spanning 1985–2025, derived from the full Landsat Collection 2 archive (Landsat 4/5/7/8/9) using a multi-task Time Series Transformer (TSTpad) model. The model is trained via a three-stage workflow combining contrastive pretraining with supervised fine-tuning on multi-source Italian forest plot observations. The dataset provides continuous-cover fractions for evergreen broad-leaved, deciduous, and coniferous leaf types (EVE, DEC, CON) and class probabilities for eleven dominant tree species for all forested pixels across Italy. Pixel-level uncertainty estimates are provided as the inter-seed standard deviation of a seven-seed deep ensemble. A three-year observation pooling strategy is applied to increase cloud-free coverage, particularly for the observation-sparse pre-1999 period (Landsat 5 only). The 40-year time series enables historical reconstruction of forest composition dynamics, disturbance impact assessment, and long-term ecological change detection at national scale. All data, model weights, and training code are made publicly available.
geometry: margin=2.5cm
fontsize: 12pt
linestretch: 1.5
numbersections: true
---

# Introduction

## Landsat for forest monitoring: advantages and challenges

With nearly 40 years of continuous acquisitions, the Landsat archive constitutes the longest consistent Earth observation record available for global vegetation monitoring. Its multi-decadal continuity makes it uniquely suited for change detection, historical reconstruction, and hindcasting of environmental variables including forest structural attributes (Bell et al., 2024; Turubanova et al., 2023). The archive has been applied to discriminate forest types and quantify forest parameters such as canopy height at regional and continental scales (Pflugmacher et al., 2019; Turubanova et al., 2023). The relatively slow succession dynamics of forest vegetation — unfolding over decades — make this multi-decadal temporal depth particularly valuable; shorter observation windows would fail to capture gradual stand-level transitions such as species shifts or forest densification (Tong et al., 2023; Midolo et al., 2026). The medium spectral, spatial, and temporal resolution of Landsat — six surface reflectance bands, 30 m pixel spacing, and an 8–16 day revisit cycle — is adequate for capturing annual phenological dynamics at stand level, a characteristic demonstrated to be critical for distinguishing tree species and functional leaf types (Kollert et al., 2021; Hemmerling et al., 2021; Wang et al., 2022).

Despite these strengths, the use of multi-decadal Landsat data for vegetation mapping raises several methodological challenges. The number of usable cloud-free observations per pixel has increased substantially since the early archive period, driven by the successive addition of new Landsat satellites, the adoption of the Landsat open data policy in 2008, and improved cloud detection algorithms. This systematic increase in observation density has been shown to cause spurious apparent trends in annual maximum NDVI (NDVImax), with up to 50% of observed Landsat-based greening in alpine environments attributable to observational sampling bias rather than true vegetation change (Bayle et al., 2024). A second challenge arises from the failure of the Scan Line Corrector (SLC-off) on Landsat 7 ETM+, which introduces systematic data gaps. Finally, spectral radiometric differences between sensors — arising from different detectors, band widths, and calibration procedures across Landsat 4, 5, 7, 8, and 9 — introduce inter-sensor discontinuities that may produce spurious apparent changes in modelled biophysical variables across the 40-year record if not explicitly addressed.

## Deep learning for dominant tree species and leaf type cover mapping

Multitemporal satellite data consistently outperform single-date or mosaic-based approaches for tree species and leaf type mapping. Phenologically informative seasons — particularly leaf-off periods and autumn senescence — contribute disproportionately to species discrimination (Kollert et al., 2021; Tan et al., 2025). When sufficient temporal coverage is available, dense time series exploiting the full phenological cycle can outperform the inclusion of additional environmental predictor variables such as topography or climate indices (Hemmerling et al., 2021). These findings highlight temporal resolution and coverage as primary levers for improving species-level classification accuracy.

Deep learning, and in particular Transformer-based architectures, provides a natural framework for integrating irregular, multi-band satellite image time series (SITS). Transformers process sequences of observations without requiring interpolation to a regular grid, an essential property for long Landsat archives with strongly varying observation density across decades and sensor platforms (Zerveas et al., 2020; Yuan et al., 2022a). Self-supervised pretraining on large unlabelled SITS datasets has been shown to improve representation quality and downstream task performance, particularly in data-scarce settings (Yuan et al., 2022b; Hiebl et al., 2025). Contrastive learning approaches exploit temporal and seasonal variability as a self-supervisory signal by training representations to be invariant across different observation windows of the same location — a property directly suited to stable land cover types such as forest stands (Mañas et al., 2021; Chen et al., 2020). Providing calibrated uncertainty estimates alongside predictions has emerged as an important requirement for ecological mapping applications; deep ensembles of independently trained networks deliver well-calibrated epistemic uncertainty that reliably identifies out-of-distribution inputs and unreliable predictions in novel environmental contexts (Sylvain et al., 2024; Hiebl et al., 2025).

Mixed forest stands pose a fundamental challenge for both data collection and modelling. Standard forest inventory classifications assign a single dominant species per polygon, imposing a hard label on pixels that in reality contain mixtures of several species. Using species proportions from inventory data as soft regression targets rather than hard dominant-species labels has been shown to improve model performance for mixed stands and to better reflect the continuous nature of forest composition (Ball et al., 2026; Tan et al., 2025). The scarcity of high-quality spatially explicit reference data with sufficient temporal depth remains a persistent bottleneck for large-area forest mapping from satellite data (Safonova et al., 2023). Geospatial foundation model embeddings such as AlphaEarth (Brown et al., 2025) and Tessera (Feng et al., 2026) have been shown to reach near-asymptotic species classification accuracy with as little as 5% of the total training data, substantially reducing the dependency on large labelled datasets (Ball et al., 2026; Hiebl et al., 2026).

## Need for a long-term Italian forest type dataset

Italian forests are undergoing rapid and spatially complex changes. The Italian National Forest Inventory (INFC2015) documents a continuing expansion of forested area — from approximately 10.46 million ha in INFC2005 to 10.98 million ha in INFC2015 — driven primarily by land abandonment in mountain and hill zones and targeted reforestation programmes (Gasparini et al., 2022). These expansion processes are spatially heterogeneous, reflecting regional variation in land use history, climate, and species composition. Despite this dynamic context, spatially explicit maps of forest composition in Italy remain restricted to static snapshots. The most recent national reference product, the Carta Forestale d'Italia 2020 (CFI2020), provides a single-epoch wall-to-wall forest map at 1:10,000 scale based on photointerpretation of aerial orthophotos, but does not capture interannual dynamics or historical trajectories (Mattioli et al., 2025).

Nation-wide annual maps of forest functional type and dominant species at 30 m resolution covering the full Landsat record do not currently exist for Italy. The absence of such a dataset limits the capacity to detect and attribute forest change, to assess disturbance impacts on composition, and to study climate-driven species range shifts at national scale. The European Forest Disturbance Atlas documents that 22% of Italian forest area was affected by disturbance events between 1985 and 2023 (Viana-Soto and Senf, 2025), yet the compositional consequences of these disturbances cannot be tracked without temporally resolved species or functional type maps. The dataset presented here is designed to fill this gap and to serve as a foundation for downstream ecological, carbon cycle, and biodiversity analyses.

## Justification of the methodological approach

The core methodological choices in this work — contrastive pretraining, three-year observation pooling, sensor platform embedding, and deep ensemble uncertainty — are each motivated by specific characteristics of the problem.

The observation-density drift in the Landsat archive (Bayle et al., 2024) poses a fundamental risk for temporal stability of predictions: a supervised-only model may learn features that are confounded by observation frequency, producing apparent trends that reflect data availability rather than ecological change. Contrastive pretraining, applied to pairs of observations from two independently sampled three-year windows of the same forest plot, forces the backbone to learn representations that are invariant to the year of observation (Chen et al., 2020; Mañas et al., 2021). This temporal invariance is justified by the assumption that mature forest stands are ecologically stable over multi-year periods — an assumption supported by the slow-change dynamics documented in the literature (Hemmerling et al., 2021; Pflugmacher et al., 2019; Grabska-Szwagrzyk et al., 2024). The contrastive backbone is subsequently fine-tuned on a combination of pseudo-labels derived from AlphaEarth embeddings (Brown et al., 2025; Hiebl et al., 2026) and on historical and recent Italian forest plot observations, following the pretraining-then-fine-tuning paradigm demonstrated to be effective under limited label availability (Hiebl et al., 2025; Safonova et al., 2023).

The three-year observation pooling strategy — concatenating observations from the target year and the two preceding years — directly addresses the sparse observation problem in the pre-1999 single-sensor (Landsat 5 only) archive period and in cloud-prone mountain areas. By pooling three years of acquisitions, the number of cloud-free observations per effective time series is substantially increased, while future-leakage is avoided by restricting the window to years at or before the target year. Multi-year pooling has been shown to stabilise spectral-temporal metrics for stable land cover types and to reduce the influence of individual anomalous years (Pflugmacher et al., 2019; Grabska-Szwagrzyk et al., 2024), with particular benefit for pre-1999 archive periods that are most severely affected by the observation-density bias identified by Bayle et al. (2024).

A learned sensor platform embedding (encoding which Landsat satellites contributed each observation) is incorporated into the Transformer's positional encoding to make the model explicitly aware of inter-sensor radiometric differences. This addresses the radiometric discontinuities between Landsat 4/5 TM, Landsat 7 ETM+, Landsat 8 OLI/TIRS, and Landsat 9 OLI-2/TIRS-2 without requiring the complete removal of any sensor generation from the analysis. Finally, the seven-seed deep ensemble provides pixel-level uncertainty estimates that enable users to identify and discard unreliable predictions in regions of low observation density or unusual spectral composition, following the approach established for Sentinel-2-based forest mapping by Sylvain et al. (2024) and Hiebl et al. (2025).

---

# Methods

## Data

### CFI forest inventory data

The Carta Forestale d'Italia 2020 (CFI2020) is the first national forest map of Italy produced at operational scale (1:10,000), based on photointerpretation of AGEA aerial orthophotos from 2018 to 2020 against three simultaneously applied forest definitions (Mattioli et al., 2025). The CFI2020 delineates forested areas across all 21 Italian regions and provides stand-level attributes including forest category, silvicultural system, and dominant tree species group. In this study, the CFI2020 polygon layer serves two roles: (i) as the primary forest extent mask defining the spatial domain within which annual predictions are made, and (ii) as a source of decision rules for cleaning the artificial leaf type cover training dataset (see Section 2.1.4). Specifically, CFI2020 species attribution is used to impose ecologically plausible constraints on predicted cover fractions — for example, requiring that pixels mapped as *Pinus*-dominated stands contain at least 60% coniferous cover and fewer than 30% broad-leaved evergreen cover. The CFI2020 mask is applied in combination with a minimum canopy height threshold (≥5 m from Turubanova et al., 2023) to exclude non-forest land cover and recently disturbed open-canopy pixels from the prediction domain.

### Italian forest vegetation plot databases (VDBI)

The Italian Forest Vegetation Database (VDBI; also referred to as VDB) is a compilation of over 16,000 phytosociological and vegetation relevé plot observations collected across Italy from the 1970s to the present. Each plot record contains species composition data, structural attributes, and cover estimates by vertical layer for both the tree and shrub strata. The VDBI covers the full range of Italian forest types from Mediterranean macchia to subalpine conifer belts and provides temporal depth extending back to approximately 1972, enabling historical training data for pre-2000 Landsat time steps. After annual splitting to account for repeat observations at the same site, the VDBI provides approximately 33,000 data points for model training and validation. Plot records include leaf type cover estimates (evergreen, deciduous, coniferous) and forest vegetation type classifications according to the EUNIS habitat scheme, allowing joint training of the regression (cover fraction) and classification (forest type) heads of the TSTpad model. A stratified 20% validation split, stratified by polygon identifier to reduce spatial autocorrelation between training and validation sets, is applied throughout all training stages (Safonova et al., 2023).

### VPO field plot observations

The Vegetation Plot Observations (VPO) dataset consists of recent field campaigns conducted within Italian National Parks and protected areas. Each site comprises four systematic 100 m² vegetation plots arranged on a regular grid, within which evergreen broad-leaved cover is estimated for three vertical layers (0–1 m, 1–10 m, and above 10 m). The VPO data used in this study consists of observations from the 2024 field season, covering five National Parks (Sila, Gran Sasso, Gennargentu, Cilento, and Nebrodi) and yielding a total of 1440 individual plot observations. The VPO dataset provides high-quality, spatially clustered reference data for the most recent Landsat time steps (post-2020) and serves as the primary validation reference for model performance in the recent high-density observation period. The spatial clustering of VPO plots into national parks is explicitly accounted for in model evaluation by applying a cluster-based spatial cross-validation scheme, preventing over-optimistic accuracy estimates due to spatial autocorrelation (Safonova et al., 2023).

### Artificial leaf type cover data

Spatially explicit wall-to-wall leaf type cover data for model training are not available for Italy. Following the approach of Kang et al. (2021) and Tan et al. (2025) — who demonstrate the use of coarser or indirectly derived data sources as proxy training targets where direct measurements are absent — an artificial leaf type cover dataset was created from the VDBI and VPO plot observations. A Random Forest regression model was trained on the combined VDBI and VPO training split, with EVE, DEC, and CON cover fractions as prediction targets. As input features, AlphaEarth embeddings (Brown et al., 2025; Hiebl et al., 2026) — dense spectral-spatial-temporal representations derived from a globally pretrained geospatial foundation model — were extracted for all training plot locations. AlphaEarth embeddings were shown to achieve near-asymptotic species classification accuracy with very limited training data in Italian mountain forests (Ball et al., 2026), making them particularly suited as inputs for the pseudo-label generation step. Tessera embeddings (Feng et al., 2026) provide a fully open-source alternative with comparable performance characteristics.

The trained Random Forest model was then applied to the full CFI2020 forest extent to generate a nation-wide pixel-level pseudo-label layer for each cover fraction. This pseudo-label layer constitutes the primary continuous-cover target during the contrastive pretraining and early fine-tuning stages. To reduce label noise introduced by model prediction errors, the CFI2020 species attribution was used to apply ecologically motivated cleaning rules: pixels within *Pinus*-dominated forest polygons were required to have at least 60% coniferous cover and fewer than 30% broad-leaved evergreen cover; analogous rules were applied to pure-stand classes of beech, oak, and Mediterranean macchia. These cleaning rules remove the most egregious pseudo-label errors while preserving the spatial completeness of the training dataset.

### Landsat time series

Annual Landsat time series were assembled for the full Italian national territory from the Google Earth Engine planetary-scale analysis environment using Landsat Collection 2 surface reflectance products from Landsat 4 TM (1982–1993), Landsat 5 TM (1984–2013), Landsat 7 ETM+ (1999–2023), Landsat 8 OLI/TIRS (2013–present), and Landsat 9 OLI-2/TIRS-2 (2021–present). Per-pixel cloud, cloud shadow, cirrus, and snow masking was performed using the Landsat Collection 2 QA_PIXEL bitfield, decoded and applied via the `sattstools` preprocessing library (Hiebl, 2025a). Per-observation quality flags derived from QA_PIXEL are propagated through the entire modelling pipeline as a key-padding mask, ensuring that cloud-contaminated or padded time steps are ignored by all attention layers of the TSTpad model. For each forested pixel, 14 spectral features are computed at each valid observation: six surface reflectance bands (blue, green, red, near-infrared, SWIR1, SWIR2) and eight derived spectral indices (NDVI, NIRv, NDMI, EVI, WDRVI, NBR, NDWI, GNDVI), computed using the `sattstools` index calculation routines (Hiebl, 2025a). The resulting multi-annual time series are stored as Zarr-compressed arrays to enable efficient random-access loading during model training.

### Additional masking data sources

Three additional data sources are used to construct the final forest prediction mask. The Copernicus HRL Forest Type product is used as an initial broad-scale delineation of forested areas across Italy. A minimum canopy height threshold of 5 m, derived from the pan-European Landsat-based canopy height time series of Turubanova et al. (2023), is applied to exclude low-stature shrub vegetation, recently disturbed open-canopy stands, and young plantation areas from the prediction domain. Snow-covered pixels are excluded from the analysis using a Sentinel-2 Level-2A Snow and Ice (SCSI) time series mask derived from the Sentinel-2 Scene Classification Layer (SCL), which identifies persistent snow-covered areas that would otherwise introduce spurious cloud-free observations in the Landsat time series for high-elevation alpine terrain. These three masking layers are combined with the CFI2020 polygon layer to produce the final forest extent mask within which annual predictions are generated.

---

## Modelling workflow

### Time Series Transformer architecture

The backbone model is TSTpad, an encoder-only Time Series Transformer extended to support irregular, gappy multi-annual satellite image time series (Hiebl, 2025b). TSTpad is based on the general multivariate time series representation learning framework of Zerveas et al. (2020), which demonstrated for the first time that unsupervised Transformer pretraining can surpass fully supervised state-of-the-art methods on multivariate time series benchmarks. The architecture employs multi-head self-attention across the temporal dimension, enabling the model to learn both short-range phenological features and long-range inter-seasonal dependencies within the 3-year observation window.

For each target year, three consecutive years of Landsat observations are concatenated — encompassing the target year and the two immediately preceding years (year−2, year−1, year) — to densify the sparse annual time series. After concatenation, observations are chronologically sorted and padded to a fixed sequence length of 100 time steps using the `compact_sort_pad` procedure (Hiebl, 2025b); positions corresponding to cloud-masked or padded time steps receive a key-padding mask that prevents these positions from contributing to attention score computations (Vaswani et al., 2017). The actual acquisition day-of-year for each observation is encoded as a sinusoidal positional encoding, enabling the model to correctly represent the irregular temporal spacing of Landsat acquisitions and to distinguish phenological phases across the 3-year observation window without requiring interpolation to a regular grid (Yuan et al., 2022a).

A sensor platform embedding with `sensor_dim=5` encodes a multi-hot vector per time step indicating which Landsat satellites (L4, L5, L7, L8, L9) contributed the observation. This embedding is added to the temporal positional encoding via a learned linear projection and makes the Transformer explicitly aware of inter-sensor radiometric differences over the 40-year archive. Input features are normalised per band using `TSRobustStandardize` — a robust standardisation based on the median and interquartile range (quantiles q=0.1 and q=0.9) — with transform parameters fitted on the training data and frozen at inference time to prevent data leakage (Hiebl, 2025a).

Two parallel task heads share the same TSTpad backbone. A classification head trained with CrossEntropyLoss maps the Transformer's output representation to class probabilities over eleven dominant tree species and three functional leaf type classes. A regression head trained with mean squared error (MSELoss) maps the same representation to continuous EVE, DEC, and CON cover fractions. This multi-task formulation allows the model to simultaneously capture discrete species identity and continuous compositional information, using independent loss terms that are summed during training (Hiebl, 2025b).

### Training workflow

The model is trained via a three-stage progressive workflow designed to maximise temporal stability and to accommodate the heterogeneous quality and temporal coverage of available reference data (Hiebl, 2025b).

**Stage 1 — Contrastive pretraining.** The backbone is trained using a joint loss that simultaneously optimises a supervised classification objective and an unsupervised NT-Xent contrastive loss (Chen et al., 2020): L = λ·NT-Xent + CE. For the contrastive term, positive pairs are formed from the same forest plot observed in two independently sampled three-year windows (year₀ and year₁ drawn at random), representing different but ecologically equivalent observation contexts for the same location. NT-Xent (normalised temperature-scaled cross-entropy; temperature τ=0.1) pushes the backbone representations of these positive pairs toward each other in embedding space while repelling representations of observations from different plots. This objective forces the backbone to learn year-invariant spectral-temporal features that are not confounded by observation density or inter-annual radiometric variability (Mañas et al., 2021). Positive pairs are further diversified by the `LandsatAugment` module, which applies three independent stochastic perturbations to each view: random temporal masking (20% of valid time steps zeroed), spectral noise injection (additive Gaussian noise with σ=0.01), and band masking (10% of spectral bands zeroed per sample). The contrastive and classification signals are routed through separate heads attached to the shared backbone: a two-layer MLP projection head (embedding dimension → 128) for NT-Xent, and the classification/regression head for CrossEntropyLoss. The λ weight of the NT-Xent term is annealed during training — starting at a high value that emphasises the contrastive objective in early epochs and decreasing progressively as the supervised signal becomes the dominant training signal. The model is optimised using AdamW (learning rate 2×10⁻⁴, weight decay 6×10⁻³) with a cosine learning rate schedule preceded by a 10% warm-up phase; training runs for 60 epochs with a batch size of 128. Reference data consist of Italian forest vegetation plots from the VDBI and VPO datasets stored as Zarr-compressed arrays. Class imbalance is addressed jointly by class-weighted CrossEntropyLoss and by sample weights set to the square root of the inverse class frequency (sample weight power=0.5), following the approach of Grabska-Szwagrzyk et al. (2024). A stratified 20% validation hold-out, stratified by plot polygon identifier, is maintained across all training stages to prevent spatial autocorrelation between training and validation sets.

**Stage 2 — Fine-tuning on labelled data.** The contrastive backbone from Stage 1 is loaded and fine-tuned under a purely supervised objective (CrossEntropyLoss + MSELoss; NT-Xent dropped). The embedding layer is kept frozen (`freeze_setting = "same embedding"`) to preserve the contrastive representations, while the task heads are retrained using a reduced learning rate of 1×10⁻⁴ to prevent catastrophic forgetting (Hiebl et al., 2025). This stage runs for 10 epochs on the full 1985–2025 Landsat time series, allowing the model to adapt the task heads to the full historical archive without disturbing the temporally invariant representations established during contrastive pretraining.

**Stage 3 — Further fine-tuning on high-quality observations.** Additional fine-tuning passes are applied from the Stage 2 checkpoint with progressively reduced and quality-filtered training subsets, giving priority to recent high-quality VPO field observations that provide the most accurate ground reference data for the present-day forest state. This stage is particularly intended to anchor the model's predictions of recent (post-2020) cover fractions to field-validated reference values, while the contrastive representations established in earlier stages ensure that this anchoring remains consistent with historical predictions.

Seven independent model instances, differing in random seed (0–6), architecture micro-choices within TSTpad, and random subsets of training and validation data, are trained per stage. The seven-seed ensemble delivers two outputs per pixel per year: the ensemble mean prediction (used as the primary data product) and the inter-seed standard deviation (used as the pixel-level uncertainty estimate). High inter-seed uncertainty identifies pixels where the model predictions are unstable, typically in regions of low observation density, unusual spectral composition, or high class confusion (Sylvain et al., 2024; Hiebl et al., 2025).

### Mapping scheme

The forest prediction domain is defined by the intersection of the CFI2020 forest extent mask, the 5 m minimum canopy height layer (Turubanova et al., 2023), and the Copernicus HRL Forest Type product, with persistent snow-cover areas excluded. For each target year from 1985 to 2025, the corresponding three-year Landsat observation window (year−2 to year, inclusive) is assembled from the harmonised Landsat Collection 2 archive, cloud-masked, and processed to the 14 spectral features described in Section 2.1.5. Features are normalised with the fixed training-time `TSRobustStandardize` parameters and padded to 100 time steps. The seven trained ensemble models are applied independently to each forested pixel, and the resulting class probability distributions and cover fraction predictions are aggregated across seeds to produce the mean prediction and inter-seed uncertainty layers.

Observation density varies substantially across the archive. Before 1999, when only Landsat 5 TM was operational, the three-year window typically yields fewer cloud-free observations than the post-2013 period when Landsat 8 and 9 operate simultaneously. This density gradient is an analogue of the observational sampling bias documented for NDVI trend analyses by Bayle et al. (2024): predictions in the early archive period carry higher uncertainty due to sparse temporal sampling, which may cause the model to have lower confidence in phenological-season attribution. This effect is explicitly quantified in the Technical Validation section (Section 4) and is flagged via the inter-seed uncertainty layer. Pixels with inter-seed uncertainty above a conservative threshold in the pre-1999 period should be interpreted with caution in trend analyses.

---

## Validation scheme

The validation strategy is designed to assess both the accuracy of the map product at individual time steps and the temporal consistency of predictions across the full 40-year archive. Three independent validation datasets are employed.

The VDBI hold-out split provides the primary historical validation reference, with plot observations dating back to approximately 1995. This split allows accuracy assessment at historical time steps (1995–2012) where field data are available, spanning the Landsat 5-only and Landsat 7/5 overlap periods. The VPO hold-out split — collected during the 2024 field season — provides the primary validation reference for recent predictions (post-2020) from the high-density Landsat 8/9 period. These two validation datasets provide complementary temporal coverage: the VDBI split quantifies historical accuracy under lower observation density, while the VPO split quantifies accuracy under the best available observation conditions.

A third validation source consists of a set of pure-stand forest polygons manually interpreted from high-resolution Google Earth Pro imagery at recent time steps. These polygons, selected to represent spectrally unambiguous mono-specific stands, enable validation of the classification output under conditions where the expected dominant species label is highly reliable, providing an upper bound on classification accuracy unconstrained by label uncertainty in mixed stands.

Accuracy metrics are reported separately for three observation-density periods: the historical Landsat 5-only period (pre-1999), the Landsat 7/8 transition period (1999–2013), and the recent high-density period (post-2013). For the classification head, overall accuracy (OA) and per-class F1 score are computed for each period. For the regression heads, root mean squared error (RMSE) and mean absolute error (MAE) are reported for each of the three cover fractions (EVE, DEC, CON). Temporal consistency is evaluated by computing year-to-year variability of predictions at stable forest sites — forest plots with no documented disturbance — and comparing contrastive-pretrained models against a supervised-only baseline trained without the NT-Xent objective. Finally, cross-sensor consistency is assessed at Landsat platform transition years (L5→L7, L7→L8, L8→L9) by visual inspection and by computing prediction discontinuity metrics at transition dates.

---

# Data Records

*To be completed once mapping runs are finalised.*

---

# Technical Validation

*To be completed once mapping runs are finalised.*

---

# Discussion

*To be completed.*

---

# Code and Data Availability

*To be completed.*

---

# References

Bayle, A., Gascoin, S., Berner, L. T., and Choler, P.: Landsat-based greening trends in alpine ecosystems are inflated by multidecadal increases in summer observations, Ecography, e07394, https://doi.org/10.1111/ecog.07394, 2024.

Ball, J. G. C., Wicklein, J. A., Feng, Z., Knezevic, J., Jaffer, S., Madhavapeddy, A., Atzberger, C., Dalponte, M., and Coomes, D.: Geospatial foundation models enable data-efficient tree species mapping in temperate mountain forests, bioRxiv preprint, https://doi.org/10.1101/2026.01.01.000000, 2026.

Bell, D. M., Gregory, M. J., and Yang, Z.: Hindcasting and updating Landsat-based forest structure mapping across years to support forest management and planning, Forest Ecology and Management, 2024.

Blickensdörfer, L., Oehmichen, K., Pflugmacher, D., Kleinschmit, B., and Hostert, P.: National tree species mapping using Sentinel-1/2 time series and German National Forest Inventory data, Remote Sensing of Environment, 304, 114069, https://doi.org/10.1016/j.rse.2023.114069, 2024.

Brown, C. F., Kazmierski, M. R., Pasquarella, V. J., Rucklidge, W. J., Samsikova, M., Zhang, C., Shelhamer, E., Lahera, E., Wiles, O., Ilyushchenko, S., Gorelick, N., Boukouvalas, A., and Kohli, P.: AlphaEarth Foundations: An Embedding Field Model for Accurate and Efficient Global Mapping from Sparse Label Data, Google DeepMind preprint, 2025.

Chen, T., Kornblith, S., Norouzi, M., and Hinton, G.: A Simple Framework for Contrastive Learning of Visual Representations, Proceedings of the 37th International Conference on Machine Learning (ICML 2020), PMLR 119, 2020.

Feng, Z., Atzberger, C., Jaffer, S., Knezevic, J., Sormunen, S., Young, R., Lisaius, M. C., Immitzer, M., Jackson, T., Ball, J., Coomes, D. A., Madhavapeddy, A., and Blake, A.: TESSERA: Temporal Embeddings of Surface Spectra for Earth Representation and Analysis, arXiv preprint, arXiv:2026.xxxxx, 2026.

Gasparini, P., Di Cosmo, L., Floris, A., and De Laurentis, D. (Eds.): Italian National Forest Inventory — Methods and Results of the Third Survey (INFC2015), Springer Tracts in Civil Engineering, Springer Nature Switzerland AG, ISBN 978-3-030-98677-3, https://doi.org/10.1007/978-3-030-98678-0, 2022.

Grabska-Szwagrzyk, E., Tiede, D., Sudmanns, M., and Kozak, J.: Map of forest tree species for Poland based on Sentinel-2 data, Earth System Science Data, 16, 2877–2891, https://doi.org/10.5194/essd-16-2877-2024, 2024.

Grünig, M., Rammer, W., Senf, C., et al.: Climate change will increase forest disturbances in Europe throughout the 21st century, Science, 391, eadx6329, https://doi.org/10.1126/science.adx6329, 2026.

Hemmerling, J., Pflugmacher, D., and Hostert, P.: Mapping temperate forest tree species using dense Sentinel-2 time series, Remote Sensing of Environment, 267, 112743, https://doi.org/10.1016/j.rse.2021.112743, 2021.

Hiebl, B.: sattstools — Satellite Remote Sensing Time Series Preprocessing Library, Python software package, University of Innsbruck, https://git.uibk.ac.at/c7161037/sattstools, 2025a.

Hiebl, B.: ls_mapping — Landsat Time Series Forest Mapping with TSTpad, code repository, University of Innsbruck, 2025b.

Hiebl, B., Alessi, N., Calvia, G., Bricca, A., Bonari, G., Zangari, G., Dorigo, W., Zerbe, S., and Rutzinger, M.: Advancing forest mapping — Pretraining strategies and deep-ensemble based uncertainty for predicting evergreen broad-leaved cover from Sentinel-2 time series, International Journal of Applied Earth Observation and Geoinformation, 142, 104734, https://doi.org/10.1016/j.jag.2025.104734, 2025.

Hiebl, B., Alessi, N., Calvia, G., Bricca, A., Bonari, G., Zangari, G., Zerbe, S., and Rutzinger, M.: Combining specialized Sentinel-2 time series features with AlphaEarth Foundations for forest type mapping, ISPRS Annals of the Photogrammetry, Remote Sensing and Spatial Information Sciences, 2026.

Kang, Y., Ozdogan, M., Gao, F., Anderson, M. C., White, W. A., Yang, Y., and Erickson, T. A.: A data-driven approach to estimate leaf area index for Landsat images over the contiguous US, Remote Sensing of Environment, 255, 112234, https://doi.org/10.1016/j.rse.2020.112234, 2021.

Kollert, A., Bremer, M., Löw, M., and Rutzinger, M.: Exploring the potential of land surface phenology and seasonal cloud free composites of one year of Sentinel-2 imagery for tree species mapping in a mountainous region, International Journal of Applied Earth Observation and Geoinformation, 94, 102208, https://doi.org/10.1016/j.jag.2020.102208, 2021.

Mañas, O., Lacoste, A., Giró-i-Nieto, X., Vazquez, D., and Rodriguez, P.: Seasonal Contrast: Unsupervised Pre-Training from Uncurated Remote Sensing Data, arXiv:2103.16607, 2021.

Mattioli, W., Romano, R., Botticelli, D., Chirici, G., D'Amico, G., Giuliarelli, D., Pecchi, M., and Corona, P.: La Carta Forestale d'Italia (CFI2020): un ritratto aggiornato dei boschi italiani, Forest@, 22, 39–44, https://doi.org/10.3832/efor4836-022, 2025.

Midolo, G., Clark, A. T., Chytrý, M., Essl, F., Dullinger, S., Jandt, U., Bruelheide, H., Dengler, J., Bonari, G., Vecera, M., Keil, P., et al.: Sixty years of plant community change in Europe indicate a shift toward nutrient-richer and denser vegetation, Science Advances, 12, eaeb2493, https://doi.org/10.1126/sciadv.aeb2493, 2026.

Pflugmacher, D., Rabe, A., Peters, M., and Hostert, P.: Mapping pan-European land cover using Landsat spectral-temporal metrics and the European LUCAS survey, Remote Sensing of Environment, 221, 583–595, https://doi.org/10.1016/j.rse.2018.12.001, 2019.

Safonova, A., Ghazaryan, G., Stiller, S., Main-Knorn, M., Nendel, C., and Ryo, M.: Ten deep learning techniques to address small data problems with remote sensing, International Journal of Applied Earth Observation and Geoinformation, 125, 103569, https://doi.org/10.1016/j.jag.2023.103569, 2023.

Sylvain, J.-D., Drolet, G., Thiffault, E., and Anctil, F.: High-resolution mapping of tree species and associated uncertainty by combining aerial remote sensing data and convolutional neural networks ensemble, International Journal of Applied Earth Observation and Geoinformation, 131, 103960, https://doi.org/10.1016/j.jag.2024.103960, 2024.

Tan, J., Li, J., Ma, T., Yan, X., and Huo, Z.: Leveraging Sentinel-1/2 time series and deep learning for accurate forest tree species mapping, Frontiers in Forests and Global Change, 8, 1599510, https://doi.org/10.3389/ffgc.2025.1599510, 2025.

Tong, X., Brandt, M., Yue, Y., Fensholt, R., Ciais, P., and Wang, K.: Reforestation policies around 2000 in southern China led to forest densification and expansion in the 2010s, Communications Earth & Environment, 4, 64, https://doi.org/10.1038/s43247-023-00735-3, 2023.

Turubanova, S., Potapov, P., Hansen, M. C., Li, X., and Tyukavina, A.: Tree canopy extent and height change in Europe, 2001–2021, quantified using Landsat data archive, Remote Sensing of Environment, 296, 113723, https://doi.org/10.1016/j.rse.2023.113723, 2023.

Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, Ł., and Polosukhin, I.: Attention Is All You Need, Advances in Neural Information Processing Systems (NeurIPS 2017), 30, 2017.

Viana-Soto, A. and Senf, C.: The European Forest Disturbance Atlas: a forest disturbance monitoring system using the Landsat archive, Earth System Science Data, 2025.

Wang, M., Zheng, Y., Huang, C., Meng, R., and Zhao, F.: Assessing Landsat-8 and Sentinel-2 spectral-temporal features for mapping tree species of northern plantation forests in Heilongjiang Province, China, Forest Ecosystems, 9, 100009, https://doi.org/10.1016/j.fecs.2022.100009, 2022.

Yuan, Y., Lin, L., Liu, Q., Hang, R., and Zhou, Z.-G.: SITS-Former: A pre-trained spatio-spectral-temporal representation model for Sentinel-2 time series classification, International Journal of Applied Earth Observation and Geoinformation, 106, 102651, https://doi.org/10.1016/j.jag.2021.102651, 2022a.

Yuan, Y. and Lin, L.: Self-Supervised Pre-Training of Transformers for Satellite Image Time Series Classification, IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing, 2022b.

Zerveas, G., Jayaraman, S., Patel, D., Bhamidipaty, A., and Eickhoff, C.: A Transformer-based Framework for Multivariate Time Series Representation Learning, arXiv:2010.02803, 2020.
