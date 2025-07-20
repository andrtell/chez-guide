# PORTS

In Scheme all input and output operations are performed through ports. A port is a pointer into a stream of data. A port may be an input port, an output port, or both simultaneously.

There are initially three ports: 

* `current-input-port` / stdin
* `current-output-port` / stdout
* `error-port` / stderr

When a `port` has reached the end of a finite stream, it returns a special `eof` object.

## Read all characters from input port

Edit `script.ss`

```scheme
#! /usr/bin/env -S scheme --script

(define consume
  (lambda (port)
    (let ([ch (get-char port)])
      (if (eof-object? ch)
	'()
	(cons ch (consume port))))))

(display (consume (current-input-port)))

(newline)
```

Run `script.ss`

```bash
$ chmod +x ./script.ss
$ echo -n "Hello" | ./script.ss
(H e l l o)
```
