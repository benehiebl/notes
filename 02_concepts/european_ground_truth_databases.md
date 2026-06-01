---
name: european_ground_truth_databases
description: Pan-European vegetation plot and tree occurrence databases (EU-Forest, sPlotOpen, ICP Forest, NFIs) as ground truth for SDMs, RS calibration, and biodiversity monitoring
metadata:
  type: reference
---

# European Ground Truth Databases

**Summary**: Several harmonised pan-European databases provide field-based tree occurrence, species composition, and plant trait data — essential ground truth for species distribution models, RS product validation, and biodiversity monitoring at continental scale.

**Sources**: [[mauri_2017_EU_tree_data]], [[sabatini_2021_splot]], [[wessely_2023_tree_species_bottleneck]], [[miettinen_2025_forest_maps_europe]], [[national_forest_inventory]]

**Last updated**: 2026-05-31

---

## Key Databases

### EU-Forest (Mauri et al. 2017) [[mauri_2017_EU_tree_data]]
- **Content**: ~249,410 plots, 242 tree species, presence/absence + DBH class
- **Coverage**: 30 European countries; 96% from NFIs, remainder from Forest Focus + Biosoil
- **Resolution**: 1 km × 1 km INSPIRE grid (aggregated from finer-scale NFI plots for privacy)
- **Access**: Open, figshare, CC BY 4.0
- **Limitations**: Presence-only (no true absences), includes planted occurrences, strong national density imbalance (Spain 74k plots vs Bulgaria 220), no survey-year standardisation
- **Use case**: Standard input for pan-European tree SDMs; calibration base for RS forest maps

### sPlotOpen (Sabatini et al. 2021) [[sabatini_2021_splot]]
- **Content**: 95,104 vegetation plots, 42,677 vascular plant taxa, presence+absence, TRY trait CWMs (18 traits)
- **Coverage**: 114 countries, 105 databases; 1888–2015
- **Resolution**: Plot-level (0.01–40,000 m² plot size); spatial location precision varies
- **Access**: Open CC license; three replicate environmentally balanced subsets (~50,000 plots each)
- **Limitations**: Heterogeneous protocols; residual geographic bias to temperate zones; no direct RS attribution
- **Use case**: Global macroecology, functional diversity mapping, RS ground truth for biodiversity monitoring

### ICP Forest (International Co-operative Programme on Assessment and Monitoring of Air Pollution Effects on Forests)
- **Content**: Long-term forest health monitoring; 18,367 plots, 132 species, 38 European countries; 1987–2017
- **Access**: Partial (data used in Wessely et al. 2024 via agreement)
- **Use case**: SDM complement to EU-Forest; provides time-series repeat visits unlike EU-Forest

### National Forest Inventories (NFIs) [[national_forest_inventory]]
- National programmes with typically stricter measurement standards and plot density than EU-Forest aggregates
- Italy (INFC): 7,000+ plots at national scale; used in [[mattioli_2025_carta_forestale]], [[amico_2025_nfi_italy]]
- Germany: basis for [[wegler_2025_tree_species_germany]], [[blickensdörfer_2024_tree_species]]
- NFI data at original plot resolution (not 1 km) preferred for regional RS calibration

## Comparison Table

| Database | Scale | Species type | Absences? | Traits? | Open? |
|----------|-------|--------------|-----------|---------|-------|
| EU-Forest | Pan-European (1 km) | Trees only | No | No | Yes |
| sPlotOpen | Global (plot) | All vascular plants | Yes | 18 CWMs | Yes |
| ICP Forest | Pan-European (plot) | Trees + shrubs | No | No | Restricted |
| National NFIs | National (plot) | Trees (main) | Design-based | No | Varies |

## Critical Caveats for RS Applications

- **Planted vs natural**: EU-Forest and ICP Forest do not distinguish natural from planted stands — important for climate niche interpretation and RS training data quality
- **Temporal mismatch**: EU-Forest surveys span decades; matching to a single RS baseline year introduces pseudo-change
- **1 km aggregation irreversible**: Sub-km species turnover is undetectable in EU-Forest; training RS classifiers at 10–30 m resolution with 1 km labels risks spatial mismatch
- **sPlotOpen plot size heterogeneity**: Plots range from 0.01 to 40,000 m²; intersecting with RS pixels requires careful scale matching
- **Absence interpretation**: EU-Forest "absence" in a cell reflects lack of detection in NFI plots, not confirmed ecological absence — cannot be used as true negative training data without caution

## Use in This Wiki's Research Context

- EU-Forest is the standard occurrence database for European tree SDMs (e.g., [[wessely_2023_tree_species_bottleneck]], [[dyderski_2025_species_shift]])
- sPlotOpen is relevant as potential ground truth for functional diversity mapping from S2 spectral heterogeneity ([[spectral_diversity_biodiversity]])
- For Italian-scale work, national NFI data (INFC, CFI2020) are preferred over EU-Forest due to higher resolution and Italian-specific survey protocols

## Related Pages

- [[national_forest_inventory]]
- [[species_distribution_models]]
- [[tree_species_mapping]]
- [[functional_diversity]]
- [[spectral_diversity_biodiversity]]
- [[mauri_2017_EU_tree_data]]
- [[sabatini_2021_splot]]
