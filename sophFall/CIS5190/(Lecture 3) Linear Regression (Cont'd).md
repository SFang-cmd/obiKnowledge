- **Input:** Dataset $Z = \{(x_{1},y_{1}), ... ,(x_{n},y_{n}\}$
- Compute
	- $\hat{\beta} = arg min_{\beta \in \mathbb{R}^{d}}\frac{1}{n} \sum\limits_{i=1}^{n}(y_{i}-\beta^{T}x_{i})^2$
- **Output:** $f_{\hat{\beta(Z)}}=\hat{\beta}(Z)^{T}x$
- Discuss algorithm later today

**Loss Minimization View of ML:**
- Design an ML algorithm by choosing a model family, then choosing a loss function to minimize

**Bias-Variance Tradeoff**
- Overfitting (high variance)
	- Fits the training data $Z$ well
	- Fits new held out data $(x,y)$ poorly
- Underfitting
	- Fits the training data $Z$ poorly
	- Fits the new data poorly

**Training/Test Split**
- **Issue:** How to detect overfitting vs. underfitting?
- **Solution:** Use **held-out test data** to estimate loss on new data
	- Typically, randomly shuffle data first
- Typically keep large portion of the data in the train set, less amount in test data set

**Training/Test Split Protocol in ML**
- **Step 1:** Split $Z$ into $Z_{train}$ and $Z_{test}$
- **Step 2:** Run linear regression with $Z_{train}$ to obtain $\hat{\beta}(Z_{train})$
- **Step 3:** Evaluate
	- **Training loss:** $L_{train}=L(\hat{\beta}(Z_{train});Z_{train})$
	- **Test (or generalization loss)** $L_{test}=L(\hat{\beta}(Z_{test});Z_{test})$ (plus other performance metrics beside the loss function)
- For **Overfitting:**
	- $L_{train}$ is small
	- $L_{test}$ is large
- For **Underfitting**
	- $L_{train}$ is large
	- $L_{test}$ is large

**Underfitting/Overfitting <=> Bias/Variance**
- **Variance:** How much do those fitted functions $\{f_{\beta}\}_{1:k}$ differ amongst each other, on average over the data distribution?
- **Bias:** How much does the average of those fitted functions $\{f_{\beta}\}_{1:k}$ deviate from the "true" function over the data distribution
- **Overfitting (high variance):**
	- *Too many constraints, so different training iterations may result in completely different models*
	- High capacity model capable of fitting complex data
	- Insufficient constraining data
- **Underfitting (high bias):**
	- *Too few constrains, so all training algorithms will result in similar curves, just doesn't fit the correct dataset*
	- Low capacity model that can only fit simple data
	- Sufficient data but poor fit

**Under/Over-fitting & Model Capacity:**
- Expanding the hypothesis class usually leads to higher variance, lower bias
- (adding new dimensions to the feature map will make the model fit better, but may lead to more volatile training)

**How to Fix Underfitting/Overfitting?**
- Three main options:
	1. Choose the right model family (not too complex, not too simple)
	2. Improve the training dataset (i.e. collect more data)

**Bias-Variance Tradeoff For Linear Regression**
- For linear regression with feature maps, increasing number of dimensions $d'$
	- Tends to **increase capacity**, **decreases bias, but increases variance**

**The Effect of Dataset Size**
- Increasing number of examples $n$ in the data...
	- Tends to **keep bias fixed** and **decrease variance**
- **As dataset size grows:**
	- Generalization error ($\approx$ "Bias" + "Variance") is dominated by bias
	- To reduce error, we select high capacity, low bias models

Larger datasets have room of expanded hypothesis class

**Regularization: Modifying the Loss Function**
- **Intuition:** We *only* asked the ML algorithm to fit the training data as well as possible, so it produced overly complex fits --> "Overfitting"
	- $L(\beta;Z)=$ Train MSE
- **Solution:** we will ask the model to produce a *"simple fit"* to the training data.
	- $L(\beta;Z)=$ Train MSE + Fit Complexity
- $L(\beta;Z)=\frac{1}{n}\sum\limits_{i=1}^{n}(y_{i}-\beta^{T}x_{i})^{2} + \lambda\cdot ||\beta||^{2}_{2}$
	- $=\frac{1}{n}\sum\limits_{i=1}^{n}(y_{i}-\beta^{T}x_{i})^{2} + \lambda\sum\limits_{j=1}^{d}\beta_{j}^{2}$
- $\lambda$ is a **hyperparameter** that must be tuned (satisfies $\lambda \geq 0$)

**Intuition on $L_{2}$ regularization**
- **Why does it help?**
	- Encourages "simple" functions
		- This is what $L_{2}$ regularization does: $\sum\limits_{j=1}^{d}\beta_{j}^{2}=||\beta||^{2}_{2}=||\beta - 0||^{2}_{2}$
		- Pulls coefficients towards 0 (want higher degree polynomials to be nearly nonexistent, i.e. $ax^5+x$ would emphasize the $x$ value, not the $x^{5}$ value)
		- As $\lambda \rightarrow \infty$, it force $\beta = 0$
	- L2 regularized linear regressionn amounts to preferring smaller weights according to a Gaussian pdf.
	- Encouraging $\beta_{j}$'2 to have small magnitude, this also induces a smaller-capacity hypothesis (capacity is not just the number of features, but the magnitude of the capacity; think almost **the number of datasets it can fit**)

**General Regularization Strategy**
- **Original Loss** + **Regularization**
	- $L_{new}(\beta;Z)=L(\beta;Z) + \lambda\cdotR(\beta)$
	- Offers a way to express a preference for "simpler" functions in family
	- Typically, regularization is independent of data
- Q: For the new parameters $\beta_{new}^{*}=min_{\beta}L_{new}$, $L_{new}$ will have a higher value in general due to the added $L_{2}$ constraint parameter (but hopefully this new loss can help make our model more accurate)

**Hyperparameter Tuning**
- $\lambda$ is a **hyperparameter** that must be tuned (satisfies $\lambda \geq 0$)
- **Naïve strategy:** Try a few different candidates $\lambda_{t}$ and choose the one that minimizes the test loss
- **Problem:** We may overfit the test set!
	- Major problem if we have more hyperparameters
- **Solution:** A new subset of data just for selecting hyperparameters

**Train/Val/Test Split for Model Selection**
- **Goal:** Choose best hyperparameter $\lambda$
	- Can also compare different model families, feature maps, etc.
- **Solution:** Optimize $\lambda$ on a **held-out validation data**
	- **Rule of thumb:** 60/20/20 split (usually shuffle before splitting)

**Basic Cross Validation Algorithm:**
- **Step 1:** Split $Z$ into $Z_{train}$, $Z_{val}$, and $Z_{test}$
- **Step 2:** For $t \in \{1,..,h\}$ hyperparameter choices:
	- **Step 2a:** Run linear regression with $Z_{train}$ and $\lambda_{t}$ to obtain $\hat{\beta}(Z_{train},\lambda)$
	- **Step 2b:** Evaluate validation loss $L_{val}^{t}=L(\hat{\beta}(Z_{train},\lambda_{t});Z_{val})$
- **Step 3:** Use best $\lambda_{t}$
	- Choose $t'=arg min_{t}L_{val}^{t}$ with lowest validation loss
	- Re-run linear regression with $Z_{train}$ and $\lambda_{t}'$ to obtain $\hat{\beta}(Z_{train},\lambda_{t'})$