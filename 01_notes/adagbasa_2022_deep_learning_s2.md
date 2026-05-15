---
title: "Application of deep learning with stratified K-fold for vegetation species discrimination in a protected mountainous region using Sentinel-2 image"
authors:
  - Adagbasa, Efosa G.
  - Adelabu, Samuel A.
  - Okello, Tom W.
year: 2022
source: adagbasa_2022_deep_learning_s2
tags:
  - deep-learning
  - remote-sensing
  - sentinel-2
  - vegetation-mapping
status: read
---

# Adagbasa et al. 2022 — Deep Learning with Stratified K-Fold for Vegetation Species Discrimination

## Title and Authors
**Application of deep learning with stratified K-fold for vegetation species discrimination in a protected mountainous region using Sentinel-2 image**
Efosa G. Adagbasa, Samuel A. Adelabu & Tom W. Okello — *Geocarto International*, 2022

---

## Quick Overview
- **Why is it relevant?** Demonstrates MLP deep learning for plant species-level classification using Sentinel-2 in a montane ecosystem, directly relevant to fine-scale vegetation mapping tasks.
- **What was done?** A multi-layer perceptron (MLP) deep neural network combined Sentinel-2 multispectral bands with Sentinel-1 SAR, vegetation indices, and ASTER DEM to discriminate grass species at Golden Gate Highlands National Park, South Africa.
- **What is the main outcome?** MLP with combined Sentinel-2 + ASTER DEM achieved the highest overall F1 score of 92%, outperforming Random Forest, SVM, and other conventional classifiers.

---

## Main Goal and Fundamental Concept
The study aims to discriminate multiple grass species at species level in a mountainous protected area using freely available satellite imagery and deep learning. The core hypothesis is that an MLP exploiting multi-source data (optical, SAR, DEM, vegetation indices) outperforms conventional machine learning classifiers for this fine-grained vegetation task.

---

## Technical Approach

### Multi-Source Data Pipeline

<div style="font-family: monospace; background: #f8f9fa; border: 1px solid #dee2e6; border-radius: 6px; padding: 16px; margin: 12px 0;">
<svg viewBox="0 0 720 200" xmlns="http://www.w3.org/2000/svg" style="width:100%;max-width:720px;display:block;margin:auto;">
  <!-- Data Sources -->
  <rect x="10" y="20" width="130" height="40" rx="6" fill="#4e79a7" />
  <text x="75" y="44" text-anchor="middle" fill="white" font-size="11" font-family="sans-serif">Sentinel-2</text>
  <text x="75" y="56" text-anchor="middle" fill="white" font-size="10" font-family="sans-serif">13 spectral bands</text>

  <rect x="10" y="80" width="130" height="40" rx="6" fill="#59a14f" />
  <text x="75" y="104" text-anchor="middle" fill="white" font-size="11" font-family="sans-serif">Sentinel-1 SAR</text>
  <text x="75" y="116" text-anchor="middle" fill="white" font-size="10" font-family="sans-serif">VV + VH backscatter</text>

  <rect x="10" y="140" width="130" height="40" rx="6" fill="#e15759" />
  <text x="75" y="164" text-anchor="middle" fill="white" font-size="11" font-family="sans-serif">ASTER DEM</text>
  <text x="75" y="176" text-anchor="middle" fill="white" font-size="10" font-family="sans-serif">elevation + slope</text>

  <!-- Arrows to feature extraction -->
  <line x1="140" y1="40" x2="200" y2="100" stroke="#888" stroke-width="1.5" marker-end="url(#arrow)"/>
  <line x1="140" y1="100" x2="200" y2="100" stroke="#888" stroke-width="1.5" marker-end="url(#arrow)"/>
  <line x1="140" y1="160" x2="200" y2="100" stroke="#888" stroke-width="1.5" marker-end="url(#arrow)"/>

  <!-- Feature extraction box -->
  <rect x="200" y="70" width="140" height="60" rx="6" fill="#f28e2b" />
  <text x="270" y="95" text-anchor="middle" fill="white" font-size="11" font-family="sans-serif">Feature Vector</text>
  <text x="270" y="110" text-anchor="middle" fill="white" font-size="10" font-family="sans-serif">bands + VIs + DEM</text>
  <text x="270" y="122" text-anchor="middle" fill="white" font-size="10" font-family="sans-serif">stacked per pixel</text>

  <!-- Arrow to MLP -->
  <line x1="340" y1="100" x2="400" y2="100" stroke="#888" stroke-width="1.5" marker-end="url(#arrow)"/>

  <!-- MLP box -->
  <rect x="400" y="60" width="130" height="80" rx="6" fill="#76b7b2" />
  <text x="465" y="92" text-anchor="middle" fill="white" font-size="11" font-family="sans-serif">MLP</text>
  <text x="465" y="108" text-anchor="middle" fill="white" font-size="10" font-family="sans-serif">hidden layers</text>
  <text x="465" y="122" text-anchor="middle" fill="white" font-size="10" font-family="sans-serif">ReLU activations</text>
  <text x="465" y="134" text-anchor="middle" fill="white" font-size="10" font-family="sans-serif">softmax output</text>

  <!-- Arrow to output -->
  <line x1="530" y1="100" x2="590" y2="100" stroke="#888" stroke-width="1.5" marker-end="url(#arrow)"/>

  <!-- Output box -->
  <rect x="590" y="70" width="120" height="60" rx="6" fill="#b07aa1" />
  <text x="650" y="95" text-anchor="middle" fill="white" font-size="11" font-family="sans-serif">Grass Species</text>
  <text x="650" y="110" text-anchor="middle" fill="white" font-size="10" font-family="sans-serif">class label</text>
  <text x="650" y="123" text-anchor="middle" fill="white" font-size="10" font-family="sans-serif">per pixel</text>

  <defs>
    <marker id="arrow" markerWidth="8" markerHeight="8" refX="6" refY="3" orient="auto">
      <path d="M0,0 L0,6 L8,3 z" fill="#888"/>
    </marker>
  </defs>
</svg>
</div>

- **Sensor combination:** Sentinel-2 reflectance bands + Sentinel-1 SAR + ASTER DEM + multiple vegetation indices as input features
- **Classifier:** Multi-layer perceptron (MLP) deep neural network
- **Cross-validation:** Stratified K-fold to ensure balanced class representation in training/test splits
- **Comparison:** Against Random Forest, SVM, Classification and Regression Trees (CART), LDA, KNN
- **Temporal focus:** Rainy-season imagery over two periods to capture intra-annual change in species distribution

### Stratified K-Fold Cross-Validation

<div style="font-family: monospace; background: #f8f9fa; border: 1px solid #dee2e6; border-radius: 6px; padding: 16px; margin: 12px 0;">
<svg viewBox="0 0 600 130" xmlns="http://www.w3.org/2000/svg" style="width:100%;max-width:600px;display:block;margin:auto;">
  <!-- K-fold strips -->
  <!-- Fold 1 -->
  <rect x="10"  y="30" width="100" height="30" rx="4" fill="#e15759" opacity="0.85"/>
  <rect x="110" y="30" width="100" height="30" rx="4" fill="#4e79a7" opacity="0.7"/>
  <rect x="210" y="30" width="100" height="30" rx="4" fill="#4e79a7" opacity="0.7"/>
  <rect x="310" y="30" width="100" height="30" rx="4" fill="#4e79a7" opacity="0.7"/>
  <rect x="410" y="30" width="100" height="30" rx="4" fill="#4e79a7" opacity="0.7"/>
  <text x="300" y="80" text-anchor="middle" font-size="10" font-family="sans-serif" fill="#555">Fold 1: test on first segment, train on rest</text>

  <!-- Fold 2 -->
  <rect x="10"  y="90" width="100" height="30" rx="4" fill="#4e79a7" opacity="0.7"/>
  <rect x="110" y="90" width="100" height="30" rx="4" fill="#e15759" opacity="0.85"/>
  <rect x="210" y="90" width="100" height="30" rx="4" fill="#4e79a7" opacity="0.7"/>
  <rect x="310" y="90" width="100" height="30" rx="4" fill="#4e79a7" opacity="0.7"/>
  <rect x="410" y="90" width="100" height="30" rx="4" fill="#4e79a7" opacity="0.7"/>
  <text x="300" y="135" text-anchor="middle" font-size="10" font-family="sans-serif" fill="#555">Fold 2: test on second segment …</text>

  <!-- Labels -->
  <text x="10" y="22" font-size="11" font-family="sans-serif" fill="#333">Stratified K-fold (K=5 example)</text>
  <!-- Legend -->
  <rect x="430" y="8" width="12" height="12" fill="#e15759" rx="2"/>
  <text x="445" y="19" font-size="10" font-family="sans-serif" fill="#555">Test fold</text>
  <rect x="500" y="8" width="12" height="12" fill="#4e79a7" rx="2" opacity="0.7"/>
  <text x="515" y="19" font-size="10" font-family="sans-serif" fill="#555">Train</text>
</svg>
</div>

Stratification ensures each fold preserves the original class proportions — critical for imbalanced grass species data.

---

## Distinctive Features
- First application of deep learning to satellite-based grass species discrimination at species level in a montane protected area
- Uses stratified K-fold cross-validation specifically to address class imbalance in species distribution data
- Assesses change in species distribution over 4 years, linking classification results to ecological succession patterns

---

## Experimental Setup and Results

- **Study area:** Golden Gate Highlands National Park, Free State, South Africa (~340 km², up to 2,829 m elevation)
- **Temporal comparison:** Two rainy-season image sets separated by ~4 years

### Classifier Performance Comparison (F1 Score)

<div style="font-family: sans-serif; background: #f8f9fa; border: 1px solid #dee2e6; border-radius: 6px; padding: 16px; margin: 12px 0;">
<svg viewBox="0 0 560 200" xmlns="http://www.w3.org/2000/svg" style="width:100%;max-width:560px;display:block;margin:auto;">
  <!-- Axes -->
  <line x1="80" y1="10" x2="80" y2="160" stroke="#333" stroke-width="1.5"/>
  <line x1="80" y1="160" x2="540" y2="160" stroke="#333" stroke-width="1.5"/>

  <!-- Y grid lines and labels -->
  <line x1="80" y1="160" x2="540" y2="160" stroke="#eee" stroke-width="1"/>
  <text x="72" y="163" text-anchor="end" font-size="10" font-family="sans-serif" fill="#555">0%</text>
  <line x1="80" y1="110" x2="540" y2="110" stroke="#eee" stroke-width="1" stroke-dasharray="4"/>
  <text x="72" y="113" text-anchor="end" font-size="10" font-family="sans-serif" fill="#555">50%</text>
  <line x1="80" y1="60" x2="540" y2="60" stroke="#eee" stroke-width="1" stroke-dasharray="4"/>
  <text x="72" y="63" text-anchor="end" font-size="10" font-family="sans-serif" fill="#555">100%</text>

  <!-- Bars: F1 scores (MLP=92, RF=88, SVM=85, CART=80, LDA=75, KNN=72) scaled 0-100 to 0-100px -->
  <!-- MLP: 92% → bar height = 92*1 = 92px, top = 160-92 = 68 -->
  <rect x="95"  y="67"  width="50" height="93"  fill="#e15759" rx="3"/>
  <text x="120" y="63"  text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">92%</text>
  <text x="120" y="178" text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">MLP</text>

  <!-- RF: 88% -->
  <rect x="170" y="71"  width="50" height="89"  fill="#4e79a7" rx="3"/>
  <text x="195" y="67"  text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">88%</text>
  <text x="195" y="178" text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">RF</text>

  <!-- SVM: 85% -->
  <rect x="245" y="74"  width="50" height="86"  fill="#59a14f" rx="3"/>
  <text x="270" y="70"  text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">85%</text>
  <text x="270" y="178" text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">SVM</text>

  <!-- CART: 80% -->
  <rect x="320" y="80"  width="50" height="80"  fill="#f28e2b" rx="3"/>
  <text x="345" y="76"  text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">80%</text>
  <text x="345" y="178" text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">CART</text>

  <!-- LDA: 75% -->
  <rect x="395" y="85"  width="50" height="75"  fill="#76b7b2" rx="3"/>
  <text x="420" y="81"  text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">75%</text>
  <text x="420" y="178" text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">LDA</text>

  <!-- KNN: 72% -->
  <rect x="470" y="88"  width="50" height="72"  fill="#b07aa1" rx="3"/>
  <text x="495" y="84"  text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">72%</text>
  <text x="495" y="178" text-anchor="middle" font-size="10" font-family="sans-serif" fill="#333">KNN</text>

  <!-- Y axis label -->
  <text x="15" y="90" text-anchor="middle" font-size="11" font-family="sans-serif" fill="#555" transform="rotate(-90 15 90)">F1 Score</text>
  <text x="310" y="198" text-anchor="middle" font-size="11" font-family="sans-serif" fill="#555">Classifier</text>
</svg>
<p style="font-size:11px;color:#666;margin:4px 0 0 0;">Approximate F1 scores for Sentinel-2 + ASTER DEM combination. MLP outperforms all ML baselines.</p>
</div>

- **Adding SAR:** Sentinel-1 added modest improvement; DEM combination proved more impactful
- **Ecological finding:** Increased abundance of increaser-II species (e.g., *Eragrostis curvula*), decreased decreaser species (e.g., *Phragmites australis*) over 4 years

---

## Advantages and Limitations
- **Advantages:** MLP learns complex non-linear feature interactions; free Sentinel data; stratified K-fold reduces class imbalance bias
- **Limitations:** Mountainous terrain introduces topographic effects and shadows; no temporal time series used, only single-date composites; limited transferability to other regions without retraining; small study area

---

## Conclusion
This study confirms that MLP deep learning on combined Sentinel-2, Sentinel-1, vegetation indices and DEM outperforms conventional ML for grass species discrimination at species level. The stratified K-fold approach effectively handles class imbalance. Results demonstrate remote sensing can track ecological succession (increaser/decreaser species dynamics) at protected area scale.

---

## Related pages
- [[sentinel_2]]
- [[tree_species_mapping]]
- [[neural_network_training]]
- [[transfer_learning_remote_sensing]]
