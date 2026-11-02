# Lab 3 – Spatial Filtering, Noise Reduction, and Image Sharpening

## Overview
This experiment implements 2D spatial correlation from scratch and uses it to explore smoothing, sharpening, and image-quality measurements. A synthetic grayscale scene represents a corridor or path with obstacles.

## Notebook
- [Experiment_03.ipynb](./Experiment_03.ipynb)

## Concepts and Operations

### 1. Custom 2D Correlation
The function `correlate2d_custom()`:
- Converts the image and kernel to floating-point arrays.
- Pads the image with zeros.
- Slides the kernel over the image using nested loops.
- Computes the sum of each image region multiplied by the kernel.

This makes the spatial filtering operation explicit rather than relying on a ready-made filtering function.

### 2. Degraded Input Generation
The notebook creates a synthetic clean scene and generates:
- Gaussian-noisy images with standard deviations (sigma) of 10 and 25.
- A motion-blurred image using a horizontal averaging kernel.

### 3. Noise Suppression with Averaging Filters
Box filters of sizes 3×3, 5×5, and 9×9 are applied to both noisy images. The results demonstrate the trade-off between noise reduction and loss of fine detail.

### 4. Boundary Recovery with Laplacian Sharpening
Four-neighbor and eight-neighbor Laplacian kernels are applied to the motion-blurred image. Their responses are used to produce sharpened outputs.

### 5. Unsharp Masking and High-Boost Filtering
A blurred version of the noisy image is subtracted from the original to form a detail mask. The mask is added back using boost factors (k=1, 1.5, 2, 3).

### 6. Quality Metrics
- **PSNR (Peak Signal-to-Noise Ratio):** compares a processed image with the clean reference using mean squared error.
- **Sharpness:** estimated using the variance of the Laplacian response.

These metrics complement the visual comparisons; a higher sharpness value does not always mean a better image.

## Libraries
- NumPy – arrays, padding, kernels, and numerical calculations.
- OpenCV (`cv2`) – imported by the notebook.
- Matplotlib – visualization.
  
## How to Run
1. Open `Experiment_03.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.
2. Install the dependencies if needed:

   ```bash
   pip install numpy opencv-python matplotlib
   ```

3. Run all notebook cells.

## Expected Output
The notebook displays:
- The clean, noisy, and motion-blurred input images.
- Averaging-filter results for different noise levels and kernel sizes.
- Results from 4-neighbor and 8-neighbor Laplacian sharpening.
- Unsharp masking/high-boost results for several boost factors.
- PSNR and sharpness values printed for the processed images.

## Notes
- The scene is generated synthetically in the notebook; no external input image is required.
- Noise is random, so metric values and visual results can vary between runs.
- The custom correlation uses zero padding at image boundaries.
