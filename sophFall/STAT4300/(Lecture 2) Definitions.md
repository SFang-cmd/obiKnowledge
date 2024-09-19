**Random Experiment:** A process whose outcome is uncertain
- E.g. tossing a coin once or several times
- Picking a card
- ...

**Sample Space:** The sample space of a random experiment is the set of all possible outcomes

**Simple Events:** The individual outcomes are called simple events

**Event:** A collection of one or more simple events

$P(A)$: The **probability** that event $A$ will occur
- If you can keep track of each event, many interpretations are equivalent

Ex. (Experiment:) Toss a coin 3 times
**Sample Space:** 
$\Omega=\{HHH,HHT,HTH,HTT,THH,THT,TTH,TTT\}$
(2 possible outcomes for each coin, so $2*2*2=8$ possible outcomes)
**Events:**
$A=\{HHH,HHT,HTH,THH\}$ - At least 2 heads

Ex2. (Experiment) Record the sex of each newborn infant until the birth of a male is observed
**Sample Space:**
$\Omega = \{M,FM,FFM,FFFM,...\}$
(infinite number of outcomes)

Ex3. An executioner offers a final chance for freedom:
- There are 20 balls, 10 white and 10 blue. All 20 are put into two urns by the prisoner
- Executioner will first pick one urn, then one ball at random
- If the ball is white, prisoner set free; blue, he will be executed
- What's the sample space describing the prisoner's possible allocation options?
	- **Sample Space:**
		- $\Omega = \{[(1,0),(9,10)]...\}$, where $\{[(w_{1},b_{1}),(w_{2},b_{2})]..\}$
	- Best chance is to leave one urn with one white ball, put the rest in the other
	- Probability is closer to $\frac{1}{2}(\frac{1}{1})+\frac{1}{2}(\frac{9}{19})$, which is closer to 75% chance of surviving

**Basic Concepts:**
- The **union** of two events $A$ and $B$, $A \cup B$, is the event consisting of all outcomes that are either in $A$ or in $B$ or in both events
	- "A or B"
- The **complement** of an event $A$, $A^{C}$, is the set of all outcomes in $\Omega$ that are not in $A$
	- "not A"
- The **intersection** of two events $A$ and $B$, $A \cap B$, is the event consisting of all outcomes that are in both events
	- "A and B"
- When two events $A$ and $B$ have no outcomes in common, they are said to be **mutually exclusive***, or **disjoint** events

Use Venn Diagram to visualize

**Rules:**
- **Commutative Laws:** $A \cup B = B \cup A, A \cap B = B \cap A$
- **Associative Laws:** $(A \cup B) \cup C = A \cup (B \cup C)$
	- $(A \cap B) \cap C = A \cap (B \cap C)$
- **Distributive Laws:** $(A \cup B) \cap C = (A \cap C) \cup (B \cap C)$
	- $(A \cap B) \cup C = (A \cup C) \cap (B \cup C)$
	- Proof: Show that one element is the subset of the other set, and vice versa
		- Suppose $x \in (A \cup B) \cap C$
		- Then $x \in A \cup B$ AND $x \in C$
		- Then ($x \in A$ OR $x \in B$) AND $x \in C$
		- If $x \in A$ and $x \in C$, then $x \in A \cap C$ OR $x \in B$ and $x \in C$, then $x \in B \cap C$
		- $x \in (A \cap C) \cup (B \cap C)$
	- Do other proof (same as 1600)
- **DeMorgan's Laws:** $(\cup_{i=1}^{n}A_{i})^{c}=\cap_{i=1}^{n}A_{i}^{c}$, $(\cap_{i=1}^{n}A_{i})^{c}=\cup_{i=1}^{n}A_{i}^{c}$
	- AKA $(A_{1}\cup A_{2} \cup ... \cup A_{n})^{c}=A_{1}^{c}\cap A_{2}^{c} \cap ... \cap A_{n}^{c}$
	- Proof:
		- $x \in (A_{1}\cup A_{2} \cup ... \cup A_{n})^{c}$
		- So $x \notin A_{1}\cup A_{2} \cup ... \cup A_{n}$
		- $x \notin A_{i}$ for all $i = 1,2,...,n$
		- So $x \in A_{i}^{c}$ for all $i = 1,2,...,n$
		- $x \in A^{c} \cap ... \cap A_{n}^{c}$

**Probability Distribution:**
- Probabilities are values of a set function, also called a **probability distribution**. This function assigns real numbers to the various subsets (events) of a sample space $\Omega$ (This event: that probability)
- Probability distributions satisfy the following rules
- **Axioms of Probability:**
	- Axiom 1: For any event $A, 0 \leq P(A) \leq 1$
	- Axiom 2: $P(\Omega) = 1$
	- Axiom 3: If $A_{1},A_{2},A_{3},...$ is a countable (finite or infinite) collection of mutually exclusive events, then
		- $P(A_{1}\cup A_{2}\cup A_{3}\cup ...) = \Sigma P(A_{i})$
- These axioms of probability requires no proofs
- The rules only serve to exclude assignments inconsistent with our intuitive notion of probability
- Probability of an event can be interpreted as the limiting relative frequency of the event

**Properties of Probability:**
- For any event $A$, $P(A^{c})=1 - P(A)$
	- Either an event is in $A$ or is in $A^{c}$
	- $\Omega = A \cup A^{c}$
- If $A \subset B$, then $P(A) \leq P(B)$
	- Proof:
		- If $A \subset B$, then
		- $B = A \cup (A^{c}\cap B)$
		- $P(B) = P(A) + P(A^{c}\cap B)$ (Since complement serves axiom 3)
		- Thus, $P(B) \geq P(A)$
- For any two events $A$ and $B$,
	- $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
	-                  $=P(A)+P(A^{c}\cap B)$
- For three events $A$, $B$, and $C$,
	- $P(A \cup B \cup C) = P(A) + P(B) + P(C) - P(A \cap B) - P(A \cap C) - P(B \cap C) + P(A \cap B \cap C)$

**Equally Likely Outcomes:**
- For many experiments, it is natural to assume that all outcomes in the sample space are equally likely to occur
- If there are $N(S)$ possible equally likely outcomes, then the probability assigned to each is $\frac{1}{N(S)}$
- **Proposition:** If there are $N(S)$ possible equally likely outcomes and an event $A$ consists of $N(A)$ outcomes, then $P(A) = \frac{N(A)}{N(S)}$

Ex. Three dice are rolled and their scores added. Are you more likely to get 9 or 10, or vice versa?
- $(x_{1},x_{2},x_{3})$
- For sum to 9:
	- (1,2,\_) ... (1,6,\_) - 5 elems
	- (2,1,\_) ... (2,6,\_) - 6 elems
	- (3,1,\_) ... (3,5,\_) - 5 elems
	- (4,1,\_) ... (4,4,\_) - 4 elems
	- (5,1,\_) ... (5,3,\_) - 3 elems
	- (6,1,\_) ... (6,2,\_) - 2 elems
	- \# triples with a sum of 9: $5+6+5+4+3+2 = 25$
- For sum to 10:
	- (1,3,\_) ... (1,6,\_) - 4 elems
	- (2,2,\_) ... (2,6,\_) - 5 elems
	- (3,1,\_) ... (3,6,\_) - 6 elems
	- (4,1,\_) ... (4,5,\_) - 5 elems
	- (5,1,\_) ... (5,4,\_) - 4 elems
	- (6,1,\_) ... (6,3,\_) - 3 elems
	- \# triples with a sum of 9: $4+5+6+5+4+3=27$
- $P(sum=9)=\frac{25}{216}$
- $P(sum=10)=\frac{27}{216}$



