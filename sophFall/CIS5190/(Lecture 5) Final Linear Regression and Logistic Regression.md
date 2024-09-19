**Indexing: From 0 or 1?**
- Our slides mostly follow the math tradition of indexing from 1
- With polynomial functions, our index starts from 0, so that $\beta_{j}$ is the coefficients for the j-th order term
		$f_{\beta}(x)=\beta_{0}+\beta_{1}x+\beta_{2}x^{2}+...$
- With intercept term ($\phi(x)=[1, x_{1}, ..., x_{d}]^t$)

**Feature Standardization**
- Unregularized linear regression is invariant to feature scaling
	- Suppose we scale $x_{ij} \leftarrow 2x_{ij}$
	- Without regularization, simply use $\beta_{j}\leftarrow \beta_{j}/2$
	- In particular, $\frac{\beta_{j}}{2}\cdot 2x_{ij}=\beta_{j}\cdot x_{ij}$
- Not true for regularized regression!
	- Penalty $(\beta_{j}/2)^{2}$ is scaled by $\frac{1}{4}$ (not cancelled out!)
- $L(\beta; Z)=\frac{1}{n}\sum\limits_{i=1}^{n}(y_{i}-\beta^{T})x_{i})^{2}+\lambda(\beta_{2}^{2}+...+\beta_{j}^{2}+...+\beta_{d}^{2})$
- $L(\beta; Z)=\frac{1}{n}\sum\limits_{i=1}^{n}(y_{i}-\beta^{T})x_{i})^{2}+\lambda(\beta_{2}^{2}/4+...+\beta_{j}^{2}/4+...+\beta_{d}^{2}/4)$

**Feature standardization**
- Rescale features to zero mean and unit variance
- $x_{i,j}\leftarrow \frac{x_{i,j}-\mu_{j}}{\sigma_{j}}$
- $\mu_{j}=\frac{1}{N}\sum\limits_{i=1}^{N}x_{i,j}$
- $\sigma_{j}=\frac{1}{N}\sum\limits_{i=1}^{N}(x_{i,j}-\mu_{j})^{2}$
	- *Do not rescale the intercept term to $x_{1}=1$*
	- Can be sensitive to outliers (which you can fix by dropping outliers)
- Makes it easier to estimate coefficients
- Often better encodes real variations in data
- **Common Rookie Error:** Must use the same transformation during training & prediction
		- Compute $\mu_{j}$ and $\sigma_{j}$ on training data and use on test data

$L_{0}$ Regularization $\rightarrow$ $L_{1}$ Regularization
- Sparsity: Can we minimize $||\beta||_{0}=|\{j|\beta_{j}\neq 0|\}$, the number of non-zero components? (This is $L_{0}$ regularization)
	- Automatic feature selection
	- Improves interpretability
- Challenge: $||\beta_{0}||$ is not differentiable, making it hard to optimize
- Solution: $L_1$ regularization
	- We can instead us an $L_1$ norm $||\beta_1||$ as the regularizer
	- Still harder to optimize than $L_{2}$ norm, but at least it is convex

**$L_{1}$ Regularization for Feature Selection**
- Step 1: Construct a lot of features and add to feature map
- Step 2: Use $L_{1}$ regularized regression to "select" subset of features

**What about for Classification Problems? (Logistic Regression:)**

**Recall for supervised learning,**
- We have input data that is labelled with desired outputs
- Using a loss function, we find optimal parameters that minimize the loss with regularization
- The output model can be validated and tested with extra data inputs

**Binary Classification**
- **Input:** Dataset $Z = \{(x_{1}, y_{1}), (x_{2},y_{2}),...,(x_{n},y_{n})\}$
- **Output:** Model $y_{i}\approx f_{\beta}(x_{i})$

**Loss Minimization View of ML**
- **Three design decisions**
	- **Model family:** What are the candidate models $f$? (E.g. linear functions)

**Let's try to come up with a model class for logistic regression**

**Try Linear regression for classification**
- After training, predict class 1 if a $\beta^{T}x_{i}\geq 0$
- And class 0 otherwise
- Doesn't work because a lot of data in the middle with low confidence values can be misclassified easily
- Inaccuracy/Error Rate:
	- $L(\beta;Z)=\frac{1}{n}\sum\limits_{i=1}^{n}1(y_{i}\neq f_{\beta}(x_{i}))$
	- While this loss function is good as a performance metric to measure performance, it's a bad loss function because it is impossible to optimize
- Need to "soften" this in some way by making more continuous

**Logistic Regression**
- How to convert from $\beta^{T}x_{i}$which lies in $(-\infty, \infty)$ to a meaningful probability?
- Logistic Regression Mode:
	- The probability that $y=1$ is the following
	- $p(y=1|x;\beta)=\sigma(\beta^{T}x)$
	- where $\sigma(z)=\frac{1}{1+e^{-z}}$
- Provides a score for each possible outcome $y = 0$ or $y = 1$
- Thus, $p(y=0)=1-p(y=1)$

**Decision Boundary?**
- $p(y=1|x;\beta)=\sigma(\beta^{T}x)=0.5$

