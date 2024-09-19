- For many experiments it is natural to assume that all outcomes in the sample space are equally likely to occur

**Ex 1.**
- You roll a fair die four times. What's the probability that you get at least one six?
	- $1 - (\frac{5}{6})^4$

**Ex 2.**
- Three balls are randomly drawn from an urn containing 6 white an 5 blue balls. What is the probability that one of the drawn balls is white and the other two blue?
	- Unequal outcomes right now, since not the same number of balls
	- Solution? Focus on separate balls:
		- 6 White: $W_{1},W_{2},W_{3},W_{4},W_{5},W_{6}$
		- 5 Blue: $B_{1},B_{2},B_{3},B_{4},B_{5}$
		- Sample space: $(X_{1},X_{2},X_{3})$
		- $N(S) = 11 * 10 * 9$
	- $N(white, blue, blue) = 6 \times 5 \times 4$
		- But we don't care which ball is white, so
	- $N(blue, white, blue) = 6 \times 5 \times 4$
	- $N(blue, blue, white) = 6 \times 5 \times 4$)
	- Thus, $N(1 white + 2 blue) = 6 \times 5 \times 4 \times 3$
		- $3$ is the number of locations the white ball can be
	- $P(1W+2B)=\frac{6 \times 5 \times 4 \times 3}{11 \times 10 \times 9}$

***Counting Properties:***
**Product Rule:**
	- A set of ordered *k-tuples*;
	- If we have $n_{1}$ possible choices for the 1st element; then there are $n_{2}$ possible choices for the second element for **each** choice of the second element, etc.
	- For each choice of the first $k-1$ elements, there are $n_{k}$ choices for the $k$th elements
	- Then there are $n_{1}n_{2}...n_{k}$ total possibilities

Ex 3. Have 4 blood types: A, B, AB, O, equally likely
- What is the probability that the blood types are exactly the same
	- $N(S) = 4^{2}= 16$, $N(same) = 4$

**If "with replacement" is absent, always assume without replacement**

Ex 4. Two balls are drawn at random with replacement from an urn containing 40 balls labeled $1,2,3,...,40$
- What is the probability that
	- The two numbers are the same?
		- $N(S) = 40 \times 40 = 1600$
		- $N(A) = 40$
		- $P(A)=\frac{40}{1600}=\frac{1}{40}$
	- The sum is $30$?
		- For pairs $(X_{1},X_{2})$, first number can be $1-29$, with the second complement being $29-1$, so $P(s30)=\frac{29}{1600}$
	- The product is 30?
		- For pairs $(X_{1},X_{2})$, $(1,2,3,5,6,10,15,30)$ with complements for $X_2$, so total $P(p30=\frac{8}{1600})$
	- The maximum is less than or equal to 10?
		- 10 total for first option, 10 total for second option, so $P(max10)=\frac{100}{1600}$
	- The maximum is 10?
		- First position is $10$, and second position is $1-10$
		- If second $X_{2}$ is guaranteed to be $10$, then $X_1$ can only be $1-9$
		- (don't want to double count)
	- The first number is larger than the second one?
		- If $X_{1}=1$, then $0$ possibilities for the second one, all the way up to $X_{1}=40$, where all $39$ are smaller for the second one, $0+1+2+...+39$
		- Recognize that there are $40$ possible numbers for each, so $1600$ total values. Subtracting the $40$ identical choices, the resulting combinations have half where $X_1$ is greater, and half where $X_2$ is greater: $\frac{1600-40}{2}$

**Birthday Problem:**
- $N(S)=365^{N}$
- $N(A^{c})=N(\text{all distinct})=365 \times 364 \times 363 \times ... \times (365 - (N - 1))$
- $P(\text{at least two people w/ same birthday})=1-\frac{365 \times 364 \times ... \times (365 - (N - 1))}{365^{N}}$

**Permutations**
- An ordered sequence of $k$ distinct objects taken from a set of $n$ distinct objects is called a *permutation* of size $k$
- The total number of permutations of size $k$ from $n$ objects is denoted by $P_{k,n}$ and
	- $P_{k,n}=n(n-1)(n-2)...(n-k+1)=\frac{n!}{(n-k)!}$
- In particular, $P_{n,n})=n!$
- Suppose we have $n$ objects, of which $n_1$ are alike, $n_2$ are alike, ... , $n_{r}$ are alike. 
- Then, the total number of permutations of **all** $n$ objects is
	- $\frac{n!}{n_{1}!n_{2}!...n_{r}!}$

Ex 4. How many different letter arrangements can be formed using the letters *Mississippi?*
$M: 1$
$i : 4$
$s : 4$
$p : 2$
Total: $\frac{11!}{1!4!4!2!}$

**Combinations**
- An unordered subset of size $k$ from a set of $n$ distinct objects is called a *combination*
- The number of combinations of size $k$ from $n$ distinct objects is denoted by $C_{k,n}$ or ${n \choose k}$
	- $C_{k,n}=\frac{P_{k,n}}{k!}=\frac{n!}{k!(n-k)!}$
	- We don't care about order, which means that the set can be chosen in any $k!$ ways

**Be consistent about whether order matters in your problems**

**Properties of Combinations:**
- A combinatorial Identity:
	- ${n \choose k} = {n - 1 \choose k - 1} + {n - 1 \choose k}$
	- If the desired ball is the $k$th item, we just need to choose the remaining $k-1$ items from the rest of the $n-1$ items. If the $k$th item is not the desired ball, then we need to choose $k$ balls from the remaining $n-1$ items.
- The Binomial Theorem:
	- $(x + y)^{n}=\sum\limits_{k=0}^{n}{n \choose k}x^{k}y^{n-k}$
- An Identity:
	- $\sum\limits_{k=0}^{n}{n \choose k} = 2^{n}$


Ex 5. Which of the following two events is more likely?
- Four rolls a die yield of at least one six
- Twenty-four rolls of two die yield at least one double six.
	- $1 - (\frac{5}{6})^4=0.5177$
	- $1 - (\frac{35}{36})^24=0.4914$

Ex 6. Probability that with 2 red balls and 3 blue balls, no 2 red balls are drawn next to each other? Enumerate all possible arrangements:
$RBRBB, RBBRB, RBBBR$
$\frac{6}{5 \choose 2}=\frac{6}{10} = \frac{3}{5}$

Ex 7. Suppose an urn contains $r$ red balls and $b$ blue balls, drawing $r + b$ balls without replacement. What is the probability that no two red balls are drawn consecutively?
- Answer:
	- $P = \frac{b+1 \choose r}{r + b \choose r}$
- Why?
	- For the denominator: imagine the balls can be chosen to slots. Then we need to choose $r$ locations amongst the $r+b$ slots where the red balls can possibly go (mississippi problem)
	- Then for the numerator, imagine there are $b$ blue balls already filled in. Then, there are $b+1$ locations where the red balls can go, where after being occupied, the next red ball cannot be in the same location, so choosing $b+1$ possible locations for $r$

