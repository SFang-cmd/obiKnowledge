**Process:**
- Take previous data, $Z=\{x_{i}\}$
- Feed through a Machine Learning algorithm to gather the most relevant groupings of different clusters
- New data input $x$ allows computer to output the correct groupings

**Applications:**
- Visualization:
	- Exploring a dataset, or a machine learning model's outputs
	- e.g. "Based on our polling data, there are three main voting blocs, based on age, race, education level, income, political beliefs, and home-ownership. However, features like marital status and \# children are irrelevant"
- Feature Learning:
	- Automatically construct lower-dimensional features
	- Especially useful with a lot of unlabeled data and just a few labeled examples (can correlate known labels to unlabeled datapoints)
	- e.g. "do our company's profits $y_{i}$" actually correlate with the weather $\mathbf{x}_{i}$?"
	- e.g. "Most of the variation between our customers is explained by their age, location, and education level"
- Generate new data
	- "Given all of Bach's work, I could generate new music that would sound like Bach"
- Image Compression
	- E.g. JPEG is adopting unsupervised machine learning approaches
	- https://jpeg.org/items/20190327_press.html

**Applications Cont'd:**
- Framing an ML problem
- Data analysis/visualization
- ML Design (hypothesis class, loss function, optimizer, hyperparameters, features)
- Validate/Evaluate

**Loss Minimization Framework:**
- To design an unsupervised learning algorithm:
	- Model Family: Choose a model family $F=\{f_{\beta}\}_{\beta'}$
	- Loss function: Choose a loss function $L(\beta;Z)$
- Resulting Algorithm:
	- $\hat{\beta(Z)}=\text{arg min}_{\beta} L(\beta;Z)$

**Types of Unsupervised Learning:**
- Clustering
	- Map samples $x \in \mathbb{R}^d$ to $f(x) \in \mathbb{N}$
	- Each $k \in \mathbb{N}$ is associated with a representative example $x_{k}\in \mathbb{R}^d$
	- Examples: $K-means$, greedy hierarchical clustering
- Dimensionality reduction
	- Map samples $x \in \mathbb{R}^d$ to $f(x) \in \mathbb{R}^{d'}$, where $d' \ll d$
	- Example: Principal component analysis (PCA)
	- Modern deep learning is based on this idea

**The Clustering Problem:**
- **Input:** Dataset $Z = \{x_{i}\}^{n}_{i=1}$
- **Output:** Model $f(x) \in \{1,\dots,K\}$
	- **Intuition:** Predictions should encode "natural" clusters in the data
	- Here, $K \in \mathbb{N}$ is a hyperparameter
- How to formalize "naturalness"?
	- Using a loss function!

**Clustering Loss:**
- Loss depends on the structure of the data we are trying to capture
- K-Means clustering aims to minimize specific loss over a specific model family

**K-Means Clustering Model Family:**
- **Parameters:** Set of **centroids** $\mu_{j}$ (for $j \in \{1,\dots,K\}$)
	- One for each cluster ($K$ is a hyperparameter)
	- **Intuition:** $\mu_{j}$ is the "center" of cluster $j$
- Given a new example $x$, assign it to the nearest cluster:
	- $f_{\mu}(x)=\text{arg min}_{j}||x - \mu_{j}||_{2}^{2}$
- Can use other distance functions

**K-Means Clustering Loss:**
- Compute MSE of each point in the training data to its centroid
- K-Means clustering chooses centroids that minimize loss of training examples $Z$
- Compute MSE of each point in the training data to its **nearest centroid:**
	- $L(\mu;Z)=\sum_{i=1}^{n}||x_{i}-\mu_{f_{\mu}(x_{i})}||_{2}^{2}$

**K-Means Clustering Summary:**
- **Model Family:** $f_{\mu}(x)=\text{arg min}_{j}||x-\mu_{j}||_{2}^{2}$
- **Loss:** $L(\mu;Z)=\sum_{i=1}^n||x_{i}-\mu_{f_{\mu}(x_{i})}||_{2}^2$
- **Optimizer:**
	- If we know the assignment of points to clusters
	- Mean of point per cluster is the vector that minimizes the squared loss!
	- Without knowledge of true assignments, this optimization is non=convex and has many local optimums
- **Optimizer Solution:** Alternating Minimization
	- Given an initial (potentially random) estimate of means,
	- Find every cluster assignment
	- Recompute means (changing them)
	- Iterate until convergence
![[Pasted image 20241007111030.png]]
Random Initialization
- Sensitive to initialization
- One strategy is to run multiple times with random centroids and choose the model with lowest MSE
- **Alternative:** K-means++
	- Randomly initialize first centroid to some $x \in Z$
	- Subsequently, choose centroid randomly according to $p(x) \propto d_{x}^2$, where $d_{x}$ is the distance to the nearest centroid so far
	- Upweights points that are father from existing centroids

**K-Means++:**
- Probability of choosing a cross is proportional to the square of the distance ($\propto d^2$), this allows elements to be more likely when farther away

**Number of Clusters:**
- As $K$ becomes large
	- MSE becomes small
	- Many clusters -> might be less useful
- Choice of $K$ is subjective
![[Pasted image 20241007113058.png]]


