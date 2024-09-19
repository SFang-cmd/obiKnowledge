Conditional Probability: $P(A|B)=\frac{P(A \cap B)}{P(B)}$
Multiplication Rule: $P(A \cap B) = P(A|B)P(B)$
Law of Total Probability: Let $A_{1},A_{2},...,A_{n}$ be a partition, then
	$P(B)=P(B|A_{1})P(A_{1})+...+P(B|A_{n})P(A_{n})$
**Bayes Rule:**
	$P(A|B)=\frac{P(B|A)P(A)}{P(B|A)P(A) + P(B|A^{c})P(A^{c})}$
	- More Generally,
	$P(A_{i}|B)=\frac{P(B|A_{i})P(A_{i})}{\sum\limits_{j=1}^{n}P(B|A_{j})P(A_{j})}$
	- When to use Bayes Rule? 
		- **If you can switch the conditional probability and it becomes easy, most likely use Bayes Rule**

Ex. For an insurance company, 30% are considered low risk, 50% are average risk, and 20% are high risk. Historic Data suggests that 5% of low risk, 10% of average risk, and 40% of high risk will be involved in an accident in the coming year.
- What is the probability that a randomly selected customer files an accident claim in the coming year?
	- $P(Claim)=P(Claim|Low)P(Low)$
	- $+ P(Claim|Average)P(Average)$
	- $+ P(Claim|High)P(High)$
	- $= 0.05\times 0.3 + 0.10 \times 0.5 + 0.4 \times 0.2 = 0.145$
	- Try using bayes rule?
	- $P(Low|Claim)=\frac{P(Claim||Low)P(Low)}{P(Claim)}$
	- $=\frac{0.05 \times 0.3}{0.145}$

![[Pasted image 20240918123009.png]]
$P(White)=P(White|Box 1)P(Box1)$
$+P(White|Box2)P(Box2)$
$+(P(White|Box3)P(Box3)$
$=\frac{1}{2}\times \frac{1}{3} + \frac{2}{3}\times \frac{1}{3}\times \frac{3}{4}\times \frac{1}{3}= \frac{23}{36}$
Why is Box 3 the most likely?
$P(Box 3|White)= \frac{\frac{3}{4}\times \frac{1}{3}}{\frac{23}{36}}$
$P(Box 2|White)= \frac{\frac{2}{3}\times \frac{1}{3}}{\frac{23}{36}}$
$P(Box 1|White)= \frac{\frac{1}{2}\times \frac{1}{3}}{\frac{23}{36}}$

**Independence**
- Two events $A$ and $B$ are said to be *independent* if
	- $P(A|B)=P(A)$
	- or $P(B|A)=P(B)$
	- or $P(A\cap B) = P(A)P(B)$
- And are dependent otherwise

Ex. **Suppose A and B are two events with**
- $P(A) = 0.5$ and $P(B) = 0.8$
- For what value of $P(A \cup B)$ would A and B be disjoint?
	- Can't because they can't be separate since $P(A) + P(B) = 1.3 > 1$
- For what value of $P(A \cup B)$ would A and B be independent?
	- $P(A \cup B)=P(A) + P(B) - P(A \cup B) = 0.5 + 0.8 - 0.5\times0.8 = 0.9$

