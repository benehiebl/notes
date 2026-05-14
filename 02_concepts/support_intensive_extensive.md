---
name: support_intensive_extensive
description: Variable support (point vs block) and spatial intensity/extensity — semantics that govern correct aggregation, disaggregation, and combination of spatial data
type: reference
tags:
  - remote-sensing
  - methodology
---

# Variable Support and Intensive vs Extensive Variables

**Summary**: Two semantic properties of every spatial variable determine which operations are valid: its *support* (whether a value refers to every point inside a geometry or summarises the geometry as a whole) and, for non-point support, whether it is *spatially intensive* (averages preserved on aggregation) or *spatially extensive* (sums preserved). Most geospatial software ignores these properties, which silently produces wrong results when datasets are combined.

**Sources**: [[pebesma_2025_spatial_data]]

**Last updated**: 2026-05-13

---

## Support: Point vs Block

A variable has **point support** if the recorded value is valid at every point inside the associated geometry. Examples:
- Soil type, land use class, fire risk category for a polygon — the whole polygon shares the value.
- Air temperature read by a sensor at its location.

A variable has **block support** (or line / area / period support) if the value summarises a property over the geometry. Examples:
- County population count, population density, standardised disease incidence rate — values are aggregates, not pointwise truths.
- Time-period rainfall total, mean monthly temperature.

Polygon boundaries on a point-support map mark where the variable *changes*; on a block-support map they are often administrative and have no relation to the aggregated variable.

Aggregating or disaggregating *point-support* variables is trivial — every value is known. For *block-support* variables, aggregation/disaggregation needs auxiliary information (dasymetric mapping, climate downscaling) and is intrinsically uncertain (source: [[pebesma_2025_spatial_data]]).

## Intensive vs Extensive (only for block / line / area support)

For block-support variables, a second property decides what to preserve when geometries change:

| Type | Preserved | Split policy | Merge policy | Examples |
|---|---|---|---|---|
| **Intensive** | Average | Duplicate value | Geometry-weighted average | Population density, mean temperature, average road width |
| **Extensive** | Sum | Geometry-ratio split | Sum | Population count, CO₂ emission, road length, county area |

These properties can differ between space and time. Annual CO₂ emissions of a power plant are **spatially extensive** (sum across plants in a region) but **temporally intensive** (mean across years), demonstrating that the flag must be defined per dimension (source: [[pebesma_2025_spatial_data]]).

## Why It Matters for Modelling

- Combining variables with non-matching geometries (point sensor + polygon census + raster reanalysis) requires correct split/merge rules; using the wrong policy silently inflates or deflates totals.
- Splitting an extensive block-support variable to point geometries is mathematically meaningless (an infinite number of zero-valued points would be needed to sum to the polygon total). Software should refuse or warn (source: [[pebesma_2025_spatial_data]]).
- Categorical variables can be conceptualised as (mostly) intensive but typically need a proportional treatment on redistricting (e.g. Tobler in Python).

## Software Status

(source: [[pebesma_2025_spatial_data]])

- **R `sf`**: each `data.frame` column carries an `agr` attribute — `constant` (point support), `aggregate` (block support), or `identity` (geometry ID). Operations that assume point support emit a warning when `agr` is missing or `aggregate`. The only library among the three to surface support semantically.
- **Python (GeoPandas, PySAL)**: no built-in propagation of support or intensiveness — responsibility falls on the user. Some PySAL modules ask the user to specify a variable type explicitly.
- **Julia**: same situation as Python — no built-in tracking.
- **File formats**: GeoTIFF has the `AREA_OR_POINT` flag; GeoPackage/FileGeoDatabase support `split policy` + `merge policy` field domains; NetCDF CF conventions encode aggregation via `cell_methods` (e.g. `time: sum`, `time: maximum`).

Pebesma et al. recommend collapsing the two policies into a single boolean `is_spatially_extensive`, since one implies the other (source: [[pebesma_2025_spatial_data]]).

## Practical Implications for Forest / RS Workflows

- When combining NFI plot data (point support — species present at a plot) with raster prediction maps (block support — pixel cover averages or counts), be explicit about which is which before aggregating to forest-type polygons.
- Population density-like raster products (e.g. canopy cover %) are spatially intensive — area-weighted averaging on upscaling.
- Counts (e.g. tree count per polygon, disturbance event count per region) are extensive — sum on upscaling, area-ratio on downscaling.
- Time-aggregated outputs (annual NDVImax, growing-season-summed NDVI) inherit temporal extensity/intensity that should be flagged before further aggregation — connects to [[sampling_bias_remote_sensing]].

## Related concepts
- [[sampling_bias_remote_sensing]]
- [[spatial_proxies_random_forest]]
- [[area_of_applicability]]
