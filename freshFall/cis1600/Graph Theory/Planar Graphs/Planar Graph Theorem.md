Thm. For any planar graph G, $\chi(G) \leq 4$ and further,
$\chi(G) \leq 5$

Prove that for any planar graph G, $\chi(G) \leq 6$
Proof: Induction on # of vertices
IH: G: planar graph on k vertices. $\chi(G)$
BC: m = 1,2,3,4,5,6
IS. G: planar graph with $k+1$ vertices
Remove a vertex of the minimum degree. By IH, $\chi(G') \leq 6$, 

Our palette has 6 colors.
$|N(v) \leq 5$
That means we are left with one unused color in the neighborhood of $v$ (since we have proof that shows the minimum degree of a planar graph, G, is at most $5$).
Thus, color the final $v$ with the color not in $N(v)$.

Thm. For any integer $k > 1, \exists \Delta- \text{ free graph G}$ s.t. $\chi(G) = k$

A relation $\chi(G)$ & the size of the largest clique in the graph shows that the clique will always be smaller