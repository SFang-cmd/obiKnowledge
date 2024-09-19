From the definition of a transition function, $\delta(q,\sigma)=$ if the automaton is in a state $q$ & reads $\sigma$, $\delta(q,\sigma)$ is the next state.

For **extended transition functions:**
$\delta^{*}:Q \times \Sigma^{*} \rightarrow Q$
$\delta^{*}(q,x)$ is the state that the automaton reaches starting at $q$ & reading string $x$

Definition of $\delta^{*}$
$\delta^{*}(q,x):$
(i) if $|x| = 0$ (i.e. $x=\epsilon$), $\delta^{*}(q,x)=q$
(ii) if $|x| > 0$, let $x = y\sigma$, $y \in \Sigma^{*}$, $\sigma \in \Sigma$
	inducting, $\delta^{*}(q,x)=\delta(\delta^{*}(q,y),\sigma)$

Essentially, you are splitting the string into a substring with the last character being an individual string, which recurses until the problem reaches the state, $q$, in which it works back up to the final state of the extended transition function. This is a recursive solution, which is much smaller, but may take more time to solve.

Given this definition, we can define a [[Language]] of [[(Deterministic) Finite Automata]] as [[Language]]