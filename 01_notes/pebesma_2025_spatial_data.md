---
title: "Spatial Data Science Languages: commonalities and needs"
authors:
  - Pebesma, Edzer
  - Fleischmann, Martin
  - Parry, Josiah
  - Nowosad, Jakub
  - Graser, Anita
  - Dunnington, Dewey
  - Pronk, Maarten
  - Schouten, Rafael
  - Lovelace, Robin
  - Appel, Marius
  - Abad, Lorena
year: 2025
source: pebesma_2025_spatial_data
tags:
  - remote-sensing
  - methodology
keywords:
  - spatial data science
  - R sf
  - GeoPandas
  - Julia Rasters
  - data cubes
  - point support
  - block support
  - intensive variable
  - extensive variable
  - geodetic coordinates
  - simple features
  - GeoParquet
  - GeoArrow
  - openEO
status: read
---

# Pebesma et al. 2025 — Spatial Data Science Languages: Commonalities and Needs

## Title and Authors
**Spatial Data Science Languages: commonalities and needs**
Edzer Pebesma, Martin Fleischmann, Josiah Parry, Jakub Nowosad, Anita Graser, Dewey Dunnington, Maarten Pronk, Rafael Schouten, Robin Lovelace, Marius Appel, Lorena Abad — arXiv:2503.16686, 24 March 2025.

## Quick Overview
- **Why is it relevant?** Distils, from two SDSL (Spatial Data Science across Languages) workshops, a set of conceptual and tooling gaps shared by R, Python, and Julia spatial ecosystems — directly relevant to building reproducible RS/forest-modelling pipelines.
- **What was done?** A community position paper reviewing common challenges across in-memory data formats, geometry support, data cubes, geodetic geometry, statistical modelling, and cross-language development.
- **What is the main outcome?** Five recommendations: cross-silo standards, explicit handling of variable support (point vs block, intensive vs extensive), spherical-geometry corrections to simple features, community/diversity stewardship, and investment in cross-language tooling.

## Main Goal and Fundamental Concept
The paper documents shared design tensions in spatial data science software and proposes how the R (`sf`, `stars`, `terra`), Python (`GeoPandas`, `xarray`, `rasterio`), and Julia (`Rasters.jl`, `GeoDataFrames.jl`, `GeometryOps.jl`) ecosystems can converge. The unifying concept is that spatial data have *semantic* properties (support, intensiveness, geodetic vs Cartesian geometry, time-varying behaviour) that current toolchains often ignore, leading to silent errors when operations cross those boundaries.

## Technical Approach
Workshop synthesis rather than empirical study. Structure:
1. History of spatial tooling in R (since the mid-1970s S roots, `sf` superseding `rgdal`/`rgeos` in 2023), Python (Shapely/Fiona/rasterio → GeoPandas → xarray), and Julia (wrapping GDAL/GEOS/PROJ via `.jll` artefacts, native `GeometryOps.jl`).
2. Inventory of common challenges with subsections per language.
3. Lessons learned: differing release/dependency cultures (CRAN reverse-dep checks vs Python conda-forge cross-compile vs Julia semver bounds).
4. Five recommendations.

## Distinctive Features
- **Cross-language perspective**: rare comparison putting R, Python and Julia spatial idioms side-by-side.
- **Formal treatment of variable support**: distinguishes *point support* (value valid at every point of the geometry; e.g. soil type, land use) from *block support* (value summarises the geometry; e.g. population count, county density), and *spatially intensive* (averages preserved on aggregation) from *spatially extensive* (sums preserved) — with table of split/merge policies.
- **Spherical-geometry deep dive**: explicit list of simple-feature standard amendments needed for the sphere (POLYGON FULL, winding order, great-circle arcs, validity).
- **GIS vs modelling community comparison table** (Cartesian/regular raster/Shapefile vs geodetic/curvilinear/NetCDF+CF).
- **Cross-language tooling map**: pixi as a language-agnostic env manager, Rocker/geocompx/b-data Docker images, openEO as a common cloud-processing API.

## Key Concepts Surfaced (selection)

**Support of a variable**
- Point support: value valid for every point of the geometry (e.g. soil type for a polygon, temperature at a sensor).
- Block support: value summarises an area/period (e.g. county population, mean monthly rainfall).
- Disaggregation of point support is trivial; disaggregation of block support requires auxiliary variables (e.g. dasymetric mapping).

**Intensive vs extensive**
- Extensive: sums preserved on aggregation (CO₂ emissions, population count, road length, county area). Split policy: geometry-ratio; merge policy: sum.
- Intensive: averages preserved on aggregation (population density, temperature, road width). Split policy: duplicate; merge policy: weighted average.
- Intensiveness may differ between the spatial and temporal dimensions (e.g. annual CO₂ emissions = spatially extensive, temporally intensive).

**Geodetic vs Cartesian geometry**
- Treating longitude/latitude as Cartesian (plate carrée) is a long-standing default but breaks at poles, at the dateline, and over large extents.
- On a sphere: any ring divides the surface into two finite parts; CW/CCW winding is ambiguous; straight lines become great-circle arcs; POLYGON FULL needs explicit representation.
- `sf` (R, since 1.0-0 in 2020) uses S2Geometry for geodetic coordinates by default; GeoPandas plans Spherely bindings; Julia largely Cartesian for now.

**Data cubes**
- n-D arrays indexed by spatial/temporal/categorical dimensions; cover Sentinel-2 stacks, weather reanalyses, climate forecasts.
- R: `stars` (generic n-D), `terra` (raster stacks), `gdalcubes` (regular cubes from STAC catalogues), `sits` (SITS classification).
- Python: `xarray` + `dask` (parallel), StackSTAC for STAC→cube, Pangeo ecosystem.
- Julia: `Rasters.jl`, `YAXArrays.jl`, `DimensionalData.jl`, `DiskArrays.jl`.
- Cloud-side: openEO is an open alternative to Google Earth Engine and Sentinel-Hub, with clients in all four languages.

**Polygonal coverage**
- True tessellations (no overlaps, no gaps) enable faster overlay and direct neighbour-graph construction; the Simple Features standard doesn't enforce this. GEOS ≥ 3.13 adds coverage validation; `geoplanar` (Python) fixes common planarity violations; tooling in R and Julia is rare.

**Cross-language development**
- `pixi` (since 2023): language-agnostic environment manager.
- Docker / Rocker / geocompx: containerised cross-language stacks — `the` reproducibility gold standard.
- Quarto: multi-language notebooks in a single document (Jupyter cannot mix languages within one notebook).

## Recommendations
1. **Open standards across silos** — work in public OGC repos and beyond; require open-source implementations for OGC adoption; broader use of GeoParquet/GeoArrow as common file/in-memory formats.
2. **Variable support and field domains** — software should warn on illegitimate operations on block-support / extensive variables; collapse split + merge policies into a single `is_spatially_extensive` boolean.
3. **Geodetic / spherical geometry** — augment Simple Features with POLYGON FULL, winding-order convention, great-circle arcs.
4. **Community management** — adopt rOpenSci / pyOpenSci-style review practices; foster diversity; reuse SDSL Discord communities.
5. **Cross-language infrastructure** — invest in environments, containers, and events that explicitly target multi-language work.

## Advantages and Limitations
- **Advantages**: rare cross-ecosystem perspective; well-grounded in concrete software examples; gives terminology (support, intensive/extensive) that bridges GIS and modelling communities; actionable recommendations.
- **Limitations**: position paper, no benchmarks; coverage skewed towards R because of authors' background; spatial network analysis, web-mapping and visualisation explicitly deferred; recommendations depend on community buy-in.

## Conclusion
Spatial data science in R, Python and Julia shares more challenges than is commonly recognised. Treating *support* and *intensiveness* of variables as first-class metadata, embracing spherical geometry as the default for geodetic coordinates, and standardising on GeoParquet/GeoArrow for storage and exchange would prevent a large class of silent errors. The authors call for cross-language infrastructure and communities to mature alongside the per-language ecosystems.

## Related pages
- [[support_intensive_extensive]]
- [[mila_2024_spatial_proxies]]
- [[schloegl_2026_reproducibility]]
- [[xu_2022_cloud_native_algorithms]]
- [[brown_2025_alphaearth]]
