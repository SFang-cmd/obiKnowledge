```C
#include <stdio.h>

int primes[] = {1,2,3,4,5};
int prime2[5] = primes;
int *prime3 = primes;
int prime4[] = primes;

printf("%d", prime2[2]);
printf("%d", prime3[2]);
printf("%d", prime4[2]);
```