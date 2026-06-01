---
title: "A climate-induced tree species bottleneck for forest management in Europe"
authors:
  - Johannes Wessely
  - Franz Essl
  - Konrad Fiedler
  - Andreas Gattringer
  - Bernhard Hülber
  - Olesia Ignateva
  - Dietmar Moser
  - Werner Rammer
  - Rupert Seidl
  - Stefan Dullinger
year: 2024
tags:
  - forest-ecology
  - machine-learning
keywords:
  - species distribution models
  - tree species
  - climate change
  - bottleneck
  - forest management
  - silviculture
  - RCP scenarios
  - continuous suitability
  - mixed forests
  - ecosystem services
status: read
---

## 1. Title and Authors

**A climate-induced tree species bottleneck for forest management in Europe**
Wessely et al. (2024), *Nature Ecology & Evolution* 8:1109–1117. DOI: 10.1038/s41559-024-02406-8

## 2. Quick Overview

- **Why is it relevant?** Introduces the critical concept that forest managers cannot select tree species for planting based on current or end-of-century suitability alone — species must be climatically suitable throughout the entire rotation period (~100 years), creating a "bottleneck" that dramatically shrinks the usable tree species pool.
- **What was done?** SDMs for 69 European tree species at 1 km resolution, decadal steps 2020–2100, under RCP 2.6/4.5/8.5; identified species continuously suitable throughout the century as the management-relevant pool.
- **What is the main outcome?** Climate change shrinks the continuously suitable species pool by 33–49% relative to the current pool; only 3.18/3.53/2.56 species per km² with high timber/carbon/biodiversity potential remain viable for planting today.

## 3. Main Goal and Fundamental Concept

The key conceptual innovation is **temporal continuity**: a species planted today must survive under current climate AND climate in 2120 (rotation period). Time-slice SDMs comparing "now" vs "2090" overestimate the usable pool because: (a) some species suitable today will become unsuitable mid-century; (b) species only suitable under future conditions cannot be planted today. The "bottleneck" is the intersection of suitability across all decades 2020–2100 — inevitably smaller than either endpoint. The bottleneck worsens at faster rates of change and longer planning horizons.

## 4. Technical Approach

- **Species data**: 238,080 plots from [[mauri_2017_EU_tree_data]] (249,410 plots) + ICP Forest (18,367 plots); combined to 1 km INSPIRE grid; 69 species with ≥50 occurrences; both natural and planted occurrences included
- **Climate variables** (4, CHELSA 1980–1999 baseline; CORDEX future downscaled):
  - Mean annual temperature
  - Temperature seasonality
  - Precipitation seasonality
  - Ombrothermic index (drought stress)
- **SDM method**: biomd2 ensemble (GLM + GAM + Random Forest + Boosted Regression Trees); 70/30 split, 3 replicates; TSS evaluation; weighted ensemble mean; binary threshold at max-TSS
- **Futures**: RCP 2.6, 4.5, 8.5; decadal steps 2020–2090; CNRM-ALADIN53/CNRM-CM5 model
- **Bottleneck quantification**: For each cell, count species with binary suitability=1 in ALL decades 2020–2100 → management-available pool; contrasted with pools at 2020–2029 (current) and 2090–2099 (future)
- **Function scoring**: Literature synthesis rating each of 69 species as high/medium/low for timber, carbon storage, biodiversity

## 5. Distinctive Features

- **Novel temporal framing**: No prior study quantified continuously suitable species vs time-slice endpoints at pan-European scale
- **Management translation**: Results directly actionable — names specific species pools per km² for practical silvicultural planning
- **Interactive map**: Results available at bdc.univie.ac.at/forest-bottleneck
- **Three ecosystem functions**: Timber + carbon + biodiversity multifunctionality assessed simultaneously

## 6. Experimental Setup and Results

| Metric | RCP 2.6 | RCP 4.5 | RCP 8.5 |
|--------|---------|---------|---------|
| Species continuously suitable (avg/km²) | 9.8 | 9.4 | 8.4 |
| Loss vs current pool | −33% | −38% | −49% |
| High-timber-potential sp./km² | — | 3.18 | — |
| High-carbon-potential sp./km² | — | 3.53 | — |
| High-biodiversity-potential sp./km² | — | 2.56 | — |
| Area with ≥2 multifunc. species | — | 56.3% | — |

- **Spatial patterns**: Central-eastern Europe least affected (−31%); Northern Europe most affected (−52%); mountain ranges buffer loss (−33.5% vs −40.3% lowlands)
- **SW Europe and hemiboreal zone most vulnerable** due to both strong warming and current species at warm-edge limits
- **End of century gains**: +85.5% new species become suitable at century end (RCP 4.5) but unavailable for planting now
- **Rate of loss**: −6.5% per decade relative to current pool (accumulating to −38% by 2090, RCP 4.5)

## 7. Advantages and Limitations

**Strengths**
- Conceptually rigorous: temporal continuity is the correct framing for management under non-stationary climate
- Uses best available European tree data ([[mauri_2017_EU_tree_data]])
- Results quantitatively useful for silvicultural planning and EU forest policy

**Critical Limitations**
- **SDM assumptions**: Niche stationarity assumed; species dispersal, biotic interactions, intraspecific adaptation not modelled — could make results either too pessimistic (adaptation) or too optimistic (dispersal barriers)
- **No extremes**: Uses climatic averages, not extremes that drive acute mortality — averages are adequate for long-term but miss drought pulses and frost events
- **Single climate model chain**: CNRM-ALADIN53 only; model uncertainty not fully represented
- **Planted occurrences included**: SDMs trained on planted occurrences may overestimate climatic tolerances beyond realised niches
- **Species richness ≠ adequate diversity**: 9.4 species continuously suitable may still be phylogenetically or functionally redundant — mixedness requires more than count
- **No non-native species**: Excluded entirely; may underestimate management options (but wisely conservative)
- **DBH/size not distinguished**: All occurrences treated equally; no separation of regeneration vs mature stands

## 8. Conclusion

Wessely et al. (2024) deliver a key reframing for European forest management under climate change: not "what species are suitable now or in 2090?" but "what species remain suitable throughout the planting-to-harvest rotation?" This bottleneck concept reduces the deployable species pool by a third to half, with the sharpest losses in already species-poor northern and southwestern Europe. The study is directly relevant to the wiki's forest ecology strand — particularly for understanding why mixed-species reforestation, while theoretically desirable, may be climatically constrained. It relies heavily on [[mauri_2017_EU_tree_data]] as the ground truth input and complements SDM literature in [[species_distribution_models]] and [[dyderski_2025_species_shift]].

## Related Pages

- [[species_distribution_models]]
- [[dyderski_2025_species_shift]]
- [[mauri_2017_EU_tree_data]]
- [[drought_mortality]]
- [[forest_disturbances]]
- [[thom_2026_disturbance_suitability]]
- [[noce_2023_altitude_shift_tree_italy]]
- [[tree_species_bottleneck_concept]]
