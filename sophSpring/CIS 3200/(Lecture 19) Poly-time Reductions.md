A language $L_{1}$ is said to be poly-time reducible to another language $L_{2}$, denoted $L_{1} \leq_{p} L_{2}$, if there exists a poly-time computable function $f$ such that for any input $x$, we have $x \in L_{1}, \iff f(x) \in L_{2}$

Claim 1: If $L_{1} \leq_{p} L_{2}$ and $L_{2} \in P$, then $L_{1} \in P$ also

Claim 2: Suppose $L_{1} \leq_{p} L_{2}$ and $L_{2} \leq_{p} L_{3}$ then $L_{1} \leq_{p} L_{3}$

**NP-Hard:** A language $L$ is said to be $NP-Hard$ if for all $L'$ in $NP$, $L' \leq_{p} L$

**NP-Complete:** A language $L$ is said to be NP-Complete if (i) $L$ is in $NP$ and (ii) $L$ is NP-Hard

NP-Complete problems are the hardest problems in NP

Claim 3: Suppose $L_{1} \leq L_{2}$ and that $L_{1}$ is NP-Hard. Then $L_{2}$ is also NP-Hard
Proof: Let $L'$ be any $NP$ language. $L' \leq_{p} L_{1}$ and $L_{1} \leq_{p} L_{2}$
By claim 2, $L' \leq_{p} L_{2}$

**A brief introduction to Boolean Formulas**
- A boolean variable $X$ takes $2$ values - True/False
- A literal is a boolean variable $X$ or its negation $\bar{X}$
- A boolean formula on $n$ boolean variables is obtained by applying Boolean operators AND, OR, and NOT to these variables

Example: $(x_{1} \lor \bar{x_{2}} \lor x_{3}) \land (\bar{x_{2}} \lor x_{4}) \land (x_{3} \lor x_{7} \lor x_{9})$
Clause: A clause is an OR of literals
Conjunctive Normal Form (CNF): A Boolean function is said to be in Conjunctive Normal Form (CNF) if it is an AND of clauses

**k-CNF formula:** A k-clause is a clause that contains k literals
- A k-CNF formula is a CNF formula where every clause is a k-clause

**k-SAT Problem**
- **Input:** A k-CNF formula F, on $n$ variables
- **Goal:** Decide if there exists an assignment that satisfies $F$

**Cook '71-Levin'73 Theorem**
- Theorem: 3-SAT is NP-Complete
- 1972: Richard Karp used it as a foundation for a lot of his work

$L_{IND}$
- **Input:** A graph $G(V,E)$ and an integer $K$
- **Goal:** Decide if $G$ contains an independent set of size $\geq K$

An independent set in a graph $G(V,E)$ is a set $X \subseteq V$ of vertices such that $\forall u,v \in X, (u,v) \notin E$

$L_{3SAT} \leq_{p} L_{IND}$
**Input:** $\emptyset = c_{1} \land c_{2} \land \dots \land c_{m}$ where each $c_{i}$ is a clause containing $3$ literals
**Goal:** Reduction function $f$ should ensure the following: $\emptyset$ has a satisfying assignment iff $G$ has an independent set of size $\leq k$

**The Graph G:** A graph with $m$ layers (layer $L_{i}$ will correspond to clause $c_{i}$)
- Logic: Because we want to link specific literals and their not-forms, we want to draw lines between them. If two of them must be true, then there will not be enough independent sets, as we will need an extra independent set if c AND not c, which will form more independent sets $\leq m$

$\implies$ Suppose $\emptyset$ has a satisfying assignment $A$. Show that $G$ has an independent set of size $\geq m$.
- Let $l_{i}$ be the literal in $c_{i}$ that evaluates to True in $A$. Let $I = \{l_{1}, l_{2}, \dots, l_{m}\}$. I forms an independent set

$\impliedby$ Suppose $G$ has an independent set of size $\geq m$ . Show that $\emptyset$ must be satisfiable. Let $I$ be an independent set of size $\geq m$. $H$ will have3 exactly $1$ vertex in each layer. Constraing assignment $A$ by setting all literals in $I$ to be True.
