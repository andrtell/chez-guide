[Up]() [Prev](./0309-compilation.md) [Next](./0311-compilation.md)

----

```sh
# inspect

ls /not/the/usual/place/easymath

libeasymath.so
easymath.h
```

```c
/// main.c

#include <easymath.h>

#include <stdio.h>
#include <stdlib.h>

int main(void) {
  int input = rand();
  int result = easymath_add(7, input);
  printf("7 + %d = %d\n", input, result);
}
```

```sh
# compile

export LIB_DIR=/not/the/usual/place/easymath

cc -I $LIB_DIR \
   -L $LIB_DIR \
   main.c \
   -leasymath \                 # -leasymath drops "lib" and ".so"
   -Wl,-rpath,$LIB_DIR \
   -o main
```

```sh
# run

./main
7 + 18042 = 18049
```


----

_From:_ `man 1 gcc`

```

```
