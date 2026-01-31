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
  int a = rand() % 11;
  int b = rand() % 11;
  int c = easymath_add(a, b);
  printf("%d + %d = %d\n", a, b, c);
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
6 + 10 = 16
```

----

_From:_ `man 1 gcc`

```
-I dir

    Add the directory dir to the list of directories to be searched for header files during preprocessing...

-Ldir

    Add directory dir to the list of directories to be searched for -l.

-Wl,option

    Pass option as an option to the linker.
    If option contains commas, it is split into multiple options at the commas.
    You can use  this  syntax to  pass an argument to the option.
    For example, -Wl,-Map,output.map passes -Map output.map to the linker.
    When using the GNU linker, you can also get the same effect with -Wl,-Map=output.map.
    NOTE: In Ubuntu 8.10 and later versions, for LDFLAGS, the option -Wl,-z,relro is used.
    To disable, use -Wl,-z,norelro.
```

_From:_ `man 1 ld`

```
-rpath=dir

    Add a directory to the runtime library search path.

    This is used when linking an ELF executable with shared objects.

    All -rpath arguments are concatenated and passed to the runtime linker,
    which uses them to locate shared objects at runtime.

    The  -rpath  option  is  also  used  when  locating  shared objects which
    are needed by shared objects explicitly included in the link ...

    ...

    If -rpath is not used when linking an ELF executable, the contents of
    the environment variable "LD_RUN_PATH" will be used if it is defined.
```
