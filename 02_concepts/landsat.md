---
name: landsat
description: Landsat satellite program overview — sensors, archive history, observation density patterns, and key limitations for time series analysis
type: reference
---

# Landsat

**Summary**: The Landsat program is a multi-decade series of Earth observation satellites operated by NASA and USGS, providing the longest continuous global land surface record in remote sensing history at 30 m spatial resolution.

**Sources**: bayle_2024_landsat_greening_inflated.pdf, chastain_2007_eve_landsat_understory.pdf

**Last updated**: 2026-05-05

---

## Satellite Generations

| Satellite | Years Active | Sensor | Key Notes |
|-----------|-------------|--------|-----------|
| Landsat 1–3 | 1972–1983 | MSS | 80 m resolution |
| Landsat 4–5 | 1982–2013 | TM | 30 m, 7 bands; workhorse of the archive |
| Landsat 7 | 1999–present | ETM+ | SLC failure 2003 → ~22% data gaps |
| Landsat 8 | 2013–present | OLI + TIRS | Improved radiometry, SNR |
| Landsat 9 | 2021–present | OLI-2 + TIRS-2 | First concurrent pair without technical failure |

## Temporal Resolution and Observation Density

- Nominal revisit time: 16 days per satellite
- Overlapping path tiles double effective revisit frequency in those areas
- Usable (cloud-free, snow-free) observations vary dramatically by location and era:
  - 1980s: ~2–4 usable growing-season observations per year in the European Alps
  - 2013+: ~8–12 usable growing-season observations per year
- The non-uniform increase over time is a major source of bias in trend analyses (source: bayle_2024_landsat_greening_inflated.pdf) — see [[sampling_bias_remote_sensing]]

## Common Derived Products

- **NDVImax**: Annual maximum NDVI from all cloud-free observations within a season — see [[ndvi]] and [[sampling_bias_remote_sensing]]
- **Tasseled Cap**: Brightness, Greenness, Wetness indices
- **Annual composites**: Medoid or median composites for land cover mapping
- **LULC time series**: Long-term land use and land cover change products (e.g., Pflugmacher et al.)

## Key Limitations for Time Series Analysis

- Observation frequency increased non-linearly over the archive → systematic bias in annual composites (see [[sampling_bias_remote_sensing]])
- SLC failure in Landsat 7 (post-2003) creates striped data gaps of ~22%
- Cloud and snow masking (CFmask/Fmask) can misclassify cold surfaces as clouds at high elevations
- Cross-sensor radiometric differences between TM, ETM+, and OLI require normalization (e.g., Roy et al. 2016 correction approach)

## Related pages

- [[ndvi]]
- [[sampling_bias_remote_sensing]]
- [[vegetation_greenness_trends]]
- [[phenology]]