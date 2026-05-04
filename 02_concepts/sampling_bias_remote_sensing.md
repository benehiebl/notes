---
name: sampling_bias_remote_sensing
description: Systematic bias in satellite time series arising from non-uniform observation frequency over time, causing spurious trends in annual composites like NDVImax
type: reference
---

# Sampling Bias in Remote Sensing Time Series

**Summary**: Sampling bias in remote sensing arises when the number of usable observations changes systematically over a multi-year record, causing spurious trends in annual composited products even when the underlying environmental signal is stable.

**Sources**: bayle_2024_landsat_greening_inflated.pdf

**Last updated**: 2026-05-05

---

## The Mechanism

Annual compositing — e.g., computing NDVImax as the maximum observed NDVI within a growing season — assumes that sampling frequency is sufficient to capture the true signal each year. When observations are sparse, the estimated annual metric systematically underestimates the true value. If sampling density increases over time (as with Landsat), the underestimation decreases in more recent years, creating a positive artifact trend even when the underlying variable is unchanged (source: bayle_2024_landsat_greening_inflated.pdf).

This mechanism produces **"false trends"** (αβF): statistically significant NDVI trends that are entirely artefactual.

The relationship between OBS_GS (growing-season observations) and NDVImax underestimation is asymptotic — early years (few observations) see large underestimation; once sufficient observations are available the curve flattens.

## Where the Bias Is Most Severe

The bias is strongest when:
- **Growing season is short**: fewer opportunities to sample the peak (high elevations, arctic, subarctic)
- **Observation density is low**: cloud cover, Landsat revisit limits, geographic remoteness
- **The phenological curve is sharply peaked**: the maximum is easy to miss with sparse sampling

In the European Alps, late-snowmelt pixels above 2400 m a.s.l. are most affected — up to 50% of observed greening trends in these zones are artefactual (source: bayle_2024_landsat_greening_inflated.pdf).

## Key Drivers (Quantified)

A random forest regression model (R² = 0.963) found that two variables explain nearly all spatial variance in false trend magnitude:
- **ΣOBS_GS**: cumulative number of clear-sky, snow-free growing-season observations over the full time series (slightly more important)
- **GSL**: growing season length in days (slightly less important but strongly correlated with ΣOBS_GS)

Short GSL combined with low ΣOBS_GS produces the largest false trends.

## Implications for Ecological Research

- Greening trend comparisons across elevation or latitude gradients are confounded if observation density co-varies with those gradients
- Arctic, subarctic, and mountain ecosystems worldwide face the same bias
- Studies interpreting Landsat-based greening at high elevations as evidence of thermophilisation (upslope migration) may be overstating real ecological change
- Papers reporting NDVImax trends without reporting observation counts per year should be interpreted with caution

## Correction Strategies

1. **Avoidance**: Restrict analysis to years or pixels with sufficient observations (e.g., minimum N per season); use only overlapping Landsat tile zones
2. **Temporal reconstruction / phenological correction**: Fit a phenological model to the observed NDVI time series and extract NDVImax from the fitted curve rather than the raw observations — decouples NDVImax from observation density
3. **Data fusion**: Combine Landsat with higher-frequency sensors (MODIS, Sentinel-2) to fill temporal gaps before compositing

## Related pages

- [[landsat]]
- [[ndvi]]
- [[phenology]]
- [[vegetation_greenness_trends]]