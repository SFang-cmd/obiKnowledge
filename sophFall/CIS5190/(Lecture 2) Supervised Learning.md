Machine Learning Problem: Take data $Z=\{(x_{i},y_{i}\}$ --> Machine Learning Algorithm --> Model $f$ that predicts the output $y$, when given an input $x$

**Question:** What **model family** (a.k.a **hypothesis class**) to consider?

1. Linear Functions:
	1. Consider the space of linear functions $f_{\beta}(x)$ defined by
	2. $f_{\beta}(x) = \beta^{T}x = [\beta_{1}...\beta_{d}][x_1...x_d]^t$
	3. $x \in \mathbb{R}^{d}$ is called an **input** (aka features or covariates)

Linear Regression Problem:
- Supervised learning model
- Find relationship between single input $x$ and single output $y$
- Goal: output a linear function $f_{\beta}(x)$ that minimizes the MSE

**Notation:**
	- i to index examples in $(x_{i},y_{i})$
	- $j$ to index components $x_{j}$ of $x \in \mathbb{R}^{d}$
	- $x_ij$ is component $j$ of input example $i$

\*Need to find a good loss function:
- $y_{i}\approx \beta^{T}x_i$ if $(y_{i}-\beta^{T}x_{i})^2$ is small
- **Mean squared error (MSE)**
	- $L(\beta; Z) = \frac{1}{n}\sum\limits^{n}_{i=1}(y_{i}-\beta^{T}x_{i})^{2}$
	- Why use mean? to account for larger or smaller amounts of data (1 million data points will result in higher sum than 1 thousand)
	- Takes the squared difference between the actual $y$ value and the function's $y$ value
	- **Benefit:** Punishes data points for being **TOO** far from the correct answer

**Key point:** For optimizing or refining a regression algorithm, can use the Mean Squared Error or the Sum of Squared Errors, because the regression algorithm will try to minimize either, MSE only useful to compare to others

Need to find Performance Metrics:
- Every loss function is a performance metric, but not every performance metric is a good loss function
- E.g. For an ML model that makes car driving decisions:
	- How frequently did it successfully go from A to B?
	- How fast did it get there?
	- How many traffic violations did it commit?
- The loss function is a *single scalar function*. Good choices:
	- express all performance metrics
	- Is "convenient" for machine learning

The "True Function" $f^{*}$:
- There exists a "true function" that encapsulates everything that causes an output (for housing: location, size, color, number of interested individuals, etc.)
- Goal of ML: Find an approximation $f_{\beta}\approx f^{*}$in our model family $f_{\beta}\in F$, $f^*$ is typically not in our model family $F$

Function Approximation View of ML:
- Framework for designing machine learning algorithms
- **Two Key Design Decisions:**
	- What is the family of candidate models $f$?
	- How to define "approximating"?

Linear Regression Framework:
- Data $Z$
- Use to minimize the MSE Loss function
- Model family is the linear function family
- Approximate the problem into a function $f_{\hat{\beta}}(x)$

How can we solve non-linear functions if we only use linear regression?
Feature Maps
- **General strategy:**
	- Model family $F = \{f_{\beta}\}_{\beta}$
	- Effectively changes the hypothesis space. This is a powerful strategy for encoding "prior knowledge" about the function we are looking to approximate
	- Special: Intercept term
		- $\phi(x)=[1,x_1...]$
		- Is almost always used
- Solving a quadratic feature mapping:
	- Consider the feature map $\phi: \mathbb{R} \rightarrow \mathbb{R}^{2}$
		- $\phi(x) = [x, x^2]$
	- Then the model family is:
		- $f_{\beta}(x) = \beta_{1}x + \beta_{2}x^{2}$
	- (e.g. $f_{\beta}(x) = 0x + 1x^{2}$)

Other feature maps:
- Handle complex data:
	- E.g. $x=$ "the food was good" and $y=$ 4 stars
	- $\phi(x) = [1("good"\in x), 1("bad"\in x)...]^T$

Algorithm for Non-linear regression
- First, select an appropriate feature map:
	- $\phi(x)=[\phi_{1}(x)...\phi_{d'}(x)]$
- Then, non-linear regression reduces to linear regression!
	- Step 1: Compute $\phi_{i}=\phi(x_{i})$ for each $x_{i}$ in $Z$
	- Step 2: Run linear regression with $Z'=\{(\phi_{1},y_{1}),...,(\phi_{n},y_{n}\}$

Why not always throw in lots of features?
- Can get very close to $R^{2}=1$
- But issue is it will not approximate new inputs and new predictions

Training vs. Test Data
- **Training data:** Examples $Z=\{(x,y\}$ used to fit our model
- **Test data:** New inputs $x$ whose labels $y$ we want to predict

**Overfitting:** Fits the training data well but not the test data
**Underfitting:** Does not fit the training data and does not fit the test data either

Role of Capacity:
- **Capacity** of a model family captures "complexity" of data it can fit
	- Higher capacity --> more likely to overfit (model family has high **variance**)
		- Too expressive
	- Lower capacity --> more likely to underfit (model family has high **bias**)
		- Not expressive enough
- For linear regression, capacity roughly corresponds to feature dimension $d$

Bias-Variance Tradeoff
- (Increased capacity means more features, or other stuff)

