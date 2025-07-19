# Linux scripts using Chez Scheme

## Script

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

## Command line

When the `--script` command-line option is present, the command-line is made available via the parameter `command-line`.

Edit `cmd.ss`

```scheme
#! /usr/bin/env -S scheme --script

(display (command-line))
(newline)
```

Run `cmd.ss`

```bash
$ ./cmd.ss 1 two III
(./cmd.ss 1 two III)
```


Would you like to know more?

[ Chez Scheme Version 10 User's Guide / Section 1.3. Parameters ](https://cisco.github.io/ChezScheme/csug10.1.0/intro.html#./intro:h3)

[Chez Scheme Version 10 User's Guide / Section 2.5. Scheme Shell Scripts ](https://cisco.github.io/ChezScheme/csug10.1.0/use.html#./use:h5)

## Environment

Edit `env.ss`

```scheme
#! /usr/bin/env -S scheme --script

(display (getenv "HOME"))
(newline)
```

Run `env.ss`

```bash
$ ./env.ss
/home/user
```

Would you like to know more?

[hez Scheme Version 10 User's Guide / Section 12.5. Source Directories and Files ](https://cisco.github.io/ChezScheme/csug/system.html#./system:h15)
