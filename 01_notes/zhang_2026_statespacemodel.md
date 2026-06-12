---
title: TSSMamba — A temporal-spectral-spatial state space model for multi-temporal remote sensing cloud removal
authors:
  - Chengyao Zhang
  - Fengyan Wang
  - Xuqing Zhang
  - Mingchang Wang
  - Feng Chen
  - Xiang Wu
  - Weitong Ma
year: 2026
tags:
  - deep-learning
  - remote-sensing
keywords:
  - cloud removal
  - state space models
  - Mamba
  - multi-temporal remote sensing
  - feature fusion
status: read
---

1. **Title and authors of the Paper:**
TSSMamba: A temporal–spectral–spatial state space model for multi-temporal remote sensing cloud removal. Zhang, Wang, Zhang, Wang, Chen, Wu, Ma (2026), International Journal of Applied Earth Observation and Geoinformation.

2. **Quick Overview:**
- **Why is it relevant?** Multi-temporal cloud removal methods built on CNNs/Transformers either have limited receptive fields or quadratic attention cost, and typically fuse temporal, spectral, and spatial information shallowly via concatenation.
- **What was done?** The authors propose TSSMamba, a dual-branch state space model (Mamba-based) that separately models temporal-spectral and temporal-spatial dependencies across three cloud-contaminated Sentinel-2 images, then fuses them via a dedicated cross-dimensional fusion block.
- **What is the main outcome?** TSSMamba outperforms five SOTA cloud removal methods (DRCRNet, CR-TS-Net, PMAA, SIF-GAN, MSC-GAN) on all four metrics (PSNR, SSIM, CC, SAM) across three benchmark datasets, while using fewer than 1M parameters.

3. **Main Goal and Fundamental Concept:**
- Reconstruct cloud-free surface reflectance from a short sequence of cloud-contaminated multi-temporal optical images (no SAR or cloud-free reference required).
- Core idea: jointly and explicitly model temporal, spectral, and spatial dependencies using structured **State Space Models (SSMs / Mamba)**, which offer linear-complexity long-range sequence modelling (vs. quadratic-cost Transformer self-attention).

4. **Technical Approach:**
- Input: three cloud-contaminated images from different acquisition dates, stacked along the temporal axis.
- A 3D-CNN residual encoder extracts a joint feature representation, preserving per-timestep identity while capturing cross-temporal cloud dynamics.
- Two parallel branches process the features:
  - **SATM (Spectrally-Aware Temporal Modeling)**: cross-spectral stacking + a parameter-free Spectral Fusion Operator (per-channel max across the three timestamps) + S-SSB (spectral state-space block) → spectrally refined features.
  - **SPTM (Spatially-Aware Temporal Modeling)**: row/column cross-stacking of the three timestep feature maps + H-SSB/V-SSB (directional four-way scanning state-space blocks) + Orthogonal Multi-Directional Spatial Operator (directional max pooling) → spatial-temporal features.
- A **Temporal-Spectral-Spatial Fusion (TSSF)** block gates and fuses the spectral and spatial branch outputs (via VSSM + S-SSB paths + 2D conv) into a unified representation.
- A lightweight 3-layer CNN decoder reconstructs the cloud-free image.
- Trained end-to-end with L1 loss, Adam, 200 epochs, batch size 1.

5. **Distinctive Features:**
- First application (per the authors) of structured SSMs (Mamba) to multi-temporal cloud removal, exploiting linear-complexity sequence modelling instead of CNN local receptive fields or Transformer quadratic attention.
- Dual-branch design that explicitly separates and then re-fuses temporal-spectral vs. temporal-spatial dependencies, rather than naive channel concatenation.
- Tailored directional ("four-directional") scanning schemes (H-SSB/V-SSB) that align same-location features across timestamps during state propagation — designed to preserve anisotropic structures (roads, ridgelines, elongated land-cover patterns).
- Extremely lightweight (<1M parameters), positioned as suitable for onboard/edge deployment.

6. **Experimental Setup and Results:**
- Three public Sentinel-2 multi-temporal cloud removal datasets: STGAN Dataset (3,130 sequences, 4 bands, 256×256), Sen2_MTC (~50 tiles × 70 sequences, 4 bands), SEN12MS-CR-TS (53 ROIs, 13 bands, 30 observations/year — North America subset used).
- Compared against DRCRNet, CR-TS-Net, PMAA, SIF-GAN, MSC-GAN.
- Results (TSSMamba vs. best competitor):
  - STGAN: PSNR 27.81 dB (vs. 27.25 CR-TS-Net), SSIM 0.8357, CC 0.7989, SAM 2.905°.
  - Sen2_MTC: PSNR 30.16 dB, SSIM 0.8682, CC 0.9227, SAM 5.658° — best across all four metrics.
  - SEN12MS-CR-TS (13-band): PSNR 30.90 dB, SSIM 0.9282, CC 0.9526, SAM 4.984° — best across all four metrics on the most spectrally diverse dataset.
- Ablations confirm each module (SATM, SPTM, TSSF, directional scanning) contributes incrementally to performance.
- Additional analyses: performance degrades gracefully under higher cloud cover; performance improves with more temporal inputs (tested on SEN12MS-CR-TS with its richer sequences).

7. **Advantages and Limitations:**
- **Advantages:** strong accuracy across diverse datasets and cloud conditions; very low parameter count (<1M) and computational cost; no reliance on SAR data or a cloud-free reference image; modular design extensible to more revisits or additional sensor channels (e.g., SAR-optical fusion).
- **Limitations:** evaluated only with three input timestamps for STGAN/Sen2_MTC (fixed temporal window); relies on availability of at least partially cloud-free information somewhere in the short multi-temporal sequence — persistent, region-wide cloud cover across all inputs is not addressed; no validation specific to forest/vegetation downstream tasks (e.g., does reconstructed imagery preserve phenological signal needed for tree species/forest type classification — relevant to [[transformer_sits]] pipelines).

8. **Conclusion:**
TSSMamba demonstrates that structured state space models (Mamba) can be effectively adapted to multi-temporal cloud removal by explicitly disentangling and then fusing temporal-spectral and temporal-spatial dependencies via a dual-branch architecture and dedicated directional scanning. It achieves SOTA accuracy on three Sentinel-2 cloud removal benchmarks with a sub-1M-parameter model, offering a lightweight alternative to CNN/Transformer/GAN-based cloud removal pipelines — relevant as a potential preprocessing step for gap-filling Sentinel-2 SITS before time-series-based forest mapping (cf. [[cloud_detection]], [[transformers_time_series]]).

## Related pages
- [[cloud_detection]]
- [[transformers_time_series]]
- [[transformer_sits]]
