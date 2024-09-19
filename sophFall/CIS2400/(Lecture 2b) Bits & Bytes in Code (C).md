**Signed vs. Unsigned Types**
- By default, all standard types are signed
	- Int, Char, Long, Double
- There are many ways to declare unsigned types in C
```C
char x = 'a';
unsigned char x = 10;

int x = -2400;
unsigned int x = 2400;

//etc.
```

**Bit Representations**
Consider the following code:
```C
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[]) {
	//a is 97 in ascii
	char x = 'a';
	printf("x is 0x%x.\n", x)

	x = -x;
	printf("x is 0x%x.\n", x)
	return EXIT_SUCCESS;
}
```
- Prints "x is 0x61"
- and "x is 0x9f"
- (since x is a signed character, so finds the 16's complement of 97 = 256 - 97 = 0x9f)

**Bit Operator: & (and)**
- Only if both bits are one, will it stay one!
- Single bits:
	- 1 & 1 = 1
	- 1 & 0 = 0
	- 0 & 1 = 0
	- 0 & 0 = 0
- Multiple digits
	-    0b0101
	- & 0b1101
	- ----------
	-    0b0101

**Bit Operator: | (or)**
- If either bits are one, will evaluate to one
- Single bits:
	- 1 | 1 = 1
	- 1 | 0 = 1
	- 0 | 1 = 1
	- 0 | 0 = 0
- Multiple digits
	-    0b0101
	- |  0b1101
	- ----------
	-    0b1101

**Bit Operator: ^ (xor)**
- ONLY IF ONE BIT is one, will evaluate to one
- Single bits:
	- 1 ^ 1 = 0
	- 1 ^ 0 = 1
	- 0 ^ 1 = 1
	- 0 ^ 0 = 0
- Multiple digits
	-    0b0111
	- ^ 0b1101
	- ----------
	-    0b1010

**Bit Operators**
- Consider the following code (for &):
```C
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[]) {
	char x = 0xff;
	char y = 0xf0;
	char z = x & y;
	printf("The value of z is %x\n.", z);
	return EXIT_SUCCESS;
}
```
- What is the char z in binary?
	- Treat the encoding as a binary translation (so each digit corresponds to the 4 base 2 bits)
	- f = 1111, so:
	- x = 0xff = 0b11111111
	- y = 0xf0 = 0b11110000
	- z = 0b11110000
- Consider the following code (for ^):
```C
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[]) {
	char x = 0xf0;
	char y = 0xf1;
	char z = x ^ y;
	printf("The value of z is %x\n.", z);
	return EXIT_SUCCESS;
}
```
- What is the char z in binary?
	- f = 1111, so:
	- x = 0xff = 0b11110000
	- y = 0xf0 = 0b11110001
	- z = 0b00000001

**C IS NOT JAVA**
- & IS NOT A LOGICAL OPERATOR; IT IS ONLY FOR BITWISE OPERATIONS
- It will **literally** evaluate to the bit value
```C
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[]) {

	int ube = foo();
	int miso = fuh();
	if(ube & miso)
	...
	...
}
```

**More Bit Operators:**
- ~ (not): This operation negates the bits
	- ~ 0b0101 --> 0b1010
- << (left shift): This operation shifts the bits ***n*** many times to the left
	- 0b00101 << 1 --> 0b01010
- >> (right shift): This operation shifts the bits ***n*** many times to the right
	- 0b00101 >> 1 --> 0b00010
	- What happened to the LSB (least significant bit)?
		- **Truncated:** Gets shifted off and dropped totally

**What about Logical (Boolean) Operators?**
- C doesn't have Booleans! (technically)
- Traditionally, just use an ***int*** to represent 1 for true and 0 for false (So new C language models just use an alias for this model)
	- Any non-zero int value == true
	- 0 == false
- && Logical And --> `if (X && Y)`
- | | Logical Or --> `if (X || Y)`
- ! Logical Not --> `if(!X)`

**Lecture Take-aways**
- We can represent anything in binary by using different encodings!
	- Numbers, colors, characters, emojis, code, etc.
- Hexadecimal is more human friendly... than binary
- Our encodings/data is limited due to finite bits
	- Especially, when we are explicit about the types we use
- Unsigned Numbers are non-negative integers
- Signed numbers use Two's Compliment to represent negative numbers
- Bitwise operators allow you to manipulate individual bits