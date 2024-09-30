
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

**kNNs Summary:**
- A simple and versatile ML approach, tied directly to the data
- No training phase. Ready to make predictions the moment you have the dataset
- "Non-parametric". For kNNs, the data *are* the parameters
- Scaling troubles, but still almost always worthwhile as your first algorithm for a new problem

**Decision Trees:**
- Data Matrix X:
	- Each row is a sample, $x_{i}$
	- Each column is a label, $y_{j}$
	- Columns $X_{j}$ denote features
- Different types of data too:
	- Numeric: numbers
	- Nominal: words
	- Ordinal: ordered sets
	- Binary: yes/no

**Data Dictionary:**
- Data sets are often accompanied by a *data dictionary* that describes each feature
- It is critical to understand the data!
- The dictionary for our data gives definitions of each datapoint
- (ex. 777 is refused, 999 is don't know for numeric data)

**Decision Trees for People:**
- Human diagnoses are often made in a "flowchart" style:
	- "Explainable" in a clear way, easy to evaluate
	- Often, a kind of flowchart based on tests! "Decision Tree"

**A Decision Tree Based on Boolean Tests:**
- For continuous features, we'll restrict our study to internal nodes that make binary decisions based on a single feature:
	- e.g. is a real-valued feature above or below some threshold?
	- e.g. is a binary-valued feature true or false?
- For discrete-valued features, we will usually create as many splits as the number of values
![[Pasted image 20240930112624.png]]

**Decision Tree Aspects:**
- "Internal Nodes"/"Splits": The questions or filters that each example goes down
- "Leaf nodes": The end result/outputs for a decision tree

**Top-Down Decision Tree Induction:**
- Let $D$ be a set of labeled instances; $D=\{(\mathbf{x}_{i},y_{i})_{i=1}^{N}\}=[X_{N\times D}, y_{N\times 1}]$
- Let $D[X_{j}=v]$ be the subset of $D$ where feature $X_{j}$ has value $v$

function `train_tree(D)`
1. If data $D$ all have the same label y, return new `leaf_node(y)`
2. Pick the "best" feature $X_{j}$ to partition $D$
3. Set `node=new decision_node(X)`
4. ...