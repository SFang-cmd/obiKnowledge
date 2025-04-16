### Approximation Algorithms
- An approximation algorithm for a problem $P$ is a poly-time algorithm $A$ that on any input instance $I$ behaves as follows:
	- It outputs a solution that satisfies
		- $A(I) \geq \frac{OPT(I)}{\alpha}$ (if $P$ is a maximization problem)
		- $A(I) \leq \alpha*OPT(I)$ (if $P$) is a minimization problem
- $A(I)$: Value of solution returned by $A$
- $OPT(I)$: Optimal solution value

### MAX 3-SAT
**Input:** A 3-CNF formula $F$ with clauses $c_{1},c_{2},\dots c_{m}$
**Goal:** Find an assignment that maximizes that \# of clauses satisfied

Design a 2-approx algorithm
$A_{1}=$ set all variables to True
$A_{2}=$ set all variables to False
Take better of these two

Observe that $m_{1}+m_{2}\geq m$
$\implies MAX\{m_{1},m_{2}\} \geq \frac{m}{2}$
Also, note that $OPT \leq m$

### Vertex Cover
**Input:** A graph $G(V,E)$
**Goal:** Output a vertex cover of smallest size
$S$ is a vertex cover of $G$ if $\forall (u,v) \in E$, we have $|S \cap \{u,v\}| \geq 1$

### Approx Algorithm for VC
- {
	- $E' = E, M = \emptyset, S=\emptyset$
	- While $E' \neq \emptyset$ do
	- {
		- Pick any edge $(u,v) \in E'$
		- $M = M + (u,v)$
		- $S = S + \{u,v\}$
		- Delete from $E'$ all edges incident on $u$ or $v$
		- }
	- Output $S$
	- }

- **Claim 1:** $S$ is a valid vertex cover
- **Claim 2:** The set $M$ of edges is a matching
- **Theorem:** If there is a |$4$|-approx algorithm for vertex cover, then $P=NP$

### Strategy for designing an $\alpha$-approximation algorithm for a minimization problem
- Given any instance $I$, identify in poly-time since lower bound $L(I)$ on the optimal solution value
- Design a poly-time algorithm to output a valid solution of cost $\leq \alpha \times L(I)$

### Approximability of TSP
**Input:** A complete undirected graph $G$ with a non-negative cost function $c$ on the edges
**Goal:** Output a TSP tour of minimum cost
**Theorem:** For any finite $\alpha$, if there is an $\alpha$-approximation algorithm for TSP, then $P = NP$
**Proof:** Suppose there is a poly-time $\alpha$-approximation algorithm $A$ for $TSP$ for some finite value of $\alpha$

We will use $A$ to solve Hamiltonian cy