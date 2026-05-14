---
name: area_of_applicability
description: Meyer & Pebesma's predictor-space distance metric for identifying parts of a prediction map that lie outside the training feature space
type: reference
tags:
  - machine-learning
  - remote-sensing
  - methodology
---

# Area of Applicability (AOA)

**Summary**: The Area of Applicability is the spatial extent in which a fitted ML model has training samples sufficiently similar (in predictor space) to make trustworthy predictions. Outside the AOA, predictions are extrapolation and should be flagged.

**Sources**: [[mila_2024_spatial_proxies]]

**Last updated**: 2026-05-13

---

## Idea

Standard ML accuracy metrics describe average error over the test set, not where on the map predictions can be trusted. Meyer & Pebesma (2021) proposed the AOA as a per-pixel diagnostic:

- Compute weighted distances in predictor space between each prediction location and the nearest training samples
- Variables are weighted by their model importance — proxies and dominant features count more
- A threshold derived from training-sample dissimilarities defines the AOA boundary
- Cells beyond the threshold are "outside the AOA" → feature extrapolation, not interpolation

Unlike convex hulls or simple variable-range checks, the AOA accounts for predictor sparsity *inside* the range and for variable importance, giving a sharper notion of feature extrapolation (source: [[mila_2024_spatial_proxies]]).

## Use in Diagnostics

Milà et al. used the percentage of the prediction area falling outside the AOA as a key diagnostic for [[spatial_proxies_random_forest]] (source: [[mila_2024_spatial_proxies]]):

- For spatial-model transfer with proxies: typically 100% of the extrapolation area falls outside the AOA → proxy values in the new area lie completely outside training-data ranges
- For clustered-sample interpolation with proxies: adding proxies pushes more of the prediction area outside the AOA
- For regular/random samples without proxies: feature extrapolation stays low even with full predictor sets

## Why it Matters

- Justifies why proxy variables produce useless predictions in new geographic regions: their range is bounded by the training-sample bounding box.
- Provides a non-statistical, predictor-space-based way to report uncertainty maps — complementary to deep-ensemble [[transfer_learning_remote_sensing]] epistemic uncertainty.
- Lets practitioners communicate map reliability spatially rather than as a single accuracy number.

## Software
Implemented in the R package `CAST` (Meyer et al.) alongside kNNDM CV and other prediction-oriented validation tools (source: [[mila_2024_spatial_proxies]]).

## Related concepts
- [[spatial_proxies_random_forest]]
- [[transfer_learning_remote_sensing]]
- [[sampling_bias_remote_sensing]]
