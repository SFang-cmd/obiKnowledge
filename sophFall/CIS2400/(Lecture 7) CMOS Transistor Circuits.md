**memcpy:**
- Function that copies a specified number of bytes at one address to another address
- Copies the next **n** bytes that **src** points to to the **dest** location
```C
int x = 5;
int y = 4;
memcpy(&x, &y, sizeof(x)); // just like x = y
```

**memmove:**
- Function that is the same as memcpy, but supports overlapping regions of memory
- Copies the next **n** bytes that **src** points to the location (supports overlap, so still can copy even if **src** overlaps onto **dest**, e.g. "move", will not copy "momo", if pointer 2 is overlapped)

**Introducing Void \*:**
```C
void swap(void *data1, void *data2, size_t nbytes) {
	char temp[nbytes];
	// store a copy of data1. in temporary storage
	memcpy(temp, data1ptr, nbytes);
	memcpy(data1ptr, data2ptr, nbytes);
	memcpy(data2ptr, temp, nbytes);
}

void main(int argc, char *argv) {
	// Usage:
	int x = 2;
	int y = 5;
	swap(&x, &y, sizeof(x));
	//swaps x and y values
}
```
- Should copy the bytes themselves into temp (since `char` are each 1 byte)

```C
#include <stdio.h>

printf("Hello, World!");
```