[Up]() [Prev](./0201-basic-memory.md) [Next](./0203-basic-memory.md)

----

```c
// greet.c

#include <stdio.h>

// 1. Placed in the .bss section and is zero-filled automatically by the OS/loader before main() starts.
//    (i.e name[0] = \0, name[1] = \0, ...)
//
// 2. OS reclaims the entire process address space on exit.
static char name[100]; 

int main() {
  scanf("%s", name);
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

Peter
Hello, Peter!
```
