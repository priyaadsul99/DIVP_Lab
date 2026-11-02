# Lab 2 – Histogram Processing and Contrast Enhancement

## Overview
This experiment explores histogram-based image enhancement. It compares histogram matching against a reference distribution and demonstrates global histogram equalization and CLAHE on a synthetic grayscale X-ray-like image.

## Notebook
- [Experiment_02.ipynb](./Experiment_02.ipynb)

## Concepts and Operations

### Problem 1: Histogram Matching
The notebook:
1. Generates a low-contrast source image using a normal distribution.
2. Generates a reference image with dark and bright intensity groups.
3. Calculates normalized cumulative distribution functions (CDFs).
4. Builds a lookup table that maps each source intensity to the reference intensity with the closest CDF value.
5. Also maps the source image to a synthetic Gaussian target distribution (the “moody” target).

### Problem 2: CLAHE
A synthetic X-ray-like image is created with a dark background, a bright region, and a faint noisy central region. The notebook compares:
- Global histogram equalization
- CLAHE with a clip limit of 2.0 and an 8×8 tile grid
- CLAHE with a high clip limit of 20.0
- CLAHE with a 32×32 tile grid

The examples illustrate how CLAHE parameters affect local contrast and noise amplification.

### Entropy
The notebook calculates image entropy from the intensity histogram:

[
H=-\sum_i p_i\log_2(p_i)
]

Entropy is used as a quantitative description of the intensity distribution; it should not be interpreted as a standalone measure of visual quality.

## Libraries
- OpenCV (`cv2`) – histogram equalization, CLAHE, and histogram calculation.
- NumPy – synthetic image generation and array operations.
- Matplotlib – display images, histograms, and CDF plots.
- SciPy (`scipy.stats`) – Gaussian probability density for the analytical target.

## How to Run
1. Open `Experiment_02.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.
2. Install the dependencies if needed:

   ```bash
   pip install opencv-python numpy matplotlib scipy
   ```

3. Run all notebook cells.

## Expected Output
The notebook displays:
- Source, reference, reference-matched, and Gaussian-target-matched images.
- Their intensity histograms and CDF curves.
- A comparison of the synthetic X-ray image after global equalization and different CLAHE settings, with entropy values.

## Notes
- The images are generated inside the notebook; no external image file is required.
- Random sampling is used to generate the synthetic images, so the exact results can vary between runs.
