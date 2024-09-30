
**k-Nearest Neighbors:**
- A simple approach, connected directly to the data
- This schematic seems to skip any explicit "model training" on data
- **kNN Classification:** To predict category label $y$ of a new point $x$:
	- Find $k$ "nearest neighbors"
	- Assign the majority label
- **kNN Regression:** To predict numeric value $y$ of a new point $x$:
	- Find $k$ "nearest neighbors"
	- Average the values associated with the neighbors
	- In each case, varying $k$ could change the predictions

*"Nearest neighbors"* = training instances with the least "distance"
*Choice of distance function is critical!!*

Commonly used distances $d(x_{1},x_{2})$ are:
- $l_{1}$ distance $\left( \sum_{j}|x_{1j}-x_{2j}|^1 \right)^{\frac{1}{1}}$
	- $\sum_{j}|x_{1j}-x_{2j}|$
- $l_{2}$ distance $\left( \sum_{j}|x_{1j}-x_{2j}|^{2} \right)^{\frac{1}{2}}$
	- Also, "Euclidean" distance
- $l_{\infty}$ distance $\left( \sum_{j}|x_{1j}-x_{2j}|^{\to \infty} \right)^{\to 0}$
	- $max_{j}(|x_{1j}-x_{2j}|)$

**As we increase the $l$ power term, the value approaches the largest difference term in the value**

**Parameters in kNN:**
- The full training dataset!
- Need all of them to calculate nearest neighbors

**Hyperparameters in kNN:**
- Distance function (often Euclidean by default)
- Choice of how many $k$ nearest neighbors

**Hypothesis Space of kNN:**
- kNN models are only limited in expressivity by the training data, so with the right training dataset, kNN models can represent *any* function

**Excellent First Algorithm to Try:**
- Recall that an important step in model evaluation is comparing to a "simple baseline"
- For many problems, k-Nearest Neighbors is a good choice of a first "simple baseline"
	- Very easy to write in code
	- Versatile, does not impose specific restrictions on the learned function, such as "linearity"
	- Very easy to interpret the outcomes because of the direct connection to training data
- Often works surprisingly well!
- kNN is not without its problems, of course. But more on that later

**Aside: Scale invariance in kNN:**
- kNN may be affected by feature scaling; one feature in the data scaled 100x plays a much bigger role than another unit
- Use feature standardization/"normalization"

**Aside: kNN Distance Functions for String Data Types:**
- **Hamming Distance** (number of characters that are different)
	- **A**BC**D**E vs **A**GD**D**F
	- 3 different chars
- **Edit Distance:** (number of character inserts/replacements/deletes to go from one to the other)
	- **RO**BOT vs BOT
- **Jaccard Distance** between sets
	- $\frac{|A\cap B|}{|A\cup B}$

**Aside: Probabilistic Predictions from kNN Classifiers**
- Easy to extend to produce probabilistic predictions too
- One Example: for a multi-class classification problem:
	- Find $k$ nearest neighbors
	- Set $P$(class i) $= \frac{1}{k}$ \* number of instances of class $i$ among the neighbors

