**Running time & Code Snippets:**
Ex1.
```pseudocode
for (i = 0; i < n, i++) {
	for(j = 0; j < i; j=j+10) {
		print("Hi")
	}
}
```

Given a tight bound on the running time of the code snippet

Find $T(n):$ worst-case running time of the code snippet on an input (i/p) of size $n$
$T(n)=\sum\limits^{n-1}_{i=0}{c\lceil \frac{i}{10} \rceil}$

| i | # iterations of 2 for loops |  |
| ---- | ---- | ---- |
| 0 | 0 |  |
| 1 | 1 |  |
| 2 | 1 |  |
| 3 | 1 |  |
O-bound
$T(n) \leq \sum\limits^{n-1}_{i=0}{\frac{i}{10} + 1}$
$=\sum\limits_{i=0}^{n-1}\frac{ci}{10}+\sum\limits_{i=0}^{n-1}c$
$=\frac{c}{10}(\frac{(n-1)(n)}{2})+cn$
$=\frac{cn^{2}}{20}-\frac{cn}{20}+cn$
$\leq cn^{2}+cn^{2}, \forall n\geq 1$
$=2cn^{2}$
$T(n)=O(n^{2}),{{c_{2}=2c}\choose {n_{0}=1}}$

 $\theta(g(n))=\{f(n)|\exists\text{ positive constants }c_{1}, c_{2}, \& n \text{ s.t. } \forall n\geq n_{0}, 0 \leq c_{1}g(n) \leq f(n) \leq c_{2}g(n)\}$

$\Omega$ bound
$T(n) \geq \sum\limits_{i=0}^{n-1}\frac{ci}{10}$
$=\frac{c}{10}(\frac{(n-1)n}{2})$
$=\frac{cn^{2}}{20}-\frac{cn}{20}$
TST
$T(n)=\Omega(n^2)$, it suffices to show that
$\frac{cn^{2}}{20}-\frac{cn}{20} \geq c_{1}n_{1}^{2}, \forall n\geq n_{0}$
$n^{2}(\frac{c}{20}*c_{1})\geq \frac{cn}{20}$

Set arbitrarily $c_{1}=\frac{c}{40}$
$n^{2}\left(\frac{c}{40}\right)\geq \frac{cn}{20}$
$n \geq 2$

$T(n)=\Omega(n^2)$ where $c_{1}=\frac{c}{40},n_{0}=2$



Ex2. 
```pseudocode
i <- n
while (i >= 10) do
	i <- i/3
	for j=1 to n do
		print(j)
```

O-Bound:
```pseudocode
i <- n
while (i >= 1) do
	i <- i/3
	for j=1 to n do
		print(j)
```

| iter# | value of i at the start of the iter |
| ---- | ---- |
| 1 | $n$ |
| 2 | $n/3$ |
| 3 | $n/3^2$ |
| ... |  |
| t | $n/3^{t-1}$ |
$\frac{n}{3^{t+1}} \geq 1$
$3^{t-1} \leq n$
$t \leq log_{3}(n) + 1$

Thus
$T(n) \leq cn(log_{3}(n) + 1)$
$=cnlog_{3}(n)+cn$
$\leq cnlog_{3}(n) + cnlog_{3}(n), \forall n \geq 3$
$=2cn log_{3}(n)$
$=O(nlog_{3}n), c_{2}=2c, n_{0}=3$

$\Omega$ bound
```pseudocode
i <- n
while (i >= 3^3) do
	i <- i/3
	for j <- 1 to n do 
		print("Hi")
```

| iter # | value of i at the start of the iter |
| ---- | ---- |
| 1 | $n$ |
| 2 | $n/3$ |
| ... |  |
| h | $n/3^{h-1}$ |
| h+1 | $n/3^h$ |
Since over algorithm goes through h iterations,
$\frac{n}{3^{h}} < 3^3$
$3^{h+3}>n$
$h+3 > log_{3}(n)$
$h > log_{3}(n) - 3$

(we assume $log_{3}(n)$)
$T(n) \geq cn(log_{3}n-3)$
$=cnlog_{3}n-3cn$
To show that $T(n) = \Omega(nlog_{3}n)$, it suffices to show that 
$cnlog_{3}n-3cn \geq c_{1}nlog_{3}n$
$nlog_{3}(n)(c-c_{1}) \geq 3cn$
Set $c_{1}=c/2$

$\frac{c}{2}*nlog_{3}n \geq 3cn$
$log_{3}(n) \geq 6$
$n \geq 3^6$
$T(n)=\Omega(nlog_{3}n),c_{1}=\frac{c}{2}, n_{0}=3^6$ 
$T(n)=\theta(nlog_{3}n),c_{1}=\frac{c}{2},c_{2}=2c,n_{0}=3^6$
$log_{3}n = \frac{log_{2}n}{log_{2}3}$
$=\theta(lg(n))$

Ex3. 
```pseudocode
for i=0 to n do
	for j=n down to 0 do
		for k=1 to j-i do
			print(k)
```

Solution:
$\theta(n^3),\theta(n)$

**O-bound**
change the code snippet:
```pseudocode
for i=0 to n do
	for j=n down to 0 do
		for k=1 to n do
			print(k)
```
clearly, this is an upper bound, so
$T(n) = O(n^{3})$

**$\Omega$** **-bound**
```pseudocode
for i=0 to n/4 do
	for j=n down to n/2 do
		for k=1 to n/4 do
			print(k)
```
above pseudocode is lower bound of running time of the above program, since i and j are both subsets of the original i and j loop in the original program

*Want a tight lower bound, so use the closest ones (don't want the "upper bound"), so for the for loop, $j-i$ is the smallest amount of reps*
*In this case, we want the smallest j-i value to prove a tight bound*

k is smallest when j=n/2 and i=n/4, so runs minimum n/4 times, so n/4 is also a subset of running time

$T(n)\geq c(\frac{n}{4}\frac{n}{2}\frac{n}{4})$

Ex4.
```pseudocode
for i=1 to n do
	for j=1 to i*i do
		for k=1 to j do
			print(k)
```
**Solution**
$T(n)=\theta(n^{5})$
$T(n)=\theta(n^4)$

```pseudocode
for i=1 to n do
	for j=1 to n^2
		for k=1 to n^2 do
```
$T(n)=O(n^5)$

**$\Omega$-bound**
```pseudocode
for i=n/2 to n do
	for j=n^2/8 to n^2/4 do
		for k=1 to n^2/8 do
			print(k)
```
can use multiple:
```pseudocode
for i=n/3 to 2n/3 do
	for j=n^2/18 to n^2/9 do
		for k=1 to n^2/18 do
			print(k)
```
preferably here, $j=\frac{n^2}{18}$ works but $j \neq 1$ since we don't know if it is a lower bound of the original program, since k=1 goes to j, and if j=1, we would need to argue why this program is valid too, safer to use j=some value

*want top of j bound to be the smallest i bound, since otherwise might not be conclusive,*
i.e. i=n/3 to 2n/3 --> j=n^2/18 to n^2/9, the n^2/9 is lower bound on the i\*i

Ex5.
```pseudocode
for (i=0,i <= n, i=2*i)
	for j=1 to i do
		print(j)
```
$T(n)=\theta(nlg(n))$, since outer loop runs $lg(n)$ times, while inner loop runs for $n$ times

**$\Omega$-bound**
```pseudocode
for (i= ;i<= ;i=2*i)
	for j=1 to n/1024 do
		print(j)
```
$T(n)=\Omega(nlg(n))$ **NOT TRUE**
Let's say for the sake of example that $T(n)=\Omega(n)$

Why is it true that $\theta(n)$ could possibly be $T(n)$?

True/false: It is possible for $T(n)=$
- $\theta(nlglgn)$ T
- $\theta(n^{1.001})$ F, since $n^{1.001}=n*n^{0.001}$, which is less than $n$ powers
- $\theta(\sqrt{n})$ F
- $\theta(nlg^{2}n)$ F

true ones are between $nlg(n)$ and $n$
$T(n)=\sum\limits_{t=0}^{lg(n)-1}c*2^{t}$
$=c(2^{0}+2^{1}+...+2^{lg(n)-1})$
$=c(2^{lg(n)}-1)=\theta(n)$

($2^t$ is from the fact that the inner loop runs as a function of the outer loop, where each increase in t, the number of iterations, each of the iterations will run twice the previous number)

| iter # | n, number of inputs in the for loop, bounds this |
| ---- | ---- |
| 1 | $2^0$ |
| 2 | $2^1$ |
| 3 | $2^2$ |
| ... |  |
| t | $2^{t-1}$ |
$2^{t-1}< n, t-1 > lg(n)$
$t \geq lg(n)$

Input: int $n \geq 0$
Output: $2^{n}$
1. po2(n)
```pseudocode
if n=0 then
	return 1
else
	return 2*po2(n-1)
```
2. po2(n)
```pseudocode
if n=0 then
	return 1
else
	return po2(n-1)+po2(n-1)
```
3. po2(n)
```pseudocode
if n=0 then
	return 1
else
	tmp <- po2(n-1)
	return tmp+tmp
```


Ex.
```pseudocode
for i=1 to n do
	for j=1 to i*i*i do
		for k=1 to \sqrt(j) do
```

First one goes n times, second goes $n^3$ times, third goes $\sqrt{n^3}$  times bc of the j value
Thus, $O(n^{5.5})$

Lower bound:
```pseudocode
for i=0 to n/2 do
	for j=n^2/4 to n^3/8 do
		for k=0 to n/2 do
		...
```

```pseudocode
for i=0 to n/2 do
	for j=n^3/8^3 to n^3/4^3 do
		for k=0 to n/sqrt(8) do
		...
```
tight bound here is
$\Omega(n^{5.5})$
*WE WANT TO FIND A TIGHT BOUND, so while $n^5$ would be a lower bond, its not the **Best bound***

**GUARANTEED PROBLEM ON CODE SNIPPETS**