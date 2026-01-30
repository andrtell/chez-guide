[Up]() [Prev](./0302-compilation.md) [Next](./0304-compilation.md)

----

```c
// main.c

int main(void) {
  return 0;
}
```

```sh
# compile

cc -g main.c
```

----

_From:_ `man 1 gcc`

```
-g  Produce  debugging  information  in  the  operating  system's  native
    format  (stabs, COFF, XCOFF, or DWARF).

    GDB can work with this debugging information.

    On most systems that use stabs format, -g enables use of extra debugging
    information that  only  GDB  can  use;

    this  extra  information  makes debugging work better in GDB but probably
    makes other debuggers crash or refuse to read the program.

    If you want to control for certain whether to generate the extra information,
    use -gvms (see below).
```
