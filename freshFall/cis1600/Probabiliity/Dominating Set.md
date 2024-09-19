Using techniques from the [[Probabilistic Method]]
$S \subseteq V$ is a dominating set in $G = (V,E)$ iff $\forall u \notin S$, $u$ must have a neighbor in $S$

**LOOK AT AGAIN** (and think about before asking people around you)
Prove or disprove:
In any graph G, 
A [[Vertex Cover]] in G = dominating set in G
(think complete 3-graph. if only one of the points is in S, then it is dominating, but not a vertex cover, since the edge between the two points outside of S don't have an element in S.)

Ex. Let $G = (V,E)$ be any graph with $\delta(G)=\delta$
Then $G$ must have a dominating set of size $\geq \frac{n}{1+\delta}(1+ln(1+\delta))$

Let $S:$ subset of V constructed by adding each vertex from $V$ in $S$ with probability $p$ **(by definition of dominating set, only need to look at $u \notin S$)**
(If pressed for time on the EXAM: Just put each of the $u$ values into the set, if $u$ does not have a neighbor in $S$)

Adding each vertex at random independently

Let $X:$ r.v. denoting $|S|$
Let $Y:$ r.v. denoting the # of vertices in $V$ that are not dominated by $S$
Add every such vertex (vertex not dominated by S) to $S$
Size of the dominating set = $X + Y$

(Not the smallest, but works to bound enough that we can determine the size is at least some number____ (Shown above))

$E[size] = E[X] + E[Y]$ (for X, binomial r.v. with probability $p$ and number n)
			$= np + \sum\limits_{u\in V}E[Y_u]$
Where $Y_u=1$ if $u \notin S$ and u is not dominated 0,0 $\notin$ w.
			$= np + \sum\limits_{u}Pr(Y_u=1)$
			$=np + \sum\limits_{u}(1-p)^{deg(u)+1}$
			$\geq np + n(1-p)^{\delta + 1}$

**(External property to know:)**
$1+u \leq e^{x}, \forall x$
Then,
			$\leq np + ne^{-p(1+\delta)}$
			$p=\frac{ln(1+\delta)}{1+\delta}$
			$\leq \frac{nln(1+\delta)}{1+\delta} + n*e^{-\frac{ln(1+\delta)}{1+\delta}(1+\delta)}$
			$=\frac{nln(1+\delta)}{1+\delta} + e^{\frac{n}{ln(1+\delta)}}$
			$=\frac{nln(1+\delta)}{1+\delta} + \frac{n}{1+\delta}$
			$= \frac{n}{1+\delta}(1+ln(1+\delta))$

