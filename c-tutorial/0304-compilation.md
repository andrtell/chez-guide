[Up]() [Prev](./0303-compilation.md) [Next](./0305-compilation.md)

----

```c
// main.c

int main(void) {
  return 0;
}
```

```sh
# compile

cc -std=gnu18 main.c
```

----

From `man 1 gcc`

```
-std=
    Determine the language standard.

    This option is currently only supported when compiling C or C++.

    ...

    gnu17
    gnu18
        GNU dialect of ISO C17.  This is the default for C code.
```
