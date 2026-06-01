---
name: national_forest_inventory
description: National Forest Inventories — purpose, sampling design principles, variables measured, and role as ground truth for remote sensing and forest policy
type: reference
tags:
  - forest-ecology
  - remote-sensing
  - methodology
---

# National Forest Inventory (NFI)

**Summary**: National Forest Inventories (NFIs) are systematic, large-scale sample surveys that provide authoritative statistics on the extent, structure, composition, and functions of a country's forests, serving as the primary ground truth for forest remote sensing and international reporting.

**Sources**: [[gasparini_2022_nfi_italy]], [[mattioli_2025_carta_forestale]], [[miettinen_2025_forest_maps_europe]], [[amico_2025_nfi_italy]], [[bell_2024_hindcasting_forest_structure]], [[blickensdörfer_2024_tree_species]], [[klehr_2025_synthetic_data]], [[qin_2026_forest_cover]], [[mauri_2017_EU_tree_data]], [[sabatini_2021_splot]]

**Last updated**: 2026-05-31

---

## Purpose

NFIs serve multiple simultaneous objectives:
- **Productive function**: estimate growing stock volume, biomass, annual increment, wood availability
- **Carbon accounting**: quantify forest carbon pools (biomass, deadwood, litter, soil) for UNFCCC/Kyoto compliance
- **Ecosystem characterisation**: biodiversity, forest health, structure, management, ownership, protective functions
- **Policy support**: national and international reporting (FAO-FRA, SoEF, CBD, SDGs)

## Sampling Design Principles

Modern NFIs (including Italy's INFC) use a **multi-phase systematic sampling** design (source: [[gasparini_2022_nfi_italy]]):

- **Systematic grid**: points placed on a regular grid (e.g., 1 km × 1 km in INFC) over national territory
- **Phase 1**: photo/image interpretation — classify all grid points by land use/land cover; identify forest vs non-forest
- **Phase 2**: subset of forest points further classified (forest type, canopy cover, etc.)
- **Phase 3**: subset visited on the ground; plots measured in detail

This multi-phase approach is efficient: expensive field measurements are concentrated on confirmed forest points. The new Italian NFI (IFNI) adopts **tessellation stratified sampling** as a more spatially balanced probabilistic design, enabling annual rolling-panel estimates rather than periodic inventories (source: [[amico_2025_nfi_italy]]).

Plot designs use **concentric circular plots** of different radii for different tree size classes (e.g., large trees on a 13 m radius plot, small trees/understory on a 4 m radius plot; source: [[gasparini_2022_nfi_italy]]).

## Key Variables Measured

| Domain | Examples |
|--------|---------|
| **Area** | Forest/OWL area by type, region, ownership |
| **Growing stock** | Volume by species, diameter class, forest type |
| **Biomass** | Aboveground biomass, carbon pools |
| **Deadwood** | Standing dead, lying deadwood, stumps |
| **Increment** | Annual volume and biomass increment |
| **Structure** | DBH distributions, height, age class, silvicultural system |
| **Biodiversity** | Species composition, deadwood, protected areas |
| **Health** | Damage agents, crown condition |
| **Carbon** | All five carbon pools (IPCC definition) |

## Italian NFI (INFC)

Three surveys completed:

| Inventory | Reference Year | Key Change |
|-----------|---------------|-----------|
| IFNI85 | 1985 | First Italian NFI; 3 km × 3 km grid |
| INFC2005 | 2005 | Three-phase design; FAO forest definition; carbon pools |
| INFC2015 | 2015 | Same methodology as INFC2005; +520,000 ha forest area |

INFC2015 headline results: 10,980,000 ha of forest (~37% of Italian territory); ongoing expansion into abandoned mountain/hilly agricultural land (source: [[gasparini_2022_nfi_italy]]).

## Forest Map of Italy (CFI2020) — Cartographic Counterpart to INFC

CFI2020 (Carta Forestale d'Italia 2020) is Italy's first national forest map at 1:10,000 scale — a **cartographic product** (wall-to-wall vector polygons), distinct from the statistical INFC sampling survey (source: [[mattioli_2025_carta_forestale]]):

| | INFC (NFI) | CFI2020 |
|-|-----------|---------|
| **Type** | Statistical sampling survey | Cartographic wall-to-wall map |
| **Output** | Area estimates + confidence intervals + forest attributes | Vector polygon map (forest/non-forest + type) |
| **Spatial coverage** | Sample plots only (not spatially continuous) | Full national territory |
| **Minimum mapping unit** | N/A (plot-based) | 2,000–5,000 m² depending on definition |
| **Scale** | Not applicable | 1:10,000 |

**CFI2020 key facts:**
- ~850,000 polygons; mean size 12.50 ha; OA ≥ 90%
- Three simultaneous forest definitions: TUFF normative (art. 3; 2000 m²/20%/20m), FAO/statistical (art. 15; 5000 m²/10%/20m), and regional definitions
- Italian forest area 2020 (FAO definition): **10,126,903 ha** (+11.47% vs INFC2015's 9,085,186 ha)
- Largest forested regions: Toscana (1.19 Mha), Piemonte (0.98 Mha)
- Available via SINFor portal; update to reference year 2024 planned
- Nomenclature links local categories to INFC, European Forest Types (EFT), and Del Favero classification

**Forest definition comparison (Italy):**

| Definition | Min area | Min cover | Used by |
|-----------|---------|---------|--------|
| TUFF art. 3 (normative) | 2,000 m² | 20% | Legal/environmental protection |
| FAO / TUFF art. 15 | 5,000 m² | 10% | INFC, FAO-FRA, CFI2020 statistical |
| Regional laws | Variable | Variable | Regional planning |

The +11.47% difference between CFI2020 and INFC2015 reflects both real forest expansion (land abandonment especially in southern Italy) and methodological differences (photo-interpretation vs statistical sampling).

## NFI and Remote Sensing

NFIs provide the ground truth that remote sensing products need to be calibrated and validated against:
- **Wall-to-wall mapping**: NFI plot data + satellite imagery used to produce spatially continuous forest attribute maps
- **Biomass estimation**: NFI-derived allometric models combined with satellite-derived canopy structure
- **Forest type mapping**: NFI species composition data used to train/validate remote sensing classifiers
- **Change detection**: NFI temporal comparisons validate satellite-derived forest loss/gain estimates

Key limitation: NFI plots are typically not publicly georeferenced — spatial linkage to satellite data requires statistical modelling rather than direct plot matching (source: [[gasparini_2022_nfi_italy]]).

**Model-assisted estimation and wall-to-wall mapping (NFI + RS):**
- kNN imputation: predict forest attributes (AGB, volume, species composition) for every RS pixel by finding k nearest NFI plots in spectral feature space; uncertainty = std of k neighbors per pixel (source: [[miettinen_2025_forest_maps_europe]])
- Pan-European example: Miettinen et al. (2025) combined 14 national NFIs (~151,000 plots) with Sentinel-2 to produce 10m AGB, volume, and deciduous-coniferous proportion maps for 40 European countries (source: [[miettinen_2025_forest_maps_europe]])
- Key design insight: including plot geographic coordinates in the kNN feature space substantially reduces RMSE by ensuring local ecological calibration (source: [[miettinen_2025_forest_maps_europe]])
- Critical limitation: kNN regression-to-mean bias — systematically overestimates low values, underestimates high values; maps unsuitable for direct pixel-counting area statistics (source: [[miettinen_2025_forest_maps_europe]])
- NFI plot density is the key quality driver: Italy (0.05 plots/km² forest) performs worse than Germany (0.36 plots/km²); areas with no national NFI plots have potentially high and erratic biases (source: [[miettinen_2025_forest_maps_europe]])

**Temporal transferability of NFI+RS models:**
- Gradient Nearest Neighbor (GNN) imputation is robust for temporal transferability: hindcast and updated models perform comparably to full models at the plot and pixel level, with small but spatially structured differences at landscape scale (source: [[bell_2024_hindcasting_forest_structure]])
- Stationarity of the spectral-forest relationship over time is the key assumption: Landsat sensor drift, shifting phenology, and canopy lichen changes can alter spectral signals independently of forest structure (source: [[bell_2024_hindcasting_forest_structure]])
- This temporal robustness makes long-term continuous map records feasible from a temporally limited field inventory, enabling both retrospective (hindcast) and forward (updated) analyses (source: [[bell_2024_hindcasting_forest_structure]])

**Next-generation NFIs — enhanced annual monitoring:**
- Traditional periodic NFIs (10–15 year cycles) are insufficient to capture rapid climate-driven disturbance dynamics (source: [[amico_2025_nfi_italy]])
- The new Italian NFI (IFNI) transitions to annual estimates via rolling panel design, integrating Sentinel-2, LiDAR (IRIDE constellation), and ICP Forests monitoring; plot coordinates released for scientific use (source: [[amico_2025_nfi_italy]])
- Enhanced NFI explicitly targets large disturbance events (windstorm, wildfire, bark beetle, drought mortality) through annual change detection (source: [[amico_2025_nfi_italy]])
- Participatory co-design with stakeholders prior to field data collection is a key innovation — ensuring inventory outputs directly match policy and management information needs (source: [[amico_2025_nfi_italy]])

## International Reporting Standards

NFI data contribute to:
- **FAO Global Forest Resources Assessment (FRA)**: forest area, growing stock, biomass
- **State of Europe's Forests (SoEF)**: European-level forest monitoring
- **UNFCCC National Inventory Reports**: forest carbon accounting
- **CBD** (Convention on Biological Diversity): biodiversity indicators
- **SDGs**: Goal 15 (Life on Land)

## Linking NFI Plots to Satellite Pixels for ML Mapping

Two practical challenges arise when using NFI plot data as training reference for ML-based species/forest type mapping (source: [[blickensdörfer_2024_tree_species]]):

1. **Variable-radius plots**: NFI plots have radii that vary by species class — exact area is plot-dependent. Pixel–plot linking requires careful matching of pixel proportions against the plot species count distribution.
2. **Mixed-species plots**: most real forest plots contain multiple species. Restricting training to "pure" plots biases the model toward homogeneous stands and over-estimates pixel-level accuracy by 4–14 percentage points (source: [[blickensdörfer_2024_tree_species]]).

**Pseudo-labelling** (source: [[blickensdörfer_2024_tree_species]]) extends NFI training data:
- Use a model trained on pure plots to predict on mixed plots
- Retain pseudo-labels that match plot species occurrence in the neighbourhood as additional training samples
- Mixed-stand validation must be performed separately to report honest accuracy

**Synthetic linear mixing** (source: [[klehr_2025_synthetic_data]]) is a complementary approach when pure-pixel reference data are scarce:
- Linearly mix pure-pixel endmembers to generate synthetic spectral library with known mixture fractions
- ANN regression on synthetic data → continuous per-pixel species fractions
- Allows 9 species + "other" class with as few as **30 pure pixels per class** — viable for rare species missing from standard NFI databases

In cloud-prone regions, NFI provincial totals can validate large-area mapping products against direct pixel-level reference data (source: [[qin_2026_forest_cover]]): annual 30 m forest cover in southern China aligns with provincial NFI (R² 0.86), while finer-resolution products outperform 500 m alternatives.

## Pan-European Harmonised Products from NFI Data

Two open-access continental databases derive from or complement European NFIs:

**EU-Forest** (Mauri et al. 2017; source: [[mauri_2017_EU_tree_data]]): 249,410 plots, 242 tree species, 1 km × 1 km INSPIRE grid harmonised from 21 national NFIs + Forest Focus + Biosoil.
- De facto standard input for continental-scale tree SDMs and RS forest product validation
- Critical caveats: presence-only (no confirmed absences); does not separate natural from planted occurrences; strong national density imbalance (Spain 74k plots vs Bulgaria 220); static snapshot with heterogeneous survey years

**sPlotOpen** (Sabatini et al. 2021; source: [[sabatini_2021_splot]]): 95,104 vegetation plots, 42,677 vascular plant taxa, 18 community-weighted functional trait means from TRY; 114 countries.
- Designed for global macroecology and RS ground truth; differs from EU-Forest by recording all plant species (not only trees) with true absences, and linking to functional traits
- Complementary to NFI data: broader taxonomic scope but heterogeneous protocols and plot sizes (0.01–40,000 m²)

See [[european_ground_truth_databases]] for a full comparison table and RS-specific caveats for both databases.

## Related pages

- [[functional_diversity]]
- [[plant_functional_traits]]
- [[landsat]]
- [[tree_species_mapping]]
- [[sentinel_2]]
- [[sentinel_1_sar]]
- [[european_ground_truth_databases]]
- [[species_distribution_models]]
