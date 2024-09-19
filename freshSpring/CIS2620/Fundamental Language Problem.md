Corresponding to any language $L \subseteq \Sigma^{*}$, there is a canonical (most natural) decision problem:

Given an input $x \in \Sigma^{*}$, does $x \in L$?
Same as [[String Examples]] and [[Binary Representation of Numbers]]

Computing any $0/1$ value function $f:\Sigma^{*} \rightarrow \{0,1\}$
is equivalent to asking does $x \in L_{f}$
$L_{f}=\{x \in \{0,1\}^{*}: f(x)=1\}$

This question is interesting because whenever you are computing a problem whose solution is either yes or no (0 or 1), it can be seen as just a language problem.

How to solve? First [[Model of Computation]]: [[(Deterministic) Finite Automata]]