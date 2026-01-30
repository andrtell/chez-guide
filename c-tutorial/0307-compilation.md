[Up]() [Prev](./0306-compilation.md) [Next](./0308-compilation.md)

----

```c
// main.c

#include <math.h>      // -lm
#include <stdio.h>     // -lc
#include <stdlib.h>    // -lc

int main(void) {
	double a = (double)rand();
	double b = sqrt(a);
	printf("The square root of %1.1f is %1.1f.\n", a, b);
}

```

```sh
# compile

# note 1: -lc is implied.
# note 2: -lm comes after main.c.

cc main.c -lm
```

```sh
# run

./a.out
The square root of 1804289383.0 is 42476.9.
```


----

_From:_ `man 1 gcc`

```
-l library
    Search the library named library when linking.

    (The second alternative with the library as a separate argument is only for POSIX
     compliance and is not recommended.)

    The  -l  option  is  passed directly to the linker by GCC.
    Refer to your linker documentation for exact details.
    The general description below applies to the GNU linker.

    The linker searches a standard list of directories for the library.
    The directories searched include several standard system directories
    plus any that you specify with -L.

    Static  libraries  are  archives  of  object  files,  and  have file names like liblibrary.a.
    Some targets also support shared libraries, which typically have names like liblibrary.so.

    If both static and shared libraries are found, the linker gives preference to linking
    with the shared library unless the -static option is used.

    It makes a difference where in the command you write this option;
    the linker searches and processes libraries and object files in the order they are  specified.
    Thus, foo.o -lz bar.o searches library z after file foo.o but before bar.o.
    If bar.o refers to functions in z, those functions may not be loaded.

```

_From:_ `man 3 sqrt`

```
LIBRARY
       Math library (libm, -lm)

SYNOPSIS
       #include <math.h>

       double sqrt(double x);
```

_From:_ `man 3 rand`

```
LIBRARY
       Standard C library (libc, -lc)

SYNOPSIS
       #include <stdlib.h>

       int rand(void);
```

_From:_ `man 3 printf`

```
LIBRARY
       Standard C library (libc, -lc)

SYNOPSIS
       #include <stdio.h>

       int printf(const char *restrict format, ...);
```
