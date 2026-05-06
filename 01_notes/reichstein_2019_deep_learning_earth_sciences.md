---
title: "Deep learning and process understanding for data-driven Earth system science"
authors:
  - Reichstein, Markus
  - Camps-Valls, Gustau
  - Stevens, Bjorn
  - Jung, Martin
  - Denzler, Joachim
  - Carvalhais, Nuno
  - Prabhat
year: 2019
source: reichstein_2019_deep_learning_earth_sciences
tags:
  - deep-learning
  - machine-learning
  - remote-sensing
status: read
---

# Reichstein et al. 2019 — Deep Learning and Process Understanding for Earth System Science

## Title and Authors
**Deep learning and process understanding for data-driven Earth system science**
Markus Reichstein, Gustau Camps-Valls, Bjorn Stevens et al. — *Nature*, 2019

## Quick Overview
- **Why is it relevant?** Foundational perspective paper arguing that deep learning in Earth sciences must go beyond pattern matching to incorporate physical process understanding — directly shaping how to design hybrid models for ecological and RS applications.
- **What was done?** Reviewed the application of machine learning and deep learning across geosciences, identified limitations of purely data-driven approaches, and proposed a roadmap for hybrid models coupling physical process models with deep learning.
- **What is the main outcome?** Purely data-driven deep learning excels at pattern extraction from big geoscience data but fails at extrapolation and process understanding; the next step is hybrid modelling that respects physical constraints.

## Main Goal and Fundamental Concept
Earth system data are "big" in all four dimensions (volume, velocity, variety, veracity), but predictive ability has not improved commensurately with data availability. Deep learning can extract spatio-temporal features automatically, overcoming limitations of classical ML. However, incorporating physical process understanding as constraints, priors, or loss function terms is necessary for reliable prediction and scientific insight.

## Technical Approach
This is a perspective/review paper, not an empirical study. Key conceptual contributions:
- **State-of-the-art review:** ML/DL applications in atmosphere, land surface, ocean
- **Spatio-temporal context:** Argues that the ability of DL to extract spatio-temporal features is key advantage over classical ML for Earth system problems
- **Hybrid modelling:** Proposes coupling physical process models with DL for improved extrapolation and interpretability
- **Problem taxonomy:** Classification, regression, forecasting, emulation, parameter estimation, causal inference

## Distinctive Features
- Published in *Nature* — defines the research agenda for an entire field
- Articulates the fundamental tension between data-driven flexibility and physical plausibility
- Introduces concept of "physics-informed neural networks" and "hybrid modelling" for geosciences
- Provides Box 1 glossary for DL terms in geoscientific context

## Key Arguments
- Classical ML maps static spatial covariates to targets; deep learning additionally captures temporal dynamics and spatial context
- Recurrent networks (LSTM, GRU) and CNNs for time series are most relevant architectures for Earth system problems
- Hybrid models: physical model provides structure/constraints; DL fills gaps and corrects systematic errors
- Key challenge: **uncertainty quantification** — DL models are overconfident; calibrated uncertainty needed for Earth science use
- Spatial autocorrelation in train/test splits is a universal concern inflating reported performance

## Advantages and Limitations
- **Advantages:** Defines the intellectual framework for a decade of research; highly cited; accessible to diverse audiences
- **Limitations:** Does not provide specific algorithmic guidance; hybrid modelling remains aspirational in many areas

## Conclusion
Deep learning is transformative for Earth system science but must be combined with physical process understanding to achieve reliable predictions beyond training data distributions. Hybrid models coupling DL with physics are the recommended path forward. This paper defines the intellectual framework under which Reichstein's group and many others work.

## Related pages
- [[transfer_learning_remote_sensing]]
- [[neural_network_training]]
- [[vegetation_greenness_trends]]
- [[phenology]]
