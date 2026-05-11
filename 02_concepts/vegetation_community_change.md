---
name: vegetation_community_change
description: Long-term plant community change via EIV bioindication; nitrogen eutrophication dominant; links to satellite vegetation greening signals
type: reference
tags:
  - forest-ecology
  - biodiversity
  - remote-sensing
---

# Vegetation Community Change

**Summary**: Long-term shifts in plant community composition across European habitats are primarily driven by nitrogen enrichment and management cessation (not warming), detectable via community-mean Ellenberg Indicator Values (CM_EIVs) and directly linked to satellite-observed vegetation greening and canopy densification trends.

**Sources**: [[midolo_2026_denser_vegetation]], [[herraiz_2025_phen_shifts_mediterranean]], [[bricca_2026_topo_diversity]], [[francioni_2026_canopy_closure]]

**Last updated**: 2026-05-05

---

## Ellenberg Indicator Values (EIVs) as Bioindication Tools

EIVs are expert-assigned ecological scores for plant species reflecting their realized niche along key environmental gradients:

| EIV | Gradient | Scale | What an increase means |
|-----|---------|-------|----------------------|
| **Light** | Full sunlight → deep shade | 1–9 | More light-demanding species present |
| **Temperature** | Alpine/boreal cold → Mediterranean warm | 1–9 | Thermophilisation; warmer conditions |
| **Moisture** | Very dry → aquatic | 1–12 | More moisture-demanding species |
| **Nitrogen** | N-poor → N-rich | 1–9 | Eutrophication; nutrient enrichment |
| **Reaction** | Very acid → very base | 1–9 | Higher soil pH; less acidic conditions |

**Community-mean EIVs (CM_EIVs)**: average EIV of all co-occurring species in a plot — a proxy for local environmental conditions without direct measurements.

Data source: **EIVE** (Ecological Indicator Values for Europe, version 1.0) — 31 regional EIV systems harmonised into one continental system for 13,874 vascular plant taxa.

**Strengths:**
- Computable from any historical species list — enables retrospective monitoring
- Robust to observer variation in vegetation surveys
- Allow multi-decadal comparison across heterogeneous datasets (EVA, ReSurveyEurope)

**Limitations:**
- EIVs partially correlated → isolating individual drivers is difficult
- Reflect realized niche, not fundamental niche; long-lived species (trees, shrubs) may lag behind actual environmental change
- Region-specific calibration — optimal performance within the calibration area (Europe)

## Key Drivers of 60-Year European Vegetation Change

Based on Midolo et al. (2026), the continent-wide community composition trends from 1960 to 2020 across forests, grasslands, scrub, and wetlands:

### 1. Nitrogen Enrichment (Eutrophication) — Dominant Driver

- **CM_EIV nitrogen: +0.25** averaged across all plots; 62% of plots show ≥+0.1 increase
- Consistent across all four major habitat types and all European regions
- Strongest in nutrient-poor habitats (dry grasslands, nutrient-poor scrub)
- **Drivers**: agricultural nitrogen runoff + atmospheric reactive nitrogen deposition (since mid-20th century); management cessation allows nitrogen build-up; CO₂ fertilization amplifies biomass response
- Consequence: competitive nitrogen-demanding, generalist species replace oligotrophic habitat specialists → loss of functional and taxonomic diversity

### 2. Vegetation Densification (Light Decline) — Mirror of Nitrogen Increase

- **CM_EIV light: -0.12** overall; strongest in grasslands and wetlands
- Vegetation becoming denser and more shade-tolerant — direct consequence of increased biomass
- Mechanistic chain: N enrichment → higher plant productivity → more biomass → higher LAI → shade-tolerant species replace light-demanding specialists
- Management cessation removes traditional disturbance (grazing, coppicing, mowing) that historically maintained open conditions
- **Forest exception**: no overall light change in forests; some disturbance-driven habitats (broadleaved evergreen, coniferous) show light increase from canopy opening

### 3. Temperature (Thermophilisation) — Weak and Spatially Restricted

- **CM_EIV temperature: +0.04** overall — unexpectedly small given ~1°C warming
- Detectable only in **alpine and subalpine** scrub and grasslands over the last two decades
- Absent or undetectable in lowland forests and most other habitats
- **Why the weak signal?**
  - Flat lowland terrain: temperature gradients span large geographic areas → thermophilous colonizers not available locally → slow community response
  - Mountain habitats: thermophilous species available immediately upslope → rapid observable shifts
  - Indirect cooling: denser vegetation (from N enrichment) cools understory → counteracts direct warming signal in closed habitats

### 4. Moisture Changes — Habitat-Specific

- **Wetlands**: strong moisture decline (-0.20) → hygrophilous species lost; driven by drainage and hydrological modification
- **Dry habitats** (Mediterranean scrub, dry grasslands): moisture CM_EIV increases → mesophilisation (generalist species replace dry-habitat specialists after management cessation)

### 5. Soil Reaction Recovery — Post-Acid-Rain

- **CM_EIV reaction: +0.02** overall; positive in forests, tundra, bogs
- Less acidophilous species gaining ground → soil pH recovery following post-1980s reduction in sulfur deposition (acid rain abatement)

## Links to Remote Sensing Observations

Community-level vegetation change has direct implications for satellite-observed signals:

- **NDVI greening**: nitrogen-driven densification (higher LAI, more biomass) is a major driver of multi-decadal positive NDVI trends observed from satellites — confounded with temperature-driven growing-season lengthening (source: [[midolo_2026_denser_vegetation]]); see [[vegetation_greenness_trends]]
- **Canopy cover increase**: light decline reflects canopy closure → directly detectable as canopy cover increase or forest densification in Landsat/Sentinel-2 time series
- **SDM predictors**: if climate–vegetation relationships are used as SDM predictors, nitrogen-driven composition shifts can create spurious climate signals — non-climatic drivers must be accounted for; see [[species_distribution_models]]
- **Temperature EIV thermophilisation in mountains**: spatially consistent with alpine NDVI greening signal (see [[01_notes/bayle_2024_landsat_greening_inflated]]); both reflect thermophilisation at high elevations

## Implications for Forest Ecology

- Forest communities shifted toward species associated with higher soil pH (acid rain recovery) and moderately higher nitrogen demand (source: [[midolo_2026_denser_vegetation]])
- No overall thermophilisation in forests — the temperature signal is masked by canopy densification cooling understory (source: [[midolo_2026_denser_vegetation]])
- Disturbance (windthrow, bark beetle, drought mortality) opens canopy → local reversal of densification trend → light increases temporarily (consistent with [[forest_disturbances]])
- EVE (evergreen broad-leaved) species expansion in Mediterranean-temperate transition zones is partly driven by eutrophication-mediated competitive advantages of generalist evergreen species (source: [[hiebl_2025_pretraining]])

**Long-term understory diversity consequences of canopy closure** (source: [[francioni_2026_canopy_closure]]):
- In 31 ICP Forests Level II permanent plots in Italy (1999–2023), understory vascular plant species richness declined significantly in boreal (−0.69 spp/yr), nemoral oak (−0.34 spp/yr), and nemoral beech (−0.20 spp/yr) forests over 25 years
- Primary drivers: progressive tree cover increase (canopy closure following management abandonment) and intensifying climate extremes (consecutive dry days, hot days frequency)
- Mediterranean forests remained stable — adapted to recurrent drought and characterised by more stable canopy cover
- Beta diversity partitioning reveals progressive community *nestedness* (irreversible species loss) rather than mere *turnover* (species replacement) in boreal and nemoral forests — a signature of directional impoverishment
- Ellenberg indicator values confirm: light values decreased (canopy densification), temperature values increased, moisture values decreased in nemoral oak (xerophilisation and thermophilisation)

## Conservation Implications

- Eutrophication and management abandonment are as important as warming for biodiversity loss (source: [[midolo_2026_denser_vegetation]])
- Habitat specialists in grasslands, wetlands, and nutrient-poor scrub are most threatened (source: [[midolo_2026_denser_vegetation]])
- Understory diversity in boreal and temperate forests is declining irreversibly under canopy closure — traditional management (grazing, coppicing, mowing) can counteract this (source: [[francioni_2026_canopy_closure]])
- Reducing nitrogen inputs at source (agriculture, combustion) essential for long-term trend reversal (source: [[midolo_2026_denser_vegetation]])
- Mountain habitats: warming thermophilisation is detectable and likely to accelerate — these communities are earliest warning indicators (source: [[midolo_2026_denser_vegetation]])

## Related pages

- [[vegetation_greenness_trends]]
- [[plant_functional_traits]]
- [[functional_diversity]]
- [[phenology]]
- [[forest_disturbances]]
- [[species_distribution_models]]
- [[topographic_microclimate]]
