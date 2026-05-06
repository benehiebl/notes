---
title: "Cloud and cloud shadow detection for optical satellite imagery: Features, algorithms, validation, and prospects"
authors:
  - Li, Zhiwei
  - Shen, Huanfeng
  - Weng, Qihao
  - Zhang, Yuzhuo
  - Dou, Peng
  - Zhang, Liangpei
year: 2022
source: li_2022_cloud_detection
tags:
  - remote-sensing
  - machine-learning
status: read
---

# Li et al. 2022 — Cloud and Cloud Shadow Detection for Optical Satellite Imagery: A Review

## Title and Authors
**Cloud and cloud shadow detection for optical satellite imagery: Features, algorithms, validation, and prospects**
Zhiwei Li, Huanfeng Shen, Qihao Weng et al. — *ISPRS Journal of Photogrammetry and Remote Sensing*, 2022

## Quick Overview
- **Why is it relevant?** Cloud contamination is a fundamental barrier to optical time series analysis; this review provides a systematic overview of methods, trends, and tools for cloud/shadow detection, essential for satellite time series preprocessing.
- **What was done?** Systematic review of 504 cloud and cloud shadow detection papers (1985–2021) covering features, algorithms, and validation approaches, plus an open-source resource catalogue (OpenSICDR).
- **What is the main outcome?** Deep learning methods are the emerging dominant approach, combining spectral-spatial-temporal features; MODIS and Landsat are the most studied sensors; cloud detection remains challenging for thin clouds and bright surfaces.

## Main Goal and Fundamental Concept
Cloud and cloud shadow (CCS) detection is a critical preprocessing step enabling time series analysis and data mining of optical satellite imagery. With global cloud fraction averaging 66%, unmasked clouds introduce systematic errors in downstream products (land cover, LAI, phenology). The review characterises the state of the art across three dimensions: features used, detection algorithms, and validation methods.

## Technical Approach
**Feature taxonomy:**
- Spectral, spectral-spatial, spectral-temporal, spectral-spatial-temporal, multi-source features
**Algorithm taxonomy:**
- Physical-rule based, temporal-change based, variational-model based, machine-learning based
**Validation:**
- Manual masks, cloud mask products, LiDAR/radar collocated data, ground-based cameras

Survey scope: 504 papers from Scopus (1985–2021), filtered for journal articles

## Distinctive Features
- First comprehensive review covering features, algorithms AND validation simultaneously
- Meta-analysis of temporal trends in publications and institutional contributions
- Launch of OpenSICDR: open-source tools and datasets for cloud/shadow detection
- Identifies top satellite platforms (MODIS, Landsat, Sentinel) and their specific challenges

## Key Findings
- Publication rate has grown consistently since 2010; deep learning accelerated after 2017
- MODIS, Landsat, AVHRR = most studied; Sentinel-2 growing rapidly
- Deep learning (CNN, LSTM) outperforms rule-based and traditional ML for complex cloud types
- Thin cloud detection and bright surface (snow, sand) discrimination remain challenging
- Temporal context (multi-temporal features) significantly improves cloud/shadow detection
- Fusion of physical models with deep learning is the most promising future direction

## Advantages and Limitations
- **Advantages:** Comprehensive scope; open resource catalogue; practical method selection guidance; identifies future directions
- **Limitations:** Literature biased toward English publications and sensor-specific studies; validation standards are inconsistent across studies

## Conclusion
Cloud and cloud shadow detection is an essential but still-evolving preprocessing step for optical time series. Deep learning combined with multi-temporal features offers the best current performance. The combination of physical radiative transfer knowledge with learned representations is the most promising direction. OpenSICDR provides a community resource for benchmarking future methods.

## Related pages
- [[landsat]]
- [[sentinel_2]]
- [[phenology]]
- [[vegetation_greenness_trends]]
