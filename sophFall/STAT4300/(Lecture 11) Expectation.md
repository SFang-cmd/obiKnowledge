**Expectation:** Center of a distribution
- $E(X)=\mu_{x}=\sum_{i}x_{i}\cdot p(x_{i})$
**Methods of Indicators:**
- If $X$ is the number of events that occur among some collection of events $A_{1}, \dots, A_{n}$, then
	- $E(X)=P(A_{1})+P(A_{2})+\dots+P(A_{n})$
- For a r.v. $X$ with possible values $\{0,1,2,\dots,n\}$
	- $E(X)=\sum_{j=1}^{n}P(X \geq j)$
- Coin toss game

**Variance:**
- The expected value measures the ***center*** of a probability distribution
- Variance measures the ***variability*** of a distribution
- Let $X$ be a discrete random variable with possible values $x_{i}$ that occur with probabilities $p(x_{i})$ and let $E(X)=\mu$. The *variance* of $X$ is
	- $\sigma^{2}=E \lfloor (\mathbf{X}-\mu)^{2} \rfloor = \sum_{i}(x_{i}-\mu)^{2}\cdot p(x_{i})$
- The variance is the weighted average of the squared deviations of the values of $X$ from their mean $\mu$, where the weights are the corresponding probabilities of each $x_{i}$
- The ***standard deviation $\sigma$*** is the positive square root of the variance of $X$

**Properties:**
- $V(X) = \sigma^{2} = E(X^{2})-[E(X)]^2$
- $V(aX + b) = \sigma^{2}_{aX + b}=a^{2}\cdot \sigma^{2}_{X}$
- $\sigma_{aX + b}=|a| \cdot \sigma_{x}$
In particular, $E(X^{2}) \geq [E(X)]^2$ and
- $\sigma^{2}_{aX}=a^{2}\cdot \sigma^{2}_{X}, \sigma_{aX}=|a|\cdot \sigma_{X},\sigma^{2}_{X + b}=\sigma^{2}_{X}$
If $X_{1},X_{2},\dots,X_{n}$ are independent, then
- $V(X_{1} + X_{2} + \dots + X_{n}) = V(X_{1}) + V(X_{2}) + \dots + V(X_{n})$

**Friendship Paradox:**
- "On average your friends have more friends than you do"
- Imagine there are $n$ people labeled 1,...,n. Let $f(i)$ be the number of friends of *person* $i$, and let $f=\sum_{i=1}^{n}f(i)$
- Let $X$ be a randomly chosen person from $1,\dots,n$ with equal probability. Then $E(f(X))=\sum_{i=1}^{n}f(i)P(X=i)=\frac{f}{n}$
- Suppose each person writes the names of all their friends, with each name written on a separate piece of paper.
- Now, choose a piece of paper at random and let $Y$ be the name on the paper. Note that $P(Y=i) = \frac{f(i)}{f}$, and
	- $E(f(Y))=\sum_{i=1}^{n}f(i)P(Y=i)=\sum_{i=1}^{n} \frac{f^{2}(i)}{f}$
- So, $E(f(Y))=\frac{E(f^{2}(X))}{E(f(X))} \geq E(f(X))$

**Special Discrete Distributions:**
- There are a collection of special discrete distributions:
	- Bernoulli Distribution
	- Binomial Distribution
	- Negative Binomial Distribution
	- Poisson Distribution
	- Hypergeometric Distribution
	- ...

**Bernoulli R.V:**
- Any random variable whose only possible values are $0$ and $1$ is called a Bernoulli random variable
- Example: Toss a coin once. Define:
	- $$X = \begin{cases}
1, & \text{if heads} \\
0, & \text{otherwise}
\end{cases}$$
$$I_{A} = \begin{cases}
1, & \text{if A occurs} \\
0, & \text{otherwise}
\end{cases}$$
**Binomial Experiment:**
- A Binomial Experiment consists of $n$ Bernoulli trials
	1. $n$ trials with $n$ fixed in advance
	2. Each trial has two possible outcomes, "success" (S) and "failure" (F)
	3. The probability of success, *p*, is constant from one trial to the next
	4. The trials are independent, the outcome of each trial is independent of the outcome of other trials
- **The Experiment:** Randomly draw $n$ balls with replacement from an urn containing 10 red balls and 20 blue balls
	- Use $S$ to denote the outcome red ball and $F$ to denote the outcome blue ball
	- Then this is a binomial experiment with $p=\frac{1}{3}$

**Binomial RV & Binomial Distribution**
- Given a binomial experiment consisting of $n$ trials, the number of successes $X$ among the $n$ trials is called a binomial random variable with parameters $(n,p)$
- A Bernoulli rv is a binomial rv with parameters $(1,p)$
- The pmf of a binomial rv $X$ is denoted by $b(x;n,p)$


**Ex.**
- What is the change that among $5$ families, each with $6$ children, exactly $3$ of the families have $4$ or more boys?
	- (Assuming boys and girls are equally likely)
- The probability of any particular family has $4$ or more boys is $p=\frac{11}{32}$, so
	- $P(3successes)={5 \choose 3}\cdot \left( \frac{11}{32} \right)^{3}\cdot \left( \frac{21}{32} \right)^{2}=0.175$

**Negative Binomial Distribution**
- The experiment consists of a sequence of independent trials
- 