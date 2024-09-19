Notion of configurations:
	Program(TM) M on input W
	At time $t=0$, $w_1$|......|$w_t$| _ | _
				^ $q_{0}$
	At time $t=1$, $\gamma_1$|$w_2$|......|$w_t$| _ | _
				^$q_1$

The idea is that once we have reached a tape state, we can simulate the future steps without even needing to know previous states or functions, given that you know the transition functions of a current TM.

At time $t=1$, $\gamma_1$|...|$\gamma_l$|$\alpha_1$|......|$\alpha_s$| _ | _
				^$q_r$

Configuration: $(q_{r},\gamma_{1},...,\gamma_{l},\alpha_{1},...,\alpha_{s})$
The configuration stores the current state value, the pointer to the current value, and the state of the tape, thus encompassing everything.

**Claim:** Suppose on inputs $w_{1}$ and $w_{2}$, the $TM$ $M$ reaches the configuration $C$ on $w_{1}$ at time $T_{1}$ and $M$ reaches $C$ on $w_{2}$ at time $T_{2}$

1. Then either $M$ accepts both $w_{1}$ and $w_{2}$
2. M rejects both $w_{1}$ & $w_{2}$
3. $M$ does not halt on $w_{1}$ & $w_{2}$

Ex. Suppose $\delta(q_{\gamma},\alpha_{1})=(q_{\gamma+1},\beta_{1},L)$, then the tape at this point will always take the same input tapes at the same state and move in the same ways afterwards

$L_{composite}=\{i \in \{0,1\}^{*}: i \text{ is the binary representation of composite numbers}\}$

```pseudocode
M(i){
1. J <- 2
2. IF (i % j == 0) && (j != i) {accept i}
3. J <- J + 1
4. go to Step 2}
```

$L(M) = L_{composite}$
