[Top]() [Prev](./0307-import.md) [Next]()

```scheme
; ./lib.ss

(library 
  (lib (1)) 
  (export value-1 value-2)
  (import (chezscheme))
  (define value-1 42)
  (define value-2 73))
```

```scheme
; ./top.ss

(import (chezscheme) (lib))
(display value-1)
(newline)
```

```
Chez Scheme Version 10.4.0-pre-release.2
Copyright 1984-2025 Cisco Systems, Inc.

> (load-program "top.ss")
42
```

```
$ scheme --program top.ss
42
```
