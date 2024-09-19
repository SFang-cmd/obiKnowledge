Q1. How many different ways of putting *n* different balls into *k* distinct boxes? (without restrictions)
- For each of the n balls, there are $k$ different boxes to put each of the balls, so $k^n$

*Q1'. What if only putting $s$ of the $n$ different balls into the $k$ distinct boxes?* 
- First, need to choose which balls will be used (since balls are different), so ${n \choose s}$, then multiply by the $k^s$, the same as last problem

Q2. How many different ways of putting $n$ different balls into $k$ distinct boxes with the respective sizes $n_{1},n_{2},...,n_{k}$ where $\sum n_{i}=n$?
- For first box, chose $n_{1}$ different balls to put there, then for second box, there are ${n - n_{1}\choose n_2}$
- Simplifies to: $\frac{n!}{n_{1}!n_{2}!...n_{k}!}$
- These are called the multinomial coefficients

Q2': What if only putting $n*$ of the $n$ different balls into the $k$ distinct boxes with the respective sizes $n_{1},n_{2},...,n_{k}$, where $\sum n_{i}=n*$?
- Visualization: Imaging we have n boxes: 1, 2, 3, ..., n*, n* + 1, ... n
	- Boxes: n_1, n_2,..., n_k, with final additional box $n - n*$
- So for first box, choose $n_{1}$ balls, then choose $n_2$ balls from $n - n_{1}$ balls for box $2$, then for the final box, choose the last $n - (n_{1} + ... + n_{k})$ balls (since we know the last box has the remaining balls that weren't chosen) and choose $n_{k+1}$, but the last additional box, you're choosing everything from the remaining balls, so then simplifies to 1.
- ${n \choose n_{1}}{n-n_{1} \choose n_2}...{n-(n_{1}+n_{2}+...+n_{k-1})\choose n_{k}}{n-n* \choose n-n*}$

Q3: How many different ways of putting $n$ identical balls into $k$ distinct boxes?
- Complicated, instead look at question 4
- This is equivalent to having $n+k$ balls, and choosing how to separate them into $k$ distinct boxes, since we can then procedurally remove the $k$ extra balls that correlate with the $k$ boxes, thus leaving some boxes empty.
- $P = {n+k-1 \choose k-1}$

Q4: How many different ways of putting $n$ identical balls into $k$ distinct boxes so that *each box contains at least one ball*?
- Box & Stars:
	- If each box has at least one ball, this is identical to asking "how many dividers can $k-1$ lines go between the $n-1$ balls"?
	- This ensures that each divider can only go between two balls once, so each divider must have one ball within
- ${n-1 \choose k-1}$

Revisit: An urn contains $r$ red balls and $b$ blue balls with $r \leq b+1$. All $r+b$ balls are drawn from the urn randomly without replacement. What is the probability that no two red balls are drawn consecutively?
- $P = \frac{b+1 \choose r}{r+b \choose r}$
- Alternate thought process:
	- Want $x_{1}+x_{2}+...+x_{r}+x_{r+1}=b$ total number of blue balls
	- Also want $x_{1}\geq 0, x_2$
	- The number of ways to arranging the blue and red balls such that no two balls are together
- Think of it this way: there are $b$ blue balls that need to be put into $r + 1$ categories (since we want to insert the $r$ slots such that each one has a blue ball), so there are ${b+1 \choose r}$ different ways to do this, because there are $b+1$ slots that the red balls can go into, and $r$ different "stripes" to place
- For the total, there are $r + b$ total balls using our previous strategy, which means that two different boxes can have no balls, so ${r+b \choose r}$

Q6. What is the probability that each pair of red balls is separated by at least 2 blue balls?

We know that 
$$
\begin{cases}
x_{1}+...+x_{k}=n \\
x_{1},...,x_{k}\geq 1
\end{cases}
= {n-1 \choose k-1}
$$
And
$$
\begin{cases}
x_{1}+...+x_{k}=n \\
x_{1},...,x_{k}\geq 0
\end{cases}
= {n+k-1 \choose k-1}
$$

So
$$
\begin{cases}
x_{1}+x_{2}+...+x_{r}+x_{r+1}=b \\
x_{1} \geq 0, x_{2},...,x_{r}\geq 2, x_{r+1} \geq 0
\end{cases}
$$
This states that there are a total of $b$ balls in each of the $x_1,...,x_{r+1}$ dividers, and based on the problem, if we want it to be separated by 2 blue balls, then we can apply a mapping to make all $x_i$ values into $y_{i}=1$:
$Let \; y_{1}=x_{1}+1, y_{2}=x_{2}-1,...,y_{r}=x_{r}-1, y_{r+1}=x_{r+1}+1$
$$
\begin{cases}
y_{1}+y_{2}+...+y_{r}+y_{r+1}=b+2-(r-1)=b-r+3 \\
y_{1},...,y_{r+1}\geq 1
\end{cases}
$$
(derived from the mapping)
So then, the solution is
${b - r + 3 - 1 \choose r + 1 - 1}={b - r + 2 \choose r}$

Ex. Seating Mixup
- Suppose that Yankee Stadium is completely sold out, but when the ticket holders arrive, they choose seats entirely at random
- What is the probability that *at least one person is seated in the seat indicated by his/her ticket?*

Ex. A Card Game
- Take two full decks of cards, shuffle them, and ask your friend to deal cards face-up slowy, one at a time, at the same time you do the same with the other shuffled deck
- You bet your friend that there will be at least one exact match in the dealt cards. ("Exact" means both suit and rank)
- Suppose you are betting money and offer your friend an even bet, **should your friend take the bet?**

**Inclusion-Exclusion Principle**
- For any $n$ events $A_{1},A_{2},...,A_{n}$,
	- $P(A_{1}\cup A_{2} \cup ... \cup A_{n})=\sum\limits_{i=1}^{n}P(A_{i})-\sum\limits_{i_{1}<i_{2}}P(A_{i_{1}}\cap A_{i_{2}})+...$
	- $+(-1)^{k+1}\sum\limits_{i_{1}<i_{2}<...<i_{k}}P(A_{i_{1}}\cap A_{i_{2}}\cap A_{i_{3}})+...+(-1)^{n}P(A_{i_{1}}\cap A_{i_{2}} \cap A_{i_{3}} \cap ... \cap A_{i_{n}})$

Suppose that each of $n$ men at a party throws his hat into the center of the room. The hats are first mixed up, then each man randomly selects a hat. What is the probability that
(a) none of the men selects his own hat?
- Complement - At least one of the men select his hat:
- Denote by $A_{i}$ the event that the $i$th man selects his own hat. Then $P(A_{1}\cup A_{2}\cup...\cup A_{n})$, the probability of at least one of them selects his own hat, is given by
	- $P(A_{1}\cup A_{2}\cup ... \cup A_{n})$
	- The probability that all of the men selecting their own respective hats is:
		- $P(A_{i_{1}}\cap A_{i_{2}}\cap ...\cap A_{i_{k}})=\frac{(n-k)!}{n!}$
		- since there are $n$ people, total possibility of choosing hats is $n!$
		- For the top, for the first $k$ people, they must choose the correct hats. For the rest of the $n-k$ people, we don't care which hats they get
	- Then, there are $n\choose k$ total number of ways to get $k$ people for their probabilities, which would then result in the correct number needed for the Inclusion/Exclusion principle
- Answer is: $1-1+\frac{1}{2!}-\frac{1}{3!}+...+(-1)^{n}\frac{1}{n!}+...$
(b) Exactly $k$ people selected their own hats?
- 