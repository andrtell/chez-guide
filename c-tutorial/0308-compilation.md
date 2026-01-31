[Up]() [Prev](./0307-compilation.md) [Next](./0309-compilation.md)

----

```c
// main.c

#include <curl/curl.h>

int main(void) {
	curl_global_init(CURL_GLOBAL_DEFAULT);
}
```

```sh
# compile

cc main.c `pkg-config --cflags --libs libcurl`
```

```sh
# observe

pkg-config --cflags --libs libcurl

-I/usr/include/x86_64-linux-gnu -lcurl
```

----

_From:_ `man pkg-config`

```
NAME

pkgconf — a system for configuring build dependency information

QUERY-SPECIFIC OPTIONS

  --cflags, --cflags-only-I, --cflags-only-other

    Display either all CFLAGS, only -I CFLAGS or only CFLAGS that are not -I.

  --libs, --libs-only-L, --libs-only-l, --libs-only-other

    Display either all linker flags, only -L linker flags, only -l linker flags
    or only linker flags that are not -L or -l.

```
