---
name: forest_disturbances
description: Forest disturbance ecology — wildfire, bark beetles, windthrow, their interactions, climate sensitivity, and implications for forest structure and carbon
type: reference
tags:
  - forest-ecology
  - remote-sensing
---

# Forest Disturbances

**Summary**: Forest disturbances are discrete, punctuated events that cause mortality of trees, alter forest structure, and reset successional trajectories — they are among the most climate-sensitive processes in forest ecosystems and are expected to intensify under climate change.

**Sources**: [[grünig_2026_climate_change_disturbances_forest]], [[albrich_2019_climate_change_mountain_forests]], [[francioni_2026_canopy_closure]], [[thom_2026_disturbance_suitability]], [[wegler_2026_canopy_cover_loss]], [[torres_2021_forest_health_remote_sensing]], [[turubanove_2023_canopy_landsat]], [[tong_2023_forest_densification_china]], [[schuldt_2020_drought_forest]], [[zhao_2022_forest_harvesting]], [[grantham_2020_anthropogenic_modification]], [[soto_2025_disturbance]]

**Last updated**: 2026-05-22

---

## Major Disturbance Agents in European Forests

### Wildfire
- The most important agent of future disturbance change in Europe (source: [[grünig_2026_climate_change_disturbances_forest]])
- Ignition probability driven by: vapour pressure deficit (VPD), temperature, lightning density, population density, topography (source: [[grünig_2026_climate_change_disturbances_forest]])
- Spread driven by: fuel load (from vegetation state), wind, topography (source: [[grünig_2026_climate_change_disturbances_forest]])
- Currently concentrated in Mediterranean Europe; projected to expand into temperate and boreal biomes under climate change (source: [[grünig_2026_climate_change_disturbances_forest]])
- Historical mean area burned in Europe (1986–2020): ~82,000 ha/yr; projected to reach ~232,000 ha/yr under RCP8.5 (source: [[grünig_2026_climate_change_disturbances_forest]])

### Bark Beetles
- Dominant biotic disturbance agent in European forests: *Ips typographus* (European spruce bark beetle) most important (source: [[grünig_2026_climate_change_disturbances_forest]])
- Climate sensitivity: warmer temperatures → more beetle generations per year (voltinism) → higher population pressure and dispersal (source: [[grünig_2026_climate_change_disturbances_forest]])
- Outbreak dynamics driven by: regional beetle pressure, host tree presence (Norway spruce), drought stress (approximated by summer VPD), density-dependent feedbacks (source: [[grünig_2026_climate_change_disturbances_forest]])
- Strongly interact with wind disturbances: windthrown trees provide low-resistance breeding habitat → beetle outbreaks follow large storm events (source: [[grünig_2026_climate_change_disturbances_forest]])
- Historical mean in Europe: ~32,000 ha/yr; projected +83% under RCP8.5 (source: [[grünig_2026_climate_change_disturbances_forest]])

### Windthrow
- Historically the largest European disturbance agent by area (source: [[grünig_2026_climate_change_disturbances_forest]])
- Severity driven by: storm intensity, species composition (conifers more susceptible than broadleaves), tree height, edge effects (source: [[grünig_2026_climate_change_disturbances_forest]])
- Climate change signal is indirect: changing forest structure (taller trees, more conifers dying) rather than changes in storm frequency (source: [[grünig_2026_climate_change_disturbances_forest]])
- Strong interactions with bark beetles: 31% of bark beetle disturbed area attributable to prior wind events (source: [[grünig_2026_climate_change_disturbances_forest]])
- Historical mean: ~68,500 ha/yr; relatively stable projected (~+12% under RCP8.5) (source: [[grünig_2026_climate_change_disturbances_forest]])

## Disturbance Interactions

Disturbance agents do not act independently — they form a cascade (source: [[grünig_2026_climate_change_disturbances_forest]]):
- **Wind → bark beetle**: windthrown trees have low defence capacity → beetle breeding habitat → regional outbreak
- **Fire → bark beetle**: fire-stressed trees are more susceptible to beetle attack
- **Bark beetle → wind**: beetle-killed snags increase storm susceptibility of remaining stand

Ignoring these interactions leads to systematic underestimation of total disturbance (by factor 2.6–3.9× in vegetation feedback experiments; source: [[grünig_2026_climate_change_disturbances_forest]]). Forest landscape simulation models show that compound disturbance interactions are a key driver of future forest structural change in mountain ecosystems (source: [[albrich_2019_climate_change_mountain_forests]]).

## Vegetation Feedbacks

Disturbances alter forest structure and composition, which feeds back into future disturbance susceptibility (source: [[grünig_2026_climate_change_disturbances_forest]]):
- A fire exhausts fuel → lower probability of severe re-burn in subsequent years
- Bark beetle outbreak removes spruce → replaced by less-susceptible species/structures
- These negative feedbacks substantially dampen disturbance rates but cannot fully buffer against climate-driven increases

Canopy opening from disturbance also affects understory diversity: in Italian forests, progressive canopy closure following management abandonment drives understory plant species loss, while disturbance-induced gap opening temporarily reverses this trend; boreal and nemoral forests showed the strongest richness declines (source: [[francioni_2026_canopy_closure]]).

## Remote Sensing of Disturbances

Forest disturbances are detectable at continental scale from Landsat time series (source: [[grünig_2026_climate_change_disturbances_forest]]):
- Annual disturbance maps derived from spectral change detection in Landsat time series (e.g., European forest disturbance map; Senf & Seidl)
- Disturbance rate = % of forest area disturbed per year; disturbance rotation = reciprocal of disturbance rate
- Used as calibration targets for process-based and AI disturbance models (source: [[grünig_2026_climate_change_disturbances_forest]])
- Remote sensing captures high-severity (stand-replacing) disturbances well; low-severity disturbances are often below detection thresholds

### European Forest Disturbance Atlas (EFDA)

The most comprehensive Landsat-based disturbance product for continental Europe (source: [[soto_2025_disturbance]]):
- **Coverage:** 35 European countries, 1985–2023, 30 m resolution, annually updatable
- **Method:** Random Forest classifier on spectral change features (NDVI, NBR, tasseled-cap components, Disturbance Index) between target year (t₀) and prior year (t₋₁); SMOTE balancing; best-available-pixel Landsat composites from FORCE pipeline
- **Key advantage over prior products:** captures **multiple disturbance events per pixel** — predecessor (Senf & Seidl 2021) was limited to the single greatest-change event
- **Agent attribution:** patch-level RF classifying wind/bark beetle, fire, and harvest; wind and bark beetle merged (disturbance complex, sparse pre-2017 bark beetle reference data)
- **Accuracy:** F1 = 0.89 overall (disturbed class: commission 17.3%, omission 22.5%); errors decrease after 2000 (commission drops to 10.6%)
- **Disturbance totals:** 439,000 km² disturbed (22% of EU forest); harvest dominant (79.2%), wind/bark beetle (12%), fire (8.8%)
- 28% of disturbed pixels experienced multiple events; especially southern Europe (reburns) and short-rotation plantations
- **Open access:** Zenodo https://doi.org/10.5281/zenodo.13333034

## Demographic and Carbon Consequences

All from source: [[grünig_2026_climate_change_disturbances_forest]]:
- Disturbances reset forest age structure → more young forests, fewer old forests
- Young forests (post-disturbance regeneration): temporarily net CO₂ sources or weak sinks
- Old forests: highest carbon density and most stable carbon stocks
- Under RCP8.5: young forests increase by up to 14%, old forests decrease by ~3% at European scale
- Loss of old forests also means loss of critical biodiversity habitat

## Management Responses

Forest landscape simulations (source: [[albrich_2019_climate_change_mountain_forests]]) and broad disturbance analyses (source: [[grünig_2026_climate_change_disturbances_forest]]) support the following management approaches:
- Mixed species forests (combining broadleaves and conifers) increase resilience to high-severity disturbance
- Uneven-aged stands buffer bark beetle and wind impacts
- Disturbance refugia exist in the high North and Mediterranean mountain ranges
- Business-as-usual even-aged management is a major risk amplifier
- Climate-adaptive management requires shifting target species composition toward more drought- and disturbance-tolerant species (source: [[albrich_2019_climate_change_mountain_forests]])

## Remote Sensing of Forest Health (RS Review 2015–2020)

Systematic PRISMA review of 107 forest health RS papers (source: [[torres_2021_forest_health_remote_sensing]]):
- Satellite multispectral sensors (Landsat) dominate; North America + Europe most studied
- Most papers assess specific stressor impact **after** visible damage — early warning remains a major gap
- Spectral indices (NDVI, red-edge VIs) and time series change detection are the dominant methods
- Machine learning adoption growing but still minority approach

## Tree Canopy Height Change in Europe 2001–2021

Annual 30 m tree canopy height maps from Landsat + lidar calibration (source: [[turubanove_2023_canopy_landsat]]):
- European tree canopy extent +1% 2001–2021 overall, but **declining after 2016**
- Tall canopy forests (≥15 m) decreased 3% across the continent
- Fennoscandia: -3.5% net canopy extent; largest losses from harvest intensification
- RMSE ≤ 4 m for height predictions; canopy extent accuracy ≥ 94%

## Species-Specific Disturbance Dynamics (Germany 2018–2024)

First national species-specific canopy cover loss assessment (source: [[wegler_2026_canopy_cover_loss]]):
- Total FCCL = 8,763 km² (2018–2024)
- **Spruce:** 4,497 km² (51.3% of total); 18.6% of initial spruce area — peak in 2020–2021
- **Pine:** 1,893 km² (21.6%); 7.4% relative loss
- **Deciduous (beech, oak):** <300 km² each; ~1% relative loss — substantially more resilient
- Spatial hotspots: Harz Mountains, Thuringian Forest, Bohemian Forest

## Post-Disturbance Regeneration: Species Suitability

Functional trait-based ranking of 53 species for large disturbed area regeneration in Central Europe (source: [[thom_2026_disturbance_suitability]]):
- ~50% of assessed species are "suitable" or "highly suitable"
- Primary suitability criteria: drought tolerance + late frost tolerance
- Southern-range natives (oaks, *Castanea sativa*, *Pinus nigra*) score well on drought tolerance
- Waterlogging tolerance is the most restrictive site filter
- Key implication: diversifying beyond Norway spruce is both feasible and necessary

## Forest Expansion and Densification via Long-Term Landsat

30-year Landsat time series reveals forest history at 30 m in southern China (source: [[tong_2023_forest_densification_china]]):
- Forest area tripled: 249,414 km² (1986) → 978,954 km² (2018)
- Reforestation policies ~2000 drove a forest area surge ~2010 (10-year maturation lag)
- Old forests were fragmented on mountain tops; expansion moved 729,540 km² downhill
- Demonstrates long-term Landsat archives can reconstruct plantation history at landscape scale

## Hotter Droughts and Mortality

A specific subclass of disturbance-relevant climate event is the **hotter drought** — drought at temperatures elevated above historical norms — which has its own dedicated concept page covering 2018 Central European drought, xylem hydraulic failure mechanisms, and 20th-century redistribution of climatic drivers:

- 2018 DACH drought MGT +3.3°C vs 1961–1990 baseline, +1.2°C vs 2003 (source: [[schuldt_2020_drought_forest]])
- Twice the area of deciduous forest in lowest NDVI quantiles vs 2003 (source: [[schuldt_2020_drought_forest]])
- Drought legacy: many beech failed to flush in 2019 (source: [[schuldt_2020_drought_forest]])
- 20th-century redistribution: T-limited area shrank by 10.8% (source: [[babst_2019_redistribution]])
- See [[drought_mortality]] for full treatment.

## Monthly Forest Harvesting Detection

Operational monthly forest harvesting maps with Sentinel-1 SAR + U-Net (source: [[zhao_2022_forest_harvesting]]):
- Mean F1 0.74–0.78, IoU 0.59–0.65 — landscape-pattern learning captures harvest shape and context
- California vs Rondônia: model trained in one site fine-tunes with sparse local samples
- Cloud-independent — operational in tropical / cloudy regions
- Distinguishes salvage logging (post-fire) vs slash-and-burn (dry season + fire) vs routine timber harvest

## Forest Integrity Index

Continuous global forest integrity index based on observed + inferred human pressures + connectivity loss (source: [[grantham_2020_anthropogenic_modification]]):
- Only **40.5%** of remaining forest has high landscape-level integrity
- Only **27%** of high-integrity forest is in protected areas
- Only **56%** of protected forest is high-integrity
- Concentrations: Canada, Russia, Amazon, Central Africa, New Guinea

## Related pages

- [[vegetation_greenness_trends]]
- [[landsat]]
- [[topographic_microclimate]]
- [[plant_functional_traits]]
- [[tree_species_mapping]]
- [[wegler_2025_tree_species_germany]]
- [[drought_mortality]]
