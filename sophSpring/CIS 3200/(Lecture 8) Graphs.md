### Agenda
- Representations of Graphs
- Graph Traversal Algorithms
- BFS and its applications
- DFS and its applications

### Graph Representations
#### Adjacency Matrices
- A graph $G(V,E)$ is represented by a $n \times n$ matrix $M$ such that 

$$
M(i, j) = 
\begin{cases}
1 & if (i,j) \in E \\
0 & else
\end{cases}
$$
- **Space:** $O(n^2)$
- **Query Time:** Decide if edge $(i,j)$ exists in $G$ - $O(1)$ time

#### Adjacency List
- A graph $G(V,E)$ is represented by $n$ linked lists, one for each vertex. For a vertex $u \in V$, $Adj[u] =$ linked list containing all vertices $v$ s.t. $(u,v) \in E$
- **Space:** $O(n + m)$
- **Query Time:** $O(n)$

#### Graph Traversal Algorithms
- Breadth-First Search (BFS)
- Depth-First Search (DFS)

```Python
def BFS(s, G):
	for v in V:
		color[v] = white
		parent[v] = NIL
	# initialize a queue Q = None
	Enqueue(s, Q)
	color[s] = gray
	while Q != None:
		u = Dequeue(Q)
		for each v in Adj[u]:
			if color[v] == white:
				color[v] = gray
				parent[v] = u
				Enqueue(v, Q)
		color[u] = black
```
- **Output:** a BFS tree rooted at $s$
- **Runtime:** $O(n + m)$

#### Applications
a. Connectivity in undirected graphs
- Is $G$ connected?
	- Run BFS from any vertex and check that all vertices are colored black at the end
b. Strong connectivity in directed graphs
- Is G strongly connected?
	- **Naive Approach:** $n$ calls to BFS
- $O(n^{2}+ mn)$ time.