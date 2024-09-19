A deterministic finite automaton (DFA) is specified by a 5-tuple
$M=(Q,q_{0},\delta,\Sigma,F)$

$Q$ - set of states
$q_{0}\in Q$ - initial state
$\Sigma$ - alphabet
$F \subseteq Q$ - set of [[Accepting State]]s
$\delta = Q \times \Sigma \rightarrow Q$ - transformation functions for each node (i.e. where different alphabet characters are an input for each of the states)

$q_{0}\in Q, f\subseteq Q, \delta: Q \times \Sigma \rightarrow Q$
So $Q$ are the set of states, $q_{0}$ is the starting state, $\delta$ is the transition function given a state and an alphabet, $\Sigma$ is the alphabet of interest, and $F$ is the final state

See [[Finite Automata Example]]

[[Automata Claims]] - 
Given a DFA $M$, with $Q$ states and alphabet $\Sigma$,
$\implies$ a program which has $1$ variable taking $|Q|$ different values, and it makes one pass on input, this program has has $|Q||\Sigma|$ many $if-then-else$ statements

Advantages of DFA machines:
- Takes $O(n)$ time to implement (only takes as long as there are inputs available, so it is linear)
- In terms of memory, you only store the current state of the program, so the memory is low (probably around 1 variable)
	- Independent of input size

**Advantages of DFA as a [[Program]]**

The goal of DFA: Find the most optimal amount of memory and storage that can be implemented through a single pass of the input in order to achieve a certain output.