
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

# Methods
### Data
##### CFI forest inventory data
##### VDBI forest plots
##### VPO plot observations
##### Artificial leaf type cover data
##### Landsat time series
##### additional data sources
Additional data sources used for masking non-forested areas:
- Copernicus forest type map
- tree height map
- Sentinel-2 L2A SCL snow cover time?

### Modelling workflow
##### Time Series Transformer
##### Training workflow
##### Mapping scheme

### Validation scheme
- VDBI split: several years of data back to 1995
- VPO split: recent data collected in the field
- pure stands: manually labelled from GE Pro for recent development
### Analysis


# Results

# Discussion

# Conclusion

# Literature

