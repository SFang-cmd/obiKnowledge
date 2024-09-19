**Strongly Connected Components:**
**Input:** Directed graph $G(V,E)$
**Objective:** To find all SCCs in G

**Algorithm:**
1. $DFS(G)$. Note f[.]
2. Compute $G^T$
3. Do $DFS(G^T)$ but when picking each root pick the one with the highest $f[.]$
4. Vectors in each tree of $DFS$ forest output by (Step 3) form a SCC in $G$

**Lemma:** $G^{SCC}$ is a DAG
**Notation:** $S \subseteq V$
$d[S]=min_{u \in S}\{d[u]\}$
$f[S]=max_{u \in S}\{f[u]\}$

**Lemma:** Let $C$ & $C'$ be $SCCs$ in $G$.
Let $x \in C$ and $y \in C'$ and let $(x,y) \in E$. Then $f[c] > f[c']$
**Proof:**
**Case 1:** $d[c]<d[c']$
Let $u \in C$ s.t. $d[u]=d[C]$
Let $v \in C'$ be an arbitrary but particular vertex. It suffices to show that $f[u] > f[v]$

At $d[u]$ there is a WP from $u$ to $v$ in $G$
By WPT, $v$ is a descendant of $u$ in the $DFS$ forest
By $PT$, $d[u]<d[v]<f[v]<f[u]$

**Case 2:** $d[c']<d[c]$
Let $u' \in C'$ s.t. $d[u']=d[C']$
Let $v'$ be any vertex in in $C'$
Let $v$ be any vertex in $C$
It suffices to show that $f[v]>f[v']$

At $d[u']$, no WP from $u'$ to $v$. By WPT, $v$ is NOT a descendant of $u'$ in the DFS forest
By PT,
$d[u']<f[u']<d[v]<f[v]$

At $d[u']$, WP from $u'$ to $v'$ in $G$.
By WPT, $v'$ is a descendant of $u'$ in the $DFS$ forest
By PT, $f[v']<f[u']$

**Theorem:** Our algorithm works
**Proof:** Induction on # of trees in the $DFS forest$
IH: Assume that the algorithm forms a SCC for the first $k$ trees of the $DFS$ forest in $G$.
BC: Let $r_1$ be the root of the 1st tree in the **DFS** forest.
Want to show that the vertices in the tree rooted at $r_{1}$ equals $=SCC(r_1)$
Let $v \in SCC(r_1)$, then $DFS$ from $r_1$ will fetch $v$

Let $w \notin SCC(r_1)$
Then $r_1$ is in the sink vertex of $(G^{SCC})^T$
Thus no path from $r_1$ to $w$ thus Tree $T_1$ is "well-behaved"

IS: Let $r_{k+1}$ be the root of $T_{k+1}$
Let $v$ be any vertex in $SCC_{G}(r_{k+1}))$. 
Clearly, $v \in T_{k+1}$
Let $w$ be any other vertex not in $SCC(r_{k+1})$
Thus there is no path from $r_{k+1}$ to $w$

Once you reach $r_{k+1}$, $k+1$ is the "sink" (one with the highest f[.])

*Note: There could be edges from $k+1$ back, but it doesn't matter because there aren't forward edges*

DONT DO TOPOLOGICAL SORT IF ITS NOT A DAG, otherwise can do that
*Note: you can construct a simple $G^{SCC}$ in O(n) time* **Can we say on the exam?**

**Shortest Paths:**
**Input:** Directed graph $G = (V,E)$
$s \in V$
weighted on non-negative edge numbers
**Objective:** To find the shortest path tree rooted at $v$
*Note: d[.] = distance from current vertex to each .*
**Algorithm:**
For each $u \in V$ do
	$d[u] = \infty$
	$\pi [u] \leftarrow NIL$
$d[s]=0$
$S \leftarrow\{\}=\emptyset$
// assume WLOG
// all vertices in G
//are reachable from $s$
while $S \neq V$ do
$u \leftarrow$ vertex with the smallest
	$d[.]$ in $V \backslash S$
$S \leftarrow S \cup \{u\}$
for each $v \in N(u)$ in $V \backslash S$ do
	if $d[v] > w_{uv}$ then
		$d[v] \leftarrow w_{uv}+d[u]$
		$\pi(v) \leftarrow u$

**Theorem:** Dijkstra's Algorithm works
**Proof:** Induction $m$ on $|S|$
IH: Assume that $d[u]=\delta_{G}(s,u), \forall u \in S$, when $|S|=k$
BC: Trivial
IS: Let $v$ be the $(k+1)$th vertex brought into $S$ 
Who brings $v$ into $S$?
Vertex $u$

Assume for contradiction that $d[v]=d[u]+w_{uv}>\delta(s,v)$
Let $P$ be the $s \rightarrow v$ path yielding the path length $\delta(s,v)$
We know that $s\rightarrow u$ is the shortest path by induction
Let $y$ be the first vertex in $P$ that is not in $S$. Let $x$ be the vertex in $P$ just before $y$.
We know that vertex $y$ exists since d
$\delta(s,v)=d[x]+w_{x->v}$
Thus, there is a contradiction, since
$d[v]=d[x]+d[x->u]+w_{uv}$
But in order for the path to go through $u$, 
