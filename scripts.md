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

[ Chez Scheme Version 10 User's Guide / Section 1.3. Parameters](https://cisco.github.io/ChezScheme/csug10.1.0/intro.html#./intro:h3)

[Chez Scheme Version 10 User's Guide / Section 2.5. Scheme Shell Scripts](https://cisco.github.io/ChezScheme/csug10.1.0/use.html#./use:h5)

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

[Chez Scheme Version 10 User's Guide / Section 12.5. Source Directories and Files](https://cisco.github.io/ChezScheme/csug/system.html#./system:h15)

## Shell command

Edit `script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(system "ls -l")
```
Run `script.ss`

```bash
$ ./script.ss
total 0
-rw-rw-r-- 1 tell tell 0 Jul 20 00:15 a.ss
-rw-rw-r-- 1 tell tell 0 Jul 20 00:15 b.ss
-rw-rw-r-- 1 tell tell 0 Jul 20 00:15 c.ss
0
```

Would you like to know more?

[Chez Scheme Version 10 User's Guide / Chapter 4. Foreign Interface](https://cisco.github.io/ChezScheme/csug9.5/foreign.html)

## Shell command (with captured output)

Edit `script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(let-values 
  ([(in out err pid) 
    (open-process-ports "ls -l" 'block (make-transcoder (utf-8-codec)))])
   (display (get-string-all out)))
```

Run `script.ss`

```bash
$ ./script.ss
total 0
-rw-rw-r-- 1 tell tell 0 Jul 20 00:15 a.ss
-rw-rw-r-- 1 tell tell 0 Jul 20 00:15 b.ss
-rw-rw-r-- 1 tell tell 0 Jul 20 00:15 c.ss
```

Would you like to know more?

[Chez Scheme Version 10 User's Guide / Chapter 4. Foreign Interface](https://cisco.github.io/ChezScheme/csug9.5/foreign.html)


