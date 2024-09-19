Let A&B be sets. Then a function from Set A to Set B is a relation s.t:
$\forall a \in A, \exists \lambda b \in B$ s.t. $(a,b) \in f$ ($\lambda$ = exactly one)

In English: A **Function** from Set A to Set B is a relation such that
$\forall a \in A$, there exists exactly one $b \in B$ s.t. $(a,b) \in f$

**Notation:**
$f: A -> B$
$A:$ domain of $f$
$B:$ co-domain of $f$
if $(a,b) \in f$, then we write $b = f(a)$
$b:$ is known as the image of $a$ under $f$
$Ran(f) = \{b \in B | \exists a \in A s.t. b = f(a)\}$
(The Range of $f$ is the set of all $b$ where the function exists)

**Definitions:** Given $f: A -> B$
**Equality:** two functions are equal if they have the same domain, same co-domain & the same mapping
(#EXAM: MEMORIZE THESE TERMS AND IF YOU CIRCLE BIJECTIVE, CIRCLE INJECTIVE AND SURJECTIVE)
$f$ is **one-to-one** or **injective** if $\forall a, a' \in A s.t. a \neq a', f(a) \neq f(a')$
$f$ is **onto** or **surjective** if $\forall b \in B, \exists a \in A s.t. b = f(a)$
$f$ is **1-1 correspondence** or **bijective** if it is **injective** and **surjective**

Ex. Let $f: A -> B$
Let $|A| = a, |B| = b$
How many different functions from $A$ to $B$ are possible?
$b^a$, since for each element $a$ in the domain, each of those can map to any of the $b$ elements, repeatable

**Practice on Surjection and Injection:**
$f_{1}: \mathbb{Z} \rightarrow \mathbb{Z}$
$f_1(x)=x^2$
$f_{2}:\mathbb{R}^{non-neg} \rightarrow \mathbb{R}^{non-neg}$
$f_{2}(x) = x^2$
injective, surjective, bijective
$f_{3}(x) = x + 1$
$f_{3}: \mathbb{Z} \rightarrow \mathbb{Z}$
injective, surjective, bijective

Putting together [[Inverse Functions]], [[Composition Functions]], and general function properties:
**Ex**
$f: A \rightarrow B, g: B \rightarrow C$
(i) Prove that if
- $f$ is surjective & $g$ is surjective, $g \circ f$ is surjective
7
Let $c \in C$. In order to show that $\exists a \in A$, $g \circ f(a) = c$
Since $g$ is surjective, $\exists b \in B$ s.t. $g(b) = c$ 
Since $f$ is surjective, $\exists a \in A$ s.t. $f(a) = b$
Thus, $g \circ f = g(f(a)) = g(b) = c$, thus showing that $\forall c, \exists a \in A$ s.t. $(g\ \circ f (a) = c)$

(ii) Prove that if $f$ and $g$ are both injective then $g \circ f$ is injective
Proof: Suppose
$g(f(a)) = g(f(a'))$
T.S.T. $a = a'$
$g$ is injective $\implies f(a)=f(a')$
$f$ is injective $\implies a = a'$

#EXAM