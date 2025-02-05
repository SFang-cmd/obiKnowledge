### LCS Problem
**Input:** A sequence $x = x_{1}x_{2}\dots x_{m}$, and a sequence $y=y_{1}y_{2}\dots y_{n}$
**Goal:** Output a longest common subsequence of $X$ and $Y$
- Focus on computing the length
- Parametrize the problem
$C[i,j]=$ length of LCS of $0 \leq i \leq m$, $x_{1}x_{2}\dots x_{i}$ and $0 \leq j \leq n$, $y_{1}y_{2}\dots y_{j}$
**Goal:** Compute $C[m,n]$
Claim: For $0 \leq i \leq m, 0 \leq j \leq n$
$$
c[i,j]=\begin{cases}
0 & if i = 0 or j = 0 \\
1 + c[i-1, j-1] & if x_{i}=y_{j} \\
MAX\{c[i-1, j], c[i, j-1]\} & else (i.e. x_{i} \neq y_{j})
\end{cases}
$$

**Proof:**
- Let $z_{1}z_{2}\dots z_{k}$ be a LCS of $x_{1}x_{2}\dots x_{i}$ and $y_{1}y_{2}\dots y_{j}$
- **Case 1:** Done
- **Case 2:** $x_{i}=y_{j}$, it must be the case that $z_{k}=x_{i}=y_{j}$
	- $\implies c[i,j]=1 + c[i-1,j-1]$
- **Case 3:** $x_{i} \neq y_{j}$, it must be the case that either $x_{i} \neq z_{k}$ or $y_{j} \neq z_{k}$ (or both)
	- so we check the subsequence before for both the first and second sequences, and we choose the one that produces the max value
	- $\implies c[i,j]=MAX\{C[i-1, j], C[i, j-1]\}$
	- 