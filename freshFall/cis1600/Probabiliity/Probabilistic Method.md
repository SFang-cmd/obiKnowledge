[[Dominating Set]],[[Vertex Cover]]
**Guaranteed** question on Probabilistic Method

Design and experiment where you construct the desired object at random, find the expected value of this object, if the expected value is of value X, then we know that there EXISTS an object of that value X.

**Definitions**
**Independent set:** $S \subseteq V$ is an independent set of $G=(V,E)$ iff $\forall u,v \in S, (u,v)\notin E$
**Ex:** Let $G=(V,E)$ be any graph.
Let $d = \frac{2m}{n} > 0$ be the average degree of a vertex in G.
Then $G$ must have an independent set of size $\geq \frac{n}{2d}$
Construct $S\subseteq V$ by looking at each vertex in $V$ and adding it to $S$ with probability $p$
Let $X:rv$ denotes $|S|$ (cardinality of set S).

(ON THE EXAM: if can't think, say take all vertices that have an edge, and remove it)

Let $Y:rv$ denoting # edges in $E$ whose both end points are in $S$.
Note: Resulting set has a size $\geq X-Y$

$n:$ cardinality of X
$m:$ cardinality of Y
**LOOK AT AGAIN \\/ (is it because $X-Y$ is always less than or equal to size? Where to use expectation? Can we equate the two?)**
(WTS) The value of $X-Y$ in expectation
$E[X-Y] = E[X]-E[Y]$
				$= np$ (because X is a binomial random variable with parameters $n,p$)
					$-mp^2$ (because (this is wrong DON'T WRITE ON EXAM)*Y is a binomial random variable with parameters $m$ and $p^2$*) (Linearity of Expectation - indicator rv for each edge - LOOK INTO IT)
$Y:$ rv total # edges w/ both end point in S
$Y_{e}= 1$ if $e = (u,v)$ has $u \in S)$ and $v \in S$
$Y = \sum\limits_{e}Y_e$
$E[Y]= \sum\limits Pr[Y_e+1]$

We are looking at each edge in set $S$. There is a $p$ probability of drawing one vertex, there is a $p$ proability of drawing the other vertex, so there is a $p^2$ probability of drawing both edges, for each edge with cardinality $m$. Thus, the probability of removing $Y$ is $mp^2$ (LOOK AT AGAIN)

$E[X-Y] = np - \frac{nd}{2}*p^2$ (from definition)
$p=\frac{1}{d}$ (there are $d$ total vertices)
$E[X-Y] = \frac{n}{d}-\frac{n}{2d} = \frac{n}{2d}$
**Do we know that this always guarantees an independent set of size ^^?**
Yes! Because graph $G$ in the set has an average degree of $d= \frac{2m}{n} > 0$  so in $X-Y$, because the expectation equals $\frac{n}{2d}$, there must be an element of the subset of independent sets of cardinality in $G$ $\geq \frac{n}{2d}$ if there is an independent set of cardinality $\leq \frac{n}{2d}$
**Do we know complementary? If a vertex is not in the independent set, then is it always guaranteed to be a set with independent sets?** 

Expectation calculation is done PER GRAPH because it is asking given any graph $G$, this must hold, (compared to first example where it was prove that there EXISTS a graph G, so we are constructing a graph G through adding points)