- Memory can be thought of as an array of bytes
	- Each byte has an index called an "Address"
	- ALL variables and data are stored inside memory
	- Exact address of variables will change between executions
		- **Cannot hard-code exact addresses, not a thing**
		- Addresses can be thought of references

```C
char c = 'a'; // could be stored at 0xF2, but could change between executions to 0xF1

char x = 'b'; //could be stored at 0xF0
```

**Memory is an array of bytes**
- Each byte has an index called an "Address"
- Some data can span multiple bytes / addresses
	- Address (&) of a multi-byte variable is the lowest address of it
- Ex. An int is four bytes

**Pointers and Arrays in Memory**
- Pointers can be stored in memory as variables
	- Pointers are 8-bytes
	- There are $2^{64}$ addresses in memory (thus memory is $2^{64}$ bytes)
- Arrays are also stored in memory
	- Arrays only have memory to store their members, no address stored or length stored

```C
char c[] = "Hi";
char *str = c;
```

*Note: Memory could store an address "0x 00 00 00 00 00 00 00 F0, pointer to that specific address since pointers are 8-bytes*, could point to 0xF0 - 'Hi'

**It's all just Bytes**
- The check-setup file takes an array of ints and converts their type to char types
- They are the ASCII encoding of each character and combined them into integers
- Using the same bytes for different datatypes, C can convert a number such as $97$ into characters such as 'a'

**Whole View of C Memory Model**
- Where all data, code, etc are stored for a program
- Broken up into several segments:
	- The stack (Last Lecture)
	- The heap (This & next lecture)
	- The kernel (Tae CIS 4480)
	- Etc.
- Each "unit of memory has an address"

**Review: The Stack**
- The stack is where we hold all local variables for the functions we call in C
- Each function "pushes" a new "stack frame", set the "stack pointer" to that location
	- Stores all local variables to that function
- That stack frame gets "popped" when we move out of that function

**Global Variabes**
- Stored at a static, unchanging address
- Reading/writing to global variables involves going to that static memory address
- Variables allocated as soon as the program starts, unallocated when program terminates

**Typedef**
- `typedef` is used for "defining" a "new" type
```C
typedef int my_int;

my_int x = 3;
// same as "int x = 3;"

typedef unsigned int my_uint;

//unsigned means value cannot

```

**Structured Data**
- A `struct` is a C datatype that contains a set of fields 
	- Similar to a Java class, but with no methods or constructors
	- Useful for defining new structured types of data
	- Acts similarly to **primitive variables**
- Generic declaration:
```C
typedef struct {
	float x;
	float y;
} Point;

Point pt;
Point origin = {0.0f, 0.0f};
pt = origin; //pt now contains 0.0f, 0.0f
```

**Accessing struct Fields**
- Use "." to refer to a field in a struct
- Use "->" to refer to a field from a struct pointer
	- Dereferences pointer first, then accesses field

```C
typedef struct {
	float x, y;
} Point;

int main(int argc, char** argv) {
	Point p1 = {0.0, 0.0};
	Point* p1_ptr = &p1;

	p1.x = 1.0;
	p1_ptr -> y = 2.0;
	return 0;
}
```

**Initializing a struct**
- Can initialize specific members of a struct
	- Use "." to refer to a field in a struct
```C
typedef struct {
	float x, y;
} Point;

int main(int argc, char** argv) {
	Point p1 = {3.0, 2.0};
	Point p2 = (Point) {
		.x = 0.0
	} //can leave .y blank
	return 0;
}
```

**Pass-by Value**
- Everything in C is pass-by-value
	- This means when we call a function, we pass in **copies** of the argument
	- We can pass pointers to simulate pass-by-references if needed

**Output Parameters**
- Pointers can be used to "return" more than one value from a function

```C
int solve_quadratic(double a, double b, double c, double* soln1, double* soln2) {
	double d = b*b - 4 * a * c;
	if (d >= 0) {
		*soln1 = (-b + sqrt(d)) / (2*a);
		*soln2 = (-b - sqrt(d)) / (2*a);
		return 1;
	} else {
		return 0;
	}
}

int main(int argc, char** argv) {
	double soln1, soln2; //populated by function call
	solve_quadratic(2.0, 4.0, 0.0, &soln1, &soln2);
	// ...
}
```

**Aside: `sizeof`**
- `sizeof` operator can be applied to a variable or a type and it evaluates to the size of that type in bytes
- Ex.
	- `sizeof(int)` - returns the size of an integer
	- `sizeof(double)` - returns the size of a double precision number
	- `struct my_struct s;`

**What is Dynamic Memory Allocation?**
- **We want Dynamic Memory Allocation**
	- Dynamic means "at run-time" (e.g. user input, etc)
	- The compiler and the programmer don't have enough information to make a final decision on how much to allocate
	- Your program explicitly requests more memory at runtime
	- The language allocates it at runtime, maybe with help of the OS
- **Dynamically allocated memory persists until either:**
	- A garbage collector collects it (automatic memory management, Java etc)
	- Your code explicitly deallocates it (manual memory management, C, C++, etc)
- **C requires you to manually manage memory**
	- More control, and more headaches

**Heap API:**
- Dynamic memory is managed in a location in memory called the "Heap"
	- The heap is managed by user-level runtime library (libc)
	- Interface functions found in `<stdlib.h>`
- Most used functions:
	- `void *malloc(size_t size)`;
		- Allocates memory of specified size
	- `void free(void *ptr)`;
		- Deallocates memory
- Note: `void*` is "generic pointer". It holds an address, but doesn't specify what it is pointing at
- Note 2: `size_t` is the integer type of `sizeof()`

**malloc()**
- `void *malloc(size_t size)`
- `malloc` allocates a block of memory of the requested size
	- Returns a pointer to the first byte of that memory
		- And returns `NULL` if the memory allocation failed!
	- You should assume that memory initially contains garbage
	- You'll typically use `sizeof` to calculate the size you need
```C
// allocate a 10-float array
float* arr = malloc(10*sizeof(float));
if (arr = NULL) {
	return errcode;
}
... // do stuff with arr
```

**free()**
- Usage: `free(pointer)`;
