Let $P$ be a [[Property of Languages]] ($P \subseteq$ set of languages)

Given any such [[property]] $P$, define $L_{p}=\{<M>:L(M) \in P\}$

The property $L_{p}$ is [[non-trivial]] 
if $\exists M_{y}, M_{n}$ s.t. $<M_{y}> \in L_{p}\;\&\;<M_{n}>\notin L_{p}$

[[Rice's Theorem]]: Any non-trivial semantic property $L_{p}$ is undecidable

Consider two properties:
1. Property $P$ language is finite -> $p=\{<m>:L(M) \text{ is finite}\}$
	- Then $L_{p}$ is undecidable
2. $P'$: language is recursively enumerable
	- $p'=\{<M>:L(M) \text{ is r.e.}\}$
	- is decideable

Create a $\phi \in P$ or $\phi \in P$
We will reduce $A_{TM}$ to $L_{p}$
$<M>,w \implies <M'>$
$M$ accepts $w$ --> $L(M') \in P$
$M$ does not accept $w$ --> $L(M') \notin P$

$M'(x)$ {
1. Run $M$ on $w$
2. If $M$ rejects $w$, reject $x$;
3. Else run $U_{TM}$ on $<M_{y}>,x$
4. Accept if $U_{TM}$ accepts
}

If $M$ doesn't halt on $w \implies L(M') = \phi)$
	$M$ rejects $w \implies L(M')=\phi$
If $M$ doesn't accept $w \implies L(M')=\phi \;\&\; L(M') \notin P$

If $M$ accepts $w$
$\implies L(M')=L(M_{y})$
$\implies L(M') \in P$

Thus, $L_p$  is undecidable
**Assumption 2:** $\phi \in P \iff \phi \notin \bar{P}$
Observe that $L(M_{n)}\notin P \iff L(M_{n)}\in \bar{P}$
$\implies L_{\bar{P}}$ is undecidable
Thus, $\bar{L_{\bar{P}}}$ is also undecidable

