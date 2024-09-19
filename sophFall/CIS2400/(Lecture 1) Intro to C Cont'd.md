Differences between C & Java:
- Java has implicit references, C only explicit references

Arrays:
- Definition: `type name[size]`
	- Allocates **size** contiguous elements of type *type*
	- Initially, array values are "garbage" (do not treat like default value, e.g. 0, "")

```C
int primes[6] = {2,3,5,6,11,13};
primes[3] = 7;
primes[100] = 0; //memory smash! (may crash program or computer, since you are messing with memory that isn't part of the program potentially)
```

Array as Parameters
- Common idiom: need to store `int size` to use in a method

C command line args
- **argc** is the number of arguments given to the program
	- The name of the program counts as an argument
- **argv** is an array of `char*`'s (strings) that are the arguments

***Common bug: Try to read the command line arguments, but you end up reading the program name***

Pointers (**EXTREMELY IMPORTANT IN C**)
- Variables that are explicit "references"
	- Holds the location to some data in computer memory
	- Must specify a type so the data being referred to can be interpreted
- Generic definition: `type* name;` or `type *name;`
- ex. `int* ptr;`

Pointer Operators
- *Dereference* a pointer using the unary $*$ operator
	- Access the memory referred to by a pointer
	- Can be used to read or write the data
	- Ex.
```C
int *ptr = ...;
int a = *ptr;
*ptr = a + 2;
```