Ex. Consider the following language:
$L_{count}\{x \in \{0,1\}^{*}: x \text{ has the same number of 0s and 1s}\}$.
**Claim:** $L_{count}$ is not regular
**Proof:** 
$x^{(l)}=0^l$
$x^{(i)}=0^{i} \& x^{(j)}=0^{j} (i \neq j)$
$z=1^{i} \implies x^{(i)}z=0^{i}1^i \in L_{count}$
$x^{(j)}z=0^{j}1^{i} \notin L_{count}$
Thus, $\{0^{l}\}^\infty$ is a set of infinitely many pairwise distinguishable strings

**Claim 2:**
$L_{repeat}=\{xx:x \in \{0,1\}^{*}\}$
$101101 \in L_{repeat}$
$1100 \notin L_{repeat}$
$101 \notin L_{repeat}$

$x^{(l)}:= 0^{l}$. Is it true that $x^{(i)}\& x^{(j)}$ are distinguishable?
$x^{(i)},x^{(j)}, (i < j)$
$z = 0^{i} \implies x^{i}z=0^{i}0^{i}\in L_{repeat}$
$x^{(j)}z=0^{j}0^{i}\in L_{repeat}$ if $i+j$ is even
$j=5,i=3,0^{j}0^{i}=8$

$x^{(l)}:=01^{l}$. For any $i \neq j, x^{(i)}$ and $x^{(j)}$ are distinguishable.
wlog, $i < j$.
$x^{(i)}=01^{i}$, $x^{(j)}=01^{j}$ are distinguishable
Choose $z=10^{i}1 \implies x^{(i)}z=0^{i}10^{i}1 \in L_{repeat}$
$x^{(j)}z=0^{j}10^{i}1, (j > i) \notin L_{repeat}$

The set $\{0^{(l)}\}^{\infty}_{l=1}$ is pairwise distinguishable w.r.t. $L_{repeat}$
Thus non-regular?

___________
$L_{3}=\{0^{i}: i(\mod 3)=1\}$ $L_{3}$ is regular
$L_{square}=\{1^{n}:\text{ n is a perfect square}\}$

**Claim: 3:**
$L_{square}$ is not regular
**Proof:**
Define $x^{(i)}=1^{i^{2}}.$ We will show that $x^{(i)}\& x^{(j)}$ are pairwise distinguishable
$i=2,j=3$, $x^{(2)}=1^{4}$ , $x^{(3)}=1^{9}$ consider $z=1^{5}\implies x^{(2)}z=1^{4},1^{5}=1^{9} \in l_square$
$i < j, z = 1^{2i+1}, x^{(3)}z=1^{9}1^{5}=1^{14}\notin L_{square}$
$\implies x^{(i)}z=1^{i^{2}}*1^{2i+1}=1^{(1+i)^{2}}\in L_{square}$
$x^{(j)}z=1^{j^{2}}*i^{2i+1}=1^{j^{2}+2i+1}$

Since $j^{2}<j^{2}+2i + 1 < (j+1)^{2}$
$x^{(j)}z \notin L_{square}$

**Claim:**
If $L$ is a regular language & y is some string, then $L \cup\{y\}$ is regular