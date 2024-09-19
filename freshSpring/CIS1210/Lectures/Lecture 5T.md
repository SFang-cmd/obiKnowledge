Deterministic Select

**Input:** Array $A$ of $n$ distinct elements
**Output:** $i$th smallest element of $A$

$Select(A,i)$ (Algorithm):
1. Divide the array into $\lfloor \frac{n}{5} \rfloor$ groups of size exactly 5 and at worst one group of at most 5 elements
2. Find the medians of each of the groups. Call this set M.
3. $x \leftarrow Select(M,\lceil \frac{n}{10}\rceil)$ \\ (Median of the medians)
4. Partition array A around x. Let $k = rank(x)$
5. if $i=k$ then return x.
6. else if $i<k$ then return Select(A[1....k-1], i)
7. else return Select(A[k+1...n], i-k)

Ex. 
$13,36,45,18,5 | 29,36,44,86,71 | 60,31,12,50$
$13,36,45,\textbf{18},5 | 29,36,\textbf{44},86,71 | 60,31,12,\textbf{50}$

$13, 36, 18, 5, 29, 36, 31, 12, \textbf{44}, 86, 71, 60, 50, 45$

18,44,50

If we take $i=6$, clearly $rank(x)>6$

**Runtime Recurrence:**
$$
T(n) = \cases{O(1)
\\T\left(\frac{n}{5}\right) + O(n)
}
$$

Let's say the following are medians:
![[Pasted image 20240213103906.png]]
Where each vertical column is the list of numbers, and the middles are medians. Note that here, the median boxed by the purple is considered the median of medians, $x$.

In the picture, we are removing the above group of numbers for sure.
![[Pasted image 20240213104128.png]]

WTS: Minimum # of elements that we can eliminate
$\geq 3(\frac{1}{2}\lfloor \frac{n}{5} \rfloor - 2)$ (we disregard the partial last element and the one with the median of medians, so minus 2)
(1/2, for the left or right processing, which is half of all the groupings.)
(n/5 is the number of groups)
(-2 for the edge cases/center case, since we don't have 5 there)
(3 for the total number of ones we know are definitely less than or greater than the number)
$\geq \frac{3n}{10}-6$

Max # elements left in the array that we recurse on is 
$\leq \frac{7n}{10}+6$

Thus the runtime recurrence is:
$$
T(n) = \cases{O(1)
\\T\left(\frac{n}{5}\right) + T\left(\frac{7n}{10} + 6\right) + O(n)
}
$$

**Not too concerned about being "sharp" in the analysis**
i.e. constants and lower power functions don't really matter in our analysis.

Need to prove $T(n)=O(n)$ | $T(n) = \Omega(n)$
$\Omega(n)$ is trivial, since we have a base case of $O(n)$ in the recurrence

For $O(n)$:
$T(n) \leq T\left(\lceil \frac{n}{5} \rceil\right)+ T(\frac{7}{10}+6)+an$

Induction:
BC: $n=140$
IH: Assume that for some int $k \geq 140$,
for all $j$ s.t. $140 \leq j \leq k-1$,
$T(j) \leq cj$
IS: Want to prove that $T(k) \leq ck$ (Using strong induction)
$T(k) \leq T\left(\lceil \frac{k}{5} \rceil\right)+ T\left(\frac{7k}{10}+6\right)+ ak$
$\leq c\left(\lceil \frac{k}{5} \rceil\right)+ c\left(\frac{7k}{10}+6\right)+ ak$ (by IH)
$\leq c\left(\frac{k}{5}+1\right)+ c\left(\frac{7k}{10}+6\right)+ ak$
$=\frac{2ck}{10}+c+\frac{7ck}{10}+6c + ak$
$=\frac{9ck}{10}+7c +ak$
$=ck + (\frac{-ck}{10}+7c +ak)$
For the above expression to be $\leq ck$, we want
$\frac{ck}{10} \geq 7c + ak$
$c\left(\frac{k}{10}-7\right)\geq ak$
$c\left(\frac{k-70}{10}\right)\geq ak$
$c \geq \frac{10ak}{k-70}$
Set $k=140$
And $c \geq 20a$
(go back and replace the n= \_\__ to satisfy the base case, etc.)

(THINK ABOUT HOW THIS MAY WORK IF $\frac{7k}{10}+6$ is instead $\frac{9k}{10}$)

**Stacks and Queues:**
**Stacks:**
- Array
- Needs support for push and pop

`push(obj)`
`//s: stack size`
`//a: array size`
*Note: s is always less than or equal to the array*
`//c: initial size of the array`
`//A[0...a-1]`
```pseudocode
Push:
A[s] <- obj
s++
if s == c then
	a <- a + c
	Copy all elements into the new array
```
$T(n)$: Worst case running time of $n$ pushes
$T(n)=O(n^2)$
$$T(n) = n + c + 2c + 3c +...+ n\\
=n + c[1 + 2 + 3 + ... + \frac{n}{c}]\\
=n + c(n/2)\\
=\theta(n^2)\\
$$

```pseudocode
Push:
A[s] <- obj
s++
if s == c then
	a <- 2*a
	Copy all elements into the new array
```
What if instead use `2*a`? No difference
Worst-case time of a single push: $O(n)$
The # of pushes $= n$
Worst case becomes $O(nlg(n))$

$T(n) =$ time for $n$ pushes + time to copy
$= n + 1 + 2 + 2^2 + ... + n$
$= n+1+2+2^2+2^3+2^{lg(n)}$
$=n + (2^{lg(n) + 1} - 1)$
$=n+(2n - 1)$
$=\theta(n)$
Copy takes linear time, while the time it takes to double the array is $lg(n)$

Worst case time of a single push is still $n$, with $n$ copies

However, the **Amortized time** of our operation is $O(1)$
**Amortized time:** $\frac{T(n)}{n}=\frac{3n}{3}=3$

```pseudocode
pop()
obj <- A[s]
s--
if s <= ______ then
	a <- a/s
```

Disadvantage of this strategy: **Thrashing**
**Thrashing** where user pushes and pops at a factor of 2 that causes significant time loss, most not optimal times. usually combatted by only reducing the array after the array size reaches 1/4 of its original size

**Queues:**
Follows First In, First Out invariant (FIFO)
![[Pasted image 20240213114113.png]]

