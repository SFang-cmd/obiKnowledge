## Agenda
- Recap of DFS
- Classification of edges
- Applications of DFS

### DFS(G)
- Initialization
- +
- Ensuring every vertex is visited

### DFS-Visit(u)
- A depth-first exploration that starts at $u$

### Output
- A collection of rooted trees
- A classification of all edges into 4 types

### Theorem
- Consider when an edge $(u,v)$ is discovered for the first time in DFS
- $Color(u)=gray$,
	- $v$ is white, is a tree edge
	- $v$ is gray, is a back edge
	- $v$ is black, is a cross/forward edge

### Timeline View
a) $(u,v)$ is a tree edge
- $d(u), d(v), f(v), f(u)$
b) $(u, v)$ is a forward edge
- Same as above
c) $(u,v)$ is a back edge
- $d(v), d(u), f(u), f(v)$
d) $(u,v)$ is a cross edge
- $d(v),f(v),d(u),f(u)$

**Claim:** Supoose there is a path from a vertex $u$ to a vertex $v$ in a graph $G$. Then if at the time we call $DFS\_Visit(u)$, if $col(v)=white$, it must be the case that $v$ is discovered before $DFS\_Visit(u)$ finishes

**Correct Version:**
- Suppose when $DFS\_Visit(u)$ is called there is a $u \to v$ path such that *every* vertex on this path is white. Then it must be the case that $v$ is visited before $DFS\_Visit(u)$ finishes

### Applications of DFS
a) Undirected connectivity $O(n + m)$ time
b) Directed strong connectivity $O(n+m)$ time
c) A Acyclicity Testing
- **Directed Graphs**
	- **Claim:** A directed graph $G$ is acyclic iff $DFS(G)$ does not produce any back edges
	- **Proof:** $\implies$ Suppose $DFS(G)$ produces a back edge, say $(u,v)$
	- $\impliedby$ Suppose $G$ has a cycle $C$
	- Assume w.l.o.g that vertex $v_{1}$ is the first vertex on the cycle that is visited by DFS
	- The edge $(v_{k},v_{1})$ will be classified as a back edge
- **Undirected Graphs**
	- If $G$ is an undirected graph, then $DFS(G)$ only produces $2$ types of edges: tree and back edges
	- **Claim:** An undirected graph $G$ is acyclic iff $DFS$ does not produce any back edges
d) Topological Sort
- Suppose you are given a set of $n$ tasks, say, $T_{1},T_{2}, \dots, T_{n}$ along with some precedence constraints of the form $(T_{i}, T_{j})$. Task $T_{i}$ must be completed before $T_{j}$ can be completed
- **Goal:** Is there an execution sequence of tasks that obeys all precedence constraints?
	- Such a sequence always exists as long as there are no cycles
	- Suppose you have a permutation $\pi$ of tasks such that DAG
- **Graph Representation:**
	- Create a graph $G(V,E)$, directed graph
	- $V=\{v_{1},v_{2},\dots,v_{n}\}$ where $v_{i}$ represents task $T_{i}$
	- $E = \{(v_{i},v_{j}) | (T_{i}, T_{j})\}$ is a precedence contraint
- **Algorithm:**
	- Run $DFS(G)$
	- Arrange vertices in decreasing order of finish times
	- **Claim:** In any DAG (Directed Acyclic Graph), for any edge $(u,v), f(u) > f(v)$ in $DFS(G)$
	- **Proof:** Consider any edge $(u,v)$. Cosider when this edge is discovered by $DFS(G)$. At this point, $color(u)=gray$
		- If $col(v)$ is white, then $f(u) > f(v)$
		- If $col(v)$ is black, $f(u)>f(v)$
		- If $col(v)$ is gray, Can't happen because $G$ is acyclic
e) Strongly connected components in a directed graph
- SCC Graph
	- Suppose $G$ has $k$ strongly connected components, say $C_{1}C_{2}\dots C_{k}$.
	- Then the SCC graph of $G$ is another directed graph $H(V',E')$
	- $V'=\{v_{1}v_{2}\dots v_{k}\}$ where $v_{i}$ represents $C_{i}$
	- $E'=\{(v_{i},v_{j})\text{ if there is an edge from a vertex in } C_{i} \text{ to a vertex in } C_{j}\}$

Extending finish times notion to SCC's
- $f(C_{i})=$ largest finish time over all vertices in $C_{i}$
- **Claim:** Suppose $C_{i} \to C_{j}$ in $G$
	- Then $f(C_{i})>f(C_{j})$
- **Proof:** Case 1: Among all vertices in $C_{i} \cup C_{j}$, suppose the first vertex visited in $DFS(G)$ is in $C_{j}$
	- Case 2: The first inserted vertex is in $C_{i}$ where $f(C_{i}) > f(C_{j})$

