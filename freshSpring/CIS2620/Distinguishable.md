**Definition:**
For any language $L \subseteq \Sigma^{*}$, two strings $x,y \in \Sigma^{*}$ are said to be distinguishable w.r.t. $L$ if $\exists z \in \Sigma^{*}$ s.t. exactly one of $xz$ and $yz$ are in $L$. If no such $z$ exists, then $x$ and $y$ are indistinguishable

Related to [[Regular Languages]]

(Intuition:)
**Claim:**
If $x \in L$ and $y \notin L$, then $x$ and $y$ are distinguishable
**Proof:**
Take $z=\epsilon$, then automatically, the condition is satisfied

Example:
Consider the strings $0$ and $00$. They are distinguishable with respect to $L_{left2}$, since you can append $z=1$. This will result in $0z=01 \in L_{left2}$, while $00z = 001 \notin L_{left2}$

Consider instead the strings $0$ and $1$. Then $0$ and $1$ are indistinguishable with respect to $L_{left2}$, $\forall z$ 2nd bit of $0z=$ 2nd bit of $1z=$ 1st bit of $z$

Essentially, we are creating partitions of the Language by separating them into distinguishable parts

Indistinguishability is an [[Equivalence Relation]], since they are all in the same group, thus having transitivity, etc.

**Lemma:**
Given a language $L \subseteq \Sigma^{*}$, if there are $k$ strings, $x^{1},x^{2},...x^{(k)},$ $x^{(i)}, x^{(k)} \in \Sigma^{*}$ s.t. $\forall i \neq j, x^{(i)}\&x^{(j)}$ are distinguishable, then any DFA for $L$ would require at least $k$ states

**Proof:**
Suppose $M$ is a DFA for $L$. $M=(Q,\Sigma,\delta,q_{0},F)$
$q_{i}:=\delta^{*}(q_{0},x^{(i)})$. For any $i \neq j, \exists z$ s.t. $x^{(i)}z \in L \& x^{(j)}z \notin L$
$\delta^{*}(q_{0},x^{(i)}z)=\delta^{*}(q_{i},x^{(i)}z) \in F$
$\delta^{*}(q_{0},x^{(i)}z)=\delta^{*}(q_{j},x^{(i)}z) \notin F$
Since the two extended transition functions evaluate to different $x$'s, this means that they must be different states, thus
$\implies q^{(i)}\neq q^{(j)} \implies |Q| \geq k$

Back to [[Calculation of Non-Regular Languages]]

**Corollary:**
If for a language $L$, there exists a sequence $\{x^{(l)}\}^{\infty}_{l=1}$ of strings s.t. $\forall i \neq j, x^{(i)} \& x^{(j)}$ are distinguishable. Then $L$ is not regular

**Proof:**
Suppose $L$ is regular $\implies \exists DFA(M) s.t. L=L(M)$
Suppose $M$ has $k$ states, Consider the strings $x^{(i)},...,x^{(k+1)}$. They are pairwise distinguishable w.r.t $L \implies \text{any DFA for } L \geq k+1 \text{ state.}$
