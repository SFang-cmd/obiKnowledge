The idea that, given some [[Regular Languages]], does it have a certain property?

Ex.
**Problem 1:** Given a DFA M, is $L(M) = \phi$? ($\phi$ represents empty)

If a DFA has $Q$ states and alphabet $\Sigma = \{0,1\}$

|  | 0 | 1 |
| ---- | ---- | ---- |
| 1 |  | $log\|Q\|$ |
| 2 |  |  |
| 3 |  |  |
| 4 |  |  |
| ... |  |  |
| Q |  |  |
To represent a number Q in binary, needs $log|Q|$ bits
Total, there are $Q$ states to account for for each of the numbers, thus there are $2Qlg|Q|$ total size of a DFA on $Q$ states.


The total size of representing a DFA on $Q$-states
($\Sigma = \{0,1\}$), ($O(Qlog|Q|$) (Order of $Qlog|Q|$)

To decide if $L(M)$ is empty, run DFA/BFS from $q_{0}$ & check whether $\exists q \in F$ is reachable from $q_{0}$. If such a $q$ exists, then $L(M) \neq \phi$ & vice-versa

Runtime = $O(|Q|log|Q|)$
If $\Sigma \neq \{0,1\}$, then runtime $O(|Q||\Sigma|log|Q|)$

**Problem 2:** Given a DFA M, decide if $L(M) = \Sigma^{*}$
Given DFA M, define $M'$ (same as M) with accepting & rejecting states flipped.

$L(M')=\Sigma^{*}\backslash L(M)$
Now, run P1 solution on $M'$

**Problem 3:** Suppose we're given 2 DFAs $M_{1}, M_{2}$. Is $L(M_{1})\cap L(M_{2}) = \phi$?
Given two languages, if the intersection is regular, then their DFA is regular too.

**Solution:** Construct the DFA $M'$ such that $L(M')=L(M_{1})\cap L(M_{2})$
Time to come up with $M' = O(|Q_{1}||Q_{2}|log|Q_{1}||Q_{1}|)$
Now run $P_1$ on this