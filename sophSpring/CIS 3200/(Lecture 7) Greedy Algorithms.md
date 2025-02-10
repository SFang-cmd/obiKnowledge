### Coin-changing Problem
- **Input:** $k$ coin denominations, say, $d_{1}, d_{2}, \dots, d_{k}$ where each $d_{i}$ is a positive integer. Also, you are given a positive integer $n$.
- **Goal:** Make change for $n$ using a smallest \# of coins
- **Example:** $d_{1}=1, d_{2}=10, d_{3}=15$
	- $n=20$
	- Greedy => 6 coins
	- Optimal solution => 2 coins (10 + 10)

**Goal:** Design an $O(nk)$ time dynamic programming algorithm for this problem
- $T[p]=$ smallest \# of coins needed to make change for $p$ ($0 \leq p \leq n$)

**Base Case:** $T[0] = 0$

**General Case:**
$$
T[p] = \begin{cases}
+\infty & \text{if } p > 0 \text{ and } \forall i, d_{i} > p \\
min_{i} \{1 + T[p - d_{i}]\} & \text{s.t. } d_{i} \leq p
\end{cases}
$$

### Fractional Knapsack
- **Input:** A set of $n$ items where each item $i$ has a positive integer profit $p_{i}$ and a positive integer weight $w_{i}$. You are also given a knapsack capacity $W$

#### Feasible Solution Vector
- A feasible solution is a vector $\bar{x}=(x_{1}x_{2}\dots x_{n})$ such that
	- (i.) $\forall i \in [1\dots n]$, $0 \leq x_{i} \leq w_{i}$, and
	- (ii.) $\sum_{i=1}^{n}x_{i} \leq W$
- Goal: Find a feasible solution vector $\bar{x}$ that maximizes $\sum_{i=1}^{n}x_{i}(\frac{p_{i}}{w_{i}})$

### A Greedy Algorithm
- Sort the items in decreasing order of profit/weight
- Assume from here on that
$\frac{p_{1}}{w_{1}} \geq \frac{p_{2}}{w_{2}} \geq \dots \geq \frac{p_{n}}{w_{n}}$

#### Initialization
- $R=W_{i}$
- $x_{1}=x_{2}=\dots =x_{n}=0$;
- We will process items in the order $1,2,\dots,n$

#### Processing of item i
- If $R \geq w_{i}$ then
- {
	- $x_{i}=x_{i} + w_{i}$;
	- $R = R - w_{i}$;
- }
- else
- {
	- $x_{i}=x_{i} + R$;
	- $R=0$
- }

**Runtime:** $O(n\log n)$ time
**Claim:** The solution vector $\bar{x}$ produced by greedy algorithm is optimal

**Proof:**
- Let $\bar{y}=(y_{1}y_{2},\dots,y_{n})$ be an optimal solution vector
- If $x_{1}=y_{1}, x_{2}=y_{2},\dots,x_{n}=y_{n}$, then $\bar{x}$ is also optimal. If this is not the case, then there is an index $i$ s.t. $x_{i} \neq y_{i}$. Choose $i$ to be the smallest index s.t. $x_{i} \neq y_{i}$
- $x_{1}=y_{1}, x_{2}=y_{2}, \dots, x_{i-1}=y_{i-1}, x_{i} \neq y_{i}$

**Observation:** $x_{i} > y_{i}$ (by Greedy's allocation rule)
- w.l.o.g assume $\sum_{i=1}^{n}x_{i}=\sum_{i=1}^{n}y_{i}=W$
- We **will** create another optimal solution
- $z=(z_{1}z_{2}\dots z_{n})$ such that
	- $x_{1}=z_{1}, x_{2}=z_{2},\dots, x_{i}=z_{i}$
- let $\Delta = x_{i} - y_{i}$

**Stuff:**
- $\bar{x}=x_{1}x_{2}\dots x_{i}x_{i+1}\dots x_{n}$
- Equals
- $\bar{y}=y_{1}y_{2}\dots y_{i}y_{i+1}\dots y_{n}$
- Equals
- $\bar{z}=z_{1}z_{2}\dots z_{i}z_{i+1}\dots z_{n}$
	- $\Delta = x_{i} - y_{i}$
	- $\sum_{j=i+1}^{n}y_{j} - \sum_{j=i+1}^{n}x_{j} = \Delta$
- Profit of $\bar{z} \geq$ Profit of $\bar{y}$
- =>$\bar{z}$ is also an optimal solution

**Knapsack Algorithm:** $O(nW)$ time
**Fractional Knapsack:** $O(n\log n)$ time

**Primality Testing:**
- **Input:** A positive integer $n$
- **Goal:** Decide if $n$ is a prime number
- $O(n)$ time
- 

