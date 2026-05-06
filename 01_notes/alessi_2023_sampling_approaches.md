---
title: "Probabilistic and preferential sampling approaches offer integrated perspectives of Italian forest diversity"
authors:
  - Alessi, Nicola
  - Bonari, Gianmaria
  - Zannini, Piero
  - Jiménez-Alfaro, Borja
  - Chiarucci, Alessandro
year: 2023
source: alessi_2023_sampling_approaches
tags:
  - forest-ecology
  - remote-sensing
status: read
---

# Alessi et al. 2023 — Probabilistic and Preferential Sampling for Italian Forest Diversity

## Title and Authors
**Probabilistic and preferential sampling approaches offer integrated perspectives of Italian forest diversity**
Nicola Alessi, Gianmaria Bonari et al. — *Journal of Vegetation Science*, 2023

## Quick Overview
- **Why is it relevant?** Addresses the fundamental question of how to sample plant diversity data for forest monitoring, with direct implications for ground truth collection strategies in remote sensing studies.
- **What was done?** Compared probabilistic (systematic, unbiased) and preferential (opportunistic) vegetation plot sampling using 804 vs. 16,259 Italian forest plots across three major forest types.
- **What is the main outcome?** Neither approach alone is sufficient — probabilistic sampling better estimates species richness while preferential sampling better detects forest-specialist species and biodiversity hotspots; combined use is recommended.

## Main Goal and Fundamental Concept
The study evaluates how different vegetation sampling strategies perform for documenting community diversity in Italian forests. The core idea is that sampling bias affects which aspects of biodiversity are captured, and that probabilistic and preferential approaches are complementary rather than competing.

## Technical Approach
- **Data:** 804 probabilistic plots + 16,259 preferential plots, balanced to 201 plots per bootstrap subset (1000 iterations)
- **Balancing:** Controlled for plot size, geographic position, and vegetation type
- **Metrics:** Shared/exclusive indicator species, multivariate space overlap (DCA), spatially-constrained rarefaction curves
- **Performance index:** Ratio of additional information gained to total information per sampling approach
- **Forest types:** Broadleaved deciduous, evergreen, and coniferous forests across Italy

## Distinctive Features
- Novel workflow using vegetation-plot exclusivities and commonalities across sampling approaches
- Explicitly compares large-scale biodiversity assessments using fundamentally different sampling philosophies
- Demonstrates that azonal and specialist forest communities are detectable only via preferential sampling

## Experimental Setup and Results
- **Probabilistic approach:** Better at estimating overall species richness, alpha and beta diversity, spatially representative
- **Preferential approach:** Better at detecting forest-specialist indicator species and biodiversity hotspots
- **No single winner:** Each approach captures exclusive species assemblages absent from the other
- **Recommendation:** Combined use for national conservation planning and monitoring

## Advantages and Limitations
- **Advantages:** Large Italian dataset; rigorous bootstrapping; practical guidance for monitoring design
- **Limitations:** Results specific to Italian temperate forests; extrapolation to other regions requires caution; preferential dataset quality is heterogeneous

## Conclusion
Italian forest plant diversity monitoring requires integrating both probabilistic (unbiased, representative) and preferential (specialist-detection, hotspot) sampling. The study provides methodological guidance for national-scale biodiversity monitoring design, directly relevant to ground truth collection for RS-based forest mapping and SDM workflows.

## Related pages
- [[national_forest_inventory]]
- [[species_distribution_models]]
- [[sampling_bias_remote_sensing]]
