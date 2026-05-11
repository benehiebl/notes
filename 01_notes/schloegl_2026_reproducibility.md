---
title: "Overcoming barriers to reproducibility in geoscientific data analysis: Challenges and practical implementation strategies"
authors:
  - Schlögl, Matthias
  - Waltersdorfer, Laura
  - Regner, Peter
  - Siposova, Andrea
  - Brenning, Alexander
year: 2026
source: schloegl_2026_reproducibility
tags:
  - remote-sensing
  - machine-learning
status: read
---

# Schlögl et al. 2026 — Reproducibility in Geoscientific Data Analysis

## Title and Authors
**Overcoming barriers to reproducibility in geoscientific data analysis: Challenges and practical implementation strategies**
Matthias Schlögl, Laura Waltersdorfer, Peter Regner et al. — *Environmental Modelling and Software*, 2026

## Quick Overview
- **Why is it relevant?** Addresses computational reproducibility as a critical dimension of scientific credibility for geospatial ML workflows — directly applicable to the wiki's research on deep learning-based RS mapping.
- **What was done?** Position paper reviewing reproducibility challenges specific to geospatial data science (spatial data structures, heterogeneous infrastructures, ML) and providing actionable guidance across the research workflow.
- **What is the main outcome?** Reproducibility requires both cultural transformation and practical interventions; the paper recommends open-source software, script automation, version control, and FAIR data principles as core enablers.

## Main Goal and Fundamental Concept
Reproducibility — the ability to independently re-execute a study and obtain the same results — is fundamental to science but systematically compromised in geospatial data analysis. The paper distinguishes three reproducibility types: methodological (same procedures), results (corroborating results from independent study), and inferential (similar conclusions). It focuses on methodological/computational reproducibility and the specific challenges of spatial data.

## Technical Approach
Position paper with:
- Conceptual framework: three reproducibility types (Goodman et al. 2016)
- Barrier taxonomy: obscurity, obfuscation, uncontrollable conditions (software versions, stochastic algorithms)
- Domain-specific challenges: spatial data structures, CRS, geodetic datums, raster alignment; heterogeneous data sources; ML non-determinism; GeoAI biases
- Actionable guidance: data governance, analysis design/documentation, code development, long-term accessibility
- Tools recommended: Git/GitHub, Docker, conda environments, DVC, FAIR principles (findable, accessible, interoperable, reusable)

## Distinctive Features
- Explicitly addresses geospatial data science and GeoAI (spatial ML, LLMs for spatial tasks)
- Distinguishes machine learning reproducibility challenges (stochastic training, version sensitivity) from traditional geospatial analysis
- Includes spectrum from "essentially irreproducible" to "full replicability" as a practical continuum
- Provides link to GitLab repository with reproducibility tools and examples

## Key Recommendations
- Use version control (git) for all code and configuration files
- Containerize analyses (Docker/conda) to fix execution environments
- Apply FAIR principles to data and code sharing
- Document analytical choices and random seeds
- Script all data preprocessing rather than using GUIs
- Share code alongside publications (not just methods descriptions)

## Advantages and Limitations
- **Advantages:** Practical, actionable; geospatial-specific framing; bridges sociology-of-science and technical perspectives
- **Limitations:** Position paper — lacks empirical validation of recommendations' effectiveness; some recommendations require institutional change beyond individual researcher control

## Conclusion
Reproducibility in geospatial data science is achievable through practical incremental improvements: open-source tools, version control, containerization, and FAIR data/code. These practices are especially important for ML workflows in remote sensing where stochastic training and environment sensitivity are pervasive. Adoption requires both tooling and cultural change in publication norms.

## Related pages
- [[transfer_learning_remote_sensing]]
- [[neural_network_training]]
- [[sampling_bias_remote_sensing]]
