[Top]() [Prev]() [Next]()

----

```c
#include <math.h>
#include <stdio.h>

// from 21st century C page 9.

int main(){
  printf("The integral of a Normal(0, 1) distribution "
         "between -1.96 and 1.96 is: %g\n",
         erf(1.96*sqrt(1/2.))
  );
}
```

```
$ cc -std=gnu11 -Wall -g -O3 -lm -o main main.c

$ ./main
The integral of a Normal(0, 1) distribution between -1.96 and 1.96 is: 0.950004
```
