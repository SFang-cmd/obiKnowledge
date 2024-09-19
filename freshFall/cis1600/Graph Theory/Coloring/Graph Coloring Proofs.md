Proofs from [[Graph Coloring]] unit
**Ex1.** Prove that a graph with maximum degree at most $k$ is $k+1$ colorable.

**Solution:**
**Important!!** Induction on the number of vertices, $n$ while keeping $k$ variable since this will prove it works for all possibilities.

Let $P(n)$ be the property that a graph with $n$ vertices and maximum degree at most $k$ is $(k+1)$ colorable.

**Base Case:**
$P(1)$ is true since the graph is of degree 0, and there is 1 color that the 1 vertex can be colored.

**Induction Hypothesis:**
Assume that the property holds for some $h \geq 1$  number of vertices.

**Induction Step:**
Want to show that P(h+1) satisfies that k is (k+1) colorable.
Remove one of the vertices along with the edges incident on $v$. Then there would be $h$ vertices with at most $k$ degrees, so because we have $k+1$ colors from the IH, and because the new degree of $h+1$ is still at most $k$, each vector $v$ can always be colored by a unique color from its at most $k$ neighbors.