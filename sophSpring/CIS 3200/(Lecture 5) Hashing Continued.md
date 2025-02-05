**Universal Hash Family**
- Fix any positive integer $m$. Let $H$ be any collection of hash functions such that every $h \in H$ is of the form $h: U \to \{0, 1, \dots, m-1\}$
- Then $H$ is a universal hash family if for every distinct pair of keys $k, l \in U$,
- We have
	- $|\{h \in H | h(k) = h(l)\}| \leq \frac{|H|}{m}$
- **Theorem:** For any positive integer $m$, there exists a universal hash family $H$ that contains $O(M^2)$ hash functions where $M = |U|$.
- Let $P$ be any prime that is longer than $M$ Bu Bertrand-Chebyshev Theorem, there always exists a prime $p \in [M, 2M]$
- $U = \{0, 1, \dots, p-1\}$
- $H = \{h_{ab} | 1 \leq a \leq p-1, 0 \leq b \leq p-1\}$ where
- $h_{ab}^{(x)} = ((ax + b) \mod p) \mod m$
- $|H| = p(p-1) = O(M^2)$

**Claim 1:**
- Fix any 2 distinct keys $k, l$. Then for any $a, b, h'_{ab}(k) \neq h'_{ab}(l)$
- **Proof:** Suppose not. Then for some $a, b, ak + b \equiv al + b (\mod p)$
	- $\implies a(k - l) \equiv 0 (\mod p)$
	- A contradiction!

**Claim 2:**
- Fix any 2 distinct keys $k, l$. Then for any $(a_{1}, b_{1}) \neq (a_{2}, b_{2})$, we have $(h'_{a_{1}b_{1}}(k), h'_{a_{1}b_{1}}(l)) \neq (h'_{a_{2}b_{2}}(k), h'_{a_{2}b_{2}}(l))$
- $(\gamma_{1}, s_{1}) \neq (\gamma_{2}, s_{2})$
- Suppose not. Then
$$
\begin{cases}
a_{1}k + b_{1} = a_{2}k + b_{2} \\
a_{1}l + b_{1} = a_{2}l + b_{2} \\
\implies (a_{1} - a_{2})k = b_{2} - b_{1} \\
\implies (a_{1} - a_{2})l = b_{2} - b_{1} \\
\implies (a_{1} - a_{2})(k - l) = b_{2} - b_{1} \\
\implies a_{1} = a_{2} \\
\implies b_{1} = b_{2}
\end{cases}
$$
- A contradiction!

Fix any 2 distinct keys $k, l$.
$|H| = p(p-1)$
\# of possible $(\gamma, s)$ pairs s.t. $\gamma \neq s$
$p(p-1)$ pairs

A collision occurs if $\gamma \mod m = s \mod m$
$(\gamma, s)$ is a bad pair if $\gamma \mod m = s \mod m$
Fix a value of $\gamma$, say $\gamma = 0$
How many values of $s$ lead $\gamma = 0'$ to collision with $\gamma$?

\# of bad choices of $s \leq \frac{p-1}{m}$
Total \# of bad $(\gamma, s)$ pairs $\leq \frac{p(p-1)}{m}$


### Dynamic Programming
**Subsequence:** Let $x = x_{1}, x_{2}, x_{3}, \dots x_{m}$ be a sequence of $m$ symbols. Let $z = z_{1}, z_{2}, \dots, z_{k}$ be another sequence. Then $z$ is a subsequence of $x$
- If there exist $1 \leq i_{1} < i_{2} < \dots < i_{k} \leq m$ such that
- $x_{i_{1}} = z_{1}, x_{i_{2}} = z_{s}, \dots, x_{i_{k}} = z_{k}$
- **Example:** $x = CADBCD$
- $z = ABCD$
- Then $z$ is a subsequence of $X$; set $i_{1}=2, i_{2}=4, i_{3}=6, i_{4}=7$

#### Longest Common Subsequence (LCS)
- **Input:** A sequence $x = x_{1}x_{2}\dots x_{m}$ and a sequence $y=y_{1}y_{2}\dots y_{n}$
- **Goal:** Find a longest sequence $z$ such that $z$ is a subsequence of both $X$ and $Y$
- Brute Force Enumeration $= O(n_{2}^m)$
- Instead, DP allows for $O(mn)$ runtime

**Parameterization:**
- For $0 \leq i \leq m$, $0 \leq j \leq n$,
- define
	- $c[i, j] =$ length of the LCS of $x_{1}x_{2}\dots x_{i}$ and $y_{1}y_{2}\dots y_{j}$
- Goal: $c[m,n]$
- Base Case:
	- $i=0, c[0,j] = 0$
	- $j=0, c[i,0]=0$
- Claim: For $0 \leq i \leq m, 0 \leq j \leq n$
$$
c[i,j]=\begin{cases}
0 & if i = 0 or j = 0 \\
1 + c[i-1, j-1] & if x_{i}=y_{j} \\
MAX\{c[i-1, j], c[i, j-1]\} & else (i.e. x_{i} \neq y_{j})
\end{cases}
$$
