Every [[(Deterministic) Finite Automata]] can be mapped to a program --> fed in with a binary string of numbers --> can be converted to a natural number, $\mathbb{N}$

There is a one-to-one mapping from the [[(Deterministic) Finite Automata]] to a binary string
								Thus each DFA can also be identified with natural numbers.
$[\text{set of finite automata identifying with } \mathbb{N}]$

A language is a subset of binary strings, which means the language is a subset of natural numbers

A given language is a subset of $\mathbb{N}$

The set of all languages is the set of subsets of natural numbers - The power set of natural numbers ($2^{\mathbb{N}}$)

There is no way to index the set of all languages with DFA, which means that there must be non-regular languages (since we can't map $2^\mathbb{N}$ to $\mathbb{N}$)

However, does not show anything about how to calculate a non-regular languages, instead need to use [[Calculation of Non-Regular Languages]]