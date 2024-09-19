**Shortest path:**
**Input:** Directed graph $G=(V,E)$
weights on edges: $+ve, s \in V$
**Objective:** To find a shortest path tree rooted at $s$

```pseudocode
Dijkstra(G,S):
	for each u in V do
		d[u] <- infty
		p[u] <- NIL
	d[s] <- 0   //MinBuildHeap() [O(n) time]
	S <- null
	while S != V do
		u <- vector in V \ s with smallest d[.]
		for each ExtractMin [O(lg(n))]:
			for each v in N(u) do
				if d[v] > d[u] + w_[uv]
					d[v] <- d[u] + w_[uv]
					p[u] <- u
					Decrease Key
```

Running Time:
$\theta(n^2)$
$O(n^2+m)$
$O(nlg(n)+m)$
$\theta(nlg(n)+mlg(n))$ --> faster time 

**Minimum Spanning Trees:**
**Input:** Undirected connected graph
$G=(V,E)$
weights on edges: non-negative
**Objective:** To find a minimum weight spanning subgraph of G that is connected.

**Lemma:** $\exists$ an optimal solution that is a tree

**Assumption:** All edge weights are distinct

1. Run Dijkstra from each vertex & take the smallest of all solutions... Instead use "Wrong Dijkstra" algorithm - just check connection cost (Prim's Algorithm)
2. Kruscal: process edges in increasing order of weights & add them if no cycle is created
3. Reverse Delete
	- process edges in decreasing order of weights
	- remove an edge, if removing it keeps the graph connected

**Lemma:** Let SC V such that $S \neq \varnothing$ and $S \neq V$
Let $e=(u,v)$ be the minimum weight edge that crosses the cut $(S,V\backslash S)$. Then every MST contains $e$
**Proof:** Assume for contradiction that $\exists$ a MST T that does not contain $e$
- Since $T$ is connected, $\exists$ edge $f$ in $T$ that crosses the cut ($S,V \backslash S$)
- $T'=T-f+e$
- $W(T')<W(T)$, a contradiction!
Problem: $T'$ may not be a tree
Fix: Any edge on $u ~ v$ path in $T$ that crosses $S,V \backslash S$

**Theorem:** Kruscal's Algorithm works
**Proof:** Let $e=(u,v)$ be an edge about to be added to the solution by Kruscal
To prove that $e$ belongs to "God's solution" (optimal solution), it suffices to show that $\exists$ cut $(S,V\backslash S)$ s.t. $e$ is the minimum weight edge crossing the cut
$S:$ connected component containing $u$

- Kruskal processes edges in increasing order of weight
- Thus $e$ is the edge with the smallest weight that crosses the cut
- It remains to show that our solution is a spanning tree
We will show that our solution is connected & acyclic

**Theorem:** Prim works
**Solution:** The current solution

**Lemma:** Let $C$ be a cycle in $G$
Let $e = (u,v)$ be the heaviest weight edge in $C$. Then $e$ does not belong to any MST

