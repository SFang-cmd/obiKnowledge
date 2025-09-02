**Theorem:** In any graph, the sum of the degrees of all vertices is equal to twice the number of edges
**Proof:** Summing up the degrees of all vertices counts all instances of some edge being incident at some vertex. But each edge is incident to two vertices, and so each edge is being counted twice, that is, once at each of its two vertices.
**Corollary:** In any graph, the number of vertices of odd degree is even
**Proof of Corollary:** The sum of degrees has to be even, by the theorem, so there must be an even number of odd integers in the sum.
**Example:** We want to construct a graph with 20 edges, with every vertex of degree 4. How many vertices must the graph have?
- Let $v=\text{the number of vertices}$, the sume of the degrees will be
- $4v=2 \times 20 = 40$
- So $v=10$
**Example:** How many edges are there in $K_{n}$, the complete graph on $n$ vertices?
$K_{n}$ has an edge between all possible pairs of vertices. At any vertex there will be edges going to each of the $n-1$ other vertices in $K_{n}$. Hence, each vertex has degree $n - 1$. The sum of the degrees is therefor $n(n-1)$. That's **twice** the number of edges, so the number of edges in $K_{n}$ is $\frac{n(n-1)}{2}$
![[IMG_9638.jpeg]]

**Example: An impossible graph**
Is it possible to have a group of $7$ people such that each person in the group knows exactly $3$ other people
- We model this problem using a graph with a vertex for each person and an edge for each pair of people who know each other. We would have a graph with $7$ vertices, each of degree $3$. But this is impossible by the corollary, because the number of vertices with odd degree must be even.

**Definition: A graph is Bipartite** if its vertices can be partitioned into two sets $V_{1}$ and $V_{2}$ and every edge joins a vertex in $V_{1}$ with a vertex in $V_{2}$. $V_{1}$ and $V_{2}$ are called the **parts** of the bipartite graph
- **Note:** $K_{2}$ is bipartite, $K_{3}$ is not bipartite and neither is $K_{n}, n \geq 3$
![[IMG_9639.jpeg]]
Circuit: $A-c-D-d-A$
$Length=4$
![[IMG_9640.jpeg]]
**Theorem: A graph is bipartite** if and only if every circuit has an even length, i.e, there are no circuits of odd length.
**Note:** There may not be any circuits at all!

**Example:** A complete bipartite graph:
![[IMG_9641.jpeg]]

**Definition:** A **Connected Component** (or briefly: a component) $H$ of a graph $G$ is a connected subgraph of $G$ such that there is no path between any vertex in $H$ and any vertex not in $H$. The connected component containing a particular vertex $x$ consists of $x$ and all vertices that may be reached from $x$ by a path in $G$
**Proof of Theorem:** Note that it suffices to prove this theorem for connected graphs.
That is, we claim that if the theorem is true for each connected component of a disconnected graph $G$, then it is true for the entire graph $G$. 
This claim follows from the fact that a graph is bipartite if and only if each of its connected components is bipartite, and the fact that any circuit in $G$ has even length if and only if any circuit in each of the connected components of $G$ has an even length.

Now onto the proof. First, we show that if a graph is bipartite, then any circuit that exists must be of even length (Note: Connectedness is not needed in this direction.)

Let's call the two parts in a given bipartite graph the left and the right parts, respectively. Any circuit $x_{1}-x_{2}-x_{3}-\dots-x_{n}-x_{1}$, assuming $x_{1}$ is on the left, has alternately a left vertex, then a right vertex, then a left vertex, then a right vertex, etc. vertices with odd subscripts are on the left, and the vertices with even subscripts are on the right. Because $x_{n}$ is adjacent to $x_{1}$, $x_{n}$ must be on the right, and therefore $n$ is even. The reasoning is similar if $x_{1}$ is on the right.

In the other direction, assume that the graph is connected and that any circuit has an even length. From this we need to show that the graph is bipartite. We use the AC principle.

Take any vertex, call it $a$. Put it on the left. Put all vertices adjacent to $a$ on the right. Put all vertices adjacent to those, i.e., all vertices that are two edges away from $a$, on the left, etc. In general, if there is a path of odd length between $a$ and a vertex $x$, put $x$ on the right. If there is a path of even length between $a$ and $x$, put $x$ on the left. If the graph is connected, this exhausts all the vertices. We still have to show that this construction is well-defined, that is, there cannot be both an odd length path $P$ and also an even length path $P'$ between $a$ and $x$. If the paths $P$ and $P'$ are mutually disjoint, i.e., $P$ and $P'$ meet **only** at $a$ and at $x$, then we would obtain a circuit of odd length by taking the path $P$ from $a$ to $x$, and then following the path $P'$ from $x$ back to $a$. This is impossible by our main assumption that there are no circuits of odd length. If the paths $P$ and $P'$ intersects in some other vertex, then a further argument is needed to construct an odd length circuit. (Exercise 18 in section 1.3 on p.30-31)

So far we split all the vertices into left and right without any overlaps. We still have to show that there are no edges between two left vertices nor between two right vertices. Suppose vertices $b$ and $c$ are on the left. By our construction, there is an even length path $Q$ joining $a$ with $b$ and an even length path $Q'$ joining $a$ with $c$. So if there were an edge $(c,b)$, then the path $Q'$ followed by that edge, would be an odd length path joining $a$ with $b$, which we showed above was impossible. 

Similarly, we show that there are no edges between any right vertices.

Hence, the graph $G$ is bipartite.