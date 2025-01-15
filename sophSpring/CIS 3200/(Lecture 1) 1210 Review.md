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
- Obs 3: Any algorithm for this problem requires \____ tests
- 

Suppose n is even, then we can't use $\frac{n}{2}$ dividing into two groups because there is one case where:
- When two chips test each other and both are good, they'll output "good, good"
- When two bad chips test each, they can output anything
- When a good chip tests a bad chip, output is good/bad

**Algorithm 1:**
- Pick a chip, and let all others $(n-1)$ chips test it
- Take the majority outcome and declare it to be the status of this chip