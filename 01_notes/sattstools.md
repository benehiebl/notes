---
title: "sattstools — Satellite Remote Sensing Time Series Preprocessing Library (code repository)"
authors:
  - Hiebl, Benedikt
year: 2025
source: sattstools
tags:
  - remote-sensing
  - deep-learning
  - machine-learning
status: read
---

# Title and Authors of the Codebase

**sattstools — Satellite Remote Sensing Time Series Preprocessing Library**
Benedikt Hiebl (University of Innsbruck / UIBK)
Repository: `00_literature/sattstools/` | `pip install git+https://git.uibk.ac.at/c7161037/sattstools`

---

## Quick Overview

- **Why is the code relevant in the context of the vault?** This library is the shared preprocessing backbone imported by all three TRACEVE training frameworks ([[traceve_pretraining]], [[ae_training]], [[ls_mapping]]) — every time series normalisation, outlier removal, smoothing, and data augmentation operation used in [[hiebl_2025_pretraining]] and [[hiebl_2026_alphaearth]] runs through sattstools.
- **What does it do?** Provides a unified Python package for satellite RS preprocessing (Sentinel-2/Landsat cloud masking, index calculation) and ML-ready time series processing (outlier detection, smoothing, normalisation, and data augmentation for PyTorch-based deep learning workflows).
- **What is the main outcome?** A pip-installable utility library that decouples the preprocessing pipeline from model training code, enabling consistent, reproducible data preparation across multiple experiments and publications.

---

## Main Goal and Fundamental Concept

Remote sensing time series for deep learning require several sequential preprocessing steps — cloud masking, outlier removal, smoothing, normalisation, and data augmentation — each of which must be consistent between training and inference. sattstools packages all these steps into a single importable library operating on xarray/dask arrays (for large-scale RS data cubes) and PyTorch tensors (for ML batch inputs), ensuring that the same transformations applied at training time can be serialised and replayed at inference time.

---

## Technical Approach

The library is organised into four modules:

### `rsutils.py` — Remote Sensing Preprocessing
Operates on `xr.DataArray` / `xr.Dataset`:
- **Cloud masking:** `mask_clouds()` with three backends:
  - `"scl"` — Sentinel-2 Sen2Cor Scene Classification Layer; masks nodata, saturated, dark, cloud shadow, unclassified, cloud medium/high, cirrus, snow by name
  - `"qa_pixel"` — Landsat Collection 2 QA_PIXEL bitfield decoding for cloud, shadow, cirrus, dilated cloud, snow
  - `"umask"` — generic binary mask
- **Baseline offset correction** — Sentinel-2 processing baseline 4.0 offset correction (DN shift)
- **DN to reflectance** scaling
- **Spectral index calculation** via `spyndex` integration (NDVI, EVI, NIRv, NDMI, kNDVI, etc.)

### `outlier.py` — Time Series Outlier Detection
Operates on `np.ndarray`; wrapped for `xr.DataArray` via `Outlier` class using `xr.apply_ufunc` / Dask `apply_along_axis`:
- **`zscore`** — rolling-window z-score with configurable window and threshold
- **`iqr`** — rolling inter-quartile range (Q1−factor×IQR, Q3+factor×IQR)
- **`iqr_optimized`** — vectorised IQR using numpy `_rolling_window` strides (faster for large arrays)
- **`iqr_smooth_detrend`** — IQR on residuals from Whittaker-smoothed or Savitzky-Golay trend (more robust to seasonal signals)
- **`iqr_polywindow_detrend`** — per-window polynomial detrending before IQR; applied via rolling `.apply()`
- **`iso_forest`** — Isolation Forest for anomaly detection (scikit-learn)
- Circular time series padding before detection to eliminate edge artefacts

### `smooth.py` — Time Series Smoothing
Operates on `np.ndarray`; wrapped for `xr.DataArray` via `Smooth` class (dask-parallelised):
- **Whittaker smoother** (`_whittaker_smooth`) — primary method; handles NaNs via weight masking; λ controls roughness penalty, d controls order; LU-factorisation cached with `@lru_cache` for repeated calls on same-length series; uses `whittaker-eilers` Rust-backed implementation
- **FFT smoothing** (`_fourier_smooth`) — retain first N harmonics; suitable for regular, gap-free series
- **RBF/Gaussian** (`_rbf_smooth`) — `scipy.ndimage.gaussian_filter1d`; fast but no NaN handling
- **Savitzky-Golay** (`_savgol_smooth`) — polynomial convolution filter

### `TSpreprocess.py` — ML Input Preprocessing (PyTorch)
Operates on `torch.Tensor` or `np.ndarray` of shape `[batch, vars, time]`:

**Normalisation/Standardisation classes** (fit `encode`/`decode` pattern):
| Class | Method |
|-------|--------|
| `TSStandardize` | z-score (mean/std); optional per-variable |
| `TSRobustStandardize` | robust z-score via quantile range (median/IQR); NaN-safe; fit/encode separated |
| `TSNormalize` | min-max to [0,1] or custom range |
| `TSPercNormalize` | percentile-based min-max (e.g., p=[0.02, 0.95]) |

All classes implement NaN-safe statistics (`_nanmean`, `_nanstd`, `_nanmedian_over_axes`, `_nanquantile_over_axes`) since satellite time series contain cloud-induced NaNs.

**Data augmentation functions:**
- `augment_optical_sparse(x)` — for raw sparse S2/Landsat SITS: Whittaker smooth → additive noise + TimeWarp (tsaug) → random cloud mask shift (`random_shift_bool_2d`)
- `augment_optical_smooth(x)` — for pre-smoothed SITS: global mean drift + TimeWarp
- `augment_climate_data(x)` — for CHELSA climate TS: circular padding → linear interpolation → tsaug Drift
- `augment_embd(x, scale, p)` — for AEF embedding vectors: per-band Bernoulli-masked Gaussian noise (feature-selective corruption)
- `prepare_mask(x)` — creates boolean attention mask from NaN positions and fills with sentinel value for Transformer key-padding

---

## Distinctive Features

- **Unified xarray + PyTorch interface:** the same processing logic operates on xarray DataArrays (via Dask parallelisation for large spatial data cubes) and PyTorch tensors (for mini-batch ML pipelines) — eliminating the need to re-implement the same operations twice
- **Modality-specific augmentation:** distinct augmentation strategies for sparse optical SITS, smoothed SITS, interpolated climate series, and dense embedding vectors — reflecting the different signal characteristics of each input type in [[hiebl_2026_alphaearth]]
- **NaN-safe PyTorch statistics:** implements `_nanmean`, `_nanstd`, `_nanmedian_over_axes`, `_nanquantile_over_axes` as custom functions since PyTorch lacks native NaN-aware reduction over arbitrary axes — critical for handling cloud gaps
- **Whittaker smoother with LRU cache:** the LU decomposition of the Whittaker operator is cached by `(N, λ, d)` key, making repeated calls on same-length time series ~10× faster
- **Serialisable transform state:** all normalisation classes store fit statistics (`mean`, `std`, `median`, `iqr`, `min`, `max`) as attributes, enabling `encode` to be called with fixed parameters computed at training time — essential for consistent inference without data leakage

---

## Experimental Setup and Results

sattstools is a utility library without standalone experiments. Its role in published results:
- **[[hiebl_2025_pretraining]]**: `TSPercNormalize` (p=[0.02, 0.95]) applied to Sentinel-2 bands before InceptionTime training; IQR outlier removal on raw S2 time series; Whittaker smoothing in MVP pretraining pipeline
- **[[hiebl_2026_alphaearth]]**: `TSRobustStandardize` (q=[0.02, 0.98]) for S2/CHELSA normalisation; `augment_optical_sparse`, `augment_climate_data`, `augment_embd` applied during training; `prepare_mask` used to generate Transformer key-padding masks
- **[[ls_mapping]]** (in progress): `TSRobustStandardize` (q=[0.1, 0.9]) for Landsat normalisation
- **[[traceve_pretraining]]**: `TSPercNormalize` in legacy code; `TSRobustStandardize` in newer experiments

---

## Advantages and Limitations

**Advantages:**
- Single source of truth for all preprocessing across the TRACEVE research line — changes in normalisation or augmentation propagate automatically to all downstream experiments
- Pip-installable with optional PyTorch dependency (`[torch]` extra) — usable without GPU for RS preprocessing tasks
- Dask integration enables out-of-core processing of large xarray data cubes without loading full time series into memory
- NaN-safe operations throughout make it directly applicable to gap-filled satellite data without prior imputation

**Limitations:**
- No versioned releases — depends on latest git commit; breaking changes may affect reproducibility across training runs
- `sarutils.py` is present but not fully documented in the README
- `tsaug` dependency for time series augmentation is a poorly maintained third-party library; warping operations may break with newer numpy/scipy versions
- No unit tests included — correctness of individual functions relies on the `test_nb/test_nb.ipynb` notebook rather than automated CI

---

## Conclusion

sattstools is the invisible foundation under all TRACEVE deep learning experiments. It standardises the full preprocessing pipeline — from raw satellite DN to ML-ready normalised PyTorch tensors — across multiple sensors (Sentinel-2, Landsat, CHELSA climate, AlphaEarth embeddings) and multiple downstream model architectures. The modality-specific augmentation functions and NaN-safe statistics are its most distinctive contributions to the vault's research context.

## Related pages

- [[traceve_pretraining]]
- [[ae_training]]
- [[ls_mapping]]
- [[hiebl_2025_pretraining]]
- [[hiebl_2026_alphaearth]]
- [[sentinel_2]]
- [[landsat]]
- [[cloud_detection]]
