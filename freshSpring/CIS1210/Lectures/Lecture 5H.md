```pseudocode
MaxHeepify(A, i):
l <- left(i), r <- right(i)
if l <= heepsize(A) AND A[l] > A[i] then
	largest <- l
else
	largest <- i
if r <= heepsize(A) AND A[r] > A[largest] then
	largest <- r
if largest != i then
	swap(A, i, largest)
	MaxHeepify(A, largest)
```

Runtime of Heepify:
$T(n)=\theta(lg(n))$

$T\left(\frac{n}{2}\right)+ O(1)$
(not full story, instead use)
$T(n) \leq T\left(\frac{2n}{3}\right)+ O(1)$
$=\theta(lgn)$

```pseudocode
BuildHeap(A):
heepsizze(A) = |A|
for i <- A down to 1 do
	MaxHeepify(A, i)
```

Runtime is NOT $\theta(nlgn)$

Lemma: there are at most $\leq \lceil \frac{n}{2^{h+1}} \rceil$ nodes at height $h$
$T(n)=O(\sum\limits_{h=0}^{\lfloor lgn \rfloor}h \cdot \lceil \frac{n}{2^{h+1}} \rceil)$
$= O(n\sum\limits_{h=0}^{\infty}{\frac{h}{2^{h}}})$
$=O(n\frac{\frac{1}{2}}{(1-\frac{1}{2})^{2}})$
$=O(n)$

$\sum\limits_{i=0}^{\infty}ic^{i}=\frac{c}{(1-c)^{2}}, |c| < 1$

```pseudocode
HS(A):
	BuildHeap(A)
	for i <- |A| down to 1 do
		Swap(A, 1, i)
		heapsize--
		MaxHeepify(A,1)
```

HS: NOT $O(n)$, cuz comparison-based sorting cannot be done better than $nlg(n)$, so running time is $\theta(nlgn)$

Why? Rationale for HS is:

**Priority Queues:**
- Set of elements
- Elements have key
- Supports following elements:
	- Maximum(A) - $O(1)$
	- ExtractMax(A) $O(lgn)$
	- IncreaseKey(A, i, key)
	- Insert(A, key)

```pseudocode
Maximum(A): (*assuming sorted heap*)
	return A[i]
ExtractMax(A):
	max <- A[i]
	swap(A, heapsize(A), 1)
	heapsize--
	MaxHeapify(A,1)
	return max
IncreaseKey(A,i,key):
	A[i] <- key
	while i > 1 and A[parent(i)] < A[i] do
		swap(A, i, parent(i))
		i <- parent(i)
Insert(A, key):
	heapsize++
	A[heapsize] <- -infinity
	Increasekey(A,heapsize,key)
	
```
