## Problem Spec
**Input:** A complete undirected graph $G(V,E)$ with a non-negative cost function $c$ on the edges that satisfies ***triangle inequality*** (i.e. $\forall x,y,z \in V$, $c(x,z) \leq c(x,y) + c(y,z)$)

**Goal:** Design a 2-approximation algorithm to find a minimum cost TSP tour

## 2-Approximation Algorithm
- Initialize a linked list $L = \phi$
- Find a MST $T$ of $G$ with respect to the cost function $c$
- Do a DFS traversal of T, starting at an arbitrary vertex $s$. Whenever DFS visits a vertex $v$, add $v$ to the end of the list $L$. This is done both when a vertex is visited for the first time, and when we backtrack a vertex
- The list $L$ contains all vertices at least once but some many times. Shortcut $L$ to eliminate repeated recurrences

**Observation 1:** Cost of MST T $\leq$ Cost of Optimal TSP Tour
**Proof:** Given any TSP tour $C$, we can get a spanning tree by deleting any one edge from $c$

**Observation 2:** Total cost of visiting all vertices in the order given by $L$, before any shortcutting, is $\leq 2*MST\;cost)$
**Proof:** Every edge in $T$ is visited exactly twice

**Observation 3:** Shortcutting does not increase the cost of visiting vertices in $L$
**Proof:** By triangle inequality, $c(c,d) \leq c(c,b) + c(b,d)$

## Metric TSP: State-of-the-Art
### Christofides '1976
- Metric TSP has a $\frac{3}{2}$-approx

### Karlin, Klein, Oveis Gharan '2020
- Metric TSP has a $\frac{3}{2}-10^{-36}$-approx

## Set Cover
**Input:** A universe $U$ of $n$ elements, and $m$ sets $s_{1},s_{2},\dots,s_{m}$ such that each $s_{i} \subseteq u$
**Goal:** Find a smallest sub-collection of sets whose union is $u$

## Decision Version of Set Cover
**Input:** Same as on the left + an integer K
**Goal:** Decide if there exists a sub-collection of $\leq k$ sets whose union is $u$

Vertex Cover (decision) $\subseteq_{p}$ set cover (decision)

## Set Cover Instance
$u = \{e_{1},e_{2},\dots,e_{m}\}$
For each vertex $i \in V$, create a set $s_{i} = \{e | e \text{is incident on vertex i}\}$
$k'=k$

$\implies$ Suppose $G$ has a vertex cover $x$ of size $\leq k$
Consider the set cover solution that consists of all sets $s_{i}$ such that $i \in x$
We choose $|x| \leq k$ sets

### Approximation Algorithm for Set Cover
{
	$u'=u$
	$F=\phi$
	while $u' \neq \phi$:
	{
		Pick a set $s_{i}$ that covers the most \# of elements in $u'$
		Set $u' = u' - s_{i}$
		Add $s_{i}$ to $F$
	}
}

**Claim:** $F$ is $\ln n$-approximate set cover
**Useful Fact:** For any positive integer $p$,
$\left( 1 - \frac{1}{p} \right)^{p}< \frac{1}{e}$

Let $p =$ # of sets used by an optimal solution
Let $n_{i} =$ # of elements that remain to be covered after greedy has chosen $i$ sets. ($n_{0}=n$)

$n_{1} \leq n - \frac{n}{p}$