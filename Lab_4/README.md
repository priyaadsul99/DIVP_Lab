# Lab 4 – Spatial Derivative Kernels

## Overview
This experiment studies the response of four 3×3 spatial derivative kernels using two synthetic test images:
- A set of one-pixel-wide diagonal lines.
- Three vertical lines, each three pixels wide.

Each kernel is applied to both images, and the original and filtered results are displayed for comparison.

## Notebook
- [Experiment_04.ipynb](./Experiment_04.ipynb)

## Kernels Used

### Kernel A – Second Derivative (Laplacian)
```text
[ 1   1   1 ]
[ 1  -8   1 ]
[ 1   1   1 ]
```
Responds to intensity changes in all eight neighboring directions and highlights edges.

### Kernel B – First Derivative (Horizontal)
```text
[-1  -1  -1 ]
[ 2   2   2 ]
[-1  -1  -1 ]
```
Measures changes across the vertical direction by comparing the center row with the rows above and below it.

### Kernel C – First Derivative (Vertical)
```text
[-1   2  -1 ]
[-1   2  -1 ]
[-1   2  -1 ]
```
Responds to changes across the horizontal direction by comparing the center column with the columns on either side.

### Kernel D – Second Derivative (Diagonal)
```text
[ 2  -1  -1 ]
[-1   2  -1 ]
[-1  -1   2 ]
```
Emphasizes diagonal intensity relationships and responses.

## Implementation
The `apply_kernel()` function:
1. Reads the image and kernel dimensions.
2. Adds zero padding around the image.
3. Moves the 3×3 kernel across each pixel location.
4. Multiplies the image region by the kernel element-wise and sums the result.
5. Stores the response in a floating-point output image.

**Terminology note:** The implementation multiplies each image region by the kernel without flipping the kernel. Strictly speaking, this operation is 2D cross-correlation rather than mathematical convolution. It is commonly described informally as applying a filter/kernel.

## Test Images
- **1-pixel image:** Three diagonal line segments drawn on a 100×100 black image.
- **3-pixel image:** Three vertical white bars, each three pixels wide, on a 100×100 black image.

## Libraries
- NumPy – image arrays, kernel definitions, and zero padding.
- Matplotlib – visualization of original and filtered images.

## How to Run
1. Open `Experiment_04.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.
2. Install dependencies if needed:

   ```bash
   pip install numpy matplotlib
   ```

3. Run all notebook cells.

## Expected Output
Two result figures are displayed:
- Original one-pixel image and its responses to kernels A, B, C, and D.
- Original three-pixel-wide image and its responses to kernels A, B, C, and D.

## Saved Output Figures
The program's two result visualizations are also saved in this folder:
- [Output_1pixel.svg](./Output_1pixel.svg) – original one-pixel diagonal lines and responses from kernels A–D.
- [Output_3pixel.svg](./Output_3pixel.svg) – original three-pixel-wide vertical lines and responses from kernels A–D.

Open either SVG file in a browser to view the output at full resolution.

## Notes
- The synthetic test images are generated in the notebook; no external image files are required.
- Derivative filter responses can contain negative values. Matplotlib displays the floating-point arrays directly, so contrast and appearance may differ from a normalized 8-bit display.
- Zero padding can create additional responses along image boundaries.
