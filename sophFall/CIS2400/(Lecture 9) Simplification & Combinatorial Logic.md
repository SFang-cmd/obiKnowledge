**PLA to Boolean Expression**
- You can simplify a PLA to a boolean expression
- Ex.
	- `(~A & ~B & ~C) | (~A | B)...`

**PLA Pros & Cons:**
- A PLA can encode any boolean logic, but may not be the most efficient

**Aside: XOR Gate**
- Performs the XOR operation

**One Bit Incrementor "PLA"**
- Implementing a single-column of an incrementor:
- Basically, XOR adds two elements, if they are both 1, then an AND gate will carry a number to the next digit (this is the incrememntor)

**N-Bit Adder**
- CarryIn: Assumed to be zero if not present
- CarryOut: Useful for detecting overflow
- Inputs: $A,B,CarryIn$
- Output: $S, CarryOut$
- Ripple Adder:
	- Not used in industry because each further down adder takes input from previous adders, so it isn't as efficient and is $O(n)$ speed

**Subtractor:**
- Build a subtractor from an adder
- Calculate `A - B = A + -B`
- Negate `B`
- Recall `-B = NOT(B) + 1`
- Approach 1:
	- Negate `B` and add `+1`, place in adder with `A`
- Approach 2:
	- Negate `B` and place in adder with `A` and carryIn `+1`

**The Multiplexer:**
- **Selector/Chooser of signals**
- Shorthand: "Mux"
- If selector bit `S = 0`, select `A`, otherwise, if `S = 1`, choose `B`
- Can do more than just 2: `S = 00,01,10,11`, can choose between 4 inputs

**Combined Adder/Subtractor:**
- Approach 1: Take the adder and subtractor and feed it into a mux to change between an adder and subtractor
- Approach 2: Take adder and mux it with input B to output either `B` or `~B`. Then take this input and adder into input and return `0` or `1`