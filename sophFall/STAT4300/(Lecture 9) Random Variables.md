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

**Addition Rule for Expectation:**
- For two random variables $X$ and $Y$,
	- $E(X + Y)=E(X) + E(Y)$
- In general, for $X_{1},\dots,X_{n}$, however dependent,
	- $E(X_{1} + X_{2} + \dots + X_{n})=E(X_{1}) + E(X_{2}) + \dots + E(X_{n})$

Ex. A box contains $n$ ropes. Each time two loose ends are randomly chosen and tied up.
- What is the expected number of loops when the process finishes?
- What is the approximate value when $n$ is large?

Expected number of loops:
- Begin with $2n$ loose ends
- Reduce the \# of loose ends by $2$ at each step
- $X_{i}=\#$ loose ends formed at the $i$th step
- So $X_{1}$, only loops if you tie the first string with itself: $\frac{2n}{2n(2n-1)}=\frac{1}{2n-1}$
- For $X_{2}$, 1 only if $\frac{2n-2}{(2n-2)(2n-3)}=\frac{1}{2n-3}$
- For $X_{i}$, 1 only if $\frac{1}{2n-2(i-1)-1}$
- $X=$ the total number of loops after **n steps**
- $X=X_{1}+X_{2}+\dots+X_{n}$
- $E(X)=E(X_{1})+E(X_{2})+\dots+E(X_{n})=\frac{1}{2n-1}+\frac{1}{2n-3}+\dots+\frac{1}{3}+1$
what is the approximate value when $n$ is large?
$H_{n}=1+\frac{1}{2}+\frac{1}{3}+\dots+\frac{1}{n}\approx \ln(n)$
$1+\frac{1}{2} + \frac{1}{3} + \dots + \frac{1}{2n} \approx \ln(2n)$
$\frac{1}{2}H_{n} = \frac{1}{2} + \frac{1}{4} + \frac{1}{6} + \dots + \frac{1}{2n} \approx \frac{1}{2}\ln(n)$
$\left( 1 + \frac{1}{3} + \dots + \frac{1}{2n-1} \right) + \left( \frac{1}{2} + \frac{1}{4} + \dots + \frac{1}{2n} \right)=\frac{1}{2}(\ln(n))$


