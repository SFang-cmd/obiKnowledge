```pseudocode
BFS(G,s):
	for each u element of V do
		disc(u) <- False
	disc(s) <- True
	i = 0, T = {S}
	L[i] <- {s}
	while L[i] != null:
		L[i+1] <- null
		for each u element of L[i]
			for each v element of N(u) #neighbors of u
				if discovered[u] = False
					Add (u,v) to T
					discovered(v) <- True
			end for
			L[i+1] <- L[i+1] and {v}
		end for
	i <- i+1
	end while
	return T
```

Running time: Every vertex is getting explored once, and each vertex traverses an edge at most once, so $\theta(n+m)$, linear time

$\theta(n+\sum\limits_{u\in V} deg(n))$
$=\theta(n+m)$

Depth First Search
```pseudocode
DFS(G):
	for each u element of V do
		color[u] <- white
		pi[u] <- null
	time <- 0
	for each u element of V do
		if color[u] = white then
		DFS.VISIT(u)

DFS.VISIT(u):
	color[u] <- Gray
	time <- time + 1
	d[u] <- time
	for each v element of N(u) do
		if color[v] is white
			pi[v] <- u # parent of v is u
			DFS.VISIT(u)
	time <- time + 1
	f[u] <- time
	color[u] <- Black
```

Runtime is $\Theta(n+m)$, use $m$ because it is more expressive

