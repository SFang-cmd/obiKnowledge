CNF Satisfiability = $\{<\phi>:\phi \text{ is a CNF formula}, \exists p s.t. \phi(\rho)=1\}$

(CNF-SAT)
$\phi(x_{1},\underline{  },x_{n})=c_{1}\land...\land c_{m}$ s.t. each "clause" $c_{i}$ is an OR over literals $c_{1}=(x_{i_{1}}\lor \neg x_{i_{2}} \lor x_{i_{3}} \lor ... \lor \neg x_{i_{k}})$
$\phi(x_{1},x_{2},x_{3})=(x_{1} \lor \neg x_{2})\land (x_{3}\lor x_{2)}\land (\neg x_{3})$
$x_{3}=0$
$x_{2}=1$
$x_{1}=1$
CNF formula $\phi$ with $m$ clauses & $n$ variables, $|<\phi>|=\theta(mn)$
**Fact:** CNF-SAT is in NP

**Cook-Levin Theorem:** CNF-SAT is NP-complete
CNF-SAT is in NP & $\forall L \in NP, L\ leq^{p}$ CNF-SAT

Given input $x$ to CNF-SAT H is polynomial time on $<\phi>$
- H runs in polynomial time
- $x \in L \iff <\phi>$ is satisfiable
$L \in NP \iff \exists V(.,.) s.t. V(x,y)$ runs in time $(|x|+|y|)^{O(1)}$
1. $x \in L \implies \exists y, V(x,y)=1$
2. $x \notin L \implies \forall y, V(x,y)=0$
Polynomial time
$V(x,.) \implies \phi_{v,x}(y,z) \text{ is a CNF formula}$
If $V(x,y)=1, \exists z s.t. \phi_{v,x}(y,z)=1$
$V(x,y)=0,\forall z \phi_{v,x}(y,z)=0$

$\phi_{v,x}$ is satisfiable
($\#$ of classes in $\phi_{v,x}$ iff $\exists y\;s.t. v(x,y)=1$)
($\#$ of variables will be bounded by $n^{\theta(1)}$)

**Fact:** Every Boolean $fn$, i.e. $f=\{0,1\}^{L}\rightarrow \{0,1\}$ has an equivalent CNF-formula $\phi_l$ s.t. $\phi_{L}(x)=1$ iff $f(x)=1$
$\phi_{L}$ has $L$ variables & at most $2^{L}$ clauses
**Proof:** Consider the function $g:\{0,1\}^{n}\rightarrow \{0,1\}$ where $g=1-f$

| $x_1$ | $x_2$ | $g$ |
| ----- | ----- | --- |
| 0     | 0     | 1   |
| 0     | 1     | 0   |
| 1     | 0     | 0   |
| 1     | 1     | 1   |
$(\bar{x_{1}}\land \bar{x_{2}}) \lor (x_{1} \land x_{2})$
For $g$, there is a DNF formula $\psi$ with $\leq 2^{L}$ terms s.t. $\psi$=1 iff $g=1$
Basically, go over each of the terms that $g=1$, at each point, we can encode the $x_{1}$ and $x_{2}$ to a clause of the DNf.
Then, 
$f = 1-g \equiv \neg(\psi)=\neg(T_{1}\lor ... \lor T_{m})$
$=(\neg T_{1}) \land (\neg T_{2})... \land (\neg T_{M})=C_{1}\land...\land C_{M}$
$T_{1}=\neg x_{1}\land x_{2}$
$\neg T_{1}=\neg(\neg x_{1}\land x_{2})= x_{1}\lor \neg x_{2}$

*Note: CNF - Conjunctive Normal Form*
*DNF - Disjunctive Normal Form* = OR of AND of literals
$\psi = T_{1} \lor ... \lor T_{m}$
where each $T_{i}$ is an AND over literals
