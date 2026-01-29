[Up]() [Prev](./0103-greet.md) [Next](./0105-greet.md)

----

```c
// greet.c

#include <stdio.h>

static char name[6] = "Peter";

int main() {
  printf("Hello, %s\n", name);
}
```

```
$ cc -W -Wall -pedantic -o greet greet.c
$ ./greet
Hello, PETER!
```

```
$ objdump -s -j .data ./greet
4000 00000000 00000000 08400000 00000000  .........@......
4010 50455445 5200                        PETER.
```
