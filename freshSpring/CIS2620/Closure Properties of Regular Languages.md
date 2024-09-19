**Lemma 1:** (Closure under set complement)
If $L$ is regular, so is $\bar{L}=\Sigma^{*}\backslash L$
(The complement of $L$)
	**Proof:**
	Let $M=(Q,\Sigma,\delta,q_0,F)$ be the [[(Deterministic) Finite Automata]] for $L$
	Then consider $M'=(Q,\Sigma,\delta,q_{0},Q \backslash F)$ (just flipping the accepting states)
	$\forall x, \delta^{*}(q_{0},x)$ (in M) $=\delta^{*}(q_{0},x)$ (in M')
	$\implies x \in L(M)$ iff $x \notin L(M')$

Equivalent lemma: If $L$ is not regular, so is $L\bar{L}$
$\bar{\bar{L}} = L$

**Lemma 2:** If $L_{1},L_{2}$ are regular, so is $L_{1} \cap L_{2}$
		($\subseteq \Sigma^{*}$)
	**Proof:** Let $M_{1}=(Q_{1},\Sigma,\delta_{1},q_{0}',F_{1})$
	$M_{2}=(Q_{2},\Sigma, \delta_{2}, q_{0}^{2},F_{2})$ be the DFA for $L_1$ and $L_2$
	*Goal:* Run $M_1$ and $M_2$ in parallel
	Define $Q:=Q_{1} \times Q_{2}$
	$Q := \{(q_{1},q_{2}): q_{1}\in Q_{1} \text{ and } q_{2}\in Q_{2}\}$
	With this $Q$, define a new automata:
		$M=(Q,\Sigma,\delta,q_0)$
		$q_{0}:=(q_{0}^{1},,,,,,q_{0}^{2})$
	$\delta((p_{1},p_{2}), \sigma)=(\delta(p_{1},\sigma_{1}),\delta_{2}(p_{2},\sigma))$

$F:=F_{1}\times F_{2}$
$:=\{((p_{1},p_{2}):p_{1}\in F_{1} \& p_{2}\in F_{2}\}$

**Claim A:**
$L(M)=L_{1}\cap L_{2}$
**Claim B:**
For all $x \in \Sigma^{*}, p_{1}\in Q, p_{2}\in Q_{2},(\delta^{*}(p_{1},p_{2}),x)=(\delta_{1}^{*}(p_{1},x)), (\delta_{2}^{*}(p_{2},x))$
$p_{1}=q^{0}^{1}, p_{2}=q^{2}_{0}$

