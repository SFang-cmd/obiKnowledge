**Image Classification:** A Core Task in Computer Vision
**Problem:** Semantic Gap 
- The idea of a "cat" is only a semantic label of what the collection of pixels a picture actually is
**Challenges:**
- Viewpoint changes
- Lighting Changes
- Deformation (different poses/positions)
- Occlusion - You can only see parts of the cat (tail, head, behind grass, etc.)
- Background Clutter (Cat can look very similar to background)
- Intraclass variation (Differences in cat shapes, sizes, colors, ages, etc.)

*So what does the code look like?*

```python
def classify_image(image):
	# Some magic here?
	return class_label
```

*Very different from algorithms class (sorting a list of numbers, etc.)*
No obvious way to hard-code the algorithm to recognize a cat
- Some have tried to identify edges, corners, procedurally, but is not scalable
- Also not sustainable bc there are so many classes

**Instead:**
**Data-Driven Approach:**
1. Collect a dataset of images and labels
2. Use Machine Learning to train a classifier
3. Evaluate the classifier on new images

```python
def train(images, labels):
	# Machine Learning!
	return model
```

```python
def predict(model, test_images):
	# Use model to predict labels
	return test_labels
```

**Now, let's look at different Classifiers:**
**Classifier #1: Nearest Neighbor:**
- `train:` Memorize all data and labels
- `predict:` Predict the label of the most similar training image
Ex. Train on CIFAR10
- 10 classes
- 50,000 training images
- 10,000 testing images
- Applying Nearest Neighbor, the closest example is way more dissimilar

**How to compare distances?**
Using **Distance Metric** to compare images
$L_1$ distance: $d_1(I_1,I_2)=\sum_p{|I^p_1-I^p_2|}$

Nearest Neighbor Code:
![[Pasted image 20240520171838.png]]

Q: With N examples, how fast are training and prediction?
A: Training is O(1), but prediction needs to be compared to each of the other datasets O(N^2)
**Bad:** We want training to be slower and prediction to be faster, there is less cost when training then when using models

**Alternative: K-Nearest Neighbors**
- Instead of copying label from nearest neighbor, take **majority vote** from k-closest points

**K-Nearest Neighbors: Distance Metric**
L1 (Manhattan) distance
$d_1(I_1,I_2)=\sum\limits_p{|I_1^p-I_2^p|}$
- More natural fit when dependent on the coordinate systems

L2 (Euclidian) distance
$d_2(I_1,I_2)=\sqrt{\sum\limits_p{(I_1^p-I_2^p)^2}}$

Between these two different distance metrics, the boundaries change slightly
- L2 cares less about coordinate boundaries, so it would fit more naturally

**Hyperparameters:** Choices about the algorithm that we set rather than learn
- What is the best value of **k** to use?
- What is the best distance to use?
- **Very problem/dataset dependent**
- **Usually need to experiment to find optimal set of hyperparameters**

**Setting Hyperparameters:**
- Idea #1: Choose hyperparameters that work best on the data
	- **BAD:** K = 1 always works perfectly on training data
- Idea #2: Split data into **train** and **test**, choose hyperparameters that work best on test data
	- **BAD:** No idea how algorithm will perform on new data
- Idea #3: Split data into **train, val,** and **test**; choose hyperparameters on val and evaluate on test
	- ![[Pasted image 20240520173420.png]]
- Idea #4: **Cross Validation**: Split data into folds, try each fold as validation and average the result
	- ![[Pasted image 20240520173616.png]]
	- Useful for small datasets, but not used too frequently in deep learning

![[Pasted image 20240520173930.png]]

*k-Nearest Neighbor on images are* **never used**
- very slow at test time
- Distance metrics on pixels are not informative (just shifting it upwards slightly or around will mess it up)
![[Pasted image 20240520174118.png]]
- Curse of dimensionality (will never get enough images to train accurately) (as the dimensions increase, we will need exponentially more training examples to fill every single distance value from known point)

**Summary:**
- In **image classification**, we start with **training set** and predict labels with the **testing set**
- The **k-Nearest Neighbors** classifiers predicts labels based on the K nearest training examples
- Distance metric and $K$ are **hyperparameters**
- Can choose optimal **hyperparameters** using a validation set
- To test accuracy, only run on test set **once** at the very end

**Linear Classification:**
- Simple, but really important in the idea of CNNs and generic Neural Networks
- Idea of neural network: Almost like layers of legos, with layers being different things such as linear classifiers, etc.
- Parametric Model:
	- Takes in an image (e.g. 32x32x3, where the 3 are the RBG values)
	- Feed this into a function $f(x,W)$
	- $x$ is the input image
	- $W$ is the parameter of weights
	- Trick in deep learning is how to combine different parameters to find an optimal model
	- Ex. $f(x,W)=Wx + b$
	- Recall our image is $32x32x3=3072$ entries, which is our $x$ vector (size is $3072\times 1$)
	- $W$ is $10\times 3072$, the weights for each of the $3072$ entries with $10$ per
	- $f(x,W)$ will return a $10 \times 1$ matrix of probabilities for each of the classes
	- $b$ is a bias term, common for a linear model
	- Weights almost create a "template" for what each of the images may look like
- Problem: The linear classifier uses one singular template for all elements of the train set, so it may be inaccurate because not all elements look exactly the same
- ![[Pasted image 20240520175700.png]]
- (Note the blurred images are reverse engineered; given a complete full value for each class, if we go backwards on the weights, what would the image look like?)
- (Horse has 2 heads)
- Linear classifiers is almost putting boundaries in a $N$-dimensional space to help separate the different classes
- ![[Pasted image 20240520175757.png]]

**Hard Cases for a Linear Classifier:**
- ![[Pasted image 20240520175855.png]]
- Multi-modal classifications: Blue category only lives in certain areas, and elsewhere is red, hard to draw a boundary that connects disconnected "islands"
- Counting and hard lines are difficult (example 1)