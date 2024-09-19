**Char is size of 1 byte**
**Revisiting: Char* & Char[]***
- C doesn't know what a "string" is
- A string in C is simply an **array of characters** with a special ending value **"\\0**
```C
char str[5];
str[0] = 'M';
str[1] = 'i';
str[2] = 's';
str[3] = '0';
str[4] = '\0';
```
- We need the Null terminator!!!!!
- array of 5 chars, total of 5 bytes (because need the last one to tell readers to stop)
- Each character takes up one byte of memory
- In C, things are byte addressable meaning that you can grab things"one byte at a time".
	- Insert or grab individual ascii values (e.g. 'M' (0x4d) in str[0])
	- **Two Hex Digits are one byte. 0xff = 0b11111111**

**Strings are Arrays of Memory**
- A more realistic view of arrays
- When you're indexing, you're really grabbing addresses
	- **Address:** Shows where the characters in the array are stored in physical computer memory

| Address  | char |
| -------- | ---- |
| 0xffff00 | 'M'  |
| 0xffff01 | 'i'  |
| 0xffff02 | 's'  |
| 0xffff03 | 'o'  |
| 0xffff04 | '\0' |
- **These characters are literally next to each other in the memory**

```C
char str[5] = "Miso";
char *ptr = str;
ptr = &str[1]
```
- In the example above, the value of the pointer ***is*** the address of the first character in the array
- In the above example, line 3 will set the address of `ptr` to "0xffff01"
```C
char str[5] = "Miso";
char *ptr = str;
ptr = &str[2];
```
- Sets `ptr` equal to the address "0xffff02" (may have address 0xffff0c)
```C
char str[5] = "Miso";
char *ptr = str;
ptr = &str[2];
char **ptr_ptr = &ptr;
```
- Here, `ptr_ptr` would store the address of the previous pointer, so `ptr_ptr = 0xffff0c` (with further address "0xffff14")

**Important idea in pointers:**
- **& Operator** grabs the address of a variable
- **\* Operator** grabs the value @ the address
- A pointer is a variable that holds the address of another variable
- We **have to be explicit** about it's type
- **On 64 bit computers, pointers are ALWAYS 8 bytes**
- (why the above pointers are separated by 8 bytes of address)

**C Strings as Arguments**
- As a parameter, it is always passed as a **char \*** (**Array Decay/array-to-pointer decay**)
- C passes the ***location or address*** of the first character rather than a copy of the whole array

```C
int doSomethingForMe(char *str) {
	str[2] = '1';
	printf("%s\n", str);
}

char ourString[5];
... // e.g. this string is "miso"
doSomethingForMe(myString);
printf("%s\n", str); // prints milo
```

Question:
```C
//What happens when we do the following?
char str[5] = "Miso";
char *ptr = str;
ptr = &str[2];
char **ptr_ptr = &ptr;
(*ptr_ptr)[1] = 't'; //What does this do?
```
- `ptr_ptr` stores the address 0xffff0c, so `*ptr_ptr` will grab the value at the address stored in `ptr_ptr = 0xffff0c`
- So this will grab the pointer `ptr`, which is the pointer pointing at 's' in the array
- Then, ptr[1] will be the first array value after the pointer location, which will chance "Miso" to "Mist"

**Char* vs. Char[]***
- char * is an 8-byte pointer
	- it stores an address of a character
- char[] is an array of characters
	- it stores the actual characters of a string
- char[] is automatically passed as a char *
	- (pointer to its first character)

**Memory Diagram of C Program**
- char * is an 8-byte pointer
	- it stores an address of a character
- char[] is an array of characters
	- it stores the actual characters in a string
- Stack Memory
	- Readable and Modifiable
	- Holds Local Variables and Function Calls
- Text/Code Segment
	- Readable only
	- Holds String Literals and Machine Code
```C
char str[5] = "Miso";
char *ptr = "Ube";
```
- str[5] can be modified, but ptr CANNOT be modified
- **In general,** the stack grows downwards as you call more functions and create more variables
- If you use too much stack space, leads to **stack overflow**

**Global Variables in C**
```C
#include <stdio.h>
#include <stdlib.h>

int x = 0;

void incr_globals() {
	x++;
}

int main() {
	printf("x: %d\n", x); // prints 0
	incr_globals();
	printf("x: %d\n", x);
	return EXIT_SUCCESS
}
```
- Global variables exist outside of any function, can be accessed from any function
- Exists throughout the entire lifespan of a program

**Global Variables in Memory**
- Global variables can be stored at stated (un-changing) address (in the **data segment**)
- Reading/writing to that variable just involves going to that static memory location
- These variables are "allocated as soon as the program is loaded"
- Program exiting will "deallocate" the variable

**Variables in Functions**
- Variables declared outside of functions (global vars) exist over the lifetime of the program
- What about variables in functions?
	- Function parameters, local varialbes, return values, etc.
	- Exists only for function, **where do they exist in memory?** **The Stack!!**

**The Stack**
- Local variables are stored in a portion of memory called the "Stack" sometimes called the "Call Stack"
	- Whenever a function is invoked, we "push" a "stack frame" for that function onto the top of the stack
	- The stack frame contains important information about the execution of the function and has space for every local variable
	- When function exits, stack frame is "**popped**"
	- Local variables are "**deallocated**"

**Memory Allocation So Far**
- 2 kinds:
	1. Global variables - Counter is **statically**-allocated
		- Allocated when program is loaded
		- *Deallocated when program exits*
	2. Local variables - vals are **automatically**-allocated
		- Allocated when function is called
		- *Deallocated when function returns*

**Lecture Take-aways**
- char * is an 8-byte pointer
	- it stores an address of a character
- char[] is an array of characters
	- it stores the actual characters of a string
- A pointer is a variable that holds the address of another variable
- Memory is split into 4 spaces
	- Stack