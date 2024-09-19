**Goal:**
- Sobel filter
	- Can be used for basic horizontal and vertical edge detection
- Sobel Operators:
	- Convolve two 3x3 kernels with original image to get derivatives

**Issue with Sobel filter**
- Gives thick and thin edges
- Not resolution Independent (Gradient spread over many pixels if it's a high resolution image)
- **Solution:** Use Canny Edge detection
	- Gets rid of the less useful edges and keep the more relevant ones

**Steps in Canny Edge Detection:**
1. Find derivatives
2. Compute Magnitude of Gradeitn
3. Edge Orientation
4. Non-maximum Suppression
5. Hysteresis

(Live Demo)
https://colab.research.google.com/drive/1rG2eMU5rmSm9fJkkSgwy5CMXLtcmYjt5#scrollTo=BAiXmUKs5F22
