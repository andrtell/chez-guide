[Up]() [Prev](./0310-compilation.md) [Next](./0312-compilation.md)

----

```sh
# observe

ls /not/the/usual/place/easymath

libeasymath.so
easymath.h
```

```c
/// main.c

#include <stdio.h>
#include <stdlib.h>

#include <easymath.h>

int main(void) {
  int a = rand() % 11;
  int b = rand() % 11;
  int c = easymath_add(a, b);
  printf("%d + %d = %d\n", a, b, c);
}
```

```sh
# compile

# note: -Wl,-rpath is missing here

export LIB_DIR=/not/the/usual/place/easymath

cc -I $LIB_DIR \
   -L $LIB_DIR \
   main.c \
   -leasymath \
   -o main
```

```sh
# run

./main

./main: error while loading shared libraries: libeasymath.so: \
   cannot open shared object file: No such file or directory

export LD_LIBRARY_PATH=/not/the/usual/place/easymath

./main
6 + 10 = 16
```

----

_From:_ `man 8 ld.so`

```
LD_LIBRARY_PATH

    A  list of directories in which to search for ELF libraries at execution time.

    The items in the list are separated by either colons or semi‐colons,
    and there is no support for escaping either separator.

    A zero-length directory name indicates the current working directory.

    This variable is ignored in secure-execution mode.

    Within the pathnames specified in LD_LIBRARY_PATH, the dynamic linker expands
    the tokens $ORIGIN, $LIB, and $PLATFORM (or the versions  using curly  braces  around  the  names)
    as described above in Dynamic string tokens.

    Thus, for example, the following would cause a library to be searched for in either the
    lib or lib64 subdirectory below the directory containing the program to be executed:

    $ LD_LIBRARY_PATH='$ORIGIN/$LIB' prog

    (Note the use of single quotes, which prevent expansion of $ORIGIN and $LIB as shell variables!)
```
