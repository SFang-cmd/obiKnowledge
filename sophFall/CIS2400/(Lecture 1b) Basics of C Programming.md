C: main(), \#include\, Hello World!
- This program just prints: "Hello World!"

```C
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[]) {
	printf("Hello World!");
	return EXIT_SUCCESS;
}
```
- stdio includes printf
- stdlib includes `EXIT_SUCCESS`

Fundamental C Types:
- Int
	- Integer types
- Double
	- Floating point numbers
- String
	- No type called "string" instead it is char*
	- Cover more on strings in the future, for now `char* = string`

C: printf format specifiers
- To specify how arguments to *printf* should be interpreted for printing we must use a **format string/format specifiers**

