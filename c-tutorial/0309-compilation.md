[Up]() [Prev](./0308-compilation.md) [Next](./0310-compilation.md)

----

```c
// easymath.h

#ifndef EASYMATH_H
#define EASYMATH_H

int easymath_add(int a, int b);

#endif
```

```c
/// easymath.c

int easymath_add(int a, int b) {
	return a + b;
}
```


```sh
# compile

cc -fPIC -shared -o libeasymath.so easymath.c
```

```sh
# inspect

file libeasymath.so

libeasymath.so: ELF 64-bit LSB shared object, ..., dynamically linked, ...
```

----

_From:_ `man 1 gcc`

```
-shared

  Produce  a  shared  object  which  can  then  be  linked  with  other objects
  to form an executable.

  Not all systems support this option.

  For predictable results, you must also specify the same set of options used for
  compilation (-fpic, -fPIC, or model suboptions)  when  you  specify this linker option.[1]


-fPIC

  If supported for the target machine, emit position-independent code,
  suitable for dynamic linking and avoiding any limit on  the  size  of  the
  global offset table.

  This option makes a difference on AArch64, m68k, PowerPC and SPARC.

  Position-independent code requires special support, and therefore works
  only on certain machines.

  When this flag is set, the macros "__pic__" and "__PIC__" are defined to 2.
```
