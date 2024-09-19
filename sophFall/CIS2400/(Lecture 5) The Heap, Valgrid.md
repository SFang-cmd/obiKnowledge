**Queue Implementation:**
- "Naïve implementation" for the queue
```C
#include <stdio.h>

typedef struct node_st {
	struct node_st* next;
	int val;
} Node;

int main(int argc, char** argv) {
	Node first, last;

	first.val = 2;
	first.next = &last;
	last.val = 0;
	last.next = NULL;
	return 0;
}
```

**Revisiting the Queue Example:**
- Simple Data structure modeling a queue
	- Implemented with a singly linked list
- Items added to the end and removed from the front
- We maintain a list of queue elements chained together with pointers
- **We can use Dynamic Allocation to create new elements*

**Queue_Add**
```C
void Queue_Add(Queue *q, int val) {
	Queue_Node* node;
	node = malloc(sizeof(Queue_Node));
	if (node == NULL) {
		printf("ERROR");
		exit(EXIT_FAILURE);
	}

	node -> next = NULL;
	node -> val = val;
	if (q -> last != NULL) {
		q -> last -> next = node;
		q -> last = node;
	} else {
		q -> first = node;
		q -> last = node;
	}
}
```

**Multi-File C Programs (Modules)**
- In our previous example, we created a queue *module*
- A module is a self-contained piece of an overall program
	- Has externally visible functions that customers can invoke
	- Has externally visible typedefs, and perhaps global variables, that customers can use
	- May have internal functions, typedefs, or global variables that customers should not look at
- The module's *interface* is its set of public functions, typedefs, and global variables

**C Header Files**
- Header: a file whose only purpose is to be \#include'd
	- Generally, has a filename `.h` extension
	- Holds the variables, types, and function prototype declarations that make up the interface to a module
	- There are <\system-defined> and "programmer defined" headers
		- `#include <stdio.h>, #include "./cstring.h`
- Main Idea:
	- Every `name.c` is intended to be a module that has a `name.h`
	- `name.h` declares the interface to that module
	- Other modules can use name by `#include`-ing `name.h`
		- They should assume as little as possible about the implementation in name.c

**C Module Conventions**
- File Contents:
	- `.h` files only contains declarations, *never* definitions
	- `.c` files never contain prototype declarations for functions that are intended to be exported through the module interface
		- Prototype declaration: `int calculateSum(int a, int b);`
- Including:
	- *NEVER* `#include` a .c file
	- Only `#include` .h files
	- `#include` all of headers you reference, even if another header (transitively) includes some of them

**C Header Guards**
- Special "things" for the compiler to be included twice
- Header files in C (and C++) need to have two lines at the top and a line at the bottom
	- These are to prevent a file from being include'd twice (which would get an error from having multiple definitions of the same thing)
```C
// pair.h

#ifndef PAIR_H_
#define PAIR_H_

typedef struct {
	int a;
	int b;
} pair;

#endif // PAIR_H_
```

```C
#ifndef UTIL_H_
#define UTIL_H_

#include "pair.h"

// a useful function (prototype declaration)
pair* make_pair(int a, int b);

#endif // UTIL_H_
```

```C
#include "pair.h"
#include "util.h"
int main(int atgc, char* argv[]) {
```

**Dynamic Memory Pitfalls**
- Buffer Overflows
	- E.g. ask for 10 bytes, but write 11 bytes
	- Could overwrite information needed to manage the heap
	- Common when forgetting the null-terminator on malloc'd strings
- Not checking for `NULL`
	- Malloc returns `NULL` if out of memory
	- Should check this after every call to malloc
- Giving `free()` a pointer to the middle of an allocated region
	- Free won't recognize the block of memory and may crash
- Giving `free()` a pointer that has already been freed
	- Will interfere with the management of the heap and likely crash
- `malloc` does NOT initialize memory
	- There are other functions like `calloc` that will zero out memory

**Memory Leaks**
- The most common Memory Pitfall:
- What happens if we malloc something, but don't free it?
	- That block of memory cannot be reallocated, even if we don't use it anymore, until it is `free`d
	- If this happens enough, we run out of heap space and program may slow down and eventually crash
- Garbage Collection
	- Automatically "frees" anything once the program has lost all references to it
	- Affects performance, but avoid memory leaks
	- Java has this, C doesn't

**Motivation:**
- The assignments will start getting bigger and are more open ended. Lots of potential for bugs
- **Debugging is a skill that you will need throughout your programming**