If you write a program, it is a **fixed** program, which is supposed to give you the correct answer no matter what the input/how long the input is. It is a fixed number not depending on how long the input size is. This is why a [[(Deterministic) Finite Automata]] is **finite**

DFA as a program:
- One pass on input
- O(1) memory (really is $log_2(Q)$ memory, since each bit stores an order of magnitude, where with $t$ bits, there are $2^t$ options)
- O(n) running time (n-size of input)

*This program is pretty optimal*