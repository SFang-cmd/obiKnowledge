**Greatest Common Divisor (GCD)**
**Input:** Positive integer $a, b$
**Output:** $gcd(a,b)$
Integer $d$ is a common divisor of integers $a,b$ if $d|a$ and $d|b$
$d$ is a $gcd(a,b)$ if
- $d$ is a common divisor of $a,b$
- if $e$ is a common divisor of $a,b$ then $d \geq e$

$gcd(a,b)$
**for** $k \leftarrow 1$ to $min(a,b)$ **do**
	if $k|a$ and $k|b$ **then**
		$ans \leftarrow k$
**return** $k$

Let $d = gcd(a,b), e = gcd(b,c)$. To show that $d = e$,

For $d \leq e$
$d|a$ and $d|b$, thus $d|c$
since $d|b$ and $d|c$, $e = gcd(b,c)$
By definition, $d \leq e$

For $d \leq e$
$d|a$ and $d|b$, thus $d|c$
since $d|b$ and $d|c$, $e = gcd(b,c)$
By definition, $d \leq e$

For $e \leq d$
$e|b$ and $e|c$, thus $e|a$
since $e|a$ and $e|b$, $d = gcd(a,b)$
By definition, $e \leq d$

Ex. 
$gcd(834,678)$
$= gcd(678, 156)$
$= gcd(156,54)$
$=gcd(54,48)$
$= gcd(48, 6)$
$= gcd(...)$

**Euclidian Algorithm:**
To find $gcd(a,b)$
$c \leftarrow a\mod b$
**if** $c = 0$ **then**
	return b
**else:**
	**return** $gcd(b,c)$
	
**Theorem:** Euclid correctly computes the gcd
**Proof:** Assume for contradiction that Euclid fails. 
Among all pairs of integers on which Euclid fails, let $(a,b)$ be a pair s.t. $a+b$ is the smallest of those pairs

**Case 1:**
$a \geq b$
If $c = 0$, Euclid returns b, which is the correct answer. Since Euclid fails, $c > 0$

   $c < b$
$+b \leq a$
$=b+c < a+b$

Since $c > 0$
Euclid returns $gcd(b,c)$
we know from the lemma that $gcd(a,b) = gcd(b,c)$
Since Euclid makes a mistake on $gcd(a,b)$, it must have made a mistake on computing $gcd(b,c)$, a contradiction!

Case II: $b>a$
... COMPLETE PROOF

**Lemma:** Let $a,b \in \mathbb{Z}$, Let $a \geq b > 0$, Let $c = a \mod b$, Then $c < \frac{a}{2}$
**Proof:**
	**Case I:** $b \leq \frac{a}{2}$
	$c < b$ (since c is a remainder of b)
	**Case II:** $b > \frac{a}{2}$
	$c = a-b$ (Since the quotient = 1)
	$< a-\frac{a}{2}$ (subtracting a smaller number, so the resulting number is greater)
	$=\frac{a}{2}$

(minimum 2)
$(a,b) --> (<\frac{a}{2},<\frac{b}{2})--2--> (\frac{a}{2^2},\frac{b}{2^{2}})--...-->(<\frac{a}{2^t},<\frac{b}{2^t})$
|--> $gcd(b, < \frac{a}{2})$

Algorithm terminates after 2t iterations
$\frac{b}{2^{t}}\leq 1$
$2^{t}\geq b$
$t \geq log b = lg(b)$ (always the second notation)

Our algorithm takes no more than $2lg(b)$ iterations
$b = 2^{300}$

**Sorting:**
**Input:** array $A[1,...,n]$ of n distince integers
**Objective:** Sort A in ascending order

**Insertion Sort (A[1...n]):**

**for** $j \leftarrow 2$ to n **do**
	$key \leftarrow A[j]$
	$i \leftarrow j-1$
	**while** $(i > 0)$ and $A[i] > key$ **do**
		$A[i+1] \leftarrow A[i]$
		$i \leftarrow i-1$
	$A[i+1] \leftarrow key$

Ex. $A: [34, 18, 7, 28]$
$A: [18, 34, 7, 28]$
$A: [7, 18, 34, 28]$
$A: [7, 18, 28, 34]$

**Prove using induction** (at the end of iteration $j$, the first $j$ blocks are sorted)

**Proof of running time:**
$IS(A[1...n])$
	**for** $j \leftarrow 2$ to n **do**
		$key \leftarrow A[j]$
		$i \leftarrow j-1$
		**while** $(i > 0)$ and $A[i] > key$ **do**
			$a[i+1] \leftarrow A[i]$
			$i \leftarrow i-1$
		$A[i+1] \leftarrow key$

| Cost | \#times |
| ---- | ---- |
| $c_1$ | $n$ |
| $c_2$ | $n-1$ |
| $c_3$ | $n-1$ |
| $c_4$ | $\sum\limits_{j=2}^{n}{}t_j$ |
| $c_5$ | $\sum\limits_{j=2}^{n}{t_{j}-1}$ |
| $c_6$ | $\sum\limits_{j=2}^{n}{t_{j}-1}$ |
| $c_7$ | $n-1$ |
For cost $c_1$ and $c_4$, the loop needs to loop again to recheck the condition

**Running time:** (No need to do this analysis... EVER, just understand that this happens)
$c_{1}n+(c_{2}+c_{3}+c_{7})(n-1) + c_{4}\sum\limits_{j=2}{n}t_{j}+(c_5+c_6)\sum\limits_{j=2}^{n}(t_{j}-1)$

**Best Case:**
$A$ is sorted in ascending order already $t_{j}= 1$
$c_{1}n+(c_{2}+c_{3}+c_{7})(n-1)+c_{4}(n-1) \approx D*n$ (for some constant)

**Worst Case:** A is sorted in descending order
$t_{j}= j$
$= c_{1}n+(c_{2}+c_{3}+c_{7})(n-1) + c_{4}\sum\limits_{j=2}^{n}t_{j}+(c_5+c_6)\sum\limits_{j=2}^{n}(t_{j}-1)$
$=(c_{1}+c_{2}+c_{3}+c_{7})n - (c_{2}+c_{3}+c_{7)}+ c_4\left(\frac{n(n+1)}{2}-1\right)+ (c_{5}+c_{6})(\frac{(n-1)(n)}{2})$
$\approx D*n^{2}+ D'*n + D''$

**Argue that it takes no more than $n^2$ times:**
$IS(A[1...n])$
	**for** $j \leftarrow 2$ to n **do**  (At most n iterations, $\leq n$)
		$key \leftarrow A[j]$
		$i \leftarrow j-1$
		**while** $(i > 0)$ and $A[i] > key$ **do**  (roughly no more than n iterations, $\leq n$)
			$a[i+1] \leftarrow A[i]$
			$i \leftarrow i-1$
		$A[i+1] \leftarrow key$

Thus, the worst case is $n^2$
We want to look for a **tight** bound, thus there exists an input that uses exactly that $n$th running time

**Can you repeat why we don't know that this is a tight analysis?**

#exam
**GUARANTEED ONE QUESTION ON STABLE MATCHING**
