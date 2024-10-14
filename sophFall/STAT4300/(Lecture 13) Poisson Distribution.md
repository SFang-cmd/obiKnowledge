- Examples: The number of customers per unit of time at a cashier's counter in a bank
- The number of patients admitted per day to the emergency room of a hospital
- The number of accident claims per day by an auto insurance company
- The number of cars passing a traffic intersection per unit time during the rush hour

**The Poisson Experiment:** 
- The experiment consists of counting the number (*X*) of times a certain event occurs during a given unit of time
- The probability the event occurs in a given unit of time is the same for all units
- The number of events that occur in one unit time is independent of the number that occur in other units

**Definition:**
- A r.v. $X$ taking on one of the values $0,1,2,\dots$ is said to have Poisson distribution with parameter $\lambda$ if the pmf of $X$ is given by
	- $p(x;\lambda) = \frac{e^{-\lambda}\lambda^{x}}{x!}, x = 0,1,2,\dots$
	- for some $\lambda > 0$
- Mean & Variance: $E(X) = V(X) = \lambda$

**Example:**
- The number $X$ of customers arriving at a cashier's counter in a bank follows (approximately) a Poisson distribution with the rate of 2 per minute
- What's the chance that in a given minute the number of arrivals will exceed 4?
- Can you tell the manager that the number of arrivals will rarely exceed 4 per minute?

**Stats Midterm Important Topics:**
- Rules of Probability
- Sample space with equally likely outcomes
	- Counting techniques
	- Inclusion-exclusion principle
- Conditional probability
	- Law of total probability
	- Bayes rule
	- Independence
- Probability distributions
	- pmf
	- Expectation & variance
	- Method of indicators

**Problems:**
- Draw red or blue balls (how likely are the red balls separated by at least one/two blue balls?)
- Draw two balls one by one, what is the probability that the second ball is blue? Take divide into two cases where the first ball is either red or blue (total probability)

**Special Distributions:**
- Binomial Distribution: $b(x;n,p)={n \choose x}p^{x}(1-p)^{n-x}, x = 0,1,2,\dots$
	- Mean & Variance: $E(X)=np, V(X)=np(1-p)$
	- Bernoulli distribution
- Negative Binomial: $nb(x;r,p)={x-1 \choose r-1}p^{r}(1-p)^{x-r}, x = r, r+1,\dots$
	- Mean & Variance: $E(X)=\frac{r}{p}, V(X)=\frac{r(1-p)}{p^{2}}$
	- Geometric distribution
- Hypergeometric Distribution:
	- $h(x;n,M,N)=\frac{{M \choose x}{N-M \choose n-x}}{N \choose n}, \text{max}(0,n - N + M) \leq x \leq \text{min}(n, M)$
	- Mean & Variance: $E(X)=n \cdot \frac{M}{N}, V(X) = (N-n)$
	- 