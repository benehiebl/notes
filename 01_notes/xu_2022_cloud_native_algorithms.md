---
title: "Analyzing large-scale Data Cubes with user-defined algorithms: A cloud-native approach"
authors:
  - Xu, Chen
  - Du, Xiaoping
  - Jian, Hongdeng
  - Dong, Yi
  - Qin, Wei
  - Mu, Haowei
year: 2022
source: xu_2022_cloud_native_algorithms
tags:
  - remote-sensing
  - machine-learning
status: read
---

# Xu et al. 2022 — Cloud-Native Approach for Large-Scale RS Analysis with User-Defined Algorithms

## Title and Authors
**Analyzing large-scale Data Cubes with user-defined algorithms: A cloud-native approach**
Chen Xu, Xiaoping Du, Hongdeng Jian et al. — *International Journal of Applied Earth Observation and Geoinformation*, 2022

## Quick Overview
- **Why is it relevant?** Addresses the practical challenge of deploying custom (non-GEE-native) algorithms — including deep learning models — on large-scale satellite data cubes without rewriting algorithms in platform-specific APIs.
- **What was done?** Developed a cloud-native processing framework using containerisation (Docker) + Data Cube Resilient Distributed Dataset (DRDD) to deploy user-defined algorithms at continental scale on the Science Earth Platform.
- **What is the main outcome?** Framework successfully executes continental-scale land cover mapping at 10 m resolution using both deep learning and machine learning algorithms, demonstrating feasibility of portable user-defined algorithm deployment on RS big data.

## Main Goal and Fundamental Concept
Remote sensing big data platforms (Google Earth Engine, BDAP) require algorithms to be implemented in their specific APIs, making it difficult to deploy custom legacy algorithms (e.g., PyTorch deep learning models, GDAL-based pipelines). The study proposes a cloud-native approach using Docker containerisation and Data Cube standards to make any user-defined algorithm deployable at scale.

## Technical Approach
Key components:
- **Processing model:** Workflow decomposed into independent steps following Data Cube structure (spatially homogeneous tiles + time dimension)
- **Composite Container:** Docker container encapsulating user-defined algorithm + its execution environment (any language/library)
- **DRDD (Data Cube Resilient Distributed Dataset):** Extension of Spark RDD concept for Data Cube structure; enables MapReduce-style parallelisation
- **Platform:** Science Earth Platform (Chinese national RS platform)
- **Validation:** Two continental-scale land cover mapping experiments at 10 m resolution using DL (CNN) and ML (Random Forest)

## Distinctive Features
- Bridges the gap between user-defined algorithms and cloud-scale RS platforms without requiring platform-specific rewrites
- Generic: any algorithm in any programming language can be containerised and deployed
- Compatible with open Data Cube standards (Digital Earth Australia-style organisation)
- Compared against Google Earth Engine and Microsoft Planetary Computer for conceptual positioning

## Experimental Setup and Results
- **Experiment 1:** Continental-scale land cover mapping via deep learning CNN — successfully executed
- **Experiment 2:** Same mapping task with machine learning (Random Forest) via GDAL-based pipeline — successfully executed
- **Resolution:** Up to 10 m continental-scale; good scalability performance
- **Comparison:** Outperforms HTCondor-based BDAP approach for complex multi-step workflows

## Advantages and Limitations
- **Advantages:** Platform-agnostic; supports arbitrary algorithms; reduces vendor lock-in; reproduces complex multi-step pipelines
- **Limitations:** Container orchestration overhead; data movement between containers; less mature ecosystem than GEE; China-specific platform access

## Conclusion
Cloud-native containerisation (Docker + DRDD) enables deployment of arbitrary user-defined algorithms on RS Data Cubes at continental scale, overcoming the primary limitation of current cloud RS platforms. This approach is particularly relevant for deep learning workflows that require PyTorch/TensorFlow environments unavailable in GEE.

## Related pages
- [[sentinel_2]]
- [[landsat]]
- [[transfer_learning_remote_sensing]]
