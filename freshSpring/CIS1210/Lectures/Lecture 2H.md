**Running time of Algorithms:**
Empirical analysis
- implement & then run it on various inputs
- **Drawbacks:**
	- Must be implemented
	- try on a limited set of inputs
	- to compare the two algorithms, one needs to implement the algorithm using the same software

**Analytical:**
- Need to develop a **Model of Computation:**
	- RAM (model)
	- high level operations take constant time:
		- arithmetic operations
		- for structure (if statements?)
		- return
		- comparison
		- assign var
		- array index
		- all integers are stored in a word in memory
		- all memory access take the same amount of time
		- unlimited memory
	- **Analysis Methods:**
		- Worst case analysis
		- Asymptotic analysis (how the algorithm works when $n \rightarrow \infty$)
		- **Asymptotic analysis:**
			- $O,\Omega,\theta,o,\omega$ (will use first 3 a lot)
			- $O(g(n))=\{f(n)|\exists\text{ positive constants }c \& n_0 \text{ s.t. } 0 \leq f(n) \leq cg(n), \forall n\geq n_0\}$
			- The $n_0$ basically says that we don't care about numbers that are finite, we are looking at "end behavior" (how it looks after a million iterations)
			- $\Omega(g(n))=\{f(n)|\exists\text{ positive constants } c \& n_{0} \text{ s.t. } f(n) \geq cg(n) \geq 0, \forall n\geq n_0\}$
			- $\theta(g(n))=\{f(n)|\exists\text{ positive constants }c_{1}, c_{2}, \& n \text{ s.t. } \forall n\geq n_{0}, 0 \leq c_{1}g(n) \leq f(n) \leq c_{2}g(n)\}$
			- Ex.
			- $$\lim_{n \rightarrow \infty} \frac{f(n)}{g(n)}=\{\begin{align*} 0 &, o(g(n))\\
\infty &, f(n)=\omega(g(n))\\
c, &, f(n)=\theta(g(n))
\end{align*}$$
Little $o$ is basically just big $O$ without the $theta$, so not the exact bound

**Asymptotic practice:**
Ex. Prove that $7n-2=\theta(n)$
**Solution:** TST $7n-2=O(n)$
i.e. TST $7n-2 \leq cn, \forall n \geq n_0$
Clearly, $7n-2 \leq 7n, \forall n \geq 1$
Here, $7=c_2,1=n_0$

TST $7n-2=\omega(n)$
i.e. TST
$7n-2 \geq cn, \forall n\geq n_0$
$(7-c)n \geq 2$
$c=6,n_{0}=2,n_0=2$

Ex. Prove that $10n^{3}+55n^{2}+10=O(n^3)$
Solution:
$10n^3+55n^2+10$
$\leq 100n^{3}+100n^{3}+100n^{3}, \forall n\geq 1$
$=\frac{300n^{3}}{c}$

Ex. Prove that $3^{66}=O(1)$
$3^{66} \leq 3^{66}*1, \forall n \geq 1$

Ex. Prove that $\frac{n^{2}}{8}-50n=\theta(n^2)$
Solution
TST $\frac{n^2}{8}-50n=O(n^2)$,
i.e. TST $\frac{n^{2}}{8}-50n\leq c*n^{2},\forall n \geq n_0$
choose $c_2=1,n_0=1$

TST $\frac{n^{2}}{8}-50n= \Omega(n^2)$
i.e. $\frac{n^{2}}{8}-50n \geq c*n^{2},\forall n \geq n_0$
$n^{2}\left(\frac{1}{8}-c\right)\geq 50n$
$n\left(\frac{1}{8}-c\right)\geq 50$
$c=\frac{1}{16}$ (arbitrarily pick a value, c)
$\frac{n}{16}\geq 50$
$n \geq 800$
So $c_1=\frac{1}{16},c_2=1,n_0=800$

Ex. Prove $7n-2=\Omega(n^{10})$
Solution: TST
$7n-2 \geq c*n^{10}, \forall n\geq n_0$
It suffices to show that $7n \geq c*n^{10}, \forall n \geq n_0$
$7 \geq c*n^9$
$n \leq (\frac{7}{c})^\frac{1}{9}$ (Not true)

Ex. Prove that
$n^{1000001}=O(n)$
Solution:
$n^{1000001} \leq c*n,\forall n\geq n_0$
$n^{0.0000001}\leq c$ (Also not true)

Ex. Prove that $lg(n)=O(n)$
Induction on $n$, we will prove that $lg(n) \leq 1*n, \forall n\geq 1$
IH: $lg(k) \leq k$ for some integer $k \geq 1$
BC: $n=1$
$LHS=lg(1)=0$
$RHS=1$
IS: TPT
$lg(k+1)\leq k+1$
$LHS = lg(k+1)$
$\leq lg(k+k)$
$=lg(2k)=lg(2)+lg(k)$
$\leq 1+k$ (by IH)

$(log_{b}n)^{x}= O(n^y)$, since any log function power function will be bounded by any power function.

Ex. prove that $3n^{100}=O(2^n)$
Proof: Induction on $n$
$3n^{100} \leq c*2^{n},\forall n \geq n_0$
$c=3*100^{100}$

IH: Assume that $3k^{100} \leq 3*100^{100}*2^{k},\forall k \geq n_0$
IS: TPT $3(k+1)^{100} \leq 3*100^{100}*2^{(k+1)},\forall k \geq n_0$
$LHS = 3(k+1)^{100}$
$=3[{100 \choose 0}k^100*1^0+{100 \choose 1}*k^{99}*1^{1}+ {100 \choose 2}*k^{98}*1^{2}+...+{100 \choose 100}*k^{0}*1^{100}]$
$\leq 3[100^{0}*k^{100}+100^{1}*k^{99}+100^{2}*k^{98}+...+100^{100}*k^0]$
$=3*k^{100}((\frac{100}{k})^{0}+(\frac{100}{k})^{1}+(\frac{100}{k})^{2}+...+(\frac{100}{k})^{100}), k \geq 200$
$3*100^{100}*2^{k}*\sum\limits_{i=0}^{\infty}(\frac{1}{2})^{i}=3*100^{100}*2^{k+1}$
(Note: $\sum\limits_{i=0}^{\infty}(\frac{1}{2})^{i}=2$)

$n^{x}=O(r^{n})$
$n^{1000000}=O(100001^{n})$

Thm. if $f(n)=O(g(n))$ &
	$g(n)=O(h(n))$ then
	$f(n)=O(h(n))$

Thm. if $f(n)=O(h(n))$ &
	$g(n)=O(h(n))$ then
	$f(n)+g(n)=O(h(n))$

Ex. Prove that
$n^{10}=O(2^{lg^{3}(n)})$ & $2^{lg^{3}(n)}=O(2^n)$
$2^{lg^{3}(n)}=(2^{lg(n)})^{lg^{2}(n)}=n^{lg^{2}(n)}$
Since $n^{10}$ and $n^{lg^{2}(n)}$ have the same base, look at these
Clearly, $10 = O(lg^{2}(n))$, so the above is true
$10=O(lg^{2}(n))$

Theorem: Polylog of $n$ is $\omega$ of power of $n$

| $n$      | $lg n$        |
|$2^{lg(n)}$ | $2^{lg(lg(n))}$ |

Any power function is bounded by an exponential function