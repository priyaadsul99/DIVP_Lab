# Lab 1 – Image Intensity Transformations

## Overview
This experiment demonstrates three point-processing techniques for changing the intensity of a grayscale image. The transformations are implemented with Python loops so that the underlying pixel operations are clear.

## Notebook
- [Experiment_01.ipynb](./Experiment_01.ipynb)

## Input
- `sunflower.jpg` – the grayscale image loaded by the notebook.
- The notebook expects this image in the same directory as the notebook. If you use a different image, update `image_path` in the code.

## Concepts and Operations

### 1. Image Negative
For an 8-bit grayscale pixel with intensity (r), the negative is:

[
s = 255-r
]

Dark pixels become bright and bright pixels become dark.

### 2. Power-Law (Gamma) Transformation
The notebook normalizes each pixel and applies a gamma exponent:

[
s = 255left(\frac{r}{255}\right)^\gamma
]

The current value is `gamma = 0.5`. Values below 1 generally brighten the image; values above 1 generally darken it.

### 3. Log Transformation
The notebook applies:

[
s = c\ln(1+r), \qquad c=\frac{255}{\ln(256)}
]

The natural logarithm is approximated manually using a Taylor-series expression in `manual_ln()`.

## Libraries
- OpenCV (`cv2`) – read the image as grayscale.
- NumPy – convert the processed Python lists to arrays for display.
- Matplotlib – display the original and transformed images.

## How to Run
1. Open `Experiment_01.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.
2. Make sure `sunflower.jpg` is available at the path specified by `image_path`.
3. Install the dependencies if needed:

   ```bash
   pip install opencv-python numpy matplotlib
   ```

4. Run all notebook cells.

## Expected Output
A figure compares the original grayscale image with:
- Manual negative image
- Manual power-law image (gamma = 0.5)
- Manual log-transformed image

## Notes
- The manual pixel transformations use nested Python loops; large images may take longer to process.
- Pixel values are clamped to the valid 8-bit range (0–255) before display.
