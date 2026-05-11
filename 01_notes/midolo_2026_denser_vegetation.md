---
title: Sixty years of plant community change in Europe indicate a shift toward nutrient-richer and denser vegetation
authors:
  - Midolo, Gabriele
  - Clark, Adam Thomas
  - Chytrý, Milan
  - Essl, Franz
  - Dullinger, Stefan
  - Jandt, Ute
  - Bruelheide, Helge
  - Dengler, Jürgen
  - Bonari, Gianmaria
  - Vecera, Martin
  - Keil, Petr
  - et al.
year: 2026
source: midolo_2026_denser_vegetation
tags:
  - remote-sensing
  - plant-community-change
  - eutrophication
  - vegetation-densification
  - Ellenberg-indicator-values
  - long-term-change
  - Europe
  - forest-ecology
  - grassland
  - bioindication
keywords:
  - community-mean-EIV
  - nitrogen-enrichment
  - thermophilisation
  - management-cessation
  - EVA-database
  - ReSurveyEurope
  - spatiotemporal-interpolation
  - random-forest
  - light-decline
status: summarized
---

## Title and Authors of the Paper

*Sixty years of plant community change in Europe indicate a shift toward nutrient-richer and denser vegetation* — Gabriele Midolo, Adam Thomas Clark, Milan Chytrý, Franz Essl, Stefan Dullinger, Ute Jandt, Helge Bruelheide, Jürgen Dengler, Gianmaria Bonari et al. (2026), Science Advances, 12, eaeb2493. DOI: 10.1126/sciadv.aeb2493. Published 10 April 2026.

## Quick Overview

- **Why is it relevant?** Large-scale, multi-decadal assessments of how environmental conditions have shifted in European plant communities were lacking, yet such trends underlie many RS-observed signals (NDVI greening, canopy densification, species range shifts).
- **What was done?** Quantified 60-year trends (1960–2020) in community-mean Ellenberg Indicator Values (CM_EIVs) for light, temperature, moisture, nitrogen, and soil reaction across 644,524 European vegetation plots and validated against 18,345 actual resurvey time series.
- **What is the main outcome?** Nitrogen demand in plant communities has increased substantially across all European habitat types (+0.25 CM_EIV), accompanied by declining light demand (denser vegetation); temperature change was weak and mostly confined to alpine habitats; results indicate a continent-wide shift driven primarily by eutrophication and management cessation, not warming.

## Main Goal and Fundamental Concept

European plant communities have been changing under multiple anthropogenic pressures (warming, eutrophication, land-use change, altered disturbance regimes), yet their combined effect on community composition across habitats and regions was unquantified at continental scale.

**Ellenberg Indicator Values (EIVs)** are expert-based, species-level ecological scores (0–10 scale) for light, temperature, moisture, soil nitrogen, and soil reaction (pH), reflecting the realized ecological niche of each species. Community-mean EIVs (CM_EIVs) — averages of EIVs across co-occurring species — provide a proxy for environmental conditions that:
- Can be computed from any existing species list (no direct measurements needed)
- Are robust to observer-related resurvey errors
- Enable retrospective reconstruction of long-term environmental change from historical species data

Data source: EIVE (Ecological Indicator Values for Europe, version 1.0) — consensus system from 31 regional expert-based EIV systems; covers 13,874 of 16,810 vascular plant taxa in the European Vegetation Archive (EVA).

## Technical Approach

**Datasets:**
- **EVA** (European Vegetation Archive): 644,524 vegetation plots (622,906 from single surveys; 21,618 from ReSurveyEurope time series)
- **ReSurveyEurope**: 18,345 resurvey plots with ≥2 observations (1960–2020); used for validation
- Four main EUNIS level-1 habitat types: forest, grassland, scrub, wetland
- Plot size standardised per habitat type: 225 m² (forests), 16 m² (grasslands), 50 m² (scrub), 25 m² (wetlands)

**Spatiotemporal interpolation approach:**
- Treat each plot as a single observation in space-time
- Train random forests to model CM_EIV as a function of: northing, easting, elevation, sampling year, species richness, plot size, habitat type
- Predict CM_EIV for each plot across all years 1960–2020 → reconstruct temporal trends
- Validated against actual time series from ReSurveyEurope (Pearson r: 0.51–0.61 for observed vs predicted EIV changes)
- Model performance: R² = 0.78 (nitrogen), 0.93 (temperature)

**Statistical analysis of time series:**
- Linear mixed-effects models (lme4) on 57,255 ReSurveyEurope observations from 18,345 plots
- CM_EIV ~ habitat type × sampling year + log₁₀(plot size) + (1|dataset/plot)
- Model coefficients give decadal change in CM_EIV per habitat type

## Key Results

**Nitrogen (strongest trend):**
- **Mean change: +0.25 CM_EIV (1960→2020)**; 62% of plots increased by ≥0.1
- Consistent positive trend across all four habitat types and across all of Europe (Fig. 2)
- Strongest increase in nutrient-poor habitats (dry grasslands, nitrogen-poor scrub) — highest relative gain from a low baseline
- Fertile habitats (tall-forb stands, some wetlands): no change or slight decrease
- **Drivers**: cropland fertilization runoff + atmospheric reactive nitrogen deposition since mid-20th century; management cessation allows nitrogen build-up in soil; amplified by CO₂ fertilization effects on biomass
- ReSurveyEurope confirms: +0.04 CM_EIV/decade in forests; +0.06 CM_EIV/decade in some habitat types (Table S1)

**Light (second strongest trend):**
- **Mean change: -0.12 CM_EIV** — vegetation has become denser and more shade-tolerant
- Negative trend in grasslands (-most pronounced) and wetlands; forests: no overall change but positive in some habitat types (coniferous, broadleaved evergreen — canopy disturbance signal)
- Mechanistic link: higher nitrogen → higher plant biomass → higher canopy/herb-layer density → reduced light at ground level → light-demanding species decline, shade-tolerant species gain
- Management cessation (grazing, coppicing) removes disturbance that historically maintained open conditions → vegetation closes in
- Light decline is the mirror image of the nitrogen increase — both reflect the same densification process

**Temperature (weakest trend):**
- **Mean change: +0.04 CM_EIV** — surprisingly small given ~1°C warming over 60 years
- Detectable thermophilisation only in alpine and subalpine scrub and grasslands (last two decades, Fig. 3)
- Forests: no detectable temperature CM_EIV trend overall; broadleaved evergreen forests positive
- **Why warming signal is weak:**
  - In flat lowland terrain, temperature gradients span large geographic areas → few thermophilous colonizer species immediately available locally → slow community response
  - In mountains: steeper elevation gradients → thermophilous species available upslope → more rapid detectable shifts
  - Indirect warming effect: denser vegetation (from N + CO₂) cools the understory → can counteract the direct warming signal in forests and closed habitats

**Moisture:**
- **Wetlands: mean -0.20 CM_EIV** (strong decline in hygrophilous species) — drainage, hydrological modification
- **Dry habitats** (Mediterranean scrub, dry grasslands): moisture CM_EIV increased → mesophilisation (more moisture-tolerant species replacing dry-habitat specialists)
- Pattern reflects contrasting drivers: wet habitats dry out; dry habitats become more mesic (management cessation + N enrichment → generalist species gain)

**Soil reaction (pH):**
- **Mean +0.02 CM_EIV** — small but detectable shift toward less acidophilous communities
- Forests: positive trend (less acid-tolerant species gaining) → soil pH recovery following abatement of sulfur deposition (acid rain) post-1980s
- Tundra, bogs, fen scrub: positive trend (consistent with acid rain recovery and increasing base cation deposition)
- Grasslands/wetlands: generally negative or flat reaction trend

**Habitat-type specifics:**

| EIV | Forest | Grassland | Scrub | Wetland |
|-----|-------|----------|-------|---------|
| Light | ~0 (disturbance in some subtypes) | Strong decrease | Moderate decrease | Moderate decrease |
| Temperature | ~0 (subalpine increase) | ~0 | Strong increase (alpine) | ~0 |
| Moisture | ~0 | Moderate increase | Moderate increase | Strong decrease |
| Nitrogen | Moderate increase | Strong increase | Strong increase | Strong increase |
| Reaction | Positive | Slight negative | ~0 | ~0 |

## Advantages and Limitations

**Advantages:**
- Largest European vegetation community change assessment: 644,524 plots across 60 years
- Both interpolation (EVA) and direct resurvey (ReSurveyEurope) approaches give consistent results — mutual validation
- Habitat-specific and continent-wide patterns simultaneously revealed
- EIVs are robust to observer effects — well-suited for meta-analyses combining heterogeneous resurvey data

**Limitations:**
- EIVs are correlated at community level → difficult to isolate individual driver effects (multicollinearity)
- EIVs reflect realised niche, not fundamental niche — community-mean shifts could reflect both environmental change and biotic interactions
- Long-lived species (trees, shrubs) may respond slowly → lags underestimate true environmental change
- Space-for-time substitution (EVA interpolation) assumes stationarity of species-environment relationships

## Environmental and RS Implications

- **NDVI greening signal partly explained**: nitrogen-driven vegetation densification → higher LAI → higher NDVI; this is a distinct driver from temperature-driven growing season lengthening; both contribute to satellite-observed greening trends — see [[vegetation_greenness_trends]]
- **Canopy cover increase**: light decline reflects increasing shade-tolerant species dominance and canopy closure → directly relevant to canopy cover change mapping from RS (e.g., [[wegler_2026_canopy_cover_loss]])
- **SDM predictors**: nitrogen and moisture EIV trends mean that historical climate-distribution relationships used in SDMs may be confounded by these non-climatic drivers
- **Management context**: eutrophication and management cessation are as important as warming for driving vegetation change — restoration and management interventions can counteract these trends; nature conservation must account for both

## Conclusion

Midolo et al. (2026) demonstrate that nitrogen enrichment and associated vegetation densification are the dominant drivers of 60-year plant community change across European habitats — more so than global warming, whose signal is weak and largely confined to alpine environments. The finding that temperature thermophilisation is detectable only in mountain habitats (where colonizer species are nearby and available) provides a key mechanistic explanation for why satellite-observed warming signals in vegetation are often clearest at high elevations. The results are directly relevant for interpreting long-term remote sensing vegetation trends: the continent-wide NDVI greening signal reflects multiple confounded drivers (nitrogen-driven densification, management changes, CO₂ fertilization, and only partially warming).

## Related Work & Obsidian Links

- [[vegetation_community_change]]
- [[vegetation_greenness_trends]]
- [[plant_functional_traits]]
- [[functional_diversity]]
- [[phenology]]

- [[bayle_2024_landsat_greening_inflated]] — Bayle et al. show sampling bias inflating Landsat greening; Midolo et al. show eutrophication/densification as a real driver; together they reveal that observed satellite greening has multiple confounded causes
- [[herraiz_2025_phen_shifts_mediterranean]] — Mediterranean species show positive NDVI trends; Midolo et al. provide the community-level mechanism: nitrogen enrichment drives generalist species with higher biomass into these systems
- [[bricca_2026_topo_diversity]] — both study vegetation community change in European forests; Bricca et al. focus on functional diversity response to temperature; Midolo et al. show temperature is the weakest driver at the community scale — eutrophication dominates
- [[grünig_2026_climate_change_disturbances_forest]] — disturbances (windthrow, bark beetles) open the canopy → increased light → temporary reversal of the light-decline trend documented by Midolo et al.; the two studies together describe opposing forces on canopy closure
- [[hiebl_2025_pretraining]] — shares co-author Gianmaria Bonari; nitrogen-driven shifts in EVE cover documented here are the macroecological context for EVE expansion monitored by Hiebl et al.

## Related pages

- [[vegetation_community_change]]
- [[vegetation_greenness_trends]]
- [[forest_disturbances]]
- [[phenology]]
- [[plant_functional_traits]]
- [[functional_diversity]]
- [[bayle_2024_landsat_greening_inflated]]
- [[herraiz_2025_phen_shifts_mediterranean]]
- [[bricca_2026_topo_diversity]]
- [[grünig_2026_climate_change_disturbances_forest]]
- [[hiebl_2025_pretraining]]
