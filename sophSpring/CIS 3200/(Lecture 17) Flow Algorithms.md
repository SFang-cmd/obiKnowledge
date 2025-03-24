### Flow Network
- A directed graph $G(V,E)$ with a non-negative capacity function $c$.
- We are also given 2 special vertices, $s$ and $t$

### Flow Function
- A non-negative function $f$ that satisfies:
	a. Capacity Constraint
	- $\forall (u,v) \in E, f(u,v) \leq c(u,v)$
	b. Flow Conservation
	- $\forall v \in V - \{s,t\}, f_{in}(v)=f_{out}(v)$
- **Max Flow Problem:** Find a flow $f$ that maximizes $|f| = f_{out}(s)$

### S-T Cuts
- An s-t cut, denoted (S,T) is a partition of V into 2 sets $S$ and $T$ s.t. $s \in S$ and $t \in T$
- Capacity of cuts (S, T) is denoted $c(S,T)$ and is given by $\sum_{u \in S}\sum_{v \in T} c(u,v)$

#### Claim 1:
- Let $f$ be any flow, and let $(S,T)$ be any s-t cut. Then $|f| = f_{out}(S) - f_{in}(S)$

#### Corollary:
- Max s-t flow $\leq$ min s-t cut

- $\forall e \in E,$ set $f(e) = 0$
- While there is an $s\to t$ path $P$ in $G$,
	- Let $\alpha$ be the smallest capacity of any edge on $P$
	- Send $\alpha$ units of flow on $P$
	- Deduct $\alpha$ from the capacity of every edge on $P$
	- Delete any edges of $0$ capacity

### Residual Flow Networks
- Let $f$ be any s-t flow in G. Then the residual flow network w.r.t. $f$, is another directed graph $G_{f}(V,E_{f})$ where $E_{f}$ contains the following edges:
	a. Forward edges
	- For any edge $(u,v) \in E$ s.t. $f(u,v) < c(u,v)$, we add an edge $(u,v)$ to $E_{f}$ with capacity $c_{f}(u,v)=c(uv,v) - f(u,v)$
	b. Backward edges
	- For any edge $(u,v) \in E$ s.t. $f(u,v) > 0$, we add an edge $(v, u)$ to $E_{f}$ with capacity $c_{f}(v,u)=f(u,v)$
- An $s\to t$ path $P$ in $G_{f}$ is called an augmenting path
- Suppose $P$ is an augmenting path in $G_{f}$, and let $\alpha$ be the smallest capacity of any edge on $P$
- (Smallest w.r.t. the residual capacity function $c_{f}$)

#### Augment(f, P, a)
- For every edge $(u,v)$ on $P$
	- If $(u,v)$ is a forward edge then (increase) by $\alpha$
	- else: $(u,v)$ is a backward edge and (decrease) by $\alpha$

### Analysis
- Let $f'=Augment(f, P, \alpha)$
- **Claim 2:** Then $f'$ is a valid flow function
- **Proof:** 
- **Capacity Constraint:** Need to check only for edges on $P$
	- **Case 1:** edge $(u,v)$ on $P$ is a forward edge
		- Then $f'(u,v)=f(u,v) + \alpha \leq f(u,v) + c_{f}(u,v)$
			  $\leq f(u,v) + c(u,v)-f(u,v)$
			  $=c(u,v)$
	- **Case 2:** $(u,v)$ on $P$ is a backward edge
		- $f'(v,u)=f(v,u)-\alpha \geq 0$
- **Flow Conservation:** Again, only need to check this for vertices that appear on $P$
	- **Case 1:** 
- **Claim 3:** $|f'|=|f| + \alpha$
	- **Proof:** Augmenting path $P$
		- Must be a forward edge since there are no incoming edges into $s$
		- $f'_{out}(s)=f_{out}(s) + \alpha \implies |f'| = |f| + \alpha$

#### Ford-Fulkenson Algorithm (G,s,t)
- $\forall e \in E$, set $f(e) = 0$
	- While there is an s-t path in $G_f$
		- Let $P$ be any s->t path in $G_{f}$ and let $\alpha$ be the smallest capacity on $P$
		- Let $f' = Augment(f, P, \alpha)$
		- set $f=f'$

### Max Flow Min Cut Theorem
- Let $f$ be any flow such that $G_{f}$ does not have any augmenting paths. Then there is an s-t cut $(S,T)$ such that $|f|=c(S,T)$
- 