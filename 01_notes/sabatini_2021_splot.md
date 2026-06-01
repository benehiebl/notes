---
title: "sPlotOpen – An environmentally balanced, open-access, global dataset of vegetation plots"
authors:
  - Francesco Maria Sabatini
  - Jonathan Lenoir
  - Tarek Hattab
  - Milan Chytrý
  - Jürgen Dengler
  - Helge Bruelheide
  - "et al. (166 authors total)"
year: 2021
tags:
  - forest-ecology
  - remote-sensing
keywords:
  - vegetation plots
  - sPlotOpen
  - plant communities
  - global biodiversity
  - ground truth
  - functional traits
  - TRY database
  - environmental stratification
  - macroecology
  - remote sensing validation
status: read
---

## 1. Title and Authors

**sPlotOpen – An environmentally balanced, open-access, global dataset of vegetation plots**
Sabatini, Lenoir, et al. (2021), *Global Ecology and Biogeography* 30:1740–1764. DOI: 10.1111/geb.13346

## 2. Quick Overview

- **Why is it relevant?** sPlotOpen is the largest open-access global dataset of vegetation plots, providing species composition, plant functional traits, and plot-level metadata — valuable as RS ground truth for biodiversity mapping.
- **What was done?** Environmentally balanced resampling of the full sPlot database (1.1M plots) using a global climatic+soil PCA, then securing open-access permissions for 95,104 plots from 105 regional databases across 114 countries.
- **What is the main outcome?** sPlotOpen: 95,104 plots, 42,677 vascular plant taxa, 18 community-weighted plant trait means/variances from TRY, three replicate resampled subsets of ~50,000 plots each for robust macroecological analysis.

## 3. Main Goal and Fundamental Concept

Existing global plant occurrence databases (GBIF, BIEN, GIFT) record presence of individual species but not co-occurrence, community composition, or species absences. Vegetation-plot data record all co-occurring species in a delimited area, providing true absence information — crucial for SDMs, biodiversity monitoring, and testing biotic interaction hypotheses. However, the sPlot database (1.1M plots) was geographically and environmentally biased (Europe and temperate zones overrepresented) and entirely restricted-access. sPlotOpen addresses both issues: environmental balancing + open release.

## 4. Technical Approach

- **Starting point**: sPlot v2.1 — 1,121,244 plots, 110 databases; after removing wetland/anthropogenic plots: 799,400 usable
- **Environmental stratification**:
  - Global PCA on 30 climate (CHELSA 19 bioclim + GDD1 + GDD5) + 7 soil variables for all terrestrial 2.5-arcmin cells
  - PC1 (47%) + PC2 (23%) = 70% environmental variance
  - 100×100 grid on PC1–PC2 space; resampling to equalise plot density per environmental cell
- **Three resampled datasets** (c. 50,000 plots each) serve as replicates to quantify method uncertainty
- **Open-access negotiation**: Permissions secured from data holders of 105 databases; 95,104 plots released
- **Functional traits**: Intersection with TRY Plant Trait Database → 18 traits (leaf area, SLA, leaf N, wood density, etc.) as community-weighted means and variances per plot

## 5. Distinctive Features

- **First environmentally balanced global plot dataset**: All prior global datasets are point-occurrence presence-only; sPlotOpen provides presence+absence co-occurrence at plot scale
- **Replicate structure**: Three subsets allow uncertainty quantification in macroecological analyses
- **TRY integration**: Community-weighted trait means allow functional diversity mapping directly
- **Remote sensing synergy**: Explicitly designed for RS ground truth intersection; 0.01–40,000 m² grain size range spans most RS pixel sizes

## 6. Experimental Setup and Results

| | sPlot database | sPlotOpen |
|---|---|---|
| Total plots | 1,121,244 | 95,104 |
| Databases | 110 | 105 (open-release subset) |
| Countries | — | 114 |
| Vascular taxa | — | 42,677 |
| Trait records (CWM) | — | 18 traits per plot |
| Temporal coverage | 1888–2015 | 1888–2015 |
| Replicate datasets | — | 3 × ~50,000 |

- Spatial resolution range: 0.01 m² to 40,000 m² (plot sizes vary widely)
- Mid-latitude temperate regions remain overrepresented even after stratification — tropical/subtropical coverage limited

## 7. Advantages and Limitations

**Strengths**
- True presence+absence data at plot scale: unique among global plant databases
- Environmental stratification reduces most severe geographic biases
- TRY trait integration enables functional diversity analysis
- Designed explicitly for RS cross-referencing and macroecological analysis
- Open CC license enabling wide reuse

**Critical Limitations**
- **Heterogeneous protocols**: 105 different databases with varying plot sizes (0.01–40,000 m²), survey standards, and recording dates — inter-database comparability is limited
- **Residual geographic bias**: Despite stratification, tropical regions remain underrepresented; sampling cannot compensate for fundamental data scarcity
- **Static plots**: Most plots surveyed once, not time series; limited for change detection
- **No remotely sensed attribution**: Plots not intersected with satellite data by default; users must handle spatial joins
- **Incomplete species sampling**: Smaller plots (<10 m²) miss rare species; coverage probability varies with plot size
- **Not representative at local scale**: sPlotOpen is designed for global macroecology, not as a representative sample of local or regional vegetation — SDM applications at regional scale need caution
- **Missing wetland/cropland vegetation**: Explicitly excluded; limits biodiversity assessment in agricultural landscapes

## 8. Conclusion

sPlotOpen is a uniquely valuable global plant community dataset providing co-occurrence, abundance, and functional trait data at plot scale — filling a gap left by occurrence-only databases. For the wiki's purposes, it is relevant primarily as: (1) potential RS ground truth for functional diversity and vegetation type mapping; (2) a data source for SDMs that need true absence data (unlike GBIF); (3) a complement to EU-Forest [[mauri_2017_EU_tree_data]] for European applications. Its limitations (heterogeneous plot sizes, no RS intersection by default, tropical gaps) mean it is most powerful for continental to global macroecological analyses rather than local RS calibration.

## Related Pages

- [[functional_diversity]]
- [[plant_functional_traits]]
- [[species_distribution_models]]
- [[national_forest_inventory]]
- [[mauri_2017_EU_tree_data]]
- [[european_ground_truth_databases]]
- [[ebv_biodiversity_monitoring]]
