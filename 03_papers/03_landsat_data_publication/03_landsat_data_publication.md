##### Potential Journals:
1. Earth System Science Data (Copernicus)
2. Scientific data (nature)
# Title:
**A 40-year annual time series of forest type and leaf type cover for Italy derived from Landsat using deep learning**

-------

> [!abstract] Motivation
> Consistent long-term maps of **forest functional type and dominant tree species cover** are lacking for Italy at high spatial resolution. We produce an **annual 30 m map time series spanning 1985–2025** using the full Landsat archive (L4/L5/L7/L8/L9), a Time Series Transformer model trained via contrastive learning, and multi-source Italian forest plot observations. The dataset provides continuous-cover fractions (EVE, DEC, CON) and dominant tree species probabilities for all forested pixels in Italy, together with **pixel-level uncertainty estimates** from a 7-seed deep ensemble.

> [!question] What main research questions will be answered?
> - Can a contrastive-learning Time Series Transformer produce **temporally stable, sensor-consistent** annual maps across four decades of Landsat?
> - How well do the modelled cover fractions and dominant species classes agree with **independent field validation data**?
> - What is the **quality, coverage, and temporal consistency** of the resulting dataset across the full Landsat archive?

> [!info] What will be done?
> - Assemble and harmonise a **40-year Landsat Collection 2 time series** for Italy (L4/L5/L7/L8/L9)
> - Train a **multi-task TSTpad model** (classification + regression heads) via a three-stage contrastive pretraining and fine-tuning workflow
> - Produce **annual 30 m maps** of dominant tree species (11 classes) and functional leaf type cover (EVE, DEC, CON fractions)
> - Publish the map time series together with **code, model weights, and training data splits**

> [!success] What are the expected results?
> **Dataset:**
> - Annual 30 m maps of EVE/DEC/CON cover and dominant tree species, 1985–2025, nation-wide Italy
> - Per-pixel inter-seed uncertainty layers
> 
> **Methodologically:**
> - Contrastive pretraining improves temporal stability compared to supervised-only baseline
> - Sensor platform embedding reduces radiometric discontinuities across the Landsat series
> - 3-year observation pooling increases cloud-free coverage, especially pre-1999

---

# Introduction

##### Landsat for forest mapping: advantages and challenges

- With 39 years, Landsat holds the longest consistent earth observation archive for vegetation monitoring
- Continuous record allows change detection, historical reconstruction and hindcasting of environmental variables [[bell_2024_hindcasting_forest_structure]] [[turubanove_2023_canopy_landsat]]
- Used to discriminate forest types and other forest parameters such as canopy height [[pflugmacher_2019_lulc_landsat]] [[turubanove_2023_canopy_landsat]]
- Slow succession of forest vegetation necessitates monitoring changes over decades [[tong_2023_forest_densification_china]] [[midolo_2026_denser_vegetation]]
- Medium spectral, spatial and temporal resolution (6 bands, 30 m, 8–16 days) is adequate for capturing annual phenology at stand level, crucial for tree species mapping [[kollert_2021_tree_species]] [[hemmerling_2021_forest_mapping_s2]] [[wang_2022_tree_species_mapping]]
- Challenges:
	- Number of usable cloud-free observations has increased over decades, leading to systematic overestimation of maxNDVI in recent years [[bayle_2024_landsat_greening_inflated]]
	- Scan line correction failure (Landsat 7 ETM+)
	- Spectral variability due to platform and sensor changes across L4–L9

##### Deep Learning for dominant tree species and leaf type cover mapping

- Multitemporal approaches consistently outperform single-date/mosaic approaches; leaf-off and senescence seasons are among the most informative time periods [[kollert_2021_tree_species]] [[tan_2025_deep_tree_species]]
- With sufficient temporal coverage, dense time series outperform explanatory environmental features [[hemmerling_2021_forest_mapping_s2]]
- Deep learning and Transformer architectures allow direct integration of irregular multi-band time series, with significant improvement from pretraining [[tan_2025_deep_tree_species]] [[hiebl_2025_pretraining]]
- Mixed forest stands remain a major challenge [[blickensdörfer_2024_tree_species]]; using inventory species proportions as soft regression targets (rather than hard dominant-species labels) improves performance for mixed stands [[ball_2026_foundation_models]]
- Transformer architectures naturally handle irregular time series without interpolation, essential for long Landsat archives with varying observation density across decades and sensors [[zerveas_2020_framework_transformer]] [[yuan_2022_sitsformer]]
- Self-supervised pretraining on satellite image time series learns robust spectral-temporal features for downstream tasks [[yuan_2023_pretraining]]
- Contrastive learning can produce year-invariant features suited for long-term multi-sensor mapping [[manas_2021_seasonal_contrast]] [[chen_2020_contrastive_framework]]
- Deep ensembles of independent networks provide calibrated epistemic uncertainty estimates identifying OOD inputs with unreliable predictions [[hiebl_2025_pretraining]] [[sylvain_2024_tree_species_uncertainty]]
- GFM embeddings (AlphaEarth, Tessera) consistently outperform conventional composites for tree species mapping; near-asymptotic accuracy reached with 5% of training data [[ball_2026_foundation_models]]
- Availability of high-quality plot observation data is scarce [[safonova_2023_small_data]]

##### Need for a long-term Italian forest type dataset

- Italian National Forest Inventory (INFI) indicates forests are expanding due to land abandonment and reforestation [[gasparini_2022_nfi_italy]] [[mattioli_2025_carta_forestale]]
- Nation-wide annual maps at 30 m covering the full Landsat record do not exist for Italy
- Existing national forest maps are static snapshots and do not resolve interannual dynamics [[mattioli_2025_carta_forestale]]
- The proposed dataset fills this gap and enables downstream ecological and change-detection analyses

##### Justification of methodological approach

- Contrastive learning approach:
	- Sensor and observation density drift over time [[bayle_2024_landsat_greening_inflated]]
	- Contrastive learning over pure and random forest stands mitigates drift [[chen_2020_contrastive_framework]]
	- Assumption: ecological and spectral stability over time enables contrastive learning [[manas_2021_seasonal_contrast]]
- Fine-tuning after contrastive pretraining: [[hiebl_2025_pretraining]], [[safonova_2023_small_data]]
	- Pseudo-labelling via AlphaEarth embeddings for functional cover mapping [[brown_2025_alphaearth]], [[hiebl_2026_alphaearth]]; Tessera as fully open-source alternative [[feng_2026_tessera]]
	- Final fine-tuning on plot observation data: historical and recent
- 3-year observation pooling:
	- Mitigates inter-annual spectral variability for stability [[grabska_2024_tree_species_map]] [[pflugmacher_2019_lulc_landsat]]
	- Densifies observations per year to increase cloud-free observation counts [[bayle_2024_landsat_greening_inflated]]
	- Target year−2: two previous historical time series used (no future leakage)

---

# Methods

### Data

##### CFI forest inventory data

##### VDBI forest plots

##### VPO plot observations

##### Artificial leaf type cover data

- As spatially explicit data of leaf type cover is not available, an **artificial cover dataset** was created based on VPO and VDBI leaf type cover [[tan_2025_deep_tree_species]] [[kang_2021_lai_landsat]]
- Both references establish the practice of generating artificial training labels from an indirect source when no spatially explicit per-pixel target data exist: Kang et al. (2021) use coarser MODIS LAI products as proxy training targets to build a 30 m Landsat LAI model; Tan et al. (2025) generate pseudo-labels for unlabelled mixed-stand pixels using a classifier trained only on pure-stand inventory samples
- A standard **Random Forest** model was trained on the training split of the plot observation data and mapped to Italy using AlphaEarth embeddings as input features [[brown_2025_alphaearth]] [[hiebl_2026_alphaearth]]; Tessera embeddings are a fully open alternative [[feng_2026_tessera]] [[ball_2026_foundation_models]]
- To decrease label noise due to regression errors, the CFI data and decision rules were used to clean the dataset; e.g. points falling within Pinus-dominated forests have at least 60% coniferous cover and less than 30% broad-leaved evergreen cover

##### Landsat time series

##### Additional data sources

Additional data sources used for masking non-forested areas:
- Copernicus forest type map
- Tree height map [[turubanove_2023_canopy_landsat]]
- Sentinel-2 L2A SCL snow cover time series

---

### Modelling workflow

##### Time Series Transformer

- The backbone model is **TSTpad** ([[ls_mapping]]), an encoder-only Time Series Transformer with support for irregular, gappy multi-annual satellite time series
- For stability and epistemic uncertainty estimation an ensemble of 6 models with differing architecture choices of TSTpad is combined; random subsets of training and validation data further diversify model outputs [[hiebl_2025_pretraining]] [[sylvain_2024_tree_species_uncertainty]]
- For each target year, **three consecutive years of Landsat observations are concatenated** (year−2, year−1, year) to densify the sparse annual time series — this 3-year aggregation window substantially increases the number of cloud-free observations available per pixel ([[ls_mapping]])
- After concatenation, observations are chronologically sorted and **padded to a fixed length of 100 time steps** (via `compact_sort_pad`); timestamp values are scaled to day-of-year units for the positional encoding ([[ls_mapping]])
- Input features per time step: **14 Landsat spectral variables** — six surface reflectance bands (blue, green, red, NIR, SWIR1, SWIR2) and eight derived indices (NDVI, NIRv, NDMI, EVI, WDRVI, NBR, NDWI, GNDVI); indices computed via [[sattstools]]
- **Sinusoidal timestamp encoding** embeds the actual acquisition day-of-year for each observation, enabling the model to correctly handle irregular temporal spacing and the 3-year observation window ([[vaswani_2023_attention_is_all]])
- A **Landsat platform embedding** (`sensor_dim=5`) encodes a multi-hot sensor vector per time step — indicating which satellites (L4, L5, L7, L8, L9) contributed each observation — and is added to the temporal encoding via a learned projection; this makes the model aware of inter-sensor radiometric differences over the 40-year archive ([[ls_mapping]])
- A **key-padding mask** derived from cloud-masked positions (Landsat QA_PIXEL) is propagated through all attention layers so the model ignores cloud-contaminated or padded time steps ([[sattstools]])
- Input normalised per band with **TSRobustStandardize** (median/IQR, quantiles q=[0.1, 0.9]); transform statistics fitted on training data and frozen at inference to prevent data leakage ([[sattstools]])
- Two parallel task heads share the same TSTpad backbone: a **classification head** (CrossEntropyLoss; dominant tree species / functional leaf type; `class_v3`) and a **regression head** (MSELoss; continuous fractional cover: EVE, DEC, CON) ([[ls_mapping]])

##### Training workflow

The training follows a **three-stage progressive workflow** implemented in [[ls_mapping]]:

**Stage 1 — Contrastive pretraining (cont)**
- A **joint loss** combining NT-Xent contrastive learning and supervised CrossEntropyLoss is optimised simultaneously: `L = λ·NT-Xent + CE` ([[ls_mapping]])
- NT-Xent (temperature τ=0.1) pushes representations of the same plot observed in **two different 3-year windows** (year0, year1 drawn independently) to be similar, while repelling representations of different plots — forcing the backbone to learn **temporally stable, year-invariant representations** ([[chen_2020_contrastive_framework]])
- Positive pairs are further diversified by `LandsatAugment`: independent random **temporal masking** (20% of valid time steps set to zero), **spectral noise injection** (Gaussian, σ=0.01), and **band masking** (10% of bands zeroed per sample) applied to each view ([[ls_mapping]])
- The **ContrastiveWrapper** routes inputs through two paths on the shared backbone: a 2-layer MLP projection head (emb_dim→128) for NT-Xent; the classification/regression head for CE — backbone weights are shared and updated by both losses ([[ls_mapping]])
- λ is annealed during training: weight of the NT-Xent term starts high (forcing contrastive objective in early epochs) and is gradually reduced as CE becomes the dominant signal ([[ls_mapping]])
- Optimiser: AdamW (lr=2×10⁻⁴, weight_decay=6×10⁻³) with **warmup cosine learning rate schedule** (10% of total steps as warmup); 60 epochs, batch size 128 ([[ls_mapping]])
- Reference data: Italian forest vegetation plots (VDB, VDBI, VPO) stored as Zarr-compressed arrays; **class-weighted CrossEntropyLoss** and **sample weight power=0.5** (square-root of inverse frequency) jointly address class imbalance ([[grabska_2024_tree_species_map]])
- Validation split: 20% hold-out stratified by plot polygon ID to reduce spatial autocorrelation between train and validation sets ([[safonova_2023_small_data]])

**Stage 2 — Fine-tuning (fine0)**
- Contrastive backbone loaded from `cont` checkpoint with `freeze_setting = "same embedding"` — the embedding layer is kept frozen while the task heads are retrained on the supervised objective only ([[ls_mapping]])
- Pure **CrossEntropyLoss / MSELoss** — NT-Xent dropped; learning rate reduced to 1×10⁻⁴ to preserve the contrastive representations while adapting the head to labelled data ([[hiebl_2025_pretraining]])
- Short targeted training (10 epochs) on the full 1985–2025 time slice, allowing the model to adapt to the long historical Landsat archive without catastrophic forgetting ([[ls_mapping]])

**Stage 3 — Further fine-tuning (fine1, fine2)**
- Additional fine-tuning passes from the fine0 checkpoint with progressively smaller datasets (e.g., prioritising recent high-quality VPO field observations) ([[ls_mapping]])
- Seven independent seeds (0–6) trained per stage; the **7-seed ensemble** provides pixel-level uncertainty estimates from inter-seed prediction variance ([[hiebl_2025_pretraining]])

##### Mapping scheme

- Forest extent mask constructed from the **Italian national forest map** (CFI2020, [[mattioli_2025_carta_forestale]]) combined with a minimum canopy height threshold (≥5 m from [[turubanove_2023_canopy_landsat]]) to exclude non-forest and recently disturbed pixels
- Annual mapping: for each year 1985–2025, the **3-year observation window** (year−2 to year) is assembled from the full Landsat archive (L4/L5/L7/L8/L9, harmonised Collection 2); cloud masking via Landsat QA_PIXEL in [[sattstools]]; 14 spectral features computed and normalised with fixed training-time statistics
- **Observation density is strongly period-dependent**: before 1999 (L5 only) the 3-year window yields fewer cloud-free observations than post-2013 (L8+L9); the 3-year aggregation and padding to 100 time steps mitigates but does not eliminate this density difference — an analogue of the sampling-bias issue documented for NDVI trends ([[bayle_2024_landsat_greening_inflated]])
- Model applied pixel-wise within the forest mask → annual maps of dominant tree species class probabilities and continuous EVE/DEC/CON cover fractions for all forested pixels in Italy ([[ls_mapping]])
- Outputs per year: mean prediction across 7 seeds + inter-seed standard deviation as uncertainty estimate; high uncertainty flags areas where the model is unreliable across the historical record ([[hiebl_2025_pretraining]])

---

### Validation scheme

- **VDBI split**: several years of data back to 1995 — provides temporal depth for historical accuracy assessment
- **VPO split**: recent data collected in the field — provides high-quality independent validation for recent years
- **Pure stands**: manually labelled from Google Earth Pro for recent time steps — enables validation of the classification output in spectrally unambiguous pixels
- Accuracy reported separately for recent (post-2013, high observation density) and historical (pre-1999, L5-only) periods to quantify the effect of observation density on model quality
- Polygons from **historical aerial imagery**

---

# Data Records

> [!todo] To be filled in once mapping runs are complete
> - File format, spatial extent, CRS, resolution
> - Variables per file (EVE, DEC, CON fractions; species class probabilities; uncertainty layers)
> - Archive location and DOI
> - Temporal coverage and file naming convention

---

# Technical Validation

##### 1. Classification and regression accuracy

- Report overall accuracy, per-class F1 (dominant species) and RMSE/MAE (EVE/DEC/CON fractions) on held-out VDBI and VPO splits
- Separate metrics for recent (post-2013) and historical (pre-1999) periods

##### 2. Temporal consistency of contrastive learning

- Compare **temporal smoothness** of annual EVE/DEC/CON cover time series between models trained with the contrastive objective (cont → fine) and a supervised-only baseline — the contrastive pretraining hypothesis predicts lower year-to-year variability while preserving long-term signal ([[ls_mapping]])
- Evaluate whether **inter-seed uncertainty is lower** across time for the contrastive model, indicating more stable learned representations ([[hiebl_2025_pretraining]])
- Take recent time series, predict values under full density → reduce density (to mimic earlier Landsat observation coverage) and predict again; compare contrastive TST against from-scratch TST to quantify the benefit of contrastive pretraining under sparse observations

##### 3. Sensor consistency

- Assess **early archive performance** (1985–1999, L5 only): does the sensor platform embedding successfully reduce the discontinuity in predicted cover between the pre- and post-Landsat 7/8 periods?
- Visual and statistical inspection of predictions at sensor transition years (L5→L7, L7→L8, L8→L9) to detect residual radiometric artefacts

##### 4. Observation density effects

- Control for **observation density artefacts**: the pre-1999 archive has substantially fewer cloud-free observations per 3-year window — spurious apparent trends in early decades need to be identified, quantified, and flagged ([[bayle_2024_landsat_greening_inflated]])
- Assess inter-seed uncertainty of predictions in low-density periods: pixels with high temporal variance across seeds should be flagged as unreliable ([[hiebl_2025_pretraining]])

---

# Discussion

#### Limitations

- Major limitation is potential overestimation of EVE in earlier years with low observation density [[bayle_2024_landsat_greening_inflated]]; the phenological signal is likely to "flatten" due to missing peaks in growing and leaf-off season
- Mixed stands are hard to label and to predict; soft-label regression targets from plot proportions partially address this [[ball_2026_foundation_models]] [[tan_2025_deep_tree_species]]
- The 3-year pooling window improves observation density but prevents mapping of abrupt within-period change (e.g. disturbance), which will appear as smoothed cover transitions [[pflugmacher_2019_lulc_landsat]]
- Disturbance effects (fires, bark beetle outbreaks) affect cover in unpredictable ways; EFDA shows 22% of Italian forest area disturbed 1985–2023 — these pulses will appear as abrupt cover shifts unrelated to species composition change [[soto_2025_disturbance]] [[grünig_2026_climate_change_disturbances_forest]]
- The forest mask is based on a single reference year (CFI2020) and does not capture afforestation or deforestation outside that snapshot [[mattioli_2025_carta_forestale]]

---

# Conclusion

---

# Code and Data Availability

---

# Literature
