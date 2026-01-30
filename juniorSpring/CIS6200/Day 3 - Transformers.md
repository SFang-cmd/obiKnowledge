- Context isn't answered in pre-transformer models
- Transformers can take context, and the embedding for just the word "light" will update when given contextual words based on weighted training of vectors (i.e. "light" vs "candle light" vs. "light the candle") have vastly different meanings
- Attention takes a word embedding of a word such as "octopus" and updates the embeddings based on the other words in the context
- Input is each word as an embedded vector, output is a new embedded vector; the output is idempotent to the input
- takes "Sequence if embedding vectors" and outputs "Sequence of embedding vectors"

## Example: Octopus
- "Look at this picture of a purple, fluffy octopus"
- Given the word octopus, the algorithm will ask all the words such as "look" and "picture": "Do you think octopus meaning should change?", different words will affect hange to the octopus

## Attention Calculation:
Calculates key $k_{8}=W_{k}e$
and value $k_{8}=W_{k}e$
Given key and value for each word, given a query for octopus $q_{9}$, we produce an inner product $<k_{4},q_{9}>$, then use a softmax to get the weights of the values

embedding $e_{9}$ for octopus $e_{9}=e_{9}+(softmax_{<k,q>})$ for each key embedding for each word

- Within an attention layer, the only things you can do to increase the model's capacity is to increase the matrix dimensions, or add more attention heads
- Usually models have multiple attention layers for more expressivity

