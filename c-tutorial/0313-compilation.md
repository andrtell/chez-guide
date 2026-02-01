[Up]() [Prev](./0312-compilation.md) [Next](./0314-compilation.md)

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
# compile (version 1.0.0)

gcc -fPIC -shared \
    -Wl,-soname,libeasymath.so.1 \
    -o libeasymath.so.1.0.0 \
    easymath.c
```

```sh
# observe

readelf -d libeasymath.so.1.0.0

Dynamic section at offset 0x2e68 contains 18 entries:
Tag                Type                 Name/Value
0x000000000000000e (SONAME)             Library soname: [libeasymath.so.1]
```

```sh
# install (version 1.0.0)

mkdir -p /usr/local/{lib,include}

cp easymath.h           /usr/local/include/
cp libeasymath.so.1.0.0 /usr/local/lib/

cd /usr/local/lib

ln -sf libeasymath.so.1.0.0  libeasymath.so.1     # SONAME symlink
ln -sf libeasymath.so.1      libeasymath.so       # Linker name symlink

ldconfig
```

----

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

cc -o main main.c -leasymath
```

```sh
# observe

ldd ./main
libeasymath.so.1 => /usr/local/lib/libeasymath.so.1

readelf -d ./main
Dynamic section at offset 0x2da8 contains 28 entries:
Tag                Type                 Name/Value
0x0000000000000001 (NEEDED)             Shared library: [libeasymath.so.1]
```

```sh
# run (works even after upgrade to libeasymath.so -> libeasymath.so.2)

./main
6 + 10 = 16
```

----

From `man 1 ld`

```
-soname=name

    When creating an ELF shared object, set the internal DT_SONAME field to the specified name.

    When an executable is linked with a shared object which has a DT_SONAME field,
    then when the executable is run the dynamic linker will attempt to load the
    shared object specified by  the  DT_SONAME  field rather than using the
    file name given to the linker.
```
