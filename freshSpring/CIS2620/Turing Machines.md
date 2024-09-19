$M$ on input $w$
1.$M$ accepts $w$
2.$M$ rejects $w$
x.$M$ goes off the left end of tape
3.$M$ never terminates on $w$

Given any $TM$, $M: L(M) = \{w: M \text{ accepts } w\}$

$CT$ Thesis: Any physically realizable model of computation can be implemented by a $TM$
- In describing $TM$s, we will describe them using pseudocode

[[(Deterministic) Finite Automata]] x, y ($|x|=n_{1}$, $|y|=n_{2}$)
- The last T positions of $x \;\&\; y$ are the same
- Starting at $q_{0}$ & reading the first $n_{1}-T$ positions of $x$, $M$ is in the state $p$
- """""""""""""""" $n_{2}-T$""""of $y$, $M$ is in state $p$

Suppose $C:=(q, w_{pre},w_{post}) \in (Q\times \Gamma^{*} \times \Gamma^{*})$
	Let $w_{post}=\gamma * w_{post}'$ ($\gamma \in \Gamma, w_{post}' \in \Gamma^{*}$)
	$\delta(q, \gamma)=(q',\gamma',R) \implies Next(C) = (q', w_{pre},\gamma',w_{post}')$
Given configuration $C=(q,w_{pre},w_{post}),$
- Either $q=q_{f}$ or $q=q_{r}$
- Otherwise, there is a uniquely defined configuration $C'=Next(C)$ which is the configuration at the next point in time

$\delta(q,\gamma) = (q',\gamma',L)$
$w_{post}=\gamma*w_{post}'$
$w_{pre}=w_{pre};*\alpha$
Transition function changes $\gamma$ to $\gamma'$
We go from current state $q$ to the next state $q'$
And we also dictate whether we move left or right.
$Next(C)=(q',w_{pre}',\alpha*\gamma'*w_{post}')$

$\delta(q',\alpha)=(q'',\alpha',R)$
$(q'',w_{pre}',\alpha',\gamma'w_{post}')$
On an input $w$ and $TM, M$,
Initial configuration = $(q_{0}, \epsilon, w) (C_{post})$
$C_{0}=c_{initial}, \forall i \geq 0, C_{i+1}=Next(C_{i})$
- Either the sequence $C_{0},C_{1},...,$ is terminating with the last $C_{j}=(q',w_{pre},w_{post})$ where $q' \in \{q_{f},q_{r}\}$
- The sequence $C_{0},C_{1},...$ is non-terminating

If is terminating,
$M$ accepts $w$ if $\exists C_{1},...,C_{T}$
$C_{0}=(q_{0},\epsilon, w)$
$C_{in}=Next(C_{1}), \forall i \geq 0$
$C_{T}=(q_{f},w_{pre},w_{post})$ for some $w_{pre}, w_{post}\in \Gamma^{*}$

**Observation:** Suppose on input w, the configuration of $TM \; M$ are $C_{0},C_{1},...$ such that $C_{i}=C_{j}=C_{j+k(j-i)}$ for any $k \geq 0$
Thus $M$ never halts on $w$

**Definition:** A language $L$ is said to be recursively enumerable (recognizable)
	if $\exists TM \; M$ s.t. $L=L(M)$

**Definition:** A language $L$ is said to be decidable if $\exists \; TM, M$ s.t. $M$ halts on every input &$L = L(M)$

Suppose we are given an equation:
$x^{3}-31x^{2}+7x+9=0$
$A()${
1. <- 1
2. WHILE(TRUE) {
3. CHECK IF $x^{3}-31x^{2}+7x+9 = 0$,
4. if yes, return 1;
5. else x <- x + 1;}

$\delta'(q,\sigma)=(q',\sigma,R)$
if $\delta(q,\sigma)=q'$
$q'(q,\gamma,)$

**Claim:** If $L$ is regular, $L$ is decidable
**Proof:** Suppose $M=(Q,\Sigma,\delta,q_{0},F)$ is a DFA for $L$.
Define $M' = (Q',\Sigma,\Gamma,\delta',q_{0}, q_{f},q_{r})$
$\Gamma = \Sigma \cup \perp$
$Q' = (Q \cup \{q_{f}\} \cup \{q_{r}\})$

Turing Machines as Strings:
**Claim:** Corresponding to any $TM$, $M$, there is a "standard representation" $<M>$ .
In particular, there is an algorithm (i.e. a halting TM) which given $<M>$ can output
1. |States = |Q|
2. |Tape alphabet| = |P|
3. |Input alphabet|
4. For any $q \in Q, \gamma \in \Gamma, \delta(q,\gamma)$

Every entry of $S$ requires $1+log|Q| + log|\Gamma|$ bits
Specifying $\delta$ requires $O(|Q||\Gamma|)\cdot (log|Q| + log|\Gamma|)$

$M=(Q,\Sigma,\Gamma,\delta,q_{0},q_{\gamma},q_{f}=2)$

Specifying $\delta$
$\delta(i,j)$ ($i \in 0,...,|Q|-1$)
($j \in 0,...,|\Gamma|-1$)
$=(i',j',\{L,R\})$

**Theorem:** There is a $TM$ called the Universal Turing Machine ($U_{TM}$) with the following properties
On input $(<M>, w)$,
1. accepts if $M$ accepts $w$
2. rejects if $M$ rejects $w$
3. does not halt if $M$ does not halt on $w$

By convention, if a string $x$ does not correspond to a valid TM, we're going to treat it as corresponding to a default TM which rejects every input

To simulate $T$ steps of $M$ on $w$, $U_{TM}$ requires $C_{M}\cdot Tlog(T)$ steps where $C_{M}$ is a constant dependent on $M$

$A_{TM} = \{<M>,w: M \text{ accepts } w\}$

**Claim:** $L(U_{TM})=A_{TM}\implies A_{TM}$ is r.e.
$U_{TM}$ is not a halting $TM$

Q: Is $A_{TM}$ decideable?
If answer were yes,...