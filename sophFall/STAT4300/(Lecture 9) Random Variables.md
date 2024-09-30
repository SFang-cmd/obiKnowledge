Ex. Suppose there are $r$ distinct types of coupons and that each time one obtains a coupon, it is, independent of previous selections, equally likely to be any one of the $r$ types
- Let T be the number of coupons that need to be collected until one obtains a complete set of at least one of each type. Find the pmf of T
	- $T \in \{r,r+1,r+2,\dots\}$
	- $P(T=n)=P(T>n-1) - P(T>n)$
	- Let event $A$ be the set of events where $T > n-1$,
	- $B = \{T > n\}$
	- $C = \{T=n\}$
- $P(A) = P(B) + P(C)$
- Let $A_{j}$ be the event that *no type $j$ coupon is among the first $n$ coupons*

**Expectation:**
For a discrete r.v. $X$ with values $x_{i}$, that occur with probabilities $p(x_{i})$, the *expectation (expected value, mean)* of $X$ is
- $E(X)=\mu_{X}=\sum_{i}x_{i}\cdot p(x_{i})$
- The expectation of a r.v. $X$ is the weighted average of the values it can assume, where the weights are the corresponding probabilities of $x_{i}$
- **Gambling Interpretation:** $E[X]$ is the fair price to pay for a return on the game

Why the derivative of n used on (1/(1-q))'