So how can we optimize for the lowest loss function?

**Strategy #1: Random Search** (BAD IDEA)
- In practice, not very good
- Takes way too much resources
- Testing trained 15.5% accuracy with this method

**Strategy #2: Follow the Slope**
- "Feel which way is down"
- Generally the strategy that us used
- In $1$-dimension, the slope is the derivative of a function:
	- $\frac{df(x)}{dx} = \lim_{h \rightarrow 0}\frac{f(x+h)-f(x)}{h}$
- In multiple dimensions, the **gradient** is the vector of (partial derivatives) along each dimension
- The slope in any direction is the **dot product** of the direction with the gradient
- The direction of steepest descent is the **negative gradient**
- How to use? FINITE DIFFERENCES
![[Pasted image 20240521153500.png]]
- However, it is VERY slow to loop over all dimensions; it is also an approximation
- Instead, directly use the loss function, since it is a function of $W$:
	- ![[Pasted image 20240521153623.png]]
- ![[Pasted image 20240521153637.png]]

**In summary:**
- Numerical gradient: approximate, slow, easy to write
- Analytic gradient: exact, fast, error-prone
- *However in practice:* Always use analytic gradient, but check implementation with numerical gradient
	- **Gradient Check**

**Gradient Descent:**
```python
# Vanilla Gradient Descent

while True:
	weights_grad = evaluate_gradient(loss_fun, data, weights)
	weights += -step_size * weights_grad
```
- **STEP SIZE IS A HYPERPARAMETER**
	- Very important to figure out at first, since we don't want to overshoot or cause inaccuracies due to this step size

**Stochastic Gradient Descent (SGD)**
- Full sum expensive when $N$ is large!
- Instead: approximate a sum using a **minibatch** of examples (typically powers of 2 (32/64/128) are common)
- Sample code:
```python
# Vanilla Minibatch Gradient Descent

while True:
	data_batch = sample_training_data(data,256) # take sample of 256
	weights_grad = evaluate_gradient(loss_fun, data_batch, weights)
	weights += -step_size * weights_grad # perform parameter update
```

*Historically, there were ways to change the image features transformations:*
E.g. polar coordinates are a better representation compared to rectangular coordinates
For example, Color Histogram:
- Globally, count the number of pixels of each "bucket" of colors, so this would make the features easier to place into models
Another example: Histogram of Oriented Gradients (HoG)
- Measures the local orientation of edges (divides int 8x8 pixel regions, identify the major edge orientations over all the 8x8 regions)
Bag of words:
- Using feature vectors, the code is able to translate the different patches of images and creates a reference "codebook", which will be able to decode what an image suggests

