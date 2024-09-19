Using [[Extended Transition Function]]

**Claim:**
$L(M_0)=L_{0}=\{x \in \{0,1\}^{*}: x \text{ ends in 11}\}$

To prove the [[(Deterministic) Finite Automata]] (Example 2 [[Finite Automata Example]] satisfies this condition, prof proved the following Lemma:
**Lemma:** $$\delta^{*}(q_0,x)=
\{\begin{align*} q_{0} \text{ if } x=\epsilon \text{ ends in 0}\\
q_{1} \text{ if } x=1 \text{ ends in 01}\\
q_{2} \text{ if } x \text{ ends in 11}
\end{align*}
$$
*Keep in mind:* $\epsilon$ is the Empty [[String]]

To prove the Lemma, apply an induction on the length of $x$:
**Base Case:** $|x|=0$, i.e. $x = \epsilon$
$\delta^{*}(q_0,x)=q_0$
	In this case, the condition is satisfied

**Induction Step:**
$x=y \sigma$

**Case:**
$\delta^{*}(q_0,x)=\{q_{0},q_{1},q_{2}\}$
$\sigma=\{0,1\}$

Suppose $\delta^{*}(q,y)=q_{0}, \sigma=0$
$\delta^{*}(q_{0},x) = \delta(q_{0},0)=q_{0}$
By induction, $y = \epsilon$ or  $y$ ends in 0
	$\implies x$ ends in $0$

Case 2:
$\delta^{*}(q_{0},y)=q_{1},\sigma=1, \delta^{*}(q_{0},x)=\delta(\delta^{*}(q_{0},y),1)=\delta(q_{1},1)=q_{2}$
By induction hypothesis, $y=1$ or $y$ ends in $01$, thus $y$ ends in $1$
$x=y\sigma$ $\implies x$ ends in $11$, since $\sigma = 1$

