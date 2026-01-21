circa. 2016-2018

### Words and Tokens
- **Tokenizers** break up words into meaningful individual components
- Traditionally:
	- e.g. meaning-ful (separate tokens due to normal words + segmented meanings)
	- From the perspective of understanding the sentence, **meaning** is universal, **ful** also has meaning
	- **meaningful** vs. **meanings** - not agreed whether "stemming" was a good or bad thing, since on one hand, roots are the same, but not the same prefix/suffixes
- Modern:
	- Turning words into values that models can learn
	- e.g. for `GPT2TokenizerFast`, "Hello" is word \#9381
	- if the model has never seen before, it'll just break it down, all the way to characters if necessary
		- **Pros:** won't throw an error bc of typos
		- **Cons:** Loses context on typos
	- Different LLMs will use different tokenizers

### For this class, 1 word = 1 token
- Reduces to simplify, but still pretty much preserves the normal meanings

**How do we get from tokens to models that can produce convincing English??**

### Part 1: Word Embeddings
- **How do we even build ML models that can output words?**
- So far, we're given
	- Input - words that can be converted to sequence of integers
	- Bounded by the set of all english words + individual characters + mispellings + math expressions, etc.
- **Goal \#1:** Convert sentences or words into numbers/values
	- Because we can't do matrix multiplication on words
	- **Old:** Bag of words (vectorized into frequency of each word in known universe)
		- **Issue:** similarity of two one-hot vectors (e.g. $similarity(daffodil, flowers)=0$)
		- In other words, there is no semantic meaning to the word itself
	- How do we get word similarities?
		- Convert one-hot vectors into a vector of the same dimension taht represents the probability that this word occurs **near the input word** (e.g. \# times the word appeared near "flowers / \# times any word appeared near flowers)
		- Now, there is a low-probability for example that aardvark and flower appear close together, so not as similarity
		- **Basically, convert one-hot vector of each word, take that, train on the probabilities of other words, then use the trained neural network to convert the one-hot vectors into vectors that output probabilities that the other words are "close by"**
		- Because we multiply by a one-hot vector, we only take that "column"; thus, the output matrix is an $h$ embedding of that word, where that column is just the probability
		- because $W$ does not need to be $|V|$, $W \in d \times |V|$, so vector is d-dimensional embedding of list of words $|V|$
		- **Our outputs now have vectors that show similarity and also show that we can add/subtract "concepts" (cats - cat) + dog = dogs**
	- **New:** Desirable to have word similarities, where similar words have a higher inner product
		- If we can use vectors, they would tell us if the words are similar, complete opposites, and other things like that, which might be useful
- ***Now we have words represented as vector embeddings!***

### Part 2: Early Models using Embeddings
- **Goal \#2:**  Use these word vectors to do learning
	- Now, we have values corresponding to words
	- How do we take our collection of word embeddings and do learning on that entire sentence/phrase?
- For example, given **input:** "The pizza tasted terrible and I got sick"
- How do we perform sentiment analysis?
	- First, can convert the words into vectors
	- **Issue:** ML algorithms fundamentally perform on fixed-length vectors, so if we have a lot of words, then we have variable length inputs to the algorithm
- **Meme paper:** Take the vectors and average the values together, then feed into a neural network and perform gradient descent
	- This is a wildly STUPID idea
	- Hypothesis of the paper: if I have words such as "terrible" and "sick", it'll have embedding dimensions that might be more negative, thus averaging it together, we can create an averaged vector that learns to train on these specific signals
	- When does it NOT work?
		- Well, when they say "The pizza tasted like dog food", since even though "dog food" has a more neutral sentiment standalone, when we compare it to human food it's supposed to be negative sentiment
	- ***This paper was such a meme because it performed state-of-the-art performance with the dumbest idea; really showed that the RNNs and stuff weren't actually that good***
- CONTEXT IS EVERYTHING!
	- The pizza tasted **terrible** and I got **sick**
	- Words like "dog food" might only be negative sentiment in the context of describing human food
	- Words like "sick" can have either **positive** or **negative** sentiment depending on the context
	- Not just an issue for sentiment - individual words have different meanings depending on context (bass vs bass, light vs light vs light, etc.)
- **Essentially, we need the idea of transformers to be able to update the current vector based on other words within the sentence**

### Transformers solve the problem of context
- Given the word "light", given "candle light", might be a wildly different vectors than "light the candle"
- Then based on those vectors, we can also add things like "reading by candle light"
- Was really expensive, cuz every word can update every other word, so the training is a pain and so much
- Early layers capture generic word vector, such as the "type of light"
- Later layers capture context, slowly nuance a word like "light" into how light was used in the sentence context

