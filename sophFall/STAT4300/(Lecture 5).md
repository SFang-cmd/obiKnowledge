**Increasing/Decreasing Sequence**
- A sequence of events $A_{1},A_{2},...,A_{n}$ is said to be an *increasing sequence* if
	- $A_{1}\subset A_{2}\subset ... \subset A_{n} \subset ...$
- Whereas it is a decreasing sequence otherwise
- If $\{A_{n}, n\geq 1\}$ is increasing, we define a new event
	- $\lim_{n\rightarrow\infty}A_{n}=\cup_{k=1}^{\infty}A_{k}$
	- Why? Because if we union everything before $n$, then all prior elements must be inclosed within the next, so the total event outcomes will be only the same as the final event outcome possibilities as $n$ approaches infinity
- $P(\lim_{n\rightarrow\infty}A_{n})=P(\cup_{n=1}^{\infty}B_{n})=\sum\limits_{n=1}^{infty}P(B_{n})$
- $=\lim\sum\limits_{k=1}^{n}P(B_{k})=\lim_{n=\infty}P(\cup_{k=1}^{n}B_{k})=\lim_{n\rightarrow \infty}P(A_n)$
- Back to [[(Lecture 1) Introduction to Probability]] example:
	- Suppose we have an infinitely large urn and an infinite collection of balls labeled 1,2,3,...
- Question of interest:
- ![[Pasted image 20240916125254.png]]
- For these two, first one there are infinite balls left, since 1-9 are kept, etc.
- For the second one, nothing left because we know the exact time that each ball is getting removed
	- For an urn, at 1 minute to 12pm, balls numbered 1-10 are placed in the urn, and a ball is randomly selected and withdrawn, same happens for 11-20 at 30 seconds to 12pm, and so on
	- In this case, how many balls are in the urn at 12pm?
		- Answer: With probability 1, the urn is empty at noon
	- Solution:
		- Let $A$ be the event that the urn is not empty at noon, and
		- Let $A_{n}$ be the event that ball \#n remains in the urn at noon
		- Then, $A = A_{1}\cup A_{2}\cup ... \cup A_{n}\cup ...$
		- First focus on a given ball, say ball #1. Denote by $A_{1,k}$ the event that ball #1 is in the urn right after the $k$-th round
		- Clearly, $A_n$ is a decreasing sequence, since
			- $A_{1,1}\subset A_{1,2}\subset ... \subset A_{1,k} \subset ...$
		- and $A_{1}=\lim_{k\rightarrow \infty}A_{1,k}$ and hence
			- $P(A_{1})=\lim_{k \rightarrow \infty} P(A_{1,k})$
		- Thus, for any $k$,
			- $P(A_{1,k})=\frac{9 \times 18 \times 27 \times ... \times (9k)}{10 \times 19 \times 28 \times ... \times (9k + 1)}$
			- Limit is hard here, so instead look at $\frac{1}{p_{k}}$
			- $\frac{1}{p_{k}}=\frac{10 \times 19 \times 28 \times ... \times (9k+1)}{9 \times 18 \times ... \times (9k)}$
			- $=(1 + \frac{1}{9})(1 + \frac{1}{18})...(1 + \frac{1}{9k})$
			- $\geq 1 + \frac{1}{9} + \frac{1}{18}+...+ \frac{1}{9k}$
			- $=1 + \frac{1}{9}(1 + \frac{1}{2} + ... + \frac{1}{k})$
			- Which approaches infinity, due to infinite series as $k \rightarrow \infty$
		- Hence, $p_{k}\rightarrow 0$ as $k \rightarrow \infty$
		- Therefore, $P(A_{1})=\lim_{k\rightarrow\infty}P(A_{1,k})=0$
		- Thus,
			- $P(A)=P(A_{1}\cup A_{2}\cup ... \cup A_{n}\cup ...) \leq \sum\limits_{n=1}^{\infty}P(A_{n})=0$
		- Thus, the probability that the urn is empty at noon is 1.

**Chapter 3: Conditional Probability**
**Conditional Probability:** The probability of an event measures how often it will occur
- A *conditional probability* predicts how often an event will occur **under specified conditions**
- Notation: $P(A|B)=$ the conditional probability that event $A$ occurs, given that event $B$ has occurred
$P(A|B)=\frac{P(A \cap B)}{P(B)}$

**Multiplication Rule:**
- Conditional Probability:
	- $P(A|B)=\frac{P(A\cap B)}{P(B)}$
- Multiplication Rule: For any two events $A$ and $B$,
	- $P(A\cap B) = P(A)P(B|A)$
- More generally,
	- $P(A_{1}\cap A_{2}\cap ... \cap A_{n})=P(A_{1})P(A_{2}|A_{1})...P(A_{n}|A_{1}...A_{n-1})$

**The Law of Total Probability:**
Suppose that the events $A_{1},A_{2},...,A_{n}$ are a partition of the sample space $\Omega$. That is, $A_{1}, A_{2},...,A_{n}$ are mutually exclusive and $\cup A_{i}=\Omega$, Then for any event B,
- $P(B) = P(B|A_1)P(A_{1})+...+P(B|A_{n})P(A_{n})$

**Example:** Which Box
- Suppose 3 boxes, where Box $i$ has $i$ white balls and $1$ black ball, $i=1,2,3$
- Then, $W=$ the ball is white
- $A_{i}=$ the ball is from $\#i, i=1,2,3$
- $A_{1},A_{2},A_{3}$ form a partition
- $P(W)=P(W|A_{1})P(A_{1})+P(W|A_{2})P(A_{2})+P(W|A_{3})P(A_{3})$
- $=\frac{1}{2}\cdot \frac{1}{3} + \frac{2}{3}\cdot \frac{1}{3}+\frac{3}{4}\cdot \frac{1}{3}$
- 