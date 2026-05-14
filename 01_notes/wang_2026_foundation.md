---
title: "Monitoring annual forest carbon stock loss using very high-resolution time series remote sensing images and earth-foundational data"
authors:
  - Wang, Zhipan
  - Chu, Bin
  - Chen, Zegang
  - Zhang, Yunfei
  - Li, Yatao
  - Peng, Duming
  - Long, Sichun
  - Zeng, Haibo
year: 2026
source: wang_2026_foundation
tags:
  - deep-learning
  - remote-sensing
  - forest-ecology
keywords:
  - forest carbon stock
  - canopy height
  - AlphaEarth
  - GEDI
  - VHR imagery
  - Siamese change detection
  - 3D forest change
  - deep learning
status: read
---

# Wang et al. 2026 — Annual Forest Carbon Stock Loss with VHR Time Series + AlphaEarth

## Title and Authors
**Monitoring annual forest carbon stock loss using very high-resolution time series remote sensing images and earth-foundational data**
Zhipan Wang, Bin Chu, Zegang Chen, Yunfei Zhang, Yatao Li, Duming Peng, Sichun Long, Haibo Zeng — *International Journal of Applied Earth Observation and Geoinformation* 149: 105320 (2026).

## Quick Overview
- **Why is it relevant?** First framework to combine **AlphaEarth foundation embeddings** + Sentinel-1/2 + GEDI for annual canopy height + VHR siamese change detection → carbon stock loss; an operational example of foundation-model use for forestry that complements [[brown_2025_alphaearth]] and [[hiebl_2026_alphaearth]].
- **What was done?** Built a multi-modal CHM model fusing Sentinel-1/2 + AlphaEarth + GEDI; trained a siamese deep change detection model on VHR (0.5–1 m) imagery; combined annual CHM + annual change to estimate 3D forest change and carbon stock loss in Hunan Province 2018–2024.
- **What is the main outcome?** Joint annual CHM + VHR change detection produces high-precision 3D forest change maps; case study (GreenHeart Park, Hunan) shows annual carbon stock loss has significantly decreased since 2021.

## Main Goal and Fundamental Concept
Estimating forest carbon stock loss requires **both** where forest cover is lost (2D change) **and** how tall the lost canopy was (vertical structure). Existing approaches do one or the other. Wang et al. integrate the two by:
1. Estimating annual 10 m canopy height from Sentinel-1/2 + AlphaEarth + GEDI (improves over single-source CHM)
2. Detecting annual forest loss at VHR (0.5–1 m) from GF-2/GF-7 imagery via Siamese-style deep change detection
3. Combining the two for accurate 3D forest change and carbon stock loss

## Technical Approach
- **Inputs**:
  - 0.5 m GF-7, 0.8 m GF-2 VHR imagery for change detection
  - Sentinel-1/2 + AlphaEarth 64-dim embeddings + GEDI for CHM
- **CHM model**: novel architecture using Sentinel-1/2 + AlphaEarth embeddings to regress GEDI canopy heights; produces annual 10 m CHM.
- **Change detection**: SiamHRnet-OCR-style siamese model trained on a large VHR forest change dataset; produces annual 2D forest loss masks.
- **3D fusion**: refine annual forest change by intersecting with annual CHM; assign vertical lost-height per loss patch.
- **Carbon stock loss**: empirical equation based on lost height × lost area.
- Case study: GreenHeart Park, Hunan Province, China, 2018–2024.
- Open-source code: https://github.com/wzp8023391/ForestCarbonEstimate

## Distinctive Features
- **First framework combining AlphaEarth embeddings + GEDI + S1/S2 for CHM** at 10 m, annual.
- **VHR (0.5–1 m) Siamese-style change detection** for forest loss with strong spatial transferability.
- **Explicit 3D fusion**: 2D loss + vertical CHM → carbon stock loss estimate.
- **Annual cadence** at very high spatial resolution.
- **Multi-modal foundation-model use**: showcases practical AlphaEarth deployment.

## Experimental Setup and Results

**CHM accuracy**
- Multi-modal (S1+S2+AlphaEarth) > single-source CHM (S2-only baseline)
- Foundation embeddings substantially improve estimation precision
- 10 m annual product, supports operational forestry

**Change detection performance**
- Siamese deep model with strong spatial-temporal transferability (vs U-Net, SegFormer baselines)
- VHR imagery resolves small-scale rotational plantation cycles

**3D forest change & carbon stock loss (GreenHeart Park 2018–2024)**
- Annual carbon stock loss has **decreased since 2021** — consistent with afforestation/conservation policies
- Captures both stand-replacing harvest and selective loss

## Advantages and Limitations
- **Advantages**: First end-to-end foundation-model-enabled 3D forest change framework; operational annual cadence; open-source code; demonstrates a clear gain from AlphaEarth embeddings; integrates VHR for stand-level fidelity.
- **Limitations**: Single regional case study (Hunan); VHR imagery still expensive; carbon stock equation simple empirical model — true biomass depends on species, age, density (not modelled); GEDI footprint coverage limits training data globally; methods complex and require substantial compute despite the AlphaEarth shortcut.

## Conclusion
**Wang et al. is the first practical demonstration that AlphaEarth foundation embeddings + GEDI + S1/S2 can replace bespoke CHM models** and that combining the result with VHR Siamese change detection produces operational 3D forest change and carbon stock loss estimates. Methodological cousin to [[hiebl_2026_alphaearth]] (AEF for forest type and EVE cover) and [[lang_2024_canopy_height]] (global CHM without AEF). Suggests Italian / Alpine forest mapping pipelines should look hard at incorporating AlphaEarth embeddings.

## Related pages
- [[transfer_learning_remote_sensing]]
- [[brown_2025_alphaearth]]
- [[hiebl_2026_alphaearth]]
- [[lang_2024_canopy_height]]
- [[fischer_2025_glocal_canopy_atlas]]
- [[zhao_2022_forest_harvesting]]
- [[turubanove_2023_canopy_landsat]]
- [[wegler_2026_canopy_cover_loss]]
- [[qin_2026_forest_cover]]
- [[bell_2024_hindcasting_forest_structure]]
- [[forest_disturbances]]
