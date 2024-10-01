**Saturated Adder:**
- Saturated Arithmetic is when arithmetic is bound to a fixed range and overflow would result in the maximum value
- How do we detect overflow?
- Consider 4 bit addition:
- 1111 + 1 = 10000 (unsaturated)
- 1111 + 1 = 1111 (saturated)

**Overflow for 2's Complements:**
- Overflow for 2C isn't always "problematic", it doesn't always result in a value that is incorrect
