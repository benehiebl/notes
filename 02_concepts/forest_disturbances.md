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

**Sources**: [[grünig_2026_climate_change_disturbances_forest]], [[albrich_2019_climate_change_mountain_forests]], [[francioni_2026_canopy_closure]]

**Last updated**: 2026-05-05

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

## Related pages

- [[vegetation_greenness_trends]]
- [[landsat]]
- [[topographic_microclimate]]
- [[plant_functional_traits]]
