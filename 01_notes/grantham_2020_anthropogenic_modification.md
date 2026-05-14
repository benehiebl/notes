---
title: "Anthropogenic modification of forests means only 40% of remaining forests have high ecosystem integrity"
authors:
  - Grantham, H. S.
  - Duncan, A.
  - Evans, T. D.
  - Jones, K. R.
  - Beyer, H. L.
  - Schuster, R.
  - Walston, J.
  - Watson, J. E. M.
  - and 36 others
year: 2020
source: grantham_2020_anthropogenic_modification
tags:
  - forest-ecology
  - remote-sensing
keywords:
  - forest integrity
  - Forest Landscape Integrity Index
  - FLII
  - anthropogenic pressure
  - protected areas
  - connectivity
  - biodiversity
  - global forests
status: read
---

# Grantham et al. 2020 — Anthropogenic Modification Leaves Only 40% of Forests with High Integrity

## Title and Authors
**Anthropogenic modification of forests means only 40% of remaining forests have high ecosystem integrity**
H. S. Grantham et al. (40+ authors, Wildlife Conservation Society lead) — *Nature Communications* 11: 5978 (2020).

## Quick Overview
- **Why is it relevant?** Provides a globally consistent **Forest Landscape Integrity Index (FLII)** that goes beyond binary "intact / not intact" classifications — directly informs RS-based prioritisation for protection, restoration, and biodiversity monitoring.
- **What was done?** Integrated observed human pressures (infrastructure, agriculture, tree-cover loss), inferred human pressures (modelled from proximity), and loss of forest connectivity into a single 0–10 continuous index for global forests (~5 m+ canopy) at the start of 2019.
- **What is the main outcome?** Only **40.5% of remaining forest (17.4 Mkm²) has high landscape-level integrity**, concentrated in Canada, Russia, Amazon, Central Africa, New Guinea; only 27% of high-integrity forest is in protected areas, and only 56% of forest within protected areas is high-integrity.

## Main Goal and Fundamental Concept
Deforestation has been mapped at high resolution since the 2000s (Hansen et al. 2013), but **forest degradation** — modification short of clear-cutting — is potentially as significant for biodiversity and climate. The paper builds an index that captures the *degree* of anthropogenic modification rather than binary deforestation, enabling fine-scale prioritisation.

## Technical Approach
- **Forest extent**: woody vegetation > 5 m, from Hansen Global Forest Change.
- **Three index components**:
  1. **Observed human pressure**: directly mappable — infrastructure (roads, urban), agriculture, recent tree-cover loss
  2. **Inferred human pressure**: modelled from proximity to observed pressures (captures un-mapped hunting, fuel-wood collection, etc.)
  3. **Loss of connectivity**: ratio of current to potential forest connectivity
- **Integration**: weighted combination → continuous FLII (0 = lowest integrity, 10 = highest).
- **Categorisation** for reporting:
  - Low: FLII ≤ 6.0
  - Medium: 6.0 < FLII < 9.6
  - High: FLII ≥ 9.6
- Benchmark categories calibrated against reference locations worldwide.

## Distinctive Features
- **Continuous index**, not binary — enables fine prioritisation gradient.
- **Integrates three modification pathways** (direct pressure, diffuse pressure, connectivity loss) rather than focusing on one.
- **Globally consistent**: applied uniformly across all forested biomes.
- **Adaptable to national / sub-national scales** with local weightings.
- **Connects to protected-area policy**: explicit assessment of integrity within designated PAs.

## Experimental Setup and Results

**Global integrity distribution**
- High integrity: **40.5%** of remaining forest (17.4 Mkm²)
- Medium integrity: ~34% (14.6 Mkm²)
- Low integrity: 25.6% (11 Mkm²)
- 91.2% of forests experience at least some inferred pressure

**Realm-level**
- No biogeographical realm has more than half its forests in the high category
- Highest integrity concentrations:
  - Palearctic (Northern Russia)
  - Nearctic (Northern Canada, Rockies, Alaska)
  - Neotropics (Amazon, Guianas, Atlantic forest, southern Chile)
  - Afrotropic (humid central Africa, drier woodlands of South Sudan, Angola, Mozambique)
  - Indo-Malayan (New Guinea, parts of Sumatra/Borneo/Myanmar)

**Protected area effectiveness**
- Only **27%** of high-integrity forest is inside protected areas
- Only **56%** of forest inside protected areas has high integrity
- Substantial conservation gap

**Regional gradients**
- Decreasing human impact northward through eastern North America
- High pressure in West-Central Europe, SE USA, mainland SE Asia (west of New Guinea), Andes, China, India, Albertine Rift, West Africa, Mesoamerica, Atlantic Forests of Brazil

## Implications
- Conservation policy must address **integrity** alongside deforestation
- Restoration potential is large in medium-integrity forests
- Protected-area effectiveness is partial — many PAs already degraded
- Continuous index enables much finer policy targeting than binary intact / not intact

## Advantages and Limitations
- **Advantages**: Globally consistent and continuous; integrates three modification pathways; transparent component weighting; can be customised regionally; clear policy translation.
- **Limitations**: 2019 snapshot only — no time series for change detection yet; some pressure datasets (especially "inferred") are model-based rather than observed; canopy-concealed modification (selective logging, sub-canopy burning) under-represented (cf. [[zhao_2022_forest_harvesting]]); weights are illustrative, not derived from empirical biodiversity outcomes.

## Conclusion
**Only 40% of remaining global forest has high ecosystem integrity, and most of it is unprotected.** The FLII provides the kind of continuous, globally consistent forest-condition product that Skidmore et al. ([[skidmore_2021_biodiversity]]) identify as a high-priority biodiversity metric. For Italian / European forest mapping, the FLII framework provides a complementary lens to species-level mapping ([[blickensdörfer_2024_tree_species]], [[grabska_2024_tree_species_map]], [[hiebl_2026_alphaearth]]) — capturing the *degradation gradient* rather than species composition.

## Related pages
- [[forest_disturbances]]
- [[ebv_biodiversity_monitoring]]
- [[skidmore_2021_biodiversity]]
- [[vihervaara_2017_ebv_remote_sensing]]
- [[lang_2024_canopy_height]]
- [[turubanove_2023_canopy_landsat]]
- [[wegler_2026_canopy_cover_loss]]
- [[bell_2024_hindcasting_forest_structure]]
- [[grünig_2026_climate_change_disturbances_forest]]
- [[zhao_2022_forest_harvesting]]
- [[qin_2026_forest_cover]]
- [[atzberger_2020_monitoring_forests_eu]]
