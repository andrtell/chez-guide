# Linux Shell scripts in Chez Scheme

## Plain script

Edit `hello.ss`

```scheme
#! /usr/bin/env -S scheme --script

(display "Hello\n")
```

Run `hello.ss`

```
$ chmod +x ./hello.ss
$ ./hello.ss
Hello
```

Chez ignores the first line of a loaded script if it begins with #! followed by a space or forward slash.

```
$ scheme
> (load "hello.ss")
Hello
```

Would you like to know more?

[Chez Scheme Version 10 User's Guide / Section 2.5. Scheme Shell Scripts ](https://cisco.github.io/ChezScheme/csug10.1.0/use.html#./use:h5)
