**Quicksort:**
```pseudocode
QS(A(lo...hi)):
if hi <= lo then
	return
pIndex <- floor((lo + hi)/2) (BUT ACTUALLY randomly chosen)
loc <- Partition(A, lo, hi, pIndex)
QS(A,lo,loc - 1)
QS(A, loc + 1, hi)
```

```pseudocode
Partition(A,lo,loc,pIndex)
pivot <- A[pIndex]
swap(A, pIndex, hi)
left <- lo, right <- hi - 1
while left <= right do
	if A(left) <= pivot then
		left++
	else
		swap(A, left, right)
		right --
end while
swap (A, left, hi)
return left
```

**Ex:**

| 1 | 2 | 3 | 4 | 5 |
| ---- | ---- | ---- | ---- | ---- |
| 44 | 16 | 28 | 49 | 64 |
pIndex = 3
pivot = 28

| 1 | 2 | 3 | 4 | 5 |
| ---- | ---- | ---- | ---- | ---- |
| 49 | 16 | 64 | 44 | 28 |
left (49), right (64)

Now, prove $T(n)=O(nlg(n))$
$T(n) = 2T\left(\frac{n}{2}\right)+ cn$
$= \theta(nlg(n))$

FINISH BOARD 2 NOTES HERE

On any array of size $n$, in expectation, the running time of QS is $\theta()$

Let $X$ be the random variable denoting the total # of comparisons
Let $X_{ij}$ be the random variable denoting # of times $y_{i}$ and $y_{j}$ are compared during the RandomQS algorithm
$X_{ij}^{k}=1$ if $y_i$ & $y_j$ are compared in the kth call to partition,
0 otherwise

$X=\sum\limits_{i=1}^{n-1}\sum\limits_{j=i+1}^{n}X_{ij}$
By LOE,
$E[X]=\sum\limits_{i=1}^{n-1}\sum\limits_{j=i+1}^{n}E[X_{ij}]$
$X_{ij}=\sum\limits_{k=1}^{n-1}X_{ij}^{k}$
Let t be the first call to partition when one of $y_{i},y_{i+1},...,y_{j}$ is chosen as a pivot point
$X_{ij}^{k}=0, k<t$ 
$X_{ij}^{t}=1,$ if $y_i$ or $y_j$ is chosen as the pivot, 0 otherwise
$X_{ij}^{k}=0, k>t$, since if it gets to this point, the pivot would not have been established previously

$E[X_{ij}]=\sum\limits_{k=1}^{n-1}E[X_{ij}^{2}]$
$=\sum\limits_{k=1}^{n-1}Pr[X_{ij}^{k}=1]$
$=Pr[X_{ij}^{t}=1]$
$=\frac{2}{j-i+1}$

$E[X]=\sum\limits_{i=1}^{n-1}\sum\limits_{j=i+1}^{n}\frac{2}{j-i+1}$
$=\sum\limits_{j=2}^{n}\frac{2}{j}(n-j+1)$
$=2(n+1)\sum\limits_{j=2}^{n}\frac{1}{1}-2\sum\limits_{j=2}^{k}\frac{j}{j}$


$\frac{2}{2}+\frac{2}{3}+...+\frac{2}{n}$
$\frac{2}{2}+\frac{2}{3}+...+\frac{2}{n-1}$
$\frac{2}{2}+\frac{2}{3}+...+\frac{2}{n-2}$
...
$\frac{2}{2}$

$2(n+1)(\sum\limits_{j=1}^{n}\frac{1}{j}-1)-2(n-1)$
$\leq 2(n+1)(ln(n))-2(n+1)$
$=2nln(n)+2ln(n)-2(n+1)$
$=\theta(nlg(n))$

$T(n)=2nln(n)$
Target: $200nln(n)$
If this is your target, we need to prove that we are still good with this algorithm
$Pr(T(n) \geq 200nln(n))] \leq \frac{2nln(n)}{200nln(n)} = \frac{1}{100}$ (Markov's Inequality bounds the probability here)

Probability that your algorithm runs in $20nln(n)=\frac{1}{10}$
$\leq \frac{1}{10} \leq \frac{1}{10} \leq \frac{1}{10} ... \leq \frac{1}{10}$
ten times,
then the probability that the formula fails in each of 10 rounds is $\leq \frac{1}{10^{10}}$
We only need for the algorithm to succeed one time?! (ASK ABOUT THIS)

(Black Box) -> Median element in an array
Goal: Make the box run in $O(n)$ time

**Input:** Array $A$ of $n$ distinct elements
**Output:** $i$th smallest element of $A$
Proposed algorithm:
1. Partition $A$ into $\lfloor \frac{n}{5} \rfloor$ groups, each containing exactly 5 elements and at most one group containing $< 5 elements$
2. Find the medians of each group
3. Find the median of the medians. Call this element X.
4. Call Partition with x as the pivot. Let $rank(x) = k$
5. if $i=k$, then return $x$
6. else if $i > k$ then find $i$th smallest element on the left side
7. else, find $(i-k)$th element on the right side.

$T(n)=T(\frac{7n}{10})+n$
