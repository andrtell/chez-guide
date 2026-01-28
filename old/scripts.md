# Linux scripts using Chez Scheme

## A Script

`script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(display "Hello\n")
```

Run it

```
$ chmod +x ./script.ss
$ ./script.ss
Hello
```

Chez ignores the first line of a loaded script if it begins with #! followed by a space or forward slash.

```
$ scheme
> (load "script.ss")
Hello
```

Would you like to know more?

[Chez Scheme Version 10 User's Guide / Section 2.5. Scheme Shell Scripts ](https://cisco.github.io/ChezScheme/csug10.1.0/use.html#./use:h5)

## The Command line

When the `--script` command-line option is present, the command-line is made available via the parameter `command-line`.

`script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(display (command-line))
(newline)
```

Run it

```bash
$ ./script.ss 1 two III
(./script.ss 1 two III)
```


Would you like to know more?

[ Chez Scheme Version 10 User's Guide / Section 1.3. Parameters](https://cisco.github.io/ChezScheme/csug10.1.0/intro.html#./intro:h3)

[Chez Scheme Version 10 User's Guide / Section 2.5. Scheme Shell Scripts](https://cisco.github.io/ChezScheme/csug10.1.0/use.html#./use:h5)

## Linux Environment

`script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(display (getenv "HOME"))
(newline)
```

Run it

```bash
$ ./script.ss
/home/user
```

Would you like to know more?

[Chez Scheme Version 10 User's Guide / Section 12.5. Source Directories and Files](https://cisco.github.io/ChezScheme/csug/system.html#./system:h15)

## Shell commands

`script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(system "ls -l")
```

Run it

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

## Shell commands (with captured output)

`script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(let-values 
  ([(in out err pid) 
    (open-process-ports "ls -l"
                        (buffer-mode block)
                        (make-transcoder (utf-8-codec)))])
   (display (get-string-all out)))
```

Run it

```bash
$ ./script.ss
total 0
-rw-rw-r-- 1 tell tell 0 Jul 20 00:15 a.ss
-rw-rw-r-- 1 tell tell 0 Jul 20 00:15 b.ss
-rw-rw-r-- 1 tell tell 0 Jul 20 00:15 c.ss
```

Would you like to know more?

[Chez Scheme Version 10 User's Guide / Chapter 4. Foreign Interface](https://cisco.github.io/ChezScheme/csug9.5/foreign.html)

[The Scheme Programming Language / Chapter 7. Input and Output](https://www.scheme.com/tspl4/io.html#./io:h0)

## File system

Chez comes with a handfull of procedures to allow you to interact with the file system.

* `(current-directory)`
* `(directory-list)`
* ... and so on ...

Would you like to know more?

[Chez Scheme Version 10 User's Guide / Section 9.16. File System Interface](https://cisco.github.io/ChezScheme/csug/io.html#./io:h16)

[The Scheme Programming Language / Section 7.10. Filesystem Operations](https://www.scheme.com/tspl4/io.html#./io:h10)
