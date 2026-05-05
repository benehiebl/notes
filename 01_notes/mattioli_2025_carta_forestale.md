---
title: La Carta Forestale d'Italia (CFI2020) — un ritratto aggiornato dei boschi italiani
authors:
  - Mattioli, Walter
  - Romano, Raoul
  - Botticelli, Davide
  - Chirici, Gherardo
  - D'Amico, Giovanni
  - Giuliarelli, Diego
  - Pecchi, Matteo
  - Corona, Piermaria
year: 2025
source: mattioli_2025_carta_forestale
tags:
  - forest-mapping
  - Italy
  - national-forest-inventory
  - forest-definition
  - cartography
  - remote-sensing-ground-truth
keywords:
  - CFI2020
  - Carta-Forestale-Italia
  - SINFor
  - TUFF
  - FAO-forest-definition
  - forest-area
  - nomenclature
  - photo-interpretation
  - INFC
status: summarized
---

## Title and Authors of the Paper

*La Carta Forestale d'Italia (CFI2020): un ritratto aggiornato dei boschi italiani* [The Forest Map of Italy (CFI2020): an updated portrait of Italian forests] — Walter Mattioli et al. (2025), Forest@, 22, 39–44. DOI: 10.3832/efor4836-022. Published online 2025-06-02. Language: Italian with English abstract.

## Quick Overview

- **Why is it relevant?** Italy lacked a coordinated, nationwide forest map at a planning-relevant scale — regional cartographies existed but were heterogeneous in definition and methodology; CFI2020 fills this gap for the first time.
- **What was done?** Produced the first national Forest Map of Italy (CFI2020) at 1:10,000 scale by merging and photo-interpreting regional forest cartographies against AGEA orthophotos (2018-2020), applying three simultaneously mapped forest definitions.
- **What is the main outcome?** Italian forest area exceeds 10 million hectares under the FAO definition (reference year 2020); the map is freely accessible via SINFor and provides a validated, homogeneous cartographic baseline for forest management, policy, and RS calibration/validation.

## Main Goal and Fundamental Concept

Italy had no national forest map at an operationally useful scale since the 1936 Milizia Forestale map (Ferretti et al. 2018). Regional cartographies existed but used incompatible forest definitions and nomenclature systems — creating legal inconsistencies and hindering national monitoring.

CFI2020 was created under Article 15 of TUFF (Legislative Decree No. 34, April 3, 2018) and is managed within SINFor (Sistema Informativo Nazionale delle Foreste e delle Filiere Forestali), the National Information System for Forests.

**Key innovation**: CFI2020 maps Italian forests simultaneously according to **three forest definitions**, allowing end-users to select the appropriate definition for their purpose:

| Definition | Min area | Min canopy cover | Min width | Use |
|-----------|---------|----------------|---------|-----|
| **TUFF normative (art. 3)** | 2,000 m² | 20% | 20 m | Legal/environmental/landscape protection |
| **FAO/statistical (TUFF art. 15)** | 5,000 m² | 10% | 20 m | National inventories (INFC), international reporting (FAO-FRA) |
| **Regional definitions** | Variable | Variable | Variable | Local regulatory compliance |

## Technical Approach

**Production workflow:**
1. Acquisition of existing regional forest cartographies (thematic maps)
2. Where existing cartographies are adequate: update and harmonise to common standards; where not: generate new polygons by photo-interpretation
3. Mosaicking all regional products into national coverage
4. Quality control and validation

**Input data:**
- Regional forest cartographies (where available and adequate)
- AGEA orthophotos (false colour, 2018-2020) — provided by the Agency for Agricultural Payments

**Output:**
- Vector map; ~850,000 polygons; mean polygon size 12.50 ha
- Smallest polygons in Province of Bolzano (local definition classifies any forest patch ≥ 500 m² with woody species including chestnuts — far smaller than the national standard → produces very numerous, small polygons)

**Polygon attributes per feature:**
- Geometric information (area, perimeter)
- Administrative jurisdiction (region, province)
- Canopy cover class (%)
- Silvicultural system (fustaie ordinariamente gestite, boschi non ordinariamente gestiti, etc.)
- Management type (cedui, fustaie)
- Disturbance information (fire, avalanche, landslide — from regional cartographies; still preliminary)

**Nomenclature system:**
- All local/regional forest categories linked to three national/international systems:
  - **INFC categories** (consistent with INFC2015 data)
  - **European Forest Types (EFT)** — for pan-European biodiversity monitoring
  - **Del Favero classification** (3 volumes covering Alpine, central Apennine, and southern/island forests)
- Enables multi-scale use: local detail preserved; national and European comparisons enabled

**Validation:**
- 250 sample points selected by stratified random sampling (stratified by forest area of regional cartographies)
- 2 km × 2 km quadrats generated around each sample point; expert photo-interpretation performed independently of CFI2020
- Overall accuracy (OA) ≥ 90% — required threshold for 1:10,000 restitution standard across all national territory

## Key Results

**National forest area (CFI2020, reference year 2020):**

| Definition | Forest area (ha) |
|-----------|----------------|
| FAO (TUFF art. 15) | 10,126,903 |
| TUFF normative (art. 3) | 10,063,436 |
| Regional definitions | 10,616,297 |

- FAO definition used for comparison with INFC and international statistics
- Difference FAO vs TUFF: ~60,000 ha — mainly timber plantations classed as forest under FAO but not TUFF

**Regional distribution (FAO definition):**
- Largest: Toscana (1.19 Mha), Piemonte (0.98 Mha), Trentino-Alto Adige combined (~0.75 Mha)
- Smallest: Valle d'Aosta (0.10 Mha), Molise (0.15 Mha)
- **Sardegna special case**: regional definition gives 1.23 Mha vs FAO 0.71 Mha — Sardinia's regional law classifies macchia mediterranea as forest; FAO definition excludes it; this is the largest national discrepancy

**Comparison with INFC 2015 (FAO definition):**

| | INFC 2015 (ha) | CFI2020 (ha) | Difference (ha) | Difference (%) |
|-|--------------|------------|----------------|---------------|
| **Total Italy** | 9,085,186 | 10,126,903 | +1,041,717 | **+11.47%** |

- Largest increases in southern Italy and islands: Calabria +28.8%, Sicilia +25.96%, Campania +21.76%, Basilicata +19.63%
- Umbria (−1.78%) and Valle d'Aosta (likely methodological) show small decreases
- Causes of increase:
  - **Real forest expansion**: land abandonment and reforestation are documented trends, especially in south Italy and islands
  - **Methodological differences**: INFC uses statistical sampling (extrapolated to area); CFI uses photo-interpretation (direct measurement) → different source of systematic bias
  - Photo-interpretation difficulty: abandoned olive groves, macchia mediterranea scrub, and timber plantations are hard to classify consistently

## Advantages and Limitations

**Advantages:**
- First wall-to-wall national forest map at planning-relevant scale (1:10,000)
- Three simultaneous definitions allow flexible use across normative, statistical, and local contexts
- Harmonised nomenclature enables connections to INFC, EFT, and Del Favero classification
- Freely accessible via SINFor portal (https://cfi.sinfor.crea.gov.it/)
- Operational tool: publicly downloadable vector GIS product for any user
- Can be integrated with other data layers (IFNI, SINFor indicators, satellite data, Lidar from new national missions)

**Limitations:**
- Disturbance information in polygon attributes is still preliminary (derived from regional cartographies, not yet uniformly validated)
- Differences from INFC2015 partly methodological — direct comparison requires caution; not all +11.47% reflects real forest growth
- Sardinia regional definition discrepancy makes national totals definition-sensitive
- No spectral/structural attributes — CFI provides forest extent and type, not biomass or carbon estimates (those remain with INFC)
- Update cycle not yet defined nationally; reference year 2024 update planned under new CREA-DIFOR MASAF agreement

## Conclusion

Mattioli et al. (2025) present CFI2020 as Italy's first operational national forest map at 1:10,000 scale — a cartographic product (not a statistical survey) mapping over 10 million ha of Italian forest as of 2020. The simultaneous three-definition approach resolves long-standing legal and methodological inconsistencies between national and regional forest definitions. CFI2020 complements rather than replaces INFC: INFC provides statistically robust area estimates and forest attribute data; CFI provides the spatial coverage (wall-to-wall polygons) needed for planning, monitoring, and RS calibration. The +11.47% increase relative to INFC2015 reflects a combination of real forest expansion and methodological improvement.

## Related Work & Obsidian Links

- [[national_forest_inventory]]
- [[sentinel_2]]
- [[tree_species_mapping]]
- [[forest_disturbances]]

**Cross-paper links (same vault):**
- [[01_notes/gasparini_2022_nfi_italy]] — INFC2015 is the statistical counterpart to CFI2020; both characterise Italian forests but with different methods; CFI2020's headline area (+11.47% vs INFC2015) explicitly references the Gasparini et al. 2022 book as the comparison baseline
- [[01_notes/hiebl_2025_pretraining]] — EVE cover mapping in Italian National Parks uses Copernicus FTY forest mask; CFI2020 is a higher-resolution Italian alternative for forest masking that could improve future RS studies
- [[01_notes/amico_2025_nfi_italy]] — D'Amico et al. on the Italian NFI system (SINFor); CFI2020 is one of the products delivered within the SINFor framework described there
