---
name: mediterranean_holm_oak_dieback
description: Hot-drought-driven crown dieback of holm oak (Quercus ilex) and Mediterranean evergreens in Italy — events, symptoms, biotic interactions, Sentinel-2 detection and driver modelling
type: reference
tags:
  - forest-ecology
  - remote-sensing
---

# Mediterranean Holm Oak Dieback (Italy)

**Summary**: Evergreen sclerophyllous vegetation, notably *Quercus ilex*, has shown repeated crown dieback after hot droughts (2012, 2017, 2022, 2024) in Italy; causes combine drought/heat with root and canopy pathogens, and Sentinel-2 vegetation-index change plus climate and terrain predictors can map and partly explain it. Evidence is mostly regional observations and one non-peer-reviewed modelling preprint.

**Sources**: [[seddaiu_2025_quercus_dieback]], [[seddaiu_2025_mediterranean_dieback]], [[puletti_2019_drought_forest_health]]

**Last updated**: 2026-10-16

---

## Events and Symptoms

- First sporadic reports of *Q. ilex* dieback in Tuscany date to 2012; broader evidence followed the 2017 heat-drought in central Italy (source: [[seddaiu_2025_quercus_dieback]]).
- 2017: no rain for >3 months and temperatures up to 8 °C above average in much of central-southern Italy (source: [[seddaiu_2025_quercus_dieback]]).
- Summer 2024: widespread dieback in Apulia, Basilicata, Sardinia and Sicily (source: [[seddaiu_2025_quercus_dieback]]).
- Symptoms: leaf yellowing/browning, shoot and branch desiccation, epicormic shoots, root necrosis; resprouting from dormant buds after rains (source: [[seddaiu_2025_quercus_dieback]]).
- Resprouts can fail later: Tuscan shoots produced in 2018–2019 largely died in 2021–2022 (source: [[seddaiu_2025_quercus_dieback]]).

## Species Response Contrast (2017, Tuscany)

- Holm oak plots classified as unhealthy showed a lasting NDVI reduction after 2017, whereas beech recovered NDVI in 2018 (source: [[puletti_2019_drought_forest_health]]).
- Downy oak (deciduous) responded more like holm oak than beech in that study (source: [[puletti_2019_drought_forest_health]]).
- Evidence is from 118 plots and one event; recovery in NDVI is not proof of physiological recovery (see [[drought_mortality]]).

## Causes: Abiotic and Biotic

- Sclerophylly is not a specific drought adaptation; high VPD causes xylem cavitation that is hard to repair (source: [[seddaiu_2025_quercus_dieback]]).
- Biotic agents reported: *Phytophthora* spp., Botryosphaeriaceae (*Diplodia*), *Biscogniauxia mediterranea*, xylophagous insects (source: [[seddaiu_2025_quercus_dieback]]).
- Regional attribution differs: Sicily preliminary survey found no pathogens or insects and points to hydric-thermal stress, while Apulia and Tuscany report pathogens (source: [[seddaiu_2025_quercus_dieback]]).
- Contradiction/uncertainty: a cited review reports that 48 % of oak-decline studies in Mediterranean-type regions attribute decline to pathogens and 17 % to climate (source: [[seddaiu_2025_mediterranean_dieback]]); the relative weights remain unresolved.
- Worst cases coincide with water-poor substrates (volcanic soils in Sicily, shallow/rocky/calcareous soils in Tuscany) and recently decorticated cork oak (source: [[seddaiu_2025_quercus_dieback]]).

## Monitoring and Remote Sensing

- ICP Forests Level I data (11 permanent plots, ~250 trees) show defoliation rising after 2016 with peaks in hot-dry years; the sample is considered unrepresentative by the authors (source: [[seddaiu_2025_quercus_dieback]]).
- Sentinel-2 change detection (August 2023 vs 2024, ΔIndex < −0.1) of six indices: NGRDI best (Acc 0.95, κ 0.71, F1 0.74); NBR and NDWI over-predict; GNDVI fails (source: [[seddaiu_2025_mediterranean_dieback]]).
- Estimated dieback: ~110,400 ha in Sardinia 2024 (source: [[seddaiu_2025_mediterranean_dieback]]).
- Drivers in spatially blocked LogitBoost/RF models: SPI-12 most important, then tree cover density and terrain ruggedness; elevation, aspect, TPI and SoilGrids soil variables contribute little (source: [[seddaiu_2025_mediterranean_dieback]]).
- Models without climate over-predicted risk (~39 % vs ~16 % of area above 60 % probability) (source: [[seddaiu_2025_mediterranean_dieback]]).
- Caveats: labels derive from the same change map (circularity), the threshold is borrowed from [[puletti_2019_drought_forest_health]], SPI-12 is a coarse single-date field, and the source is a preprint (source: [[seddaiu_2025_mediterranean_dieback]]).
- Citizen science: the SilvaCuore app had 33 holm oak reports in five regions; self-selected and not a sampling design (source: [[seddaiu_2025_quercus_dieback]]).

## Implications for Evergreen Mapping

- Holm oak is among the evergreen broad-leaved species whose cover is mapped in this wiki's evergreen work ([[evergreen_broadleaved_expansion]]); dieback causes spectral decline, resprouting and structural change (high forest to shrub forms), so annual cover maps can show false "losses" or gaps (inference from [[seddaiu_2025_quercus_dieback]], needs verification).
- Climate drying is a counter-driver to warming-driven expansion in the Mediterranean zone; this should be tested explicitly in the planned analysis in [[03_papers/04_evergreen_distribution_change]].
- Knowledge gaps: no systematic extent/severity data, no pathogen occurrence layer, no multi-year recovery quantification.

## Related pages

- [[drought_mortality]]
- [[forest_disturbances]]
- [[sentinel_2]]
- [[ndvi]]
- [[evergreen_broadleaved_expansion]]
- [[area_of_applicability]]
- [[spatial_proxies_random_forest]]
