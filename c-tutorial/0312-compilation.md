[Up]() [Prev](./0311-compilation.md) [Next](./0313-compilation.md)

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
# install

mkdir -p /usr/local/{lib,include}

cp easymath.h     /usr/local/include/easymath.h
cp libeasymath.so /usr/local/lib/libeasymath.so

# symlinks (optional)

ln -s /usr/local/lib/libeasymath.so  /usr/local/lib/libeasymath.so.1

# update the dynamic linker cache

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
	libeasymath.so => /usr/local/lib/libeasymath.so (0x000077e79c73b000)
```

```sh
# run

./main
6 + 10 = 16
```


