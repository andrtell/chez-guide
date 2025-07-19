## Loading files

Files can be loaded.

Edit `hello.ss`

```scheme
#! /usr/bin/env -S scheme --script

(display "Hello\n")

(load "goodbye.ss")
```

Edit `goodbye.ss`

```scheme
(display "Goodbye\n")
```

Run `hello.ss`

```bash
$ ./hello.ss
Hello
Goodbye
```

From the REPL.

```scheme
$ scheme
> (load "hello.ss")
Hello
Goodbye
> (load "goodbye.ss")
Goodbye
```

Would you like to know more?

[Chez Scheme Version 10 User's Guide / Chapter 2. Getting Started](https://www.scheme.com/tspl4/start.html#./start:h0)

[Chez Scheme Version 10 User's Guide / Section 12.4. Compilation, Evaluation, and Loading ](https://cisco.github.io/ChezScheme/csug/system.html#./system:h4)

[Chez Scheme Version 10 User's Guide / Section 12.5. Source Directories and Files ](https://cisco.github.io/ChezScheme/csug/system.html#g121)
