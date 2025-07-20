# PORTS

In Scheme all input and output operations are performed through ports. A port is a pointer into a stream of data. A port may be an input port, an output port, or both simultaneously.

There are initially three ports: 

* `(current-input-port)` / stdin
* `(current-output-port)` / stdout
* `(current-error-port)` / stderr

When a `port` has reached the end of its stream, a special `eof` object is returned.

## Read characters from an input-port

Edit `script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(define read-from
  (lambda (port)
    (let ([ch (get-char port)])
      (if (eof-object? ch)
	'()
	(cons ch (read-from port))))))

(display (read-from (current-input-port)))

(newline)
```

Run `script.ss`

```bash
$ chmod +x ./script.ss
$ echo -n "Hello" | ./script.ss
(H e l l o)
```

Would you like to know more?

[The Scheme Programming Language / Chapter 7. Input and Output](https://www.scheme.com/tspl4/io.html#./io:h0)

## Write characters to an output-port

Edit `script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(define write-to
  (lambda (port ls)
    (if (null? ls)
      	#f
	(begin
	  (put-char port (car ls))
	  (write-to port (cdr ls))))))

(write-to (current-output-port) '(#\a #\b #\c))

(newline)
```

Run `script.ss`

```bash
$ ./script.ss
abc
```

Would you like to know more?

[The Scheme Programming Language / Chapter 7. Input and Output](https://www.scheme.com/tspl4/io.html#./io:h0)

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

Run `script.ss`

```bash
$ ./script.ss
(1. red 2. green 3. blue)
```

Would you like to know more?

[The Scheme Programming Language / Section 7.9. Convenience I/O](https://www.scheme.com/tspl4/io.html#./io:h9)
