### Graph Theory
- **Definition: An (undirected) graph** $G=(V,E)$ consists of a finite set $V$ of vertices and a finite set $E$ of edges joining distinct (unordered) pairs of distinct vertices
- In this example:
	- ![[IMG_9556.jpeg]]
	- $V=\{a, b, c, d\}$
	- $E=\{(a,b), (a,c), (a,d), (b,d), (c,d)\}$
- Notes:
	1. Our definition of a graph does **not** allow two different edges to join the same two vertices
	2. An edge cannot loop
	3. The two ends of an edge may be written in either order
- **Definition: A path** $P$ in a graph is a sequence of distinct vertices, written
	- $P=x_{1}-x_{2}-x_{3}-\dots-x_{n}$
	- where each pair of consecutive vertices $(x_{i}, x_{i+1})$ is joined by an edge. 
- **Circuit:** In addition, if there is an edge $(x_{n}, x_{1})$, then the path $x_{1}-x_{2}-x_{3}-\dots-x_{n}$ is called a circuit
	- Examples: $b-d-a-c$ is a path, but not a circuit, but $a-b-d-c-a$ is a circuit
- **Definition: A graph is connected** if there is a path between any pair of vertices
	- Example: Our graph above is connected, e.g. vertices b and c have a path between them
- **Definition:** The number of all edges incident to a vertex is called the **degree** of the vertex
- **Neighborhood Watch:**
	- Every block should be watched from at least one of its corners.
	- What is the smallest number of watch members that can do this?
	- ![[IMG_9557.jpeg]]
	- **First:** try to get a lower bound
		- There are 14 blocks (edges)
		- Corners (vertices) $b, c, e, f, h, j$ have degree $3$ and corners (vertices) $a, d, g, i, k$ have degree $2$
		- because $4$ vertices can be incident to at most $4\times 3=12$ edges and there are $14$ edges total, we will need at least $5$ neighborhood watch members for our task (Pigeonhole Principle)
	- **Second:** can we actually hit $5$?
	- General observations:
		- If all 5 watch members were positioned at degree $3$ vertices, then $5\times 3=15$ blocks are watched. Since there are only $14$ blocks, some block would be covered by watch members at both corners, which is fine. However, if $4$ watch members are positioned at degree $3$ vertices and $1$ watch member at degree $2$ vertex, then exactly $14$ blocks are watched, and no edge is covered at both ends
		- If $2$ watch members are at degree $2$ vertices and $3$ watch members at degree $3$ vertices, then that would cover $3\times 3+2\times 2=9+4=13$, so blocks would not be watched
	- With these general observations, we can now try a systematic analysis to find the $5$ vertices that together (collectively) are adjacent to all $14$ edges
- **Exploration:**
	- Consider the edge $(c,d)$
	- Suppose this edge is watched from the vertex $d$
	- Then the other vertex of that edge $c$ cannot also have a watch member positioned on it, because, as we noted in our general discussion, if we use a degree $2$ vertex, such as $d$, then no block is watched from both ends. But $(c,g)$ must be watched, from $g$. Note that $g$ is also of degree $2$ of degree $2$, $d$ and $g$, but we showed in the general discussion that that way would cover only $13$, not all $14$, blocks.
	- **Reflection:** How DID we get into this trouble? By putting somebody on $d$, so that's **wrong!!**
- **Other:**
	- We proved that there cannot be anybody at $d$. So, let's put someone at $c$ and not at $d$, so the block $(d,h)$ must be watched from $h$. Next, what about the block $(h,k)$? There is already somebody at $h$, so there shouldn't be anyone at $k$. This is because $k$ is of degree $2$, and if we put someone at $k$, then no edge an be watched from both ends. So, no one should be at $k$. 
	- But the edge $(j,k)$ has to be watched. So put someone at $j$.
	- **Recap:** We have people at vertices $c, h, j$
	- By similar reasoning, there cannot be anyone at vertex $i$ and hence there must be someone at vertex $e$. Thus, there cannot be anyone at vertex $a$. 
	- And hence we put the 5th person on vertex $b$
	- **Note:** in face, we ended up with $5$ degree $3$ vertices and indeed the block $(b,c)$ is being watched from both ends
- **Definition:** A set $C$ of vertices in a graph $G$ is called an **edge cover** if every edge of $G$ is incident to at least one vertex in $C$
	- In the example just above we showed that the minimal size of an edge cover in that graph is $5$
- Reflect on our strategy:
	1. We assumed that a 5-vertex edge cover existed
	2. We deduced several helpful consequences from this assumption. The key consequence was: If an edge $(x,y)$ is between a degree $3$ vertex $x$ and a degree $2$ vertex $y$, then at most one of $x$ or $y$ can be used in a 5-vertex edge cover
- A useful name for this strategy is the $AC$ principle
	- **A**ssumptions generate helpful **C**onsequences
- **Note:** the AC principle could also be used that a graph does not have some property! That is, we assume that the graph does have the property, and we deduce consequences and then we show that the consequences lead to a contradiction.