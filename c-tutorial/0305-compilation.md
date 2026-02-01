[Up]() [Prev](./0304-compilation.md) [Next](./0306-compilation.md)

----

```c
// main.c

int main(void) {
  return 0;
}
```

```sh
# compile

cc -O3 main.c
```
----

From `man 1 gcc`

```
Without any optimization option, the compiler's goal is to reduce the
cost of compilation and to make debugging produce the expected results.

Turning on optimization flags makes the compiler attempt to improve the
performance and/or code size at the expense of compilation time and possibly
the ability to debug the program.

The compiler performs optimization based on the knowledge it has of the program.

Compiling multiple files at once to a single output file mode allows the compiler
to use information gained from all of the files when compiling each of them.

-O1 Optimize.

    Optimizing compilation takes somewhat more time,
    and a lot more memory for a large function.

-O2 Optimize even more.

-O3 Optimize yet more.

-O0 Reduce compilation time and make debugging produce
    the expected results.

    This is the default.
```
