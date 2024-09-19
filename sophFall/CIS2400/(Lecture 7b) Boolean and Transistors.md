**Boolean Simplification:**

**De Morgan's Law**
- `~(A & B) = ~A | B`
- `~(A | B) = ~A & ~B`
- Provides a way to convert between AND to OR

**De Morgan's Law: Demo**
- Write a statement equivalent to OR, but without using OR
	- `A | B`
	- `~~(A | B)`
	- `~(~A & ~B)`

**Charge, Current, Voltage**
- Charge can be either positive or negative
- Current: the rate of flow of positive charge
- Voltage: Positive charge want to move from places with higher voltage to lower voltage

**What is a Transistor (MOSFET Type)?**
- An electrical device that acts like an **electrical switch**
- 3 Electrical Contacts/Terminals: Gate, Drain, Source (G, D, S)
- Gate controls flow of current between Drain and Source terminals; this style transistor is called a MOSFET

**Two Types of MOSFET**
- nMOS
	- GATE Voltage MUST BE > Body, Source, Drain to be ON
	- (voltage must be high)
- pMOS
	- GATE Voltage MUST BE < Body, Source, Drain to be ON
	- (Voltage must be low)

**Voltage as Bits**
- Transistors are the basis for all digital electronics
	- We've seen that they work by controlling the flow of charge
- We can map bits onto different voltages:
	- High voltage - we'll call this state "1"
	- Low voltage - we'll call this state "0"

**CMOS Transistors Simplified**
- nMOS:
	- If 1 - it is connected
	- If 0 - it is disconnected
- pMOS:
	- If 1 - disconnected
	- If 0 - connected

**CMOS Circuits as Logical Circuits**
- Instead of thinking of voltages, we can analyze our circuit think of in terms of bits "1" or "0"
- Consider the previous circuit:
	- Output is the same as whatever "source" it is connected to
	- pMOS: on when input is low
	- nMOS: on when input is high

**PUN & PDN**
- We can split our "NOT" circuit into two halves:
- Pull Up Network (PUN)
	- "Pulls" the output "Up" to "1"
	- <u>Can only contain pMOS Transistors</u>
- Pull Down Network (PDN)
	- "Pulls" the output "down" to "0"
	- **<u>Can only contain nMOS Transistors</u>**
- Output can only be connected to "1" or "0" at any time
	- **Exactly one** of PUN or PDF can be "ON" at a time
- We will see more complex examples in a moment

**Rules & Suggestions for Design**
- Rules:
	- You cannot have pMOS transistors in the PDN
	- You cannot have nMOS in the PUN
	- Exactly one of PDN/PUN must be "on," at a time
		- Cannot have neither connected to output
		- Cannot have both connected to output
	- Every transistor in the PDN must have a complimentary transistor in the PUN
		- When any transistor is PDN is ON, its compliment transistor is OFF
- Suggestions
	- Start with the PDN and then do the PUN (most find it easier)
	- Simplify logic before you design any part of the circuit
