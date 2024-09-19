Union Find (maintain disjoint sets):
- make set (x)
- find (x)
- union (x,y)

Kruskal:
```pseudocode
for each u in V do
	makeset(u)
S <- null
Sort edges in increasing order of weights
for each e = (u,v):
	if find(u) != find(v) then
		add e to S
		union(u,v)
```
(Check again how union works??)
Properties:
(P1) For any non-root node $x: rank(\pi(x))>rank(x)$
(P2) Let $x$ be a root node of rank $k$. Then there are $\geq 2^{k}$ nodes in the subtree rooted at $x$
(P3) $\leq \frac{n}{2^{k}}$ nodes of rank $k$
Max height of the tree = lg(n)
Runtime:
$O(mlg(n))$

Union by rank using path compression:
```pseudocode
find(x)
if x != pi(x):
	pi(x) <- find(pi(x))
return pi(x)
```
(here, you set all of the x value's parents to the true parent.)


The sequence of finds & unions starting from an empty data structure amortized cost of a
$find=O(lg^{*}(n))$
(find just finds the parent of a node)

Total # finds: $O(m)$
- In path compression $rank(x)$ no longer denotes the height of node $x$
- However, the 3 properties still hold

$log^{*}(x)$: # of successive log calls to $n$ until the resulting # $\leq 1$
(e.g. $lg(lg(lg(lg(2^{1000}))))$)

Partition the non-zero ranks of any node as follows:
$\{1\}, \{2\}, \{3,4\}, \{5,...,2^{4}\}, \{17,18,...,2^{16}\}, \{2^{k}+1,...,2^{25536}\}$

Each interval is of the form $\{k+1,k+2,...,2^{k}\}$
$\# intervals=log^{*}(n)$
Target runtime: $O(mlg^{*}(n))$

**Pocket money:**
Consider the interval $\{k+1,k+2...2^{k}\}$
$\#$nodes whose ranks fall in this interval $\leq$
$\frac{n}{2^{k+1}}+\frac{n}{2^{k+2}}+... \leq \frac{n}{2^{k}}$
Total pocket money given to a node in this interval $\leq \$2^k$
Thus total money given to all nodes in this interval $\leq n$

We have total a $mlg^{*}(n)$ and $nlg^{*}(n)$ of runtime to use
**Case 1:**
"Big jump"; My parent has a different interval than me.
In this case, runtime is $mlg^{*}(n)$, since the big jumps take $lg(n)$ and there are $m$ total elements that can use find.

**Case 2:**
"Small jump"; My parent & I are in the same interval. I need to pay my own pocket money. 
Thus,
rank of my new parent $>$ rank of my old parent

**Case 3:**
"Small jumps, then big jumps"; Pocket money still accounts for everything

Target runtime: $O(mlg^{*}(n)) + O(nlg^{*}(n))=O(mlg^{*}(n))$
$m$ is the total number of times $find$ is called
$n$ is the maximum number in an interval.

In total, finding a new parent will take $nlog^{*}(n)$ time, since there are less than $n$ total elements per interval and $log^{*}(n)$ total intervals.
What is $n$? If the parents have higher $n$ than a child is $n$ of find just the parent's max?

For every call to the $find$ function, the function can, at most jump up $log^{*}(n)$ total layers, taking the same amount of operations, so over $m$ find calls, there are a total of less than $mlog^{*}(n)$ jumps.

This is a worst-case runtime? Or is it a strict runtime? Can we find a better runtime?

If there are $m$ finds taking $O(mlog^{*}(n)) + O(nlog^{*}(n))$, wouldn't the running time be higher, since $nlog(n)$ is much larger than the $m$, thus meaning amortized over $m$ runs, it would be must greater than $log(n)$ - $m$ is actually about the same as $n$.

$m$ is about the same as the number of $n$, constant factor from Kruskal's will check $m$

**$m$ is to the order of the number of edges**
