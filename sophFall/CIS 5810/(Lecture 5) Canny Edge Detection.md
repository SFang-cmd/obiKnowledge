**Image Processing: Edge Orientation & Image Axis**
- For the image coordinate system,
- First pixel = top left = `image[0, 0]`
- Last pixel = bottom right = `image[image.shape[0] - 1, image.shape[1] - 1]`
- Positive rotation = clockwise direction

*Basic Image Processing tutorials exist online*

**Canny Edge Detection**
*Smoothing*
- Noise can lead to false edges
- (e.g. goose feathers could create high contrast black and white false edges)

*Compute Gradient*
- Convolve w/ Sobel kernels --> first derivative in horizontal direction ($G_{x}$) and vertical direction ($G_{y}$)
$$
G_{x}=
\begin{bmatrix}
+1 & 0 & -1 \\
+2 &  \\ \end{bmatrix}
$$

*Magnitude and Orientation of Gradient*
- Combine to give the gradient magnitude
	- $G = \sqrt{G_{x}^{2} + G_{y}^{2}}$
- Combine to give the gradient direction

