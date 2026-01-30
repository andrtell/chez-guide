[Up]() [Prev](./0301-compilation.md) [Next](./0303-compilation.md)

----

```c
// main.c

int main(void) {
  return 0;
}
```

```sh
# compile

cc -o main main.c
```

----

_From:_ `man 1 gcc`

```
-o file

   Place the primary output in file file.

   This applies to whatever sort of output is being produced, whether it be an executable file,
   an  object file, an assembler file or preprocessed C code.

   If  -o is not specified,
   the default is to put an executable file in a.out,
   the object file for source.suffix in source.o, its assembler file in source.s,
   a precompiled header file in source.suffix.gch,
   and all preprocessed C source on standard output.
```
