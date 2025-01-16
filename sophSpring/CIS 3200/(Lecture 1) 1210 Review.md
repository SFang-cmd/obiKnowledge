**Overview of Course Content:**
A. Core Design & Analysis Techniques
- Divide & Conquer
- Dynamic Programming
- Greedy Paradigm
- Amortized Analysis
B. Efficient Algorithms for Fundamental Problems
- Network Design and Routing (Network Flows)
- File Similarity
- Load Balancing on Servers
- Network Reliability
C. Connections Between Problems (Reductions)
- All-pairs shortest paths problem reduces to matrix multiplication
- Arbitrage detection reduces to negative cycle detection
- Google's page-rank algorithm reduces to solving a system of linear equations

**Part 1:** Review of sorting, selection, and basic data structures
**Part 2:** Advance design analysis techniques
- Dynamic Programming
- Greedy Paradigm
**Part 3:** Graph Algorithms
- Network Design
- Shortest Paths
- Network Flow and Applications
**Part 4:** NP-Completeness & Approximation Algorithms
**Part 5:** Sublinear Algorithms

Lecture 1 warm-up problem: **The Chip Testing Problem**
- *Input:* A set of $n$ chips, some of which are bad
- *Goal:* Identify all bad chips, by performing the smallest \# of pairwise tests
- Obs 1: To solve this problem, it suffices to *identify one good chip*
- Obs 2: For this problem to be solvable, it must be that good chips *are in strict majority*
- Obs 3: Any algorithm for this problem requires \__$\Omega(n)$\__ tests

Suppose n is even, then we can't use $\frac{n}{2}$ dividing into two groups because there is one case where:
- When two chips test each other and both are good, they'll output "good, good"
- When two bad chips test each, they can output anything
- When a good chip tests a bad chip, output is good/bad

**Algorithm 1:**
- Pick a chip, and let all others $(n-1)$ chips test it
- Take the majority outcome and declare it to be the status of this chip

**Algorithm 2:**
- If $n=1$ or $2$, then return **any chip as good**
- If $n$ is odd then let $(n-1)$ chips test one of them. If majority decision is good then we are done. Otherwise discard the tested chip
- Pair up the chips into $\left\lfloor  \frac{n}{2}  \right\rfloor$ pairs in an arbitrary manner
	- (a) If a pair is B-B or B-G then discard both chips
	- (b) If a pair is G-G, throw away one chip in each such pair
- Recursively find a good chip among the remaining chips

**Analysis:**
- $T(n) \leq (n-1) + \left( \frac{n}{2} \right) + T\left( \frac{n}{2} \right)$
- $\leq \frac{3n}{2} + T\left( \frac{n}{2} \right)$
- $\leq \frac{3n}{2}+\frac{3n}{4}+T\left( \frac{n}{4} \right)$
- $\leq 3n$

