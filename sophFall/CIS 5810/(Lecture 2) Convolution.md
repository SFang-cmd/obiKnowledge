Boundaries in the optical illusion can only be taken by one object, not two next to each other
- Your brain can't see holes, it only sees the objects, then fills out the other
- (Why can't soccer players shoot at the goal? Cuz they can't see holes lol)

Optical Illusions:
- Vase vs Face (Which one looks like the hole? The black or white?)
- Trouble of sizing - two identical shapes can look different sizes
	- Our brain processes images locally, can notice local changes, but not global
- Trouble of focusing - focusing on different objects can cause others to move (optical illusions)

**How to think of images?**

**Concept: Images are really just made out of gradient black and white patterns** 

What is a 2D Fourier Transform?
- Algorithm - Broken code - 2D Fourier Transform
- Code takes image through Fourier Transform (convolutions)
- Combination of two gradient patterns will combine and form a combination of images through the Fourier Transform
- (Ex. two different gradients can come together and form a rough blob image)
- **Eventually, adding enough gradient patterns of orienting lines will create blobs that can become any image**

**Concept 2: Image Scales matters**
- You can shrink or expand images
- Details get lost when shrinking
- Looking at edges, which scales should I use (high resolution or low resolution works better?)
	- Try from lowest to highest resolution to find the best edges
	- At certain scales, different edges can be enhanced, so image scale matters a lot
- **Different scales of images encodes different edge response**

**Edge Detection:**
- Edge Formation Factors
	- Depth discontinuity - Checks foreground from background edges
	- Illumination discontinuity - Shadows and different lighting conditions of the same objects form edges (brain ignores the shadow, so computer has to learn how to override this type of signal)
	- Surface color discontinuity - Check different colors on the same surface (good for telling where the road is)
	- Surface normal discontinuity - textures and other elements on the same objects
- Edge detection is complicated because the computer needs to identify which edges are important and which ones aren't

**Image filtering:**
- Any 2D matrix can be seen as an image
- DO NOT LOOP OVER PIXELS
- Instead, learn how to do *vectorization* instead - parallel processing

**Linear Filtering (a bit different from convolution):**
- 2 Concepts:
	1. "Peer Pressuring" - I have an image, given values of an image $I$, replace each pixel value by the weighted average of its neighbors, based on the values given in the Kernel of $f$
		1. So if we trust the top right value 0.5, right value 0.5, value itself 1.5, and bottom value -0.5, with values 200, 10, 100, and 100 respectively
		2. $0.5 * 200 + 0.5 * 10 + 1.5 * 100 + -0.5 * 100 = 205$
		3. So central value will take 205 as its weighted average
		4. Apply kernel everywhere, then run in parallel for all 3x3 image filtering
		5. Image filtering causes matrices to "flip"
		6. ![[Pasted image 20240905102656.png]]
		7. From $I$ to $g$
	2. Filtering can be thought of as expansion of the signals - Every pixel through this kernel is sending info to someone.

**Simple Neural Network:**
- Signals get amplified or negated, so linear filtering operation can be thought of as a simple neural network
- (Takes image I and multiplies it by f as a "dot product", which leads to resulting g)

**Anatomy of the Eye**
- Has aperture - iris
- Has lens - lens
- Has sensors - Retina (With Fovea in high-resolution)

**Photo-sensors**
- Light pass through retina cells, excites rods and cones
- **Cone:** Color (spectral) sensitive, R, G, B, 6 million
- **Rod:** More light (photo) sensitive, peak at 580nm (yellow), 120 M
- What happens if you miss one type of cone cell

**Linear Filtering Examples:**

| 0   | 0   | 0   |
| --- | --- | --- |
| 0   | 1   | 0   |
| 0   | 0   | 0   |

**Vision is half mathematical operations, half what it actually looks like on an image**

**Image Convolution**
- Image filtering is the physical intuition behind convolution
- Def: $I \otimes f$
- Let $I$ be a signal (image), Convolutional kernel $f$,
	- $g[m,n] = \sum\limits_{k,l}I(m - k, n - l) * f(k, l)$
	- Here, $g$ is the output image, $I$ is the input image, and $f$ is the kernel image
	- (Essentially you're just looking at the surrounding elements of an image and multiplying by a weighted sum of the images around it into the pixel itself)
- (Everything is flipped - ask prof **why**)
- Filtering shifts in the wrong direction - **need to flip the kernel horizontally and vertically**

**Impulse Functions shift images**
- Convolution is filtering with kernel flipped
- Convolution is commutative
- ![[Pasted image 20240905105539.png]]
- **So here is the kernel f the original kernel? And I need to flip before calculations?**

**Output Size of Image Convolution:**
- What is the output size?
	- Full - image can get bigger (edges get expanded when empty grids get extra values based on $g$) (usually makes sense when $f$ and $g$ are both kernels (sections not the whole image))
	- Same - cut image so that only the size of itself gets convolutionalized
	- Valid - Takes image and only convolutions the pixels that have a full $g$ convolution around it (no taking average of 0 grids) (concerned about the blur of the image not having funny values)
- Python syntax: `signal.convolve(in1, in2, mode="full", method="auto")`
- `signal.convolve(in1, in2, mode="full", boundary="fill")`
	- What to do about edges? Mirror the edges so that they get repeated
	- Many different methods

**Image Convolution: types of filter kernels**
- Gaussian Averaging
	- Rotationally symmetric
	- Weights nearby pixels more than distant ones
		- Makes sense as probabilistic inference
		- Also makes sense since images used to have lots of sensor defects
	- Gaussian gives a good model of a fuzzy blob - is good for making corners more rounded
	- ![[Pasted image 20240905110611.png]]
- 3 Types:
- ![[Pasted image 20240905110745.png]]
- Gaussian - blurs and will do "funny things" to corners
- Derivative of Gaussian - used for edge detection
- "Second Derivative Function of the Gaussian" (Laplacian of Gaussian) - Used to call the Mexican Head Operator - Used for many things


