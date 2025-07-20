# PORTS

In Scheme all input and output operations are performed through ports. A port is a pointer into a stream of data. A port may be an input port, an output port, or both simultaneously.

There are initially three ports: 

* `current-input-port` / stdin
* `current-output-port` / stdout
* `error-port` / stderr

These are procedures to needs to be called to get the port value i.e `(current-input-port)`.

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
