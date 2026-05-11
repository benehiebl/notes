---
title: Altitudinal shifting of major forest tree species in Italian mountains under climate change
authors:
  - Noce, Sergio
  - Cipriano, Cristina
  - Santini, Monia
year: 2023
source: noce_2023_altitude_shift_tree_italy
tags:
  - species-distribution-models
  - MaxEnt
  - climate-change
  - altitudinal-shift
  - Italy
  - forest-tree-species
  - mountain-forests
  - Apennines
  - Alps
  - forest-ecology
keywords:
  - habitat-suitability
  - RCP-4.5
  - RCP-8.5
  - INFC-2005
  - bioclimatic-indicators
  - European-beech
  - Silver-fir
  - European-larch
  - Turkey-oak
  - treeline
  - VHR-REA-IT
status: summarized
---

## Title and Authors of the Paper

*Altitudinal shifting of major forest tree species in Italian mountains under climate change* — Sergio Noce, Cristina Cipriano, Monia Santini (2023), Frontiers in Forests and Global Change, 6, 1250651. DOI: 10.3389/ffgc.2023.1250651. Published 08 September 2023.

## Quick Overview

- **Why is it relevant?** Italian mountain forests are highly sensitive to climate change but species-specific projections at high spatial resolution and for the full Italian altitudinal range were lacking.
- **What was done?** Applied MaxEnt SDMs to 20 major Italian forest tree species using INFC 2005 occurrence data and very-high-resolution (2.2 km) downscaled climate projections (RCP 4.5 and 8.5; 2021–2050) across five Italian mountain sections.
- **What is the main outcome?** Most species face contraction of their altitudinal suitability range; silver fir is the most consistently vulnerable; European larch and Turkey oak are notable winners; the tree line is expected to shift upward broadly; Northern/Northwestern Apennines are the most impacted region.

## Main Goal and Fundamental Concept

Italian mountain forests provide critical ecosystem services (timber, carbon, biodiversity, hydro-geological protection) and are uniquely exposed to warming because mountain ecosystems are temperature-limited and warm faster than lowlands. The study projects how climate suitability for 20 tree species will shift altitudinally under two RCP scenarios to inform conservation and silvicultural adaptation.

**Species studied (20 total — 13 broadleaved, 7 needleleaved):**
- Key broadleaved: *Fagus sylvatica* (European beech), *Quercus cerris* (Turkey oak), *Quercus ilex* (Holm oak), *Quercus pubescens* (Downy oak), *Castanea sativa* (Chestnut), *Fraxinus ornus* (Manna ash), *Ostrya carpinifolia* (Hop hornbeam), *Carpinus betulus* (European hornbeam), *Acer campestre* (Field maple)
- Key coniferous: *Abies alba* (Silver fir), *Picea abies* (Norway spruce), *Larix decidua* (European larch), *Pinus cembra* (Swiss stone pine), *Pinus halepensis* (Aleppo pine), *Pinus pinaster* (Maritime pine), *Pinus sylvestris* (Scots pine)

## Technical Approach

**Occurrence data:**
- INFC 2005 (Second Italian National Forest Inventory): systematic 1 km × 1 km sampling grid; presence-only; freely available for research
- Rarefied at 20 km distance to reduce spatial autocorrelation
- Sample sizes: 87 (*Pinus cembra*) to 2,111 (*Quercus pubescens*)

**Environmental predictors (21 total):**
- **Climate**: VHR-REA_IT dataset (2.2 km resolution); ERA5 downscaled via COSMO-CLM; 4 variables (Tmax, Tmin, Tmean, Precipitation) at hourly resolution → converted to 19 WorldClim-style bioclimatic indicators (BIO1–BIO19 analogs); historical period 1991–2020
- **Topographic**: EU-DEM (25 m, Copernicus CLMS) → altitude + slope
- **Collinearity screening**: Pearson |r| > 0.7–0.9 excluded; SDMtoolbox feature selection

**Modelling:**
- **MaxEnt v3.4.3** with SDMtoolbox v2.5; ODMAP protocol followed
- Feature classes: Linear, Quadratic, Product, Hinge, Threshold; regularization multiplier 0.5
- Background selection: Minimum Convex Polygon, 500 km buffer distance
- 5 replicates; spatial and non-spatial segregation; 20% random test percentage
- Model selection: AUC → True Skill Statistic (TSS) → Omission Error Rate (OER)
- Clamping enabled for future projections (prevents extrapolation beyond calibration range)

**Future projections:**
- VHR-PRO_IT (COSMO-CLM simulation, CMCC-CM driver); RCP 4.5 and RCP 8.5; 2021–2050
- Bias-corrected against VHR-REA_IT: temperature = additive correction; precipitation = multiplicative correction (capped at ratio < 4)
- Results expressed as anomaly (%) between future and historical mean suitability per altitude band (150m bands)

**Study regions (Italian Ecoregion Map, Blasi et al. 2014/2018):**
- Section 1: Western Alps (1,794,031 ha; 26–4,790 m)
- Section 2: Central and Eastern Alps (3,656,143 ha; 25–3,950 m)
- Section 3: Northern and Northwestern Apennines (3,880,014 ha; 10–2,142 m)
- Section 4: Central Apennines (2,639,776 ha; 0–2,850 m)
- Section 5: Southern Apennines (1,943,464 ha; 32–2,250 m)

## Key Results

**Species-level outcomes across all sections:**

| Species | General trend | Key finding |
|---------|--------------|------------|
| **Silver fir** (*Abies alba*) | **Strong loser** | Consistent loss across all 5 sections and both scenarios (−20 to −45%); most vulnerable species |
| **European beech** (*Fagus sylvatica*) | **Mixed** | Loss in Northern Apennines; gains above 1,500m in Central and Southern Apennines; upward shift of tree line |
| **European larch** (*Larix decidua*) | **Winner in Alps** | Strong gains (+33 to +40%) especially in Western and Central Alps; extends above current tree line |
| **Turkey oak** (*Quercus cerris*) | **Winner in Apennines** | Gains in suitability across Apennines (+11 to +38%); thermophilous broadleaved expanding upward |
| **Maritime pine** (*Pinus pinaster*) | **Winner in Southern Apennines** | +15 to +46% in Southern Apennines; candidate for reforestation |
| **Norway spruce** (*Picea abies*) | **Mixed** | Gains at high altitudes (>1,200m) in Alps; gains mainly above threshold |
| **Swiss stone pine** (*Pinus cembra*) | **Range shift** | Optimal range shifts ~450m upward; high AUC (0.963) = reliable projection |
| **Aleppo pine** (*Pinus halepensis*) | **Loser** | Major losses in most sections (already near thermal limit at Mediterranean margins) |
| **Common hazel** | **Loser** | −27 to −57% in Alps; substantial losses |
| **Holm oak** (*Quercus ilex*) | **Loser in Alps** | Suitability declines in north; thermophilous but not Alpine |

**Altitudinal shift pattern (consistent across sections):**
- Most species: suitability decreases at lower elevations, increases above mid-elevations → upward contraction/shift
- Tree line expected to move upward: larch and spruce gain suitability above current tree line in Alps; beech gains above 1,500m in Central/Southern Apennines
- Consequence: loss of nival vegetation and alpine grassland habitats; loss of area of high-mountain ecosystems

**Geographic vulnerability:**
- **Northern and Northwestern Apennines**: greatest and most widespread impacts on ALL species; highest vulnerability to climate change
- Alpine sections: generally less severe, but Silver fir consistently declines even here

**RCP 4.5 vs. RCP 8.5:**
- RCP 4.5 generally slightly better outcomes; RCP 8.5 more extreme
- Several species show **divergent projections** between scenarios (Manna ash, Hop hornbeam, Maritime pine) — adds uncertainty; useful as upper/lower bounds

## Model Performance

- AUC: 0.771 (Downy oak, broad generalist) to 0.963 (Swiss stone pine, narrow specialist)
- Pattern: higher AUC for species with smaller, more specific ranges; lower for generalists — consistent with known MaxEnt behavior
- TSS and OER used as secondary selection criteria
- All 20 species retained suitable model performance for projection

## Advantages and Limitations

**Advantages:**
- Very high spatial resolution climate data (2.2 km) — much finer than standard WorldClim (1 km at equator but coarser in practice); better captures topographic heterogeneity
- ODMAP protocol ensures reproducibility and transparent reporting
- Altitudinal band analysis (150m bands) directly translates to spatial management information
- Two RCP scenarios bracket the uncertainty range

**Limitations:**
- Occurrence data from INFC 2005 (not 2015) — temporal mismatch with 1991-2020 climate baseline (~20yr lag)
- INFC provides only SW corner of 1km grid cell → introduces positional uncertainty (considered negligible at 2.2km climate resolution)
- SDMs assume stationarity: climate-distribution relationships of 1991-2020 projected forward → no adaptation, migration, or biotic interaction changes
- Soil, disturbance, management, and wind effects not included
- Species dispersal limitations not modelled — suitability ≠ actual occupancy
- Short projection horizon (2021-2050): climate signal still relatively modest; longer projections would show more divergent outcomes

## Silvicultural and Conservation Implications

1. **Diversify forest stands**: move from monocultures toward mixed stands → improve resilience to disturbances and species-specific climate impacts
2. **Prioritise winners for reforestation**:
   - Alps: European larch (strong gains); Norway spruce (high-altitude gains)
   - Apennines: Turkey oak, Maritime pine (Southern), Pedunculate oak (Central)
3. **Phase out highly vulnerable species from low-altitude plantings**:
   - Silver fir: reduce at low elevations across all sections
   - Aleppo pine, Scots pine: loss in most Apennine sections
4. **Protect high-altitude refugia** and manage treeline zones carefully — ski facilities and new slopes near current tree line upper limit should be avoided
5. **Monitor** upward-shifting species via repeated NFI surveys and RS change detection

## Conclusion

Noce et al. (2023) demonstrate that Italian mountain forests face divergent but predominantly negative climate change impacts on tree species suitability over 2021–2050. Silver fir is the most consistently vulnerable species across all Italian mountain regions; European larch and Turkey oak show potential gains that could play significant roles in maintaining forest cover. The tree line is projected to shift upward in most sections, impacting European beech (the keystone high-altitude species in Italy) negatively at lower elevations while creating opportunities above 1,500m. The Northern and Northwestern Apennines emerge as the region of greatest vulnerability. The results provide operational guidance for adaptive silviculture and species selection for Italian mountain forests.

## Related Work & Obsidian Links

- [[species_distribution_models]]
- [[leaf_habit_latitudinal_gradient]]
- [[forest_disturbances]]
- [[national_forest_inventory]]
- [[topographic_microclimate]]

- [[gasparini_2022_nfi_italy]] — INFC 2005 is the occurrence data source for all 20 species in this study; Gasparini et al. 2022 describes the INFC 2015 methodology which supersedes it
- [[hiebl_2025_pretraining]] — both work in Italian National Parks and mountain forests; Hiebl et al. map EVE (*Quercus ilex*, etc.) cover; Noce et al. project that Holm oak (*Q. ilex*) suitability declines in the Alps but the Turkey oak (thermophilous broadleaved) gains — relevant for interpreting EVE expansion dynamics
- [[bricca_2026_topo_diversity]] — Bricca et al. show temperature drives functional diversity in Italian forests; Noce et al. show temperature-driven altitudinal range shifts; together they demonstrate that both diversity and composition of Italian mountain forests are climate-sensitive
- [[grünig_2026_climate_change_disturbances_forest]] — both address climate change impacts on European forests; Grünig et al. focus on disturbance regimes; Noce et al. on habitat suitability — the two are coupled (disturbance opens habitat for range-expanding species)
- [[jin_2023_drivers_differentiation_evergreen]] — Jin & Qian document the latitudinal EV/deciduous gradient; Noce et al. project that thermophilous species (Turkey oak, which is deciduous) will expand while cold-adapted species (Silver fir, beech) contract — an altitudinal analog of that latitudinal process

## Related pages

- [[species_distribution_models]]
- [[leaf_habit_latitudinal_gradient]]
- [[topographic_microclimate]]
- [[forest_disturbances]]
- [[national_forest_inventory]]
- [[gasparini_2022_nfi_italy]]
- [[hiebl_2025_pretraining]]
- [[bricca_2026_topo_diversity]]
- [[grünig_2026_climate_change_disturbances_forest]]
- [[jin_2023_drivers_differentiation_evergreen]]
