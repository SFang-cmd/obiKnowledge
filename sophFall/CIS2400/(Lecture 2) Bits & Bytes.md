**Base 10 (Decimal Numbers)**
- **Humans** typically process numbers in base 10
- For the number 5934:

| Digit  | 5      | 9      | 3      | 4      |
| ------ | ------ | ------ | ------ | ------ |
| Pow    | $10^3$ | $10^2$ | $10^1$ | $10^0$ |
| $10^x$ | 3      | 2      | 1      | 0      |

**Base 2:**
- Digits 0-1 (0 to base-1)
- For Base 2 "1011" = Base 10 "11"

| Digit | 1                          | 0     | 1     | 1                           |
| ----- | -------------------------- | ----- | ----- | --------------------------- |
| Pow   | $2^3$                      | $2^2$ | $2^1$ | $2^0$                       |
| $2^x$ | 3                          | 2     | 1     | 0                           |
|       | eights                     | fours | twos  | ones                        |
|       | Most significant bit (MSB) |       |       | Least significant bit (LSB) |
- $1*2^{3} + 0*2^{2} + 1*2^{1} + 1*2^{0} = 11$ (base 10)
- $1*8 + 0*4 + 1*2 + 1*1 = 11$ (base 10)
- **For number "1111111",**

| Digit | 1     | 1     | 1     | 1     | 1     | 1     | 1     |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| Pow   | $2^6$ | $2^5$ | $2^4$ | $2^3$ | $2^2$ | $2^1$ | $2^0$ |
| $2^x$ | 6     | 5     | 4     | 3     | 2     | 1     | 0     |
- The $i$'th bit represents $2^i$
- Use prefix '0b' to denote base 2 (e.g. **0b1101***)

**Conversion from Decimal to Binary:**
- Algorithm 1:
	- Find the largest power of $2 \leq num$
	- Subtract the largest power of $2$ from $num$
	- Place a '1' in the bit position corresponding to this power of $2$
	- Repeat until number is $0$
	- Table:

| n   | $2^n$ |
| --- | ----- |
| 0   | 1     |
| 1   | 2     |
| 2   | 4     |
| 3   | 8     |
| 4   | 16    |
| 5   | 32    |
| 6   | 64    |
| 7   | 128   |
| 8   | 256   |
| 9   | 512   |
| 10  | 1024  |
	- Ex. 104
		- 104 - 64 = 40 (64 is $2^6$, so bit 6 is a '1')
		- 40 - 32 = 8 (32 is $2^5$, so bit 5 is a '1')
		- 8 - 8 = 0 (8 is $2^3$, so bit 3 is a '1')
		- 104 = 0b1101000
- Algorithm 2:
	- Divide by two - remainder will be the next smallest bit
	- Keep dividing until answer is 0
	- Ex. 104:
		- 104 / 2 = 52 r 0 (bit 0 is 0)
		- 52 / 2 = 26 r 0 (bit 1 is 0)
		- 26 / 2 = 13 r 0 (bit 2 is 0)
		- 13 / 2 = 6 r 1 (bit 3 is 1)
		- 6 / 2 = 3 r 0 (bit 4 is 0)
		- 3 / 2 = 1 r 1 (bit 5 is 1)
		- 1 / 2 = 0 r 1 (bit 6 is 1)
		- 104 = 0b1101000
	- Why? Well, dividing by 2 is essentially removing the last digit order (dividing a base 10 number by 10 results in one less 0, so same thing here)

**Byte Values:**
- What is the minimum and maximum base 10 value a single byte (8 bits) can store?
- minimum = 0
- maximum = 255
- Why?

| num   | 1   | 1   | 1   | 1   | 1   | 1   | 1   | 1   |
| ----- | --- | --- | --- | --- | --- | --- | --- | --- |
| $2^x$ | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0   |
- **Strategy 1:** $1*2^{7}+1*2^{6}+1*2^{5}+1*2^{4}+1*2^{3}+1*2^{2}+1*2^{1}+1*2^{0}=255$
- **Strategy 2:** $2^{8}-1=255$ (next bit minus one)

**Multiplying and Dividing by Bases**
- Multiplying:
	- 1450 x 10 = 1450***0***
	- 0b1100 x 2 = 0b1100***0***
	- (Key Idea: Inserting 0 at the end multiplies by the bases)
- Dividing:
	- 1450 / 10 = 145
	- 0b1100 / 2 = 0b0110
	- (Key Idea: Removing 0 at the end divides by the base)

**Hexadecimal**
- When working with bits, we can have large numbers with up to 64 bits (Not very funy)
- Instead, represent bits in *base-16 instead*; called **hexadecimal**
- E.g. {0110} {1010} {0011} (Every 4 bits is a base-16 digit) (So stores 0-15)
- Digits of hexadecimal:
	- 0 1 2 3 4 5 6 7 8 9 a b c d e f
- **Pneumonic:** 0xf, means the bits are *full* and there are *four*: 0b1111 == 0xf
- Use prefix '0x' to denote hexadecimal

Decimal, Binary, Hexadecimal:
- 1523 (Base-10:)
	- Human-readable, but cannot easily interpret on/off bits
- 0b10111110011 (Base-2)
	- Yes, computers use this, but not human-readable
- 0x5F3 (Base-16)
	- More "portable" as a human-readable format (half-byte is called a **nibble**)

**Hex Spelling (Hexspeak)**
- 0x8BADF00D
	- "ate bad food"
		- Used by Apple in iOS crash reports, when an application takes too long to launch, terminate, or respond to system event
- 0xDEADBEEf
	- Originally used to mark areas of memory that had not yet been initialized
- 0xDEADFA11
	- "dead fall"
		- When the user force quits an iOS application crash report
- 0x000CACA
	- "Caca"
		- Just for fun

**Encoding**
- We can represent more than just numbers with bits
	- We just need an agreed upon **encoding**
- Decimal Numbers
	- 0 --> 0x00, 1 --> 0x01, ..., 240 --> 0xF0
- Characters
	- A --> 0x41, B --> 0x42, C --> 0x43
- Colors
	- "Blue" --> 0x281EF2, "Mahogany" --> 0x990000

Meaning of Bits
- *A sequence of bits can have many meanings*
- Consider hex sequence 0x4E6F21
	- Common interpretations include:
	- The decimal numbers 5140257
	- The characters "No!"
	- The background color of this slide
	- The real number 7.203034 x $10^{-39}$
- E.g. 0x94000005 means `bl 0x100003f90 <_printf...>`
- It is up to the program/programmer to decide how to **interpret** the sequence of bits

**ASCII**
- We can encode binary values to represent characters:
- ![[Pasted image 20240904224828.png]]
- ASCII:
	- **A**merican **S**tandard **C**ode for **I**nformation **I**nterchange
	- Designed to communicate American letters, numbers, control signals
		- Used only 7 bits to minimize number of bits transmitted
		- Not considering other languages

**Unicode**
- Unicode Standard UTF-8 is an alternate text encoding
	- Uses between 8 and 32 bits for each "character"
	- Characters include more than just English
	- Includes emojis
- https://unicode-table.com/en/

**Unsigned Integers**
- Any positive integer or 0 (no negatives)
- Converting between decimal and binary - no difference
- Ex.
	- 0b0001 = 1
	- 0b0101 = 5
	- 0b1011 = 11
	- 0b1111 = 15
- The range of an unsigned number is 0 --> $2^{w} - 1$
	- Where $w$ is the number of bits
	- E.g. a **32-bit integer** can represent 0 to $2^{32}-1$ (4,294,967,295)
- ![[Pasted image 20240904225334.png]]

**Overflow:**
- If you exceed the maximum value of your bit representation, you wrap around or **overflow** back to the smallest bit representation:
	- 0b1111 + 0b1 = 0b0000
- Going below the minimum value will **overflow** back to the largest bit representation:
	- 0b0000 - 0b1 = 0b1111
- (Assuming we have only 4 bits to work with)

**Signed Numbers: Where are the Negatives?**
- **Challenge:** How can we represent negative *and* positive numbers in binary?
- Ideally, addition would work just like it usually does
	- $10 + -10 = 0...$
- BUT
	-    0b0101 (5 in decimal)
	- + 0b???? (should be -5 in decimal)
	- ----------
	-    0b0000
- The negative number is the positive number **inverted, plus one!!**
	-    0b0101 (5 in decimal)
	- + 0b1011 (should be -5 in decimal)
	- ----------
	-    0b0000 (Extra 1 carries all 1s over and gets a 0)
- ![[Pasted image 20240904230606.png]]

**Two's Compliment**
- Here, we represent a positive number as **itself**, and its negative equivalent as the **two's complement of itself**
- **Two's Compliment:** A number's binary digits inverted, plus 1
- Splits 4 bits into negatives and positives across 0
- **Nice Consequence:** All negative numbers have a 1 in the **Most Significant Bit** section
- You can use this to go from positive to negative and negative to positive
	- E.g. 0b1111 --> (invert) 0b0000 --> (plus 1) 0b0001
	- From -1 to 1

**Size Determines Range:**
![[Pasted image 20240904231130.png]]

**Overflow issues still happen**