**Testing Bipartiteness:**
Input: Undirected graph $G = (V,E)$
Objective: Output yes if $G$ is bipartite and No otherwise

Bipartite graph:
- 2-colorable
- no odd cycles

Algorithm:
```pseudocode
T <- BFS(G)
vertices in even layers are colored RED
vertices in odd layers are colored BLUE
for each e=(u,v) in G
	if u & v are colored the same
		output NO
output YES
```
*Idea: You create a tree because trees have to be bipartite, and then check if the output we created is a valid coloring of the bipartite graph*

Proof of Correctness:
- When we output YES, we have verified the 2-coloring
- When we output No,
	- Let (u,v) be an edge s.t. u&v are colored the same, i.e. $color(u) = color(v)$
	- Then these two points need to be on the same layer, by property of BFS
	- let s be the lca(u,v)
	- odd cycle: s ~ u - r ~ s

```pseudocode
DFS(G)
for each u in V
	color[u] <- white
	pi[u] <- NIL
time <- 0
for each u in V
	if color(u) is white
		DFS.VISIT(u)
```

```
DFS.Visit(u)
color[u] <- Gray
time <- time + 1
d[u] <- time
for each v in N(u)
	if color[v] = white
		pi[v] <- u
		DFS.VISIT(v)
time <- time + 1
f(u) <- time
color(u) <- black
```

When is a vertex v a descendant of vertex $u$ in the DFS first?

**Property 1:** Vertex v is a descendant of u in the DFS forest iff $v$ is discovered when $u$ is gray
**Property 2 (Parenthesis Theorem):** u,v: any two vertices in G
Exactly one of the following happens:

Proof: WLOG let du < dv
Case 1: dv > fu
then this would mean that both of the cases are disjoint.
Case 2: dv < fu
then this would mean that dv would need to occur at some time before fu
**Observations:** $v$ is discovered when $u$ is Gray. 
By P1, $v$ is a descendant. of $u$ in the DFS forest.
DFS Search is at $v$. $v$ is colored Black when all its neighbors are explored. Then the search returns to $u$. Thus $fv < fu$
Corollary: $v$ is a descendant of $u$ iff $du < dv < fv < fu$

**Property 3 (White Path Theorem):**
Vertex $v$ is a descendant of vertex $u$ iff at $d[u]$ there is a white path from $u$ to $v$ in $G$
**White path** means a path consisting of only white vertices

**Proof:**
$v$ is a descendant of $u \implies$ that at time $d[u]$, there is a WP from $u$ to $v$ in $G$

Let $P$ be the path from $u$ to $v$ in the DFS forest:
$u$ ~ $w$ ~ $v$
$w:$ any vertex in P. At $d[u]$, $w$ must be white

From property 1, clearly $w$ is discovered when $u$ is gray. We know the $w$ is a descendant of $u$. Property 1 tells us that $w$ was discovered when $u$ is gray. This must mean that $w$ was white, which means that all points between $u$ and $v$ are white. Thus, P is a white path in G

($\impliedby$) at time $d[u]$, there is a WP from $u$ to $v$ in $G$ $\implies$ $v$ is a descendant of $u$ in the DFS forest

Proof: Contradiction, let $P$ be the White Path. $P:$ u~x~x~y~x~x~v
Let $y$ be the first vertex going from $u$ to $v$ s.t. $y$ is not a descendant of $u$ in the DFS forest. Let $x$ be the vertex in $P$ just before $y$

By the parenthesis theorem,
du ----------------- fu
		dx---fx
	dy ---------- fy

- [dy,fy] cannot be contained in [du,fu] (By parenthesis theorem)
- dy > fx, since $x$ cannot finish when it has a white neighbor.
- Thus, dy < du which is a contradiction

Edge classification
- Label all edges during DFS - first time an **edge** is explored (all edges can only have ONE label)

Tree edges: all edges in DFS forest
Back: (u,v) is a back edge if the search is at $u$ and $v$ is $u$'s ancestor
Forward edge: (u,v) is a forward edge if the search is at $u$ & $v$ is $u$'s descendant
Cross edge: All else

back edge means that v comes before u, which means that v is gray at u
forward edge means that u comes before v, which means that v must be black for a forward edge not in the TREE EDGE (like if there is a cycle somewhere that goes back to v, this must mean another path already traversed that v).

DFS on an undirected graph yields
Tree edges and Back edges ONLY (none of the rest)