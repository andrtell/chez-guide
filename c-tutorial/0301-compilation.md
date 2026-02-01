[Up]() [Prev](./0204-basic-memory.md) [Next](./0302-compilation.md)

----

```c
// main.c

external void f(void);

int main(void) {
  f();
}
```

```sh
# compile

cc -c main.c
```

```sh
# observe

objdump -S main.o

main.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <main>:
   0:	f3 0f 1e fa          	endbr64
   4:	55                   	push   %rbp
   5:	48 89 e5             	mov    %rsp,%rbp
   8:	48 8d 05 00 00 00 00 	lea    0x0(%rip),%rax        # f <main+0xf>
   f:	48 89 c7             	mov    %rax,%rdi
  12:	e8 00 00 00 00       	call   17 <main+0x17>
  17:	b8 00 00 00 00       	mov    $0x0,%eax
  1c:	5d                   	pop    %rbp
  1d:	c3                   	ret
```

----

From `man 1 gcc`

```
-c  Compile or assemble the source files, but do not link.  The linking stage simply is not done.
    The ultimate output is in the form of an object file for each source file.

    By default, the object file name for a source file is made by replacing the
    suffix .c, .i, .s, etc., with .o.

    Unrecognized input files, not requiring compilation or assembly, are ignored.
```
