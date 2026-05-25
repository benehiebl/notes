---
name: evergreen_broadleaved_expansion
description: Drivers, distribution, and remote sensing of evergreen broad-leaved (laurophyllous) species expansion into deciduous European forests
type: reference
tags:
  - forest-ecology
  - remote-sensing
---

# Evergreen Broad-Leaved Expansion (Laurophyllisation)

**Summary**: The naturalisation and spread of evergreen broad-leaved (laurophyllous) species — both native (e.g. *Hedera helix*, *Ilex aquifolium*, *Laurus nobilis*) and exotic (e.g. *Prunus laurocerasus*, *Trachycarpus fortunei*) — into deciduous lowland forests of southern and Mediterranean Europe. The expansion is enabled by rising winter temperatures since the 1970s but driven proximally by propagule pressure and land-use change (abandoned coppices, ornamental gardens), not climate warming alone. Mapping EVE cover from satellite time series is the wiki's primary research target.

**Sources**: [[berger_2006_distribution_eve]], [[conedera_2018_drivers_evergreen]], [[chelli_2017_climate]], [[fady_2025_native_trees_mediterranean]], [[yang_2020_modis_evergreen]], [[hiebl_2025_pretraining]], [[hiebl_2026_alphaearth]], [[alessi_2019_refugia]], [[fang_2016_eve_mosaics]]

**Last updated**: 2026-05-16

---

## The Phenomenon

Since the late 1970s, evergreen broad-leaved species have spread into deciduous lowland forests around the Insubrian lakes (southern Switzerland, northern Italy) — initially mapped by Gianoni et al. 1988 and Walther 2000. Both native species long present in the area and exotic ornamentals (introduced for parks and gardens since the 19th century) participate in the expansion (source: [[berger_2006_distribution_eve]], [[conedera_2018_drivers_evergreen]]).

The process has been termed **laurophyllisation** — a biome-shift candidate where deciduous forests transition toward an evergreen broad-leaved character similar to pre-Pleistocene vegetation south of the Alps.

## Drivers: Climate vs Land-Use

The original interpretation (Walther 2000, 2005) framed EVE expansion as a textbook ecological footprint of **climate warming**: rising mean January temperatures, fewer frost days, allowing previously frost-limited species to survive.

Subsequent quantitative work nuances this:
- **Climate warming is permissive but not the trigger** — comparable winter temperatures occurred in 1915–1925 and 1950–1960 without invasion, because the necessary conditions (mature host forest, propagule pressure) were absent (source: [[conedera_2018_drivers_evergreen]]).
- **Propagule pressure** (distance to nearest ornamental garden) is the **dominant driver** for 3 of 4 studied species (*H. helix*, *P. laurocerasus*, *T. fortunei*) when controlling for climate, stand structure, and disturbance (source: [[conedera_2018_drivers_evergreen]]).
- **Land-use abandonment** of chestnut coppices and vineyards since 1950s created mature shaded forest stands — a previously empty ecological niche EVE species can occupy (source: [[conedera_2018_drivers_evergreen]]).
- **Coldest-month temperature** retains a secondary role for non-native thermophilous species (*P. laurocerasus*, *T. fortunei*) (source: [[conedera_2018_drivers_evergreen]]).

The hierarchy: **climate prepares the niche → propagule pressure colonises it → stand-structure change consolidates it**.

## Spatial Structure within the Insubrian Region

Within the area where climate now permits EVE survival, distribution partitions along precipitation and bedrock gradients (source: [[berger_2006_distribution_eve]]):

- **W (high precipitation, siliceous)**: *Cinnamomum glanduliferum*, *Trachycarpus fortunei*, *Prunus laurocerasus*
- **E (low precipitation, calcareous)**: *Quercus ilex*, *Viburnum tinus*
- **Region-wide**: *Laurus nobilis*, *Hedera helix*, *Ligustrum lucidum*

Calcareous bedrock → shallow soils + lower water storage → drought stress → favours sclerophyllous Mediterranean species (*Q. ilex*, *V. tinus*); siliceous + humid favours laurophyllous types (source: [[berger_2006_distribution_eve]]).

## Broader Mediterranean Context

Across Italy, EVE expansion sits within a broader pattern of vegetation response to warming + drying. Italian climatic-zone reviews (source: [[chelli_2017_climate]]) emphasise that:
- Drought can override warming benefits even in non-Mediterranean zones
- Thermophilisation and shrub encroachment are widespread cross-zonal patterns
- Community / ecosystem-level changes (treeline shift, EVE expansion, biome transition) often differ from species-level responses

Mediterranean native tree species (source: [[fady_2025_native_trees_mediterranean]]) face their own range shifts under climate change — competition + climate together shape the future composition.

## Remote Sensing of EVE Cover

EVE fractional cover from satellite time series is the central RS target of the wiki's research:

- **Classic NDVI time-series approach**: FEVC-CV method using intra-annual NDVI minimum + coefficient of variation (source: [[yang_2020_modis_evergreen]]) — sub-pixel fractional cover at 250 m MODIS resolution; OA > 90%; relies on stable seasonal contrast between evergreen (flat NDVI year-round) and deciduous (large amplitude).
- **DL transfer-learning approach**: 1D Sentinel-2 SITS with InceptionTimeEnsemble + supervised pretraining on VDB + MVP self-supervised pretraining → fine-tune on small VPO2024 reference set (source: [[hiebl_2025_pretraining]]).
- **Foundation-model approach**: AlphaEarth + Sentinel-2 Cross-Attention fusion at 10 m (source: [[hiebl_2026_alphaearth]]) — TST_AEF,S2 best (RMSE 0.161, Acc 0.757); AEF matches S2 accuracy 10–24× faster.

## Native Laurophylls in Italy: Non-equilibrium and Expansion Potential

(source: [[alessi_2019_refugia]])

Using 17,087 Italian vegetation plots, Alessi et al. (2019) identified **11 native Italian laurophylls** (two subgroups: mesothermic ME including *Ilex aquifolium*, *Buxus sempervirens*; macrothermic MA including *Hedera helix*, *Laurus nobilis*, *Ruscus aculeatus*) and found:

- **9 of 11 species occupy < 50% of their potential range** → non-equilibrium with current climate
- **Central Apennines** = core Quaternary refugia; richest realised aggregations
- Italian forests show **HIGH potential for native laurophyll expansion** throughout the Apennines, pre-Alps (Insubrian region), Sicily, Sardinia
- **Dispersal limitation + human forest clearance** explain non-equilibrium better than ongoing climate change
- **Land-use abandonment** → increasing forest maturity → more suitable late-successional niches for EVE species
- Climate change plays a secondary amplifying role, not the primary trigger

This reframes EVE mapping objectives: current RS training samples represent only a fraction of where EVE species are ecologically capable of occurring.

## Within-Stand EVE Mosaic Drivers

At stand scale (20-ha subtropical EBLF in China), the evergreen-deciduous mosaic is driven by **habitat heterogeneity** rather than biotic interactions (source: [[fang_2016_eve_mosaics]]):

- **Soil phosphorus** is the key driver at all scales (> 0.27–0.30 g/kg favours deciduous dominance)
- Deciduous trees prefer higher-P, lower-slope, moister sites; evergreens tolerate lower-P, steeper, drier sites
- Environmental controls operate hierarchically: temperature/elevation at landscape scale, soil P at stand scale, micro-topography at fine scale (<20 m)
- Fine-scale habitat heterogeneity (< 20 m) generates mosaic patterns, consistent with [[topographic_microclimate]] buffering

Implication for EVE mapping: edaphic and microtopographic predictors (soil P proxy from terrain / SRTM, slope, moisture index) may add information independent of spectral-temporal signals.

## Implications for Forest Type Mapping

Any Italian forest type / EVE cover mapping product must contend with:
- **Climate × land-use co-driver structure**: proximity to settlements / abandoned coppice is informative independent of climate (source: [[conedera_2018_drivers_evergreen]])
- **Precipitation × bedrock structure** for species-level partitioning (source: [[berger_2006_distribution_eve]])
- **Phenological signal robustness**: NDVI minimum captures evergreen presence reliably (source: [[yang_2020_modis_evergreen]])
- **EVE expansion is non-stationary**: training samples from the 2010s may not reflect the future distribution (cf. [[dyderski_2025_species_shift]], [[alessi_2019_refugia]])
- **Edaphic and microtopographic signals** at sub-stand scale complement spectral-temporal predictors (source: [[fang_2016_eve_mosaics]])

## Related concepts
- [[tree_species_mapping]]
- [[leaf_habit_latitudinal_gradient]]
- [[species_distribution_models]]
- [[vegetation_community_change]]
- [[topographic_microclimate]]
- [[phenology]]
- [[ndvi]]
- [[plant_functional_traits]]
