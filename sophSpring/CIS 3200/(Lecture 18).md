### Ford-Fulkenson (G,s,t)
- $\forall e \in E, f(e) = 0$
	- While there is an s-->t path in $G_{f}$
		- Let $P$ be any s-->t path in $G_{f}$
		- and let $\alpha$ be the smallest capacity on $P$
		- $f'=Augment(f,P,\alpha)$
		- $f=f'$

#### Max Flow Min Cut Theorem