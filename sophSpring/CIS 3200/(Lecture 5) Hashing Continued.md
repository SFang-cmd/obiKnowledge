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
\implies (a_{1} - a_{2})l = b_{2} - b_{1}
\end{cases}
$$