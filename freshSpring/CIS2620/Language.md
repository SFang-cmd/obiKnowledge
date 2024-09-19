**Language:** Given an alphabet $\Sigma$, a language $L$ over $\Sigma$ is a subset of $\Sigma^{*}$

**Definition:**
A language, $L(M)=\{x \in \Sigma^{*}: \delta^{*}(q_{0},x) \in F\}$
$M = (Q, \Sigma, \delta, q_{0}, F)$
(uses [[Extended Transition Function]])

Suppose $\Sigma = \{0,1\}$
$L_{odd}=\{x \in \{0,1\}^{*}: \text{ x has an odd number of 1's}\}$
(\*Note: The star denotes strings over $0,1$)
Thus, $1 \in L_{odd}, 10 \in L_{odd,}111 \in L_{odd}, 101 \notin L_{odd}, \epsilon \notin L_{odd}$

Ex. See [[Binary Representation of Numbers]]

There is one problem that is the basis of language: 
[[Fundamental Language Problem]]

[[Theorem]]: The smallest state of a [[(Deterministic) Finite Automata]] is always unique

Can use [[(Deterministic) Finite Automata]] to solve a [[Decision Problem]]

[[Regular Languages]]