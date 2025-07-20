# PORTS

In Scheme all input and output operations are performed through ports. A port is a pointer into a stream of data. A port may be an input port, an output port, or both simultaneously.

There are initially three ports: 

* `(current-input-port)` / stdin
* `(current-output-port)` / stdout
* `(current-error-port)` / stderr

When a `port` has reached the end of its stream, a special `eof` object is returned.

## Read characters from an input-port

`script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(define read-characters
  (lambda (port)
    (let ([ch (get-char port)])
      (if (eof-object? ch)
	'()
	(cons ch (read-characters port))))))

(let* ([port (current-input-port)]
       [characters (read-characters port)])
  (display characters)
  (newline))
```

Run it

```bash
$ chmod +x ./script.ss
$ echo -n "Hello" | ./script.ss
(H e l l o)
```

Would you like to know more?

[The Scheme Programming Language 4th / Chapter 7. Input and Output](https://www.scheme.com/tspl4/io.html#./io:h0)

[Chez Scheme Version 10 User's Guide / Chapter 9. Input/Output Operations](https://cisco.github.io/ChezScheme/csug/io.html#./io:h1)

## Write characters to an output-port

Edit `script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(define write-characters
  (lambda (port cs)
    (if (null? cs)
      	#f
	(begin
	  (put-char port (car cs))
	  (write-characters port (cdr cs))))))

(let ([port (current-output-port)]
      [cs '(#\a #\b #\c)])
  (write-characters port cs)
  (newline))
```

Run it

```bash
$ ./script.ss
abc
```

Would you like to know more?

[The Scheme Programming Language / Chapter 7. Input and Output](https://www.scheme.com/tspl4/io.html#./io:h0)

[Chez Scheme Version 10 User's Guide / Chapter 9. Input/Output Operations](https://cisco.github.io/ChezScheme/csug/io.html#./io:h1)

## Read lines from a file

`lines.txt`

```
1. red
2. green
3. blue
```

`script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(define read-lines
  (lambda (port)
    (let f ([ln (get-line port)])
      (if (eof-object? ln)
	'()
	(cons ln (f (get-line port)))))))

(let* ([port (open-input-file "lines.txt")]
       [lines (read-lines port)])
  (display lines)
  (newline))
```

Run it

```bash
$ ./script.ss
(1. red 2. green 3. blue)
```

Would you like to know more?

[The Scheme Programming Language / Section 7.9. Convenience I/O](https://www.scheme.com/tspl4/io.html#./io:h9)

[Chez Scheme Version 10 User's Guide / Chapter 9. Input/Output Operations](https://cisco.github.io/ChezScheme/csug/io.html#./io:h1)
