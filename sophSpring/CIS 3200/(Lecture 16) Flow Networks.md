### Flow Network
- A flow network is a directed graph $G(V,E)$ with a non-negative capacity function $c$ on the edges
- We are also given 2 special vertices $s,t$ where $s$ is a source vertex and $t$ is a sink vertex
- For now, interpret $c(e)$ as indicating the rate at which data can be sent along the edge $e$
- **Informal Goal:** Find a way to send data from $s$ to $t$ at a maximum

#### Interpretation 1:
Find a single $s\to t$ path $p$ such that we maximize the minimum capacity that appears on this path
![[IMG_7047.jpeg]]

- Use Dijkstra's instead, think about it
- Not the max flow problem interpretation
- Just look at the max flow going into each node, and the max path is the path that has the maximum incoming total nodes

#### Interpretation 2
- Find a collection of $s\to t$ paths, say $P_{1}, P_{2}, \dots, P_{q}$ such that we send $f(P_{i})$ units of data along the path $P_{i}$, for $1 \leq i \leq q$; subject to the constraint
- $Maximize \sum_{i\geq 1}f(P_{i})$
- Subject to: $\forall e \sum_{P_{i}\;s.t. e\in P_{i}}f(P_{i}) \leq c(e)$
- Solution:
	- $P_{1}$: $s\to a\to c\to t, f(P_{1})=3$
	- $P_{2}$: $s\to a\to d\to t, f(P_{2})=1$
	- $P_{3}$: $s\to b\to d\to t, f(P_{3})=5$

##### S-T Flows
- An $s-t$ flow is a non-negative function $f$ defined over edges that satisfies $2$ constraints:
	a) **Capacity Constraints:** $\forall e, f(e) \leq c(e)$
	b) **Flow conservation:** $\forall v \in V-{s,t}$,


