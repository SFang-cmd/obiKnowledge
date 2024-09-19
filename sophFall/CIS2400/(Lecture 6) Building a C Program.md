**Building a C Program**
- We can compile C-programs from scratch!
- Compilation Flags
	- Compile: `clang-15 -Wall -save-temps -g3 -o small small.c`
	- `-g/-g3` - makes the compiler debuggable
	- `clang-15` - Your compiler
	- `-Wall` - Show all warnings
	- `-save-temps` - saves all temporary files created during compilation
- Compilation steps:
	- C Preprocessor: small.i
	- The C preprocessor is run over each source file in your program before it passed to the compilation stage
- **Conditional Compilation:**
	- You can include or exclude parts of the program according to various conditions
	- So if you `#include` a file that is already implicitly `#include`'d, then it is fine because C will just ignore the second occurrence

```C
#ifndef FILE_FOO_SEEN
#define FILE_FOO_SEEN

entire file

#endif /* FILE_FOO_SEEN */
```

`#include` and the C Preprocessor
- The C preprocessor (`cpp`) transforms your source code before the compiler runs
- Processes directives it fines in your code
- Removes comments
- **Directive:** `#directive`
	- e.g. `#include <ll.h` is replaced by the post-processed content of `ll.h`
	- e.g. `#define str 'hi!'` defines a symbol (a string!) and replaces later occurrences
- Automatically run on behalf by `clang` during compilation
- **Note: `#include <foo.h>` looks in system (library) directories; `#include "foo.h"` looks first in current directory, then system**
- Manually run the preprocessor:
	- `cpp` is the preprocessor (can also use `clang -E`)
	- "`-P`" option suppresses some extra debugging annotations

**Quick Asside: small.s**
- The Assembly Language version of the file
	- X86 (Intel Processors, e.g.)
	- Arm (M1 Chips, Raspberry Pi's, etc)
- We'll talk more about Assembly very soon!
	- (In a couple of weeks)

**Multiple File Compilation (Linking)**
- More complex programs require multiple files
- Even printing to the terminal requires the import of the standard library
	- `#include <stdio.h>` for `printf`
- Can include your own string library implementations
- When `#include`ing external files, the compiler will compile both the current file and the `#include`d file, then combine the compiled `.o` object files into a total: `clang -o prog utils.o prog.o` --> `prog`
- using the `-o` tag will link multiple files (one file with its dependencies):
	- `clang -o prog utils.o prog.o`, since `prog.o` depends on `utils.o`

**Recompilation Management**
- The "theory" behind avoiding unnecessary compilation is a *dependency dag* (**d**irected, **a**cyclic **g**raph)
- To create a target $t$, you need sources $s_1,s_2,...,s_n$ and a command $c$ that directly or indirectly uses the sources
	- If $t$ is newer than every source (file-modification times), assume there is no reason to rebuild it
	- Recursive building: if some source $s_{i}$ is itself a target for some other sources, see if it needs to be rebuilt
	- Cycle "makes no sense"!
- Ex.
	- if `clang-15 -c utils.c` is already compile, no need to recompile since `clang-15 -c prog.` can just be compiled independently, then plug into `clang -o prog utils.o prog.o`
	- if a `.h` file changes, may need to recompile more

**Makefiles**
- The **make** tool is used to simplify the development and building of multiple files
- Allows you to specify dependencies between soruce files in your project and indicates how they should be compiled to produce the ***final result***
- Think of the Makefile as a recipe for building your final program from the source file
- A makefile contains a bunch of *triples*:
```makefile
target: sources
<-tab-> command
```
- Colon after target is *required*
- `sources` are the list of files that are dependencies for building the target
- Command lines must start with a **TAB, NOT SPACES**
- Multiple commands for same target are executed *in order*
	- Can split commands over multiple lines by ending lines with '\\'
- Ex.
```makefile
foo.o: foo.c foo.h bar.h
<-tab-> gcc -Wall -o foo.o -c foo.c
```

**Using `make`**:
`bash$ make <target>`
- Defaults
	- If no `target` specified, will use the first one in the file
	- Will interpret commands in your default shell
- Target execution:
	- Check each source in the source list:
		- If the source is a target in the makefile, then process it recursively
		- If some sources does not exist, then error
		- If any source is newer than the target (or target does not exist), run `command` (presumably to update the target)

**Makefile Writing Tips:**
- *When creating a Makefile, first draw the dependencies!*
- C Dependency Rules:
	- `.c` and `.h` files are never targets, only sources
	- Each `.c` file will be compiled into a corresponding `.o` file
		- Header files will be implicitly used via `#include` (need to still include in makefile however)
	- Executables will typically be built from one or more `.o` file
- Good Conventions:
	- Include a `clean` rule
		- `clean: rm talk *.o`
	- If you have more than one "final target", include an `all` rule
		- Makes build from the top, then goes down the list of dependencies
	- The first/top target should be your singular "final target" or `all`

**`make` Variables**
- You can define variables in a makefile:
	- All values are strings of text, no "types"
	- Variable names are case-sensitive and can't contain ':', '#', '=', or whiespace
- Example:
```makefile
CC = gcc
CFLAGS = -Wall -std=c17
OBJFILES = foo.o bar.o baz.o
widget: $(OBJFILES) $(CC) $(CFLAGS) -o widget $(OBJFILES)
```
- Easier to change things (especially in multiple commands)
	- Common to use variables to hold filename lists
- Can also specify/overwrite variables on the command line:
	- (e.g. `make CC=clang CFLAGS=-g)

**"Phony" Targets**
- A make target whose command does not create a file of the target's name (i.e., a "recipe")
	- As long as target file doesn't exist, the commands will be executed because the target must be "remade"
- e.g. target `clean` is a convention to remove generated files to "start over" from just the source
- e.g. target `all` is a convention to build all "final products" in the makefile
	- Lists all of the "final products" as sources

**Funny Character Conventions**
- Special Variables:
	- `$@` for target name
	- `$^` for all sources
	- `$<` for left-most source (first source)
	- `%.h` - matches any file ending in `.h`, `%` stands for "any"
	- Lots more! - see the documentation

**Files**
- C files are very ***simple*** objects - they consist of a sequence of bytes
	- Can be ASCII values, UTF-8, machine code to execute, etc.
	- Generally, files start off as "closed"
- To read from a file (i.e. to see what it contains)
	- You need to open it first
	- Then you can read from it
- To write to a file (i.e. change its contents or add to it)
	- You need to open() it first
	- Then you can write() to it
- When done reading/writing to a file
	- You need to then close() it (**in some cases**)

**Files: How to refer to them?**
- In Unix and Unix like systems, **File \*** are pointers that refer to file handlers
- You can use these to refer to files that you've opened
- Three file handlers your programs will always have:
	- `stdin`: standard-input (terminal)
	- `stdout`: standard-output (terminal, for output)
	- `stderr`: standard-error (terminal, for error message)
- stdin, stdout, and stderr
	- Defined in `#include <stdio.h>`
	- `printf("hi\n") and fprintf(stdout, "hi\n");`
- These are equivalent!
	- `fprintf(stderr, "Your program failed.\n");`

**Reading from stdin is not straightforward:**
- `int getline(char ** line_buf, int *num_bytes, FILE *handler)`
	- `line_buf`: **the address of a `char *` you declare**
		- `getline` will modify this pointer to hold a pointer to a **heap allocated** array that holds the line that was read if *line_buf* is null
	- `num_bytes`
		- The address of an int you declare
		- `num_bytes` is the length of the array you pass in via line_buf
		- If it is 0, it will be updated to the size of the array it heap allocates for you
	- `handler`
		- The file handler/file you want to "read from"
		- For us, *stdin* is the file handler to grab input from terminal
	- Returns the number of bytes put in line_buf

**Reading Variables from Format String**
- `int sscanf(char *str, char * format, ...);`
	- Allows us to insert values from a string into corresponding variables
	- Best shown by example
![[Pasted image 20240917150643.png]]
- Here,
	- `num1 = 123`
	- `num2 = 45.6`
	- `word = "hello"`
- count will be the number of variable correctly assigned
	- here it will be 3

**Generics**
- We always want to write code that is as general-purpose as possible
- Generic code reduces code duplication and means you can make improvements and fix bugs in one place rather than many
- Generics is used throughout C for functions to sort any array, search any array, free arbitrary memory, etc.
- How can we write generic code in C? (Pointers are key!)

**We want to write *one* function to swap two values of any single type**
- `void *`: a generic pointer to some memory address
- Also store `size_t nbytes`: the number of bytes in the datatype
- `char temp[nbytes]`: A char array that stores every single data point

**memcpy:**
- **memcpy** is a function that copies a specified number of bytes at one address to another address
- It copies the next **n** bytes that **src** points to to the location pointed by **dest**