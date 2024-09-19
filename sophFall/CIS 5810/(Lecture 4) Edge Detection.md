Image Convolution: type of filter kernels

Gaussian Averaging:
- Rotationally symmetric
- "Fuzzy blocks"
Derivative of Gaussian:
- Used for edge detection (more broad edges)
Laplacian of Gaussian:
- "Mexican head operator"
- Also used for edge detection (more sharp changes)

**Canny Edge Detection**
- Objective: to localize edges given an image.
$$
B(i,j) = \begin{cases} 1, \text{if $I(i,j)$ is an edge}\\
0, \text{if $I(i,j)$ is not an edge} \\
\end{cases}\
$$
- Binary image indicating edge pixels

**Canny Edge Detection Algorithm:**
1. Compute Image Gradient
	- Filter out noise and compute derivative
	- Derivative of the gaussian
	- $(\frac{\delta}{\delta x} \otimes G)$ (Gradient of the Gaussian)
$$Gaussian=
\begin{bmatrix}
1 & 4 & 1 \\ 4 & 9 & 4 \\ 1 & 4 & 1 \\
\end{bmatrix}$$
	- Final: $I \otimes (\frac{\delta}{\delta x} \otimes G)=I_{x},I_{y}$ Smoothed derivative
```Python
dx, dy = np.gradient(G, axis = (1,0))
Ix = signal.convolve2d(I,dx,'same')
Iy = signal.convovle2d(I,dy,'same')
```
2. Compute the magnitude of the gradient
	- $I_{m} = np.sqrt((I_{x})^{2}+(I_{y})^2)$
	- Now, we roughly know where the edges are, but we need their precise location

**Canny Edge Implementation**
```Python
img = Image.open('image.png')
img = img.convert('LA')

# Value for high and low thresholding
threshold_low = 0.035
threshold_high = 0.175

# Gaussian filter definition
G = [2,4,5,4,2;4,9,12,9,4;5,12,15,12,5;4,9,12,9,4;2,4,5,4,2]
G = (1/159) * G

# Filter for horizontal and vertical direction
dx = [1, -1]
dy = [1;-1]

# Convolution of image with Gaussian
Gx = signal.convolve2d(G, dx, 'same')
Gy = signal.convolve2d(G, dy, 'same')

# Convolution of image with Gx and Gy
Ix = signal.convolve2d(img, Gx, 'same')
Iy = signal.convolve2d(img, Gy, 'same')

#generate separate maps for the gradient and orientation of the edge
mag = math.sqrt(Iy^2 + Ix^2)
angle = np.arctan2(Iy, Ix)
```

*How do I find the one pixel that is the most "edge" pixel?*
- Pick one pixel that should be maximum in some sense "most maximal edge"
- Start at one pixel, then follow that edge along its angle
- Need to perform non-maximum suppression

Why blur an image? The image may look jagged, so all you need to do is blur the kernel and apply to operation gradient

What's stopping you from starting at each most intense value, then tracing along the angle?