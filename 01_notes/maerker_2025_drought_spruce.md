---
title: "Emerging drought sensitivity for large Norway spruce trees at high elevation in the High Tatras, Slovakia"
authors:
  - Frederik Märker
  - Mario Trouillier
  - Saroj Basnet
  - Andreas Burger
  - Zuzana Homolová
  - Michal Gazovic
  - Martin Wilmking
year: 2025
tags:
  - forest-ecology
  - drought
keywords:
  - Picea abies
  - tree rings
  - dendrochronology
  - climate sensitivity
  - tree size
  - non-stationarity
  - treeline
status: unread
---

## Title and Authors of the Paper

Märker, F., Trouillier, M., Basnet, S., Burger, A., Homolová, Z., Gazovic, M., Wilmking, M. (2025). "Emerging drought sensitivity for large Norway spruce trees at high elevation in the High Tatras, Slovakia." *Trees* 39:7. https://doi.org/10.1007/s00468-024-02576-9 (published online 12 December 2024).

## Quick Overview
- **Why is it relevant?** It shows that even at a supposedly temperature-limited alpine treeline, Norway spruce growth is becoming increasingly constrained by drought, and that this drought sensitivity is emerging specifically in the largest trees.
- **What was done?** Tree-ring cores from 150 Norway spruce trees (treeline and adjacent closed-canopy forest, High Tatras, Slovakia) were grouped into four size classes using the size-class-isolation (SCI) method and analyzed with 31-year moving-window climate-growth correlations against temperature, precipitation, and SPEI3 (1950-2019).
- **What is the main outcome?** Climate-growth correlations are non-stationary across all size classes; trees remain generally temperature-limited (June/July temperature, shifting toward July in recent decades), but the largest ("Big") size class has developed an increasing, significant negative sensitivity to drought (previous-year August/September SPEI3) that is not seen to the same degree in smaller trees.

## Main Goal and Fundamental Concept

- Test whether tree size modulates climate sensitivity of *Picea abies* (Norway spruce) at an alpine treeline, and how this sensitivity has changed over time (1950-2019).
- Motivation: trees at temperature-limited sites (e.g., alpine treelines) are often assumed to simply benefit from warming, but increasing drought events could offset this benefit; larger trees are frequently reported (though inconsistently) in the literature to suffer more under drought.
- Core method: size-class isolation (SCI) — building artificial ring-width chronologies that hold stem diameter constant over time (rather than using each tree's full lifetime series), so that size effects on climate sensitivity are not confounded with age/size-at-sampling effects.

## Technical Approach

- **Study site**: High Tatra Mountains, Slovakia; two 1-ha plots near Popradske Pleso — a closed-canopy forest plot (PF, ~1550 m a.s.l.) and an adjacent treeline plot (PT, ~1575 m a.s.l.).
- **Sampling**: All living *P. abies* trees with DBH > 10 cm cored in 2021 (n=158 initially; n=150 after removing trees younger than 33 years to increase series overlap; n_PT=54, n_PF=96).
- Ring widths measured, cross-dated, detrended with a 30-year cubic smoothing spline (dplR in R).
- **Climate data**: CRU TS monthly temperature and precipitation (1901-2019, 0.5° resolution); SPEI3 (3-month Standardized Precipitation Evapotranspiration Index) calculated from these to capture soil moisture/drought conditions.
- **Size classes** (via SCI, based on raw ring width + pith offset, in 100 mm moving steps, min. 10 trees/class/year): Tiny (1-11 cm), Small (12-22 cm), Middle (24-34 cm), Big (35-45 cm) stem diameter.
- **Statistics**: Principal Component Gradient Analysis (PCGA) to check for sampling-design artifacts between plots (none found, so plots pooled); bootstrapped monthly climate-growth correlations (static, whole period); 31-year moving-window correlations per size class to assess non-stationarity; significance tested at p ≤ 0.05.
- DBH was used as a proxy for tree height (measured relationship was non-linear/saturating, not perfectly 1:1).

## Distinctive Features

- Uses the SCI method to explicitly decouple tree size from age when building chronologies — a methodological alternative to simply treating DBH as a covariate or splitting trees into size classes by final diameter.
- Directly compares four size classes' climate sensitivity through time via moving-window correlations, rather than a single static correlation, allowing detection of *emerging* (not just existing) sensitivities.
- Focuses specifically on a treeline ecotone where trees are assumed a priori to be temperature-limited, making any detected drought signal a stronger/more surprising result.
- Distinguishes current-year vs. previous-year (lagged) climate effects — the key finding (drought sensitivity in Big trees) is a **previous-year** (August/September) SPEI3 effect, interpreted via non-structural carbohydrate (NSC) storage dynamics rather than a same-year physiological drought response.

## Experimental Setup and Results

- **Static (whole-period) correlations**: All size classes positively correlated with June/July temperature and preceding October temperature; positive precipitation correlations in January and preceding December; negative correlations with June-September SPEI3. Correlation strength was generally low (r ≈ ±0.3-0.4); Big and Middle trees correlated with more monthly climate variables than Small/Tiny trees, but there was no consistent size-ranked pattern.
- **Moving-window (non-stationary) correlations**: Significant positive temperature correlations shifted from June to July across all size classes over 1950-2019 (interpreted as reflecting a lengthening/later growing season, following Ponocná et al. 2018).
- Previous-year July temperature correlations decreased over time, while previous-year July precipitation and previous-year August/September SPEI3 correlations increased across size classes — a general trend toward higher drought sensitivity to prior-season conditions.
- **Big trees specifically**: developed almost constant, significant positive correlations to previous-year August (from ~1976-2006 onward) and September (from ~1974-2004 onward) SPEI3, plus significant negative previous-year July temperature correlations in the most recent windows — a pattern that emerged over time and was more pronounced/consistent than in Tiny, Small, or Middle trees.
- Contrary to much of the literature reviewed by the authors (which more often reports larger trees as more drought-sensitive), the static analysis showed **no clear consistent size-ranked pattern** — the size effect only became apparent as a temporal (emerging) trend, not as a fixed difference.

## Advantages and Limitations

- **Strengths**: Relatively large sample for a dendroecological study (150 trees, 158 cores); explicit methodological control for size-age confounding via SCI; robust bootstrapped/moving-window statistics; directly addresses a specific, well-motivated hypothesis (size-modulated drought sensitivity at treeline).
- **Small/uneven per-class-per-year replication**: minimum sample size within each size class per year was only 10 trees in some periods — the authors themselves flag this as reducing robustness; Trouillier et al. (2019, cited by the authors) recommend >500 trees per size class for this method, far more than used here.
- **Sampling imbalance**: treeline trees were generally smaller than forest trees, so bigger trees from the treeline plot may be underrepresented in larger size classes (spatial/plot bias); the authors argue this is likely minor since PCGA found no distinct high-frequency separation between plots, but this is an assumption, not a proven absence of bias.
- **Single site, single species**: results come from one specific (if typical) treeline site in the High Tatras; the authors explicitly note it is unclear whether the pattern generalizes to a broader spatial scale.
- **DBH as height proxy**: relationship between DBH and height is non-linear (saturating curve), so the "Big" size class is not guaranteed to be the tallest trees — a potential mismatch with the physiological (height-related hydraulic) mechanisms invoked in the discussion.
- **Correlative, not causal/mechanistic**: climate-growth correlations do not establish the underlying physiological mechanism; the paper is explicit that a conclusive understanding of *why* large trees might become more drought-sensitive (hydraulic limitation vs. NSC depletion vs. atmospheric coupling) "is still lacking" in the field generally, and this study does not resolve it — it proposes NSC depletion and increased atmospheric coupling/isohydric behavior as plausible but untested explanations.
- Climate data are coarse-resolution gridded CRU TS (0.5°), not on-site microclimate measurements, which may not capture fine-scale treeline microclimatic variation relevant to individual trees.

## Conclusion

- Climate-growth correlations of Norway spruce at the High Tatras treeline are non-stationary across all size classes, with a general shift from June- to July-temperature sensitivity over 1950-2019.
- Growth remains generally temperature-limited during the growing season, but an increasing drought signal (previous-year late-summer SPEI3, previous-year July precipitation) has emerged across the population.
- Critically, the largest ("Big") trees have developed an increasing and significant sensitivity to previous-year August/September drought conditions not shared to the same extent by smaller size classes — an emerging, not static, size effect.
- The authors interpret this as consistent with a global shift from energy- to moisture-limited tree growth (citing Babst et al. 2019) and argue that drought stress needs to be considered even at treelines traditionally assumed to be purely temperature-limited.
- They call for future work disentangling the roles of tree size vs. canopy position, and for testing whether this pattern holds across a broader spatial range of treeline sites.

## Related pages

- [[babst_2019_redistribution]]
- [[schuldt_2020_drought_forest]]
- [[chelli_2017_climate]]
- [[wegler_2026_canopy_cover_loss]]
- [[noce_2023_altitude_shift_tree_italy]]
- [[drought_mortality]]
- [[topographic_microclimate]]
- [[treeline_ecotone_theory]]
