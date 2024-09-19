- NEVER think of images as separate pixels
- Think of unified image instead

**Image Scale:** At what scale of an image does the individual start standing out?
- Zooming more in causes edges to blur more/less detail
- **Zoomed in is equivalent to using a large Gaussian Kernel** (more blur)

*Layers of a neural network are almost like a pyramid - multiple inputs concentrated into one output*
Given a photo of a pyramid, the layer 22 abstraction was saying "An isosceles triangle"

**CLIP-ViT Findings:**
- What ViT layer and head learns
	- Layer 23, Head 10 - "number head"
	- Layer 22, Head 4 - "shape head"

CLIP - Linking images to text
DINO - Image segmentation and motion tracking
MAE - Learned through self-supervision, matches patches and has neural networks to predict patches

**Image Pyramids**
- Known as Gaussian Pyramid
	- In computer graphics, a *mip map*
	- A precursor to *wavelet transform*

**Detour:**
**Image encoding-decoding**
- Back then, sending messages was expensive - how can we predict what someone's gonna say?
1. Image statistics: pixel in neighborhood are correlated, encode per pixel value is redundant
2. Predictive Coding: use raster scan, predice based on pass value, and store only the error in prediction. Simple and fast
	- Error corrections are small - can get away with sending less info
	- Big idea - just decode edges, since this is where errors are big
	- Just send one pixel along with a few edges and then can reconstruct original image

**Non-causal prediction**
- Non-causal involves typically transform, or solution to a large sets of equations. Encode block by block. Bigger compression but slower

**Can use more general building blocks of image**
- Strategy number 1: Use deep learning package to decompose image I into various weights
- Strategy number 2: Use linear algebra's least squares strategies
- Strategy number 3: Use jpatch

**Coding book of DCT (discrete Cosine)**

**How to do Image Pyramid:**
1. Image sub-sampling
	- Throw away every other row and column to create a 1/2 or 1/4 or 1/8 size image
		- called *image sub-sampling*
	- When the image is small, brain tries to fill in the blanks and "pretends" that the image is full resolution
	- To smooth out really pixelated images, use gaussian blur because it causes squares to eventually become circular in a sense
2. Sampling
	- Sample often or sample wisely
	- Bad Sampling: Alters the image completely; aliasing does not work
	- If you don't like the answer, change the question: get rid of fine detail, sample every other pixel
3. Gaussian Pre-filtering
	- Solution: filter the image, *then* subsample
		- Filter size should double for each $\frac{1}{2}$ size in reduction. Why?
	- Using the original image, first blur the image, then subsample
	- How to speed it up?
	- Image Reduce:
		- $g_{l}=\sum\limits_{m=-2}^{2}\sum\limits_{n=-2}^{2}w(m,n)g_{l-1}(2i + m, 2j + n)$, where for the current layer, the $2i$ is because every element in $g_{l}$ is every other element in the layer below, $g_{l-1}$
		- $g_{l}=[g_{l-1}\otimes ...]$
	- Choosing your weighting function (weighted average):
		- $\hat{w}(0)=a$
		- $\hat{w}(1)=\hat{w}(-1)=\frac{1}{4}$
		- $\hat{w}(2)=\hat{w}(-2)=\frac{1}{4} - \frac{a}{2}$
		- Do a little smoothing and a little sharpening: $a=0.6$
4. Image Expansion:
	- $g_{l}(i,j)=4\sum\limits_{m=-2}^{2}\sum\limits_{n=-2}^{2}w(m,n)\cdot g_{l+1}(\frac{i-m}{2}, \frac{j-n}{2})$
	- Stretch the image out into native resolution, set empty pixels to 0, then horizontally smooth using the above equation
	- Basically a form of interpolation
	- **Note:** Need to multiply by 4 to account for 0 magnitudes
- **Question:** So is 4 a constant, if you have a larger kernel, the 4 might not be the correct ratio of 0s to colored pixels (couldn't you feasibly blow out an image potentially?)
- **Question:** Is the weighted function the same?

- Laplacian values are mostly 0, so while original image data values is an $n\times n$ image with $2^8$ image values, it can go down to $n^{2}\times 2^1$ bits vs. $n^{2}\times 2^{8}$ bits so much smaller