
# Title:
**Mapping 40 years of dominant tree species and leaf type cover for Italys forests using Landsat**

-------

> [!Motivation]
> Climate and landuse changes alter forest compositions in deciduous forests in Italy. Milder winters and dryer summers **favor evergreen broad-leaved tree species**, which might displace deciduous tree species. Comprehensive **nation-wide mapping of evergreen broad-leaved species distribution and cover over several decades are lacking**.

> [!What main research questions will be answered?]
> - What changes can be observed in **dominant tree species distributions and functional leaf type cover**?
> - Are observed changes in line with general **winter greening trends**?
> - What is the potential of the **Contrastive Learning** approach for longterm Landsat forest mapping?

> [!What will be done?]
> Implementation of a **multi-step contrastive learning approach** based on several forest vegetation datasets to model:
> - **functional leaf type cover** (EVE, DEC, CON)
> - **dominant tree species** (11 classes)
> 
> The workflow is based on **annual Landsat timeseries fed to a Time Series Transformer** model.
> The analysis of maps will be nation-wide for forested areas.

> [!What are the expected results?]
> **Ecologically:**
> - Latitudinal and altitudinal shift of EVE species 
> - increase of EVE cover in transition zones in deciduous dominated forests
> 
> **Methodologically:**
> - Contrastive Learning improves temporal stability of the predictions

---

# Introduction
##### Changes in (sub-)mediterranean forests
##### Landsat for forest mapping: advantages and challenges
##### Dominant tree species and leaf type cover mapping using Deep Learning (and Landsat?)
##### Deep Learning training approaches that work in this context
##### Research questions
1. Is there a winter greening trend observable in mixed deciduous/evergreen broad-leaved forests?
2. Are latitudinal and altitudinal shifts of evergreens observable?
3. Which climatic or anthropogenic drivers influence this shift?
4. Is climate changing faster than forest structure?
5. Is it a gradual shift or is there a climatic tipping point?

##### Methodological approach justification
- contrastive learning approach: 
	- sensor and observation density drift over time [[bayle_2024_landsat_greening_inflated]]
	- contrastive learning over pure and random forest stands to mitigate drift [[chen_2020_contrastive_framework]], 
	- assumption: ecological and therefore spectral stability over time enables contrastive learning [[manas_2021_seasonal_contrast]], also: "slow changing systems [[herraiz_2025_phen_shifts_mediterranean]]"
- finetuning after contextual pre training: [[hiebl_2025_pretraining]], [[safonova_2023_small_data]]
	- pseudo labeling via Alpha earth embeddings for functional cover mapping [[brown_2025_alphaearth]], [[hiebl_2026_alphaearth]]
	- final finetuning on plot observation data: historical and recent
- pooling/aggregating 3 years:
	- mitigating inter annual spectral variabilities for stability [[grabska_2024_tree_species_map]] [[pflugmacher_2019_lulc_landsat]]
	- downside: inter-annual changes are leveled [[pflugmacher_2019_lulc_landsat]]
	- densify observations per year to increase observation counts [[bayle_2024_landsat_greening_inflated]]
	- target year-2: taking two previous historical time series for stability (no future leakage)
# Methods
### Data
##### CFI forest inventory data
##### VDBI forest plots
##### VPO plot observations
##### Artificial leaf type cover data
- As spatial explicit data of leaf type cover is not available an **artificial cover dataset** was created based on the VPO and VDBI leaf type cover [[tan_2025_deep_tree_species]] [[kang_2021_lai_landsat]]
- Both papers establish the practice of **generating artificial training labels from an indirect source** when no spatially explicit per-pixel target data exist: Kang et al. (2021) use coarser **MODIS LAI products as proxy training targets** to build a 30 m Landsat LAI model — no direct Landsat-resolution LAI measurements exist, so a model-derived product fills the gap; Tan et al. (2025) **generate pseudo-labels for unlabeled mixed-stand pixels using a classifier** trained only on pure-stand inventory samples
- A standard **Random Forest** model was trained on the training split of the plot observation data and mapped to Italy using Alpha Earth embeddings as input features [[brown_2025_alphaearth]] [[alessi_2019_refugia]] [[hiebl_2026_alphaearth]]
- To decrease label noise due to regression errors we used the CFI data and decision rules to clean the dataset; e.g. points that fall within pinus dominated forests have at least 60% coniferous cover and less than 30% broad-leaved evergreen cover

##### Landsat time series
##### additional data sources
Additional data sources used for masking non-forested areas:
- Copernicus forest type map
- tree height map
- Sentinel-2 L2A SCL snow cover time?

### Modelling workflow
##### Time Series Transformer

- The backbone model is **TSTpad** ([[ls_mapping]]), an encoder-only Time Series Transformer with support for irregular, gappy multi-annual satellite time series
- For stability and epistemic uncertainty estimation an ensemble of 6 models with differing architecture choices of TSTpad is combined; Additionally random subsets of training and validation data is used to further diversify model outputs [[hiebl_2025_pretraining]] [[sylvain_2024_tree_species_uncertainty]]
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
- Reference data: Italian forest vegetation plots (VDB, VDBI, VPO) stored as Zarr-compressed arrays; **class-weighted CrossEntropyLoss** and **sample weight power=0.5** (square-root of inverse frequency) jointly address class imbalance in species-dominated training distributions ([[grabska_2024_tree_species_map]])
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

### Justification of methodological approach
### Validation scheme
- VDBI split: several years of data back to 1995
- VPO split: recent data collected in the field
- pure stands: manually labelled from GE Pro for recent development
### Analysis

##### 1. Temporal trend analysis of functional leaf type cover (1985–2025)

- Compute **per-pixel linear trends** in EVE, DEC, and CON cover over the 40-year time series using Sen's slope estimator (robust to outliers); significance tested with Mann-Kendall test
- Identify pixels with **statistically significant EVE increase** and map their spatial distribution to test whether expansion is concentrated in transition zones between Mediterranean and temperate forest belts ([[hiebl_2025_pretraining]])
- Compare trend magnitude and spatial patterns against **long-term NDVI winter greening trends** from the Landsat archive to test whether EVE cover increase is a plausible driver of the observed winter greening signal ([[herraiz_2025_phen_shifts_mediterranean]])
- Control for **observation density artefacts**: the pre-1999 archive (L5 only) has substantially fewer cloud-free observations per 3-year window than the post-2013 period (L8/L9) — spurious trends in early decades need to be identified and masked or corrected ([[bayle_2024_landsat_greening_inflated]])
- Assess inter-seed uncertainty of trend estimates: pixels with high temporal variance in model predictions (low temporal consistency across seeds) should be flagged and excluded from trend analysis ([[hiebl_2025_pretraining]])

##### 2. Latitudinal and altitudinal gradient analysis

- Aggregate mean EVE cover per 0.1° latitude band for each decade (1985–1994, 1995–2004, 2005–2014, 2015–2025) and test whether the **northern boundary of high EVE cover has shifted poleward** ([[jin_2023_drivers_differentiation_evergreen]])
- Analyse EVE cover along **elevational transects** in the main Italian mountain systems (Alps, Apennines) to test whether the EVE–DEC boundary has moved upslope over 40 years ([[noce_2023_altitude_shift_tree_italy]])
- Differentiate the response by **canopy layer**: EVE expansion is theoretically faster in the canopy than in the understory along the temperature gradient — the dominant species maps provide an indirect test of this at the stand scale ([[jin_2023_drivers_differentiation_evergreen]])
- Stratify the latitudinal analysis by **topographic exposure** (south-facing vs. north-facing slopes) — topographic microclimate modulates the effective temperature experienced by trees and is expected to accelerate or dampen EVE expansion at local scale ([[bricca_2026_topo_diversity]])

##### 3. Transition zone dynamics

- Delineate the **EVE–DEC transition zone** as pixels where long-term mean EVE cover falls in the 20–70% range and quantify how the area and location of this zone has shifted over 40 years
- Within the transition zone, identify **pixels that have crossed a cover threshold** (e.g., EVE > 50%) since 1985 to estimate the rate of functional type conversion; compare this rate between decades to test whether change has accelerated ([[midolo_2026_denser_vegetation]])
- Test whether transition zone shifts are **gradual or punctuated**: changepoint detection (BFAST or CUSUM) on per-pixel EVE cover time series to identify abrupt transitions vs. smooth linear trends ([[tong_2023_forest_densification_china]])
- Relate the spatial pattern of transition zone change to **forest disturbance history** (bark beetle, windthrow, fire): disturbance-induced canopy opening may accelerate thermophilisation by creating regeneration niches for EVE species ([[grünig_2026_climate_change_disturbances_forest]])

##### 4. Climate driver attribution

- Correlate per-pixel EVE cover trends with **long-term climate trends** from CHELSA (annual mean temperature, summer maximum temperature, winter minimum temperature, annual precipitation deficit / aridity index) at the pixel and regional level ([[herraiz_2025_phen_shifts_mediterranean]])
- Partial regression or random forest importance to disentangle the relative contribution of **warming vs. drying**: Mediterranean EVE species are favoured both by milder winters (reduced frost limiting their range) and by summer drought (their sclerophyllous leaves are more drought-tolerant than deciduous leaves) ([[noce_2023_altitude_shift_tree_italy]])
- Test the hypothesis that **climate is changing faster than forest structure**: compare the rate of climate-space shift (velocity of the local climate niche boundary) against the rate of observed EVE cover change — a lag would indicate forest composition change is slower than the underlying climate pressure ([[albrich_2019_climate_change_mountain_forests]])
- Control for **land use change**: afforestation, management abandonment, and harvesting can cause EVE cover changes independent of climate; cross-reference with the Italian forest inventory time series ([[gasparini_2022_nfi_italy]]) and national forest maps ([[mattioli_2025_carta_forestale]])

##### 5. Consistency with winter greening signal

- Extract annual **winter NDVI and NIRv** from the same Landsat archive and compute 40-year winter greenness trends per pixel
- Test whether **EVE cover increase spatially predicts winter greenness increase** at the pixel level (spatial correlation) and whether changes co-occur temporally (cross-correlation with lag analysis)
- Identify pixels where **winter greenness increased but EVE cover did not** — these may reflect alternative explanations (e.g., shrub encroachment, management change, or the observation-density artefact documented in ([[bayle_2024_landsat_greening_inflated]]))

##### 6. Methodological evaluation: temporal consistency of contrastive learning

- Compare **temporal smoothness** of annual EVE cover time series between models trained with the contrastive objective (cont → fine) and a baseline trained without it (pure → fine) — the contrastive pretraining hypothesis predicts that year-to-year variability is lower for the contrastive model while long-term trends are preserved ([[ls_mapping]])
- Evaluate whether **inter-seed uncertainty is lower** across time for the contrastive model, indicating more stable learned representations ([[hiebl_2025_pretraining]])
- Assess **early archive performance** (1985–1999, L5 only): does the sensor platform embedding successfully reduce the discontinuity in predicted cover between the pre- and post-Landsat 7/8 periods?

# Results

# Discussion

# Conclusion

# Literature

