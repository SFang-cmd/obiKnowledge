GUARANTEED QUESTION IN EXAM
(Most likely) Relations and counting OR relations and set proofs

Let's represent relations as a directed graph
R: $rel^n$ on set A
vertices: elements on A
edges: $aRb \implies (a,b) \in E$
(two edges are **always** adjacent)

**Relation Definitions on Directed Graphs**
- R is **reflexive** iff each vertex in *G is adjacent* to itself
- R is **symmetric** iff $\forall u,v \in V, u \neq v, (u,v) \in E \implies (v,u) \in E$
- R is **antisymmetric** iff $\forall u,v \in V, u \neq v$, either:
	- no edges between $u \& v$ OR
	- exactly one edge between $u \& v$
	- $u R v \land vRu \implies u=v$ **(They have to be equal, or they don't exist, this condition is if $u \neq v$ in the original given)**
- R is **transitive** iff . 

**Operations on relations:**
- $R_1,R_2$
- $R_{1}\cup R_2$
- $R_{1}\cap R_2$
- $R_{1} \backslash R_2$
- $R_{2}\backslash R_1$

Ex. A: set of all students at Penn
B: set of all courses at Penn

$R_1$ contains (a,b) if student a in A has taken course $b \in B$.
$R_2$ contains (a,b) if student a needs b to graduate

$R_{1}\cap R_2$: Set of relations where student a needs b to graduate and they've already taken it

Inverse of a relation on $n$
$R: rel^{n}$ from A to B
$R^{-1}=\{(b,a)|aRb\}$

$A = \{1,2,3\}$
$R = \{(1,1),(2,2),(3,3),(1,2)\}$
$R^{-1}=\{(1,1),(2,2),(3,3),(2,1)\}$

**Proof.** R is a relation on set A
Then R is symmetric iff $R=R^{-1}$
Solution:
($\implies$) R is symmetric $\implies R=R^{-1}$
Let $(a,b) \in R$
To show that $(a,b) \in R^{-1}$,
$(b,a) \in R$ ($\therefore$ R is symmetric)
$(a,b) \in R^{-1}$ (by definition of inverse)
$(b,a) \in R^{-1}$ be an arbitrary but particular element.
To show that $(b,a) \in R$,
$(a,b) \in R$ (by definition of inverse)
$(b,a) \in R$ (R is symmetric)

(ADD IN BACK IMPLIES)

Composition of relation
$R: rel^n$ from set A to set B
$S: rel^n$ from set B to set C
Composition of S with R is given by
$S \circ R = \{(a,c) | \exists b \text{ s.t. } aRb \land bSc\}$

Ex.
$R: rel^{n}on set A$
$R^{1} = R$
$R^{2}= R \circ R$
$R^{3}= R \circ R \circ R$
...
$R^{n+1}= R^{n}\circ R$

**Thm:** R: Relation on set A
Then R is transitive iff $\forall n \geq 1, R^{n}\subseteq R$
Proof:
($\impliedby$)$\forall n \geq 1, R^{n}\subseteq R \implies$ R is transitive
	$R^{1}\subseteq R, R^{2}\subseteq R, R^{3}\subseteq R...$
(WTS) given $u,v,w \forall A, uRv \land vRw \implies uRw$
Since $uRw \in R \circ R$, then because $R \circ R = R^{2}\subseteq R$, (THIS STEP COMES FROM THE SUBSET PROOF METHOD (i.e. if x in W then x in S means W is a subset of S))
This means that $uRw \in R$, thus transitive, since $R^{n}\subseteq R$ and $uRw \in R$ and $uRw \in R^n$

$R^{2}= R \circ R = \{(x,z) | xRy \text{ and } yRz\}$

($\implies$)R is transitive $\implies \forall n\geq 1, R^{n}\subseteq R$
(Use Induction:)
**IH:** Let $k \geq 1$ be an integer. Assume that $R^{k}\subseteq R$
**BC:** $R^{1}= R$
**IS:** TST $R^{k+1} \subseteq R$,
Let $(x,y)$ be an arbitrary but particular element in $R^{k+1}$
TST $(x,y) \in R$,
By definition, $R^{k+1}=R^{k}\circ R$.
$\exists z \in A$ such that
$(x,z) \in R$ and $(z,y) \in R^k$
Since $R$ is transitive, $(x,y) \in R$

(Can't just say a,b,c,d, etc. bc we can't prove that a,d is in R, even if it is in R^n)