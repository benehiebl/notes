---
title: "Mapping forest in the Swiss Alps treeline ecotone with explainable deep learning"
authors:
  - Nguyen, Thiên-Anh
  - Kellenberger, Benjamin
  - Tuia, Devis
year: 2022
source: nguyen_2022_forest_mapping_explainable
tags:
  - deep-learning
  - remote-sensing
  - forest-ecology
status: read
---

# Nguyen et al. 2022 — Explainable Deep Learning for Forest Mapping at the Alpine Treeline

## Title and Authors
**Mapping forest in the Swiss Alps treeline ecotone with explainable deep learning**
Thiên-Anh Nguyen, Benjamin Kellenberger, Devis Tuia — *Remote Sensing of Environment*, 2022

## Quick Overview
- **Why is it relevant?** Demonstrates how to incorporate expert domain knowledge (forest definitions based on tree height + canopy density) directly into a CNN architecture, producing explainable forest maps and revealing annotator biases.
- **What was done?** Proposed a rule-informed CNN that explicitly predicts intermediate variables (tree height, canopy density) and combines them according to forest definition rules, applied to VHR aerial imagery at the Swiss Alps treeline ecotone.
- **What is the main outcome?** Rule-informed model achieves accuracy close to a black-box CNN while providing interpretable spatial explanations, and can reveal inconsistencies in manual forest annotation labels.

## Main Goal and Fundamental Concept
Standard deep learning forest mapping models learn a direct mapping from pixels to forest labels without encoding the forest definition criteria (e.g., tree height ≥ 5 m and canopy density ≥ 30%). This study proposes a model that explicitly quantifies intermediate semantic variables (tree height, canopy density), applies definition rules mechanistically, and includes a correction pathway for annotator inconsistencies — increasing trust and interpretability.

## Technical Approach
- **Architecture:** CNN with explicit intermediate outputs (tree height, canopy density) + rule combination module + correction pathway
- **Input data:** Very high resolution aerial imagery, Vaud and Valais Alps, Switzerland
- **Forest definitions:** Multiple definitions with different tree height and canopy density thresholds tested
- **Explainability:** Model produces per-pixel maps of intermediate variables (height, density) alongside forest type predictions
- **Validation:** Swiss National Forest Inventory measurements; comparison with standard black-box CNN

## Distinctive Features
- One of the first studies to explicitly encode forest definition rules as a differentiable computational graph within a deep learning model
- Correction pathway separates rule-derived predictions from annotator-label deviations, quantifying label heterogeneity
- Specifically designed for treeline ecotone where forest boundaries are diffuse, definition-sensitive, and ecologically complex
- Interpretability enables diagnosis of annotator biases in training labels

## Experimental Setup and Results
- **Performance:** Rule-informed model achieves accuracy close to black-box CNN on standard metrics
- **Explanation:** Provides spatially explicit tree height and canopy density maps used to justify each forest/non-forest prediction
- **Reveals annotation bias:** Correction pathway identifies areas where manual labels deviate from the stated forest definition
- **Treeline sensitivity:** Different forest definitions produce substantially different boundary locations at the treeline

## Advantages and Limitations
- **Advantages:** Interpretable; encodes domain knowledge; reveals label quality issues; useful for regulatory/management contexts requiring explainability
- **Limitations:** Requires prior knowledge of the forest definition; VHR aerial imagery not globally available; more complex training than standard CNN

## Conclusion
Explainable deep learning that encodes domain-specific forest definition rules can match black-box CNN accuracy while providing interpretable, decision-relevant explanations. This is particularly valuable at definition-sensitive locations (alpine treeline) and for building user trust. The correction pathway is a novel diagnostic tool for quantifying annotator inconsistency in training labels.

## Related pages
- [[transfer_learning_remote_sensing]]
- [[neural_network_training]]
- [[topographic_microclimate]]
- [[national_forest_inventory]]
- [[nguyen_2024_treeline_monitoring]]
- [[treeline_remote_sensing_monitoring]]
- [[treeline_ecotone_theory]]
