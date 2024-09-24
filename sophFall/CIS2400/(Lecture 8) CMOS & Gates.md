**NOR Circuit Design:**
- Start with the boolean expression
	- NOR is NOT-OR, which is
		- `~(A|B)` <- statement for when output is 1 (True)
- Since I like to start with PDN, find the cases when output is FALSE (output connected to GND), then simplify
- With the simplified expression for PDN, negate it to get the expression for PUN
	- `(A|B)` becomes `~(A|B)`
- From here, convert to (`~A & ~B`) into a PUN

**PLA's:**
- PLA: Programmable Logic Array
- A device where we can configure AND, OR, and NOT gates to implement a function (truth table)
- A brute force method to find a circuit given **only** a **truth table**