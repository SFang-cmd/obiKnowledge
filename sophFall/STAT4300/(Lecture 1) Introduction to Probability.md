Probability vs. Statics:
- Probability finds the chances of events occurring in an idealized population of infinite size
- This we can use to test on sample sizes
- Statistics uses these sample sizes and generalizes to an idealized population
- Thus, this is a cycle

Randomly positive a few times. We want to know what's going to happen next. What's the output? For us, the pistons, we see the output first. We see the output and want to know what's the truth, whether the coin is fair, whether the value is fair. So there are many interesting problems in both ways. 

This class goes in this direction. If you take the follow-up statistics classes, you will learn much more about data analysis. You have to run your experiments, observe the outcomes, and want to know whether the treatment is effective, whether the treating strategy is profitable, and so on.

Motivating Examples
- A simple game:
	- You have a fair coin and your friend has another fair coin, which you decide to toss.
		- You win $3, HH
		- You win $1 if TT
		- You lose $2 if HT or TH
	- What if you choose which side to show?
- Motivating questions:
	- Fair game?
	- How to optimally play this game?

A Paradox:
- Suppose that we have an infinitely large urn and an **infinite** collection of balls labelled 1, 2, 3...
	- 1 minute before, 1-10 are placed and randomly selected
	- 1/2 minutes before, 11-20 are placed in the urn and randombly selected
	- 1/4 minutes before, 21-30 are randomly placed and selected
	- ...
- Question: How many balls are in the urn at 12pm?
	- Infinity minus infinity, so we can prove that with probability 1, the urn is empty
- Tweak slightly:
	- Always remove multiple of 10 ball
		- Prove it is infinity
	- Always remove the smallest ball
		- Is 0, I know exactly when the balls are removed

Polya's Urn Scheme
- An urn contains 1 black and 2 white balls. One ball is drawn at random and its color is noted. The ball is replaced, together with an additional ball of its color. There are now four balls in the urn.
	- Again, one ball is drawn at random from the urn, then replaced along with an additional ball of its color
	- The process contains in this way
- What is the expected number of black balls in the urn just before the 100-th ball is drawn?

Birthday Cake Problem
- Imagine you are having a birthday cake for your friend
- In the cake, we have one candle
	- Use two dials to randomly divide the cake into two pieces
	- The cake is then cut to be that size
- Question: How big will the cake be?
	- Will be the bigger part of the cake

The Envelope Problem:
- Two envelopes, each containing a check, are placed in front of you. You are to choose one of the envelopes, open it, and see the amount of the check. At this point, you can either accept that amount, or you can exchange it for the check in the unopened envelope.

The Best Prize Problem:
- You are to be presented with *n **distinct prizes in sequence***. After being presented with a prize you must imediately decide whether to accept it or to reject and consider the next prize.
- The only information you are given when deciding whether to accept a prize is the relative rank of that prize compared to ones already seen
- Once a prize is rejected it is lost. Your objective is to maximize the probability of obtaining the best prize.
- **What is your best strategy?**
- **How well can you do?**

Ants on a Stick:
- **100 ants are placed randomly on a meter stick.** One more ant named **Alice is placed at the center** of the stick.
- At a certain moment, every ant starts moving in a randomly chosen direction left or right at a constant speed of one meter per minute
- When two ants meet, they instantaneously reverse directions.
- When an ant reaches an end of the stick, it also instantaneously reverses direction.
- **After one minute, all the ants stop. What is the probability that Alice is back at the center of the stick?**

Random Walk
- Your friend Adam asks you to play a game. You draw 100 digits randomly and independently from the set of numbers $\{0,1,2,3,...,9\}$. He asks you to do the following:
	1. Randomly choose one of the first 10 digits
	2. Move forward as many digits as the number that is chosen (move forward 10 digits when a 0 is hit)
	3. Repeat.
	4. Stop when the next move goes beyond digit 100. Record the last digit that is hit.
- Adam then tells you that he knows the digit you recorded
1. Is he bluffing or does he really know?
2. Why?
	1. There is a high probability that two different paths will intersect, at which point they will never be able to separate ever again

Remarks:
- This course studies **randomness** and **uncertainty**
- It introduces the foundational concepts and principles necessary for understanding statistics, machine learning, and data-driven AI
- This is an **interesting and important course**
- **It is NOT an easy course**
- If you work hard, you will be rewarded
	- this course, other courses, job interviews, etc...