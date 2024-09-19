**Recall:** Linear Classifier
**TODO:**
1. Define a **loss function** that quantifies our unhappiness with the scores across the training data
2. Come up with a way of efficiently finding the parameters that minimize the loss function **(optimization)**

**Loss Function:** A function that will quantify how good or bad a set of weights is $W$
Example:
![[Pasted image 20240521144331.png]]
- Note the $W$ is a specific set of weights, which will output a $3 \times 1$ vector of values for each class
- Here, the **loss function** tells how good our current classifier is
- Given a dataset of examples, $\{(x_{i},y_{i})\}_{i=1}^{N}$
	- Where $x_{i}$ is image and $y_{i}$ is (integer) label
	- Loss over the dataset is a sum of loss over examples:
	- $L=\frac{1}{N}\sum\limits_{i}L_{i}(f(x_{i},W),y_{i})$

For **Multiclass SVM loss:**
- Given an example $(x_i,y_i)$ where $x_i$ is an image and $y_{i}$ is an integer label and where $s = f(x_i,W)$
- The SVM loss has form:
$$\sum\limits_{j \neq y_{i}}\cases{0 ,\text{if $s_{yi} \geq s_{j}+1$}\\
s_{j}-s_{yi}+1, \text{Otherwise}
}$$

![[Pasted image 20240521145414.png]]

**Comprehension Questions:**
1. What happens to loss if car scores decrease by 0.5 for this training example?
	1. Nothing, loss does not hinder the fact that car is still greater than the other classes
2. **What is the min/max possible SVM loss $L_{i}$?**
	1. Min possible loss is $0$
	2. Max possible loss is infinity
3. At initialization W is small so all $s \approx 0$. What is the loss $L_{i}$ assuming $N$ examples and $C$ classes?
	1. $N-1$, since there are $N-1$ incorrect classes, since there is only one correct classes, so we add the margin value $1$.
	2. Good for debugging, since this is what it should look like at the beginning
4. What if the sum was over all classes (including $j=y_{i}$?
5. What if we used mean instead of sum?
	1. Nothing, since we change the scores by a constant
6. What if instead we used $L_{i}=\sum\limits_{j\neq y_i}\text{max}(0,s_{j}-s_{y_{i}}+1)^2$
	1. Can be useful to differentiate extreme examples, things that are good are REALLY good and things that are bad are REALLY bad.

**Multiclass SVM Loss: Example Code**
![[Pasted image 20240521150127.png]]
- Note that you "zero out" the desired value $y$

E.g. suppose that we found a $W$ such that $L=0$. Is this $W$ unique?
- **No**, $2W$ is also $L=0$
- However, problem is that we don't want to fit training data

**We care about this classifier on test data, so having a $2W$ should have the same result as $W$**.

**Data loss:** Model predictions should match training data; problem of **overfitting**
- Instead, we add a **Regularization** function, that makes the model "simpler"
- **Occam's Razor:** Among competing hypotheses, the simpler one is often the correct answer
- $L=\frac{1}{N}\sum\limits_{i}L_{i}(f(x_{i},W),y_{i}) + \lambda R(W)$

*Regularizations in common use:*
- **L2 Regularization:** $R(W)=\sum\limits_{k}\sum\limits_{l}W_{k,l}^2$
- L1 Regularization: $R(W)=\sum\limits_{k}\sum\limits_{l}|W_{k,l}|$
- $L2$ Regularization prioritizes normalizing the weights, if the weights are closer together, $R(W)$ will be smaller

**Another Loss Function:**
**Softmax Classifier** (Multinomial Logistic Regression):
- Multiclass SVM did not have too much interpretation toward what the scores mean
- But for softmax,
	- SCORES = Unnormalized log probabilities of the classes
	- $s = f(x_i;W)$
	- $P(Y=k|X=x_{i})=\frac{e^{s_k}}{\sum\limits_{j}{e^{s_{j}}}}$
	- Want to maximize the log likelihood, or (for a loss function) to minimize the negative log likelihood of the correct class:
	- $L_{i}=-log(P(Y=y_{i}|X=x_{i}))$
	- $L_{i}=-log(\frac{e^{s_{y_{i}}}}{\sum\limits_{j}e^{s_{j}}})$
	- ![[Pasted image 20240521152344.png]]

**SVM vs. Softmax:**
![[Pasted image 20240521152437.png]]

**Recap:**
- We have some dataset of $(x,y)$
- We have a **score function:** $s=f(x;W)=Wx$
- We have a **loss function:**
- **Goal:** Minimize the loss function
![[Pasted image 20240521152846.png]]

