---
title: "TorchGeo: Deep Learning With Geospatial Data"
authors:
  - Adam J. Stewart
  - Caleb Robinson
  - Isaac A. Corley
  - Anthony Ortiz
  - Juan M. Lavista Ferres
  - Arindam Banerjee
year: 2022
tags:
  - deep-learning
  - remote-sensing
keywords:
  - TorchGeo
  - PyTorch
  - geospatial data loaders
  - GeoDataset
  - samplers
  - reprojection and resampling
  - benchmark datasets
  - ImageNet pretraining
  - multispectral transforms
  - software library
status: unread
---

## Title and Authors of the Paper

"TorchGeo: Deep Learning With Geospatial Data" — Adam J. Stewart, Caleb Robinson, Isaac A. Corley, Anthony Ortiz, Juan M. Lavista Ferres, Arindam Banerjee (2022). arXiv:2111.08872v4 [cs.CV]. University of Illinois at Urbana-Champaign / Microsoft AI for Good Research Lab / University of Texas at San Antonio.

## Quick Overview

- **Why is it relevant?** Deep learning frameworks (torchvision, PIL) are built for fixed 3-channel RGB imagery and standard fixed-length datasets, which does not match the heterogeneous, multispectral, differently-projected, differently-resolved nature of remote sensing data — creating a real engineering barrier to applying deep learning to EO data.
- **What was done?** The authors built and released TorchGeo, an open-source Python/PyTorch library providing geospatial-aware datasets, on-the-fly reprojection/resampling/cropping, samplers for spatiotemporal (rather than integer-indexed) data, multispectral-compatible transforms, pretrained multispectral models, and training recipes, then benchmarked it on 8 datasets.
- **What is the main outcome?** TorchGeo achieves close to state-of-the-art results on all benchmarked datasets with a simple, reproducible training setup, demonstrates that GridGeoSampler is markedly faster than random samplers, and shows ImageNet pretraining significantly improves out-of-domain (spatial generalization) performance even though it does not help in-domain performance.

## Main Goal and Fundamental Concept

- Core problem: geospatial raster/vector data layers a researcher wants to combine (e.g. Landsat imagery + a land-cover label raster) are rarely **pixel-aligned** — they differ in coordinate reference system (CRS), spatial resolution, and spatial/temporal extent — so building a training dataset normally requires manual, non-scalable GIS preprocessing (reprojecting, cropping, resampling) before any deep learning pipeline can even start.
- TorchGeo's fundamental idea: index geospatial datasets by **spatiotemporal coordinates** (bounding box + optional timestamp) rather than by integer index, and perform reprojection/resampling/cropping **on the fly** at data-loading time, so heterogeneous layers can be composed and sampled without pre-processing or GIS tooling knowledge.
- Datasets can be composed algebraically: `UnionDataset` (sample from the union of two layers' spatial extent) and `IntersectionDataset` (sample only where both layers overlap) — e.g., combining Landsat 7 + 8 as a union, or Landsat + Cropland Data Layer (CDL) labels as an intersection.

## Technical Approach

TorchGeo is organized into five submodules:

- **Datasets**: `GeoDataset` subclasses (geospatial-metadata-aware, indexed by bounding box) for both *benchmark datasets* (fixed input+label pairs for a specific task, e.g. EuroSAT, RESISC45, So2Sat) and *generic datasets* representing raw geospatial layers (e.g. any collection of Landsat scenes, or the Cropland Data Layer) that can be sampled for any purpose, including non-imagery layers.
- **Samplers**: since geospatial datasets have no natural integer "length," three sampler types are implemented — `RandomGeoSampler` (uniform random fixed-size bounding boxes across the full extent), `RandomBatchGeoSampler` (batches of random boxes from a single scene at a time), and `GridGeoSampler` (regular grid pattern over scenes) — all standard PyTorch-DataLoader-compatible.
- **Transforms**: wrappers around the Kornia augmentation library extended to support arbitrary-channel (multispectral) imagery, unlike most existing augmentation libraries which assume 3-channel RGB.
- **Models**: wrappers around common architectures adapted for variable-channel multispectral inputs, plus pretrained weights for models using all Sentinel-2 bands (first library, per the authors, to offer pretrained multispectral-band models) and geospatial-specific architectures (e.g. Fully Convolutional Siamese Network for change detection).
- **Trainers**: PyTorch Lightning-based training recipes, including dataset-specific routines and general routines such as an implementation of BYOL self-supervised pretraining.
- On-the-fly alignment mechanics: given a query (spatiotemporal coordinates + destination CRS + target resolution), each `GeoDataset` returns reprojected, resampled, cropped data for that query — trading some data-loading compute for eliminating the need to duplicate/pre-align entire raster layers on disk.

## Distinctive Features

- Spatiotemporal-coordinate indexing (rather than integer indexing) is the central design choice that enables all downstream composability (union/intersection of layers, arbitrary samplers, multimodal fusion) without custom per-dataset glue code.
- First library (per the paper) to provide pretrained models that use all Sentinel-2 bands, directly enabling transfer learning for multispectral remote sensing tasks with limited labels.
- Provides a standardized catalog of 27 benchmark datasets (Table 1: classification, regression, semantic segmentation, object detection, instance segmentation, time series, change detection) plus 13 generic geospatial data layers (Table 2: imagery sources like Landsat/Sentinel/NAIP/DEMs, and label sources like Cropland Data Layer, GBIF, iNaturalist, Open Buildings) through one common interface.
- Publishes reproducible benchmark numbers (Table 3, mean ± std over 10 training seeds) directly tied to the library's own training recipes, intended so future methodological improvements can be compared against a known baseline without re-running expensive training from scratch.

## Experimental Setup and Results

- **Data loader speed benchmarks** (Landsat + CDL, 151 GB on disk): `GridGeoSampler` is markedly faster than `RandomGeoSampler`/`RandomBatchGeoSampler` at nearly all batch sizes (up to ~800–900 patches/sec vs ~100 patches/sec), attributed to GDAL's least-recently-used (LRU) cache being hit more often for sequential/grid access patterns; pre-processing and caching data ahead of time further increases sampling rate for all samplers, most dramatically for `GridGeoSampler`.
- **Benchmark dataset results** (8 datasets: RESISC45, So2Sat, LandCover.ai, Chesapeake Land Cover, ETCI 2021, EuroSAT, UC Merced, COWC Counting): TorchGeo's simple ResNet/U-Net + ImageNet-pretraining training recipes achieve results close to previously reported task-specific state-of-the-art (e.g. EuroSAT 99.20% vs 99.61% in-domain-pretrained; LandCover.ai within 0.75% mIoU of a more complex DeepLabv3+/Xception71/DPC baseline), despite using comparatively simple architectures (ResNet18/50, U-Net) rather than task-specialized ones.
- **ImageNet pretraining vs random initialization on spatial generalization**: using the Chesapeake Land Cover dataset's cross-state splits (train on Delaware, test on Maryland/New York/Pennsylvania/Virginia/West Virginia), ImageNet-pretrained models outperform randomly-initialized models on every out-of-domain state test split (by >6 mIoU points in most cases, up to +12 points in Virginia), while in-domain (Delaware) performance is statistically indistinguishable between the two initializations — a genuine spatial-generalization effect, not merely a data-efficiency effect.
- So2Sat (out-of-domain by design: validation/test cover urban areas absent from training) shows most models cannot meaningfully reduce out-of-domain validation loss, but ImageNet-pretrained models still show large accuracy gaps over randomly-initialized ones (+7% to +10%).

## Advantages and Limitations

**Advantages:**
- Directly solves a real, previously ad hoc engineering bottleneck (manual GIS pre-alignment of heterogeneous raster/vector layers) that likely affects most custom remote-sensing deep learning pipelines, including this wiki's own [[traceve_pretraining]], [[ae_training]], and [[ls_mapping]] pipelines and their shared [[sattstools]] preprocessing utilities.
- Open source, actively benchmarked, PyTorch-native — low adoption friction for existing PyTorch-based workflows.
- Reproducible benchmark numbers with explicit uncertainty (10-seed mean ± std) is a good scientific practice, rare in remote-sensing ML tooling papers.
- The ImageNet-pretraining-improves-spatial-generalization finding is a genuinely useful, non-obvious result (in-domain performance is unaffected, but out-of-domain/spatial-transfer performance benefits substantially) — directly relevant to any pipeline concerned with geographic transferability, not just accuracy.

**Limitations (critical read):**
- This is a software/systems paper, not a novel modeling contribution — the "results" are mostly demonstrations that a simpler, generic pipeline can approach (not exceed) prior task-specific state-of-the-art; several benchmark comparisons are against baselines the authors selected themselves rather than a systematic reproduction of the strongest possible prior method.
- The favorable data-loader speed results for `GridGeoSampler` are specific to sequential/cache-friendly access patterns; the paper is transparent that random samplers are far slower, which is a genuine trade-off practitioners must consider (most users are pointed toward `GridGeoSampler` for inference, but training often requires randomized sampling).
- Benchmarking was performed on a fixed hardware/software configuration (Azure VM, specific CPU/SSD) with a single fixed random seed for the data-loader speed experiments (only the dataset-benchmark results use 10 seeds) — throughput numbers may not generalize to other infrastructure.
- As of this paper (2022, v4 Sept 2022), the library and its dataset/model catalog were rapidly evolving; the specific benchmark numbers reported likely reflect an early library version and warrant a version-check against the wiki's other TorchGeo-adjacent codebases before treating them as current.
- The paper does not address annotation/label quality, class imbalance, or domain shift beyond the single geographic-generalization experiment (Chesapeake Land Cover) — broader claims about "spatial generalization" rest on one dataset.

## Conclusion

TorchGeo directly addresses the engineering gap between the abundance of freely available multispectral, multi-resolution, multi-projection satellite imagery and the RGB/fixed-length assumptions baked into standard deep learning tooling (PIL, torchvision). Its core contribution — spatiotemporal-coordinate-indexed `GeoDataset`s with on-the-fly reprojection/resampling and composable union/intersection semantics — removes the need for manual GIS pre-alignment before training. Benchmark results are competitive rather than state-of-the-art by design (the library favors simplicity/reproducibility over squeezing out maximum accuracy), but the demonstrated finding that ImageNet pretraining meaningfully improves spatial (cross-region) generalization, without helping in-domain accuracy, is a useful and specific result for any pipeline — including this wiki's own SITS pretraining and geospatial foundation model work — concerned with model transferability across geography.

## Related pages

- [[sattstools]]
- [[traceve_pretraining]]
- [[ae_training]]
- [[ls_mapping]]
- [[transfer_learning_remote_sensing]]
- [[geospatial_foundation_models]]
- [[manas_2021_seasonal_contrast]]
- [[sentinel_2]]
- [[sentinel_1_sar]]
