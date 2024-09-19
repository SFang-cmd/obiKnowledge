**Huffman Properties:**
A **prefix code** for a set $S$ of letters is a function $\gamma$ that maps each letters $x \in S$ to some sequence of zeros and ones, in such a way that for any distinct $x,y \in S$, the sequence $\gamma(x)$ is not a prefix of the sequence $\gamma(y)$.
**Lemma 1:** The encoding of $S$ constructed from $T$ going through each edge of a tree is a **prefix code**
**Lemma 2:** The binary tree corresponding to an optimal prefix code is full
**Lemma 3:** There is an optimal prefix code, corresponding to tree $T^{*}$, in which the two lowest-frequency letters are assigned to leaves that are siblings in $T^{*}$
**Theorem 1:** The Huffman code for a given alphabet $S$ achieves the minimum average number of bits per letter of any prefix code
**Lemma 4:** With $T, T',$ and $w$ as defined above, we have
$ABL(T')=ABL(T)-f_{w}$

**BFS Properties:**
**Proposition 1:** For each $k \geq 1$, the layer $L_{k}$ produced by BFS consists of all nodes at distance exactly $k$ from $x$. Moreover, there is a path from $s$ to $t$ in $G$ iff $t$ appears in some layer (i.e. iff $t$ is visited by the BFS traversal)
**Proposition 2:** Let $G$ be a graph in which vertices $x$ and $y$ share an edge. Let $T$ be a BFS tree of $G$. In $T$, let vertices $x$ and $y$ belong to layers $L_{i}$ and $L_{j}$, respectively. Then $i$ and $j$ differ by at most $1$.
**Proposition 3:** Running BFS on a graph $G = (V,E)$ given as an adjacency list takes $O(m+n)$ time, where $n=|V|$ and $m=|E|$. That is, BFS is a linear time algorithm
**Lemma 1:** BFS correctly computes the shortest paths from the source in an unweighted graph

**DFS Properties:**
**Lemma 1:** In the DFS forest, $v$ is a descendant of $u$ if and only if $v$ is discovered during the time in which $u$ is gray.
**Theorem 1: (Parenthesis Theorem)** In any DFS of a (directed or undirected) graph $G=(V,E)$, for any two vertices $u$ and $v$, exactly one of the following three conditions holds:
- The intervals $[u.d,u.f]$ and $[v.d,v.f]$ are entirely disjoint, and neither $u$ nor $v$ is a descendant of the other in the DFS forest
- The interval $[u.d,u.f]$ is contained entirely within the interval $[v.d,v.f]$, and $u$ is a descendant of $v$ in a DFS tree
- The interval $[v.d,v.f]$ is contained entirely within the interval $[u.d,u.f]$, and $v$ is a descendant of $u$ in a DFS tree
**Corollary 1: (Nesting of Descendants' Intervals)** Vertex $v$ is a proper descendant of vertex $u$ in the DFS forest for a (directed or undirected) graph $G$ if and only if $u.d < v.d < v.f < u.f$
**Theorem 2 (White Path Theorem (WPT))** In a DFS forest of a graph $G=(V,E)$, vertex $v$ is a descendant of vertex $u$ if and only if at the time $u.d$ when the search discovers $u$, there is a path from $u$ to $v$ in $G$ consisting entirely of white vertices.
**Theorem 3:** In a DFS of an **undirected** graph $G$, every edge of $G$ is either a tree edge or a back edge.

**BFS Bipartite Algorithm Properties:**
**Proposition 1:** If a graph $G$ is bipartite, then it has no odd cycles
**Proposition 2:** Let $G$ be a connected graph, and let $L_{0},L_{1},...$ be the layers produced by BFS starting at a node $s$. Then exactly one of the following two things must hold:
1. There is no edge of $G$ joining two nodes of the same layer. In this case, $G$ is a bipartite graph in which the nodes in even-numbered layers can be colored red and the nodes in odd-numbered layers can be colored blue.
2. There is an edge of $G$ joining two nodes of the same layer. In this case, $G$ contains an odd cycle, and so it cannot be bipartite.
**Theorem 1:** A graph $G$ is bipartite iff it contains no odd cycles.

**DAGs and Topological Sorting:**
**Proposition 1:** $G$ is a DAG iff it has a topological ordering
