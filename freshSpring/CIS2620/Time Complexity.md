Definition: Let $\tau: \mathbb{N} \rightarrow \mathbb{N}$ be an increasing function.
Let $M$ be a $TM$. Then the **time complexity** of $M$ is said to be $\tau(n)$ if for all inputs $x$ of length $n$, $M$ halts on $x$ in $O(T(n))$ steps

Ex.
$(T(n)=n^2)$
On inputs of length $n$, $M$ takes $\leq 6n^{2}+2n$ steps

**Definition:** We say a language $L \in DTIME(T(n))$ if $\exists$ a TM $M$ s.t. $L=L(M)$ & the time complexity of $M$ is $\tau(n)$

**Fact:** If $f(n), g(n)$ are increasing functions, & $f(n)=O(g(n))$ $[\frac{f(n)}{g(n)} \leq c \text{ as n } \rightarrow \infty]$

$DTIME(f(n)) \subseteq DTIME(g(n))$
$f(n)=n^{2}, g(n)=n^{3}$
$DTIME(n^{2})\subseteq DTIME(n^3)$

Time Hierarchy Theorem: If $f(n)\& g(n)$ are such that $f(n)log(f(n))=o(g(n))$, $(\frac{f(n)log(f(n))}{g(n)}\rightarrow 0$ as $n \rightarrow \infty)$
$L_{2}=\{<M>:\text{ On input <M>, if M halts in } O(n^{2}) steps, then <M> \in L_{2} \text{ iff M doesn't accept <M>}\}$
**Fact:** For any $k-tape$ TM $M, \exists$ simple tape TM $M'$ s.t. $L(M) = L(M')$ & further, if on input $x$, $M$ halts $T_x$ steps, then $M'$ halts in $T_{x}^{2}$ steps.

**Fact:** For any program, in the RAM model, $\exists$ single tape TM $M'$ s.t. $L(M)=L(M')$ s.t. $L(M) = L(M')$ & if $M$ halts in $T_{x}$ steps on input $x$, then $M'$ halts in $O(T_{x}^{3})$ steps.

$P:=\cup_{k \geq 1}DTIME(n^k)$
(P - proxy for efficiently solvable problems)

**Claim:** Class $P$ is invariant for single-tape TMs, multitape TMs, and RAM machines.

**Proof:** If $L \in DTIME (n^{c})$ for k-tape TM,
	$\implies L \in DTIME(n^{2})$ for single tape TM

**Claim:** The class $P$ is closed under union, complement & intersection
**Proof:** Let $L \in P$, i.e, $M$ is a halting TM s.t. $L=L(M)$ & $M$ halts in $O(n^{c})$ steps.
Then consider

**Claim:** Let $L_{1}$ and $L_{2} \in P$. Then $L_{1}\cdot L_{2}=\{x\cdot y:x \in L_{1},y \in L_{2}\}$ is also in $P$.

(Given a number $x$ s.t. $0 \leq x \leq N$), decide if $x$ is a prime or not.)
Point is the elementary algorithm to decide if alg is prime or not is not actually polynomial time.

(Agarwal-Kayal-Saxena gave the first deterministic polynomial time algorithm for primality testing-$O(logN)^{6}$)

Elementary Algorithm takes $O(\sqrt{N})$ steps = $2^{log(N)/2}$

**Fact:** For two numbers $x,y$ between $0$ and $N$, we can add them in time $O(log(N))$.

**Fact:** For two numbers $x,y$ between $0$ and $N$, the grade school multiplication algorithm takes $O(log^{2}(N))$ time.

Schönage-Strassen (70's) can be improved to $O(log(N)\cdot log(log(N)))$

Ex.
Suppose you have been given $N$ integers $0 \leq w_{1},w_{2},...,w_{N}$. $\{1,...,N\}$
Is it possible to split $\{1,2,...,N\}$ into $2$ sets $(S,\bar{S})$ s.t.
$\sum\limits_{i \in S}w_{i}=\sum\limits_{i\in\bar{S}}w_{i}$
Algorithm for this problem which runs in time, $O(N^{2}M)$, which runs in square of number of integers times the integer value.

Size of input = $O(Nlog(M))$
Because using $t$ bits, we can represent an integer of size $M$ with $log(M)$ bits, so there are $2^{t}=M$ total integers possible.

Running time is polynomial in the **input size** $t$.

Thus, algorithm runs in $O(N^{2}2^{t})$ time
**Basically the algorithm does not run in polynomial time bc for each increase in bit number, the number of possible integers it encodes increases exponentially**

Polynomial time Algorithms:
Any graph on $n$ vertices can be represented as a matrix of size $n\times n$
where each entry is $\{0,1\}$
- Size of input $\Theta(n^2)$ relative to $n$ vertices number

**Claim:** Let's assume that $L_{1},L_{2}\in P$. Then $L_{1}\cdot L_{2}=\{x \cdot y: x \in L_{1},y \in L_{2}\}$ is also in $P$.
**Proof:** Let $M_{1},M_{2}$ be TMs for $L_{1}$ & $L_{2}$ respectively. The running time of $M$ is $n^{c_{1}}$ & $M_2$ is $n^{c_{2}}$ (for some $c_{1},c_{2} > 0$)
Can just use pseudocode.
```pseudocode
M(z){
1. n <- length(z)
2. For (i=0 to n) {
3. let x <- z_[0:i],y <- z_[i+1:n]
4. Run Mz on x and M2 on y; accept if both accept;
5. reject z}
}
```
Run time = $n$ iterations of for loop & the ith iteration takes time $O(i^{c_{1}}+(n-i)^{c_{2}})$
$\leq O(n^{c_{1}}+n^{c_{2}})$
Total time = $n\cdot(Oln^{c_{1}}+n^{c_{2}})$
$=n^{max\{c_{1}+1,c_{2}+1\}}$

Do not apply concatenation repeatedly for the homework question

Let $G$ be an undirected graph
Can you color with 3 colors such that adjacent vertices do not have the same color?

A language $L \in NP$ if $\exists$ an algorithm $V(\cdot, \cdot)$ & has the following guarantees
(i) $V(x,y)$ runs in time $O((|x|+|y|)^{G})$ for $c_{1}>0$
(ii) If $x \in L, \exists y$ s.t. $|y| \leq |x|^{c_{2}}$ & $V(x,y)=1$
(iii) If $x \notin L, \forall y$ s.t. $|y| \leq |x|^{c_{2}}$, $V(x,y)=0$

3-COLORING = $\{<G>:G\}$ is colorable
**Claim:** 3-Coloring is in NP
**Proof:** $V(<G>,S)$ where $S$ is a list of colors; one per vertex
Size of $S=O(n)$ (because for each vertex, we require $O(1)$ bites)
	**Verification Algorithm:** Goes over every pair $(u,v) \in E$ & vertices that $S(u) \neq S(v)$
	Total time = $O(|E|)=O(n^{2})$

