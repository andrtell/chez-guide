[Up]() [Prev](./0102-greet.md) [Next](./0104-greet.md)

----

```c
// greet.c

#include <stdio.h>

static char name[100];  // Allocated as part of data-segment. Cleaned up by OS when process exit.

int main() {
  scanf("%s", name);

  printf("Hello, %s\n", name);
}
```

```
$ cc -W -Wall -pedantic -o greet greet.c
$ ./greet
Peter
Hello, Peter!
```

