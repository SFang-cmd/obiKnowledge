**Quick Review:**
- Law of Total Probability: Let $A_{1},A_{2},\dots,A_{n}$ be a partition, then
	- $P(B)=P(B|A_{1})P(A_{1})+..$

 Ex.
 - There are 3 dice:
	 - Die 1: {2,2,2,5,5,5}
	 - Die 2: {3,3,3,3,3,6}
	 - Die 3: {1,4,4,4,4,4,}
- Player A rolls a die of his choice and then player B rolls one of the remaining dice. Whoever gets the higher number wins.
- Do you want to go first or second?
	- Die 1 vs. Die 2:
		- $A = \{\text{Die 2 shows a higher number than Die 1\}}$
		- $P(A)=P(A|\text{Die 1 shows 2})P(\text{Die 1 shows 2})$
		- $+ P(A|\text{Die 1 shows 5})P(\text{Die 1 shows 5})$
		- $=1\times \frac{1}{2} + \frac{1}{6}\times \frac{1}{2}$
		- $=\frac{7}{12}$
	- Die 2 vs. Die 3:
		- B = event that Die 3 shows a higher number than Die 2
		- P(B) = P(B|Die 2 shows 3)P(Die 2 shows 3) + P(B|Die 2 shows 6)P(Die 2 shows 6)
		- $=\frac{5}{6} \times \frac{5}{6} + 0 \times \frac{1}{6}$
		- $=\frac{25}{36}$
	- Die 3 vs. Die 1:
		- C = event that Die 1 shows a higher number than Die 3
		- P(C) = P(C | Die 3 shows 1)P(Die 3 shows 1) + P(C | Die 3 shows 4)P(Die 3 shows 4)
		- $1 \times \frac{1}{6} + \frac{1}{2} \times \frac{5}{6}$
		- $=\frac{7}{12}$

Ex.
- Two coins, A and B show heads with respective probabilities 1/4 and 3/4. Suppose that one of these coins is randomly selected
- Suppose the selected coin is tossed twice and both land heads, what is the probability that coin B was the one selected?
	- B = {The selected coin is B}
	- HH = {The coin shows heads on both tosses}
	- $P(B|HH) = \frac{P(HH|B)P(B)}{P(HH|B)P(B)+P(HH|B^{c})P(B^{c})}$
	- $=\frac{\left( \frac{3}{4} \right)^{2} \frac{1}{2}}{\left( \frac{3}{4} \right)^{2} \frac{1}{2} + \left( \frac{1}{4} \right)^{2} \frac{1}{2}}$
	- $=\frac{9}{10}$
- What if the selected coin is tossed 3 times and all land heads?
	-  $P(B|HHH) = \frac{P(HHH|B)P(B)}{P(HHH|B)P(B)+P(HHH|B^{c})P(B^{c})}$
	- $=\frac{\left( \frac{3}{4} \right)^{3} \frac{1}{2}}{\left( \frac{3}{4} \right)^{3} \frac{1}{2} + \left( \frac{1}{4} \right)^{3} \frac{1}{2}}$
	- $=\frac{27}{28}$

**Ex. Polya's Urn Scheme**
- An urn contains 1 black and 2 white balls. A ball is drawn at random and its color is noted. The ball is replaced, along with an additional ball of its color. There are now 4 balls in the urn.
- Again, one ball is drawn at random from the urn, then replaced along with an additional ball of its color.
- The process continues in this way.
- Q1: What is the probability that the 2nd ball is black?
	- $B_{i}=\{\text{The ith ball is black}\}$
	- $W_{i}=\{\text{The ith ball is white}\}$
	- $P(B_{2})=P(B_{2}|B_{1})P(B_{1}) + P(B_{2}|W_{1})P(W_{1})$
	- $\frac{2}{4} \times \frac{1}{3} + \frac{1}{4} \times \frac{2}{3}$
	- $=\frac{1}{3}$
- Q2: Given that the 2nd ball is black, what is the probability the 1st ball is black?
	- $P(B_{1}|B_{2})=\frac{P(B_{2}|B_{1})P(B_{1})}{P(B_{2})}$
	- $=\frac{\frac{1}{6}}{\frac{1}{3}} = \frac{1}{2}$
- Q3: What is the probability that the 3rd ball is black?
	- Many possibilities:
		- $B_{1} \cap B_{2}$
		- $B_{1} \cap W_{2}$
		- $W_{1} \cap B_{2}$
		- $W_{1} \cap W_{2}$
	- These form a partition:
		- $P(B_{3})=P(B_{3}|B_{1} \cap B_{2})P(B_{1} \cap B_{2}) + P(B_{3}|B_{1}\cap W_{2})P(B_{1} \cap W_{2})$
		- $+P(B_{3}|W_{1}\cap B_{2})P(W_{1}\cap B_{2}) + P(B_{3}|W_{1} \cap W_{2})P(W_{1} \cap W_{2})$
		- $=\frac{3}{5} \left( \frac{1}{3} \times \frac{2}{4} \right) + \frac{2}{5}\left( \frac{1}{3} \times \frac{2}{4} \right) + \frac{2}{5} \left( \frac{2}{3} \times \frac{1}{4} \right) + \frac{1}{5} \left( \frac{2}{3} \times \frac{3}{4} \right)$
		- $=\frac{1}{3}$

Ex.
- Adam has a coin that shows heads with a probability of $\frac{1}{4}$, while Bob has a coin that shows heads with a probability of $\frac{3}{4}$. They take turns tossing their coins, with Adam going first, following the sequence ABABAB.... The first person to get heads wins.
- What is the probability that Adam wins?
- Consider the 3 events
	- H = 1st toss heads,
	- TH = 1st toss tails, 2nd toss heads
	- TT = 1st and 2nd toss tails
- $P(A)=P(A|H)P(H) + P(A|TH)P(TH) + P(A|TT)P(TT)$
- $=1 \times \frac{1}{4} + 0 \times \dots + P(A) \times \frac{3}{4} \times \frac{1}{4}$
	- *Note:* $P(A|TT) = P(A)$, since no improvement from either person, so same as original probabilities
- $\left( 1-\frac{3}{16} \right)P(A)=\frac{1}{4}$
- $=\frac{4}{13}$

Ex. 100 Prisoners Problem
- The warden of a prison offers 100 death row prisoners, who are numbered from 1 to 100, a last chance
- The warden goes into a room and prepares 100 boxes with lids that are labeled 1-100. Then he randomly shuffles 100 tickets, also labeled 1-100, thoroughly, and puts one ticket in each box, closing the lid behind it
- The prisoners enter the room, one after another. Each prisoner may open and look into 50 boxes in any order. The boxes are closed again afterwards. If, during the search, every prisoner fines their number in one of the boxes, all prisoners are pardoned. If just one prisoner does not find his number, all prisoners die
- Before the first prisoner enters the room, the prisoners may discuss strategy - but may not communicate once the first prisoner enters to look in the boxes
- **Is there a good strategy?**
- **What is the optimal strategy?**
- 