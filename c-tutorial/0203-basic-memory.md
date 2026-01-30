[Up]() [Prev](./0202-basic-memory.md) [Next](./0204-basic-memory.md)

----

```c
// greet.c

#include <stdio.h>

// 1. Placed in the .data section.
// 2. OS reclaims the entire process address space on exit.
static char name[] = "PETER";

int main() {
  printf("Hello, %s\n", name);
}
```

```sh
# compile

cc -o greet greet.c
```

```sh
# run

./greet
Hello, PETER!
```

We can inspect the `.data` section.

```
objdump -s -j .data ./greet

0000000000004010 <name>:
    4010:	50 45 54 45 52 00                                   PETER.
```
