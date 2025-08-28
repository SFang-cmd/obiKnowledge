Read ahead: 1.3, 1.4

## Consider a Different Scenario:
- Committee Meetings
- Vertices: Committees
- Edges: Indicate Overlapping Committee Membership
- **Schedule of committee meetings needs to avoid schedule conflicts**

If two committees include the same person, then these two committees cannot meet at the same time
- What is the largest set of committees that **can** meet at the same time?

- Definition: a set of vertices in a graph, which have no edges between any two vertices in $S$  is called an **independent** set of vertices

## Redefined Task
Find the largest independent set of vertices
![[IMG_9557.jpeg]]

### An important observation!
- Independent Set of 6 Vertices: $a, d, f, g, i, k$
- Last time: Edge Cover of 5 Vertices: $b, c, e, h, j$
- **These two sets are complements of each other**

- **General Fact:** If $V$ is the set of all vertices in the graph $G$, then for any subset of vertices, $I \subseteq V$, $I$ is an independent set of vertices if and only if the complement $V \setminus I$ (also written as $I^C$, or $\bar{I}$) is an edge cover
**Proof:**
- $\implies$: Assume $I \subseteq V$ is an independent set of vertices, i.e, there are no edges between any two vertices in $I$. Take an edge. Both of its vertices cannot be in $I$, i.e. at least one of its vertices is in the complement, $V \setminus I$. That is, $V \setminus I$ is an edge cover.
- $\impliedby$: Conversely, if $C \subseteq V$ is a set of vertices which is an edge cover, i.e. each edge has at least one of its vertices in $C$, then any two vertices **not** in $C$, i.e. any two vertices in $V \setminus C$ cannot have any edges between them
- Why? Suppose the contrary, i.e. there is some edge between two vertices both in $V \setminus C$, i.e. both vertices **not** in $C$, but now this contradicts the assumption that $C$ is an edge cover, meaning that at least one vertex of **each** edge must be in $C$. Q.E.D.

### Graph Isomorphism
- Definition: Two graphs $G$ and $G'$ are called **isomorphic** if there exists a one-to-one correspondence between the vertices in $G$ and the vertices in $G'$ such that a pair of vertices are adjacent (i.e. joined by a single edge) in $G$ if and only if the corresponding vertices are adjacent in $G'$
- Such a one-to-one correspondence, which preserves and reflects adjacency, is called a **graph isomorphism**
- Intuitive Idea: Isomorphic Graphs are just renamings of each other

Example: ![[IMG_9585.jpeg]]
- All remaining 3 vertices in each graph are all mutually adjacent, so in fact we scould do any matchup
- e.g. $a,b,c$ with $1,2,3$ respectively
	- Indeed, we have built a one-to-one correspondence
	- a~1
	- b~2
	- c~3
	- d~4
	- e~5
- Which is an isomorphism!
- Comments:
	1. Degrees are preserved under isomorphism
- Definition: A **subgraph** $H$ of a graph is a graph formed by some subset of vertices and edges of $G$
	2. If two graphs $G$ and $G'$ are isomorphic, then subgraphs $H$ and $H'$ formed by corresponding vertices and edges are also isomorphic
	3. Subgraphs could therefore be used to test for an isomorphism, e.g. if we can find corresponding subgraphs that themselves are not isomorphic, then the two given (big) graphs cannot be isomorphic
	4. Complete graphs can be seen as building blocks of large graphs. On the other hand, any graph is a subgraph of a complete graph (carving out vs. building completely up)
- Definition: A graph with $n$ vertices in which each vertex is adjacent to all vertices is called the **complete graph** on $n$ vertices, denoted $K_{n}$
	- in fact, in our example, we have a $K_{2}$ and a $K_{4}$ joined at one vertex
![[IMG_9587.jpeg]]