Ex. Suppose $\Sigma = \{0,1\}$. How many [[String]]s are there over $\Sigma$ of length k?
$2^{k}$, since for every element $i$ in $k$, there are exactly 2 possibilities for which [[Alphabet]] character it could be
__
For general $\Sigma$, the size would be $|\Sigma|^k$

Q: How many strings are there over $\Sigma = \{0,1\}$ of length $\leq k$
$2^{0}+2^{1}+2^{2}+...+2^{k}=2^{k+1}-1=2*2^{k}-1$
Of all of the strings of at most $k$, half of them have a length $k$, so most of them have lengths exactly $k$.