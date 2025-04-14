**Vertex Cover:**
- Given a graph $G(V,E)$, a vertex cover is a set $S \subseteq V$ of vertices such that $\forall (u,v) \in E$, we have $|S \cap \{u,v\}| \geq 1$
	- At least one of the vertices are within the set
- **Goal:** Find a vertex cover of smallest size

### Vertex Cover Reduction
- Show that VC is NP-Hard by reduction from Independent Set ($L_{IND} \leq_{p} L_{VC}$)
- **Independent Set:**
	- $<G,K>$
	- Does $G$ contain an independent set of size $\geq k$?
- Prove there exists a function $f$ that is poly-time computable to vertex cover $<G',K'>$
- **Vertex Cover:**
	- $<G', K'>$
	- Does G' contain a vertex cover of size $\leq k'$?
- Want to make conditions:
	- $G' = G$
	- $K' = n - K$
	- where $n = |V|$
- Note that generating $<G', K'>$ from $<G, K>$ takes poly-time. $O(n + m)$ time
- $\implies$ Suppose $G$ has an independent set $I$ of size $\geq K$
	- **Goal:** Show that $G'$ has a vertex cover of size $\leq K'$
	- **Claim:** S is a vertex cover of $G$
	- **Proof:** Suppose not. Then $\exists$ an edge $(u,v) \in E$ s.t. neither $u$ nor $v$ are in $S$. But then, $u,v \in I$. A contradiction to the fact that $I$ is an independent set.
- $\impliedby$ Suppose $G' = G$ has a vertex cover $S$ of size $\leq K' = n-K$.
	- Define $I=V-S$. Clearly, $|I| \geq K$
	- **Claim:** $I$ must be an independent set in $G$

### Hamiltonian Cycle Problem
**Hamiltonian Cycle and Path:**
	- A Hamiltonian Cycle in a graph $G$ is a simple cycle that goes through al the vertices
	- A Hamiltonian path in a graph $G$ is a simple path that goes through all vertices
- **Theorem:** Hamiltonian cycle and path are NP-Complete in both directed and undirected graphs
**Traveling Salesman Problem (TSP)**
	- **Input:** A complete undirected graph $G(V,E)$ with a non-negative cost function $c$ on the edges, and a parameter $k$
	- **Goal:** Does $G$ contain a TSP tour (i.e. a Hamiltonian cycle) of cost $\leq k$
- Show that TSP is NP-Hard by doing a reduction from the Hamiltonian Cycle problem in undirected graphs.