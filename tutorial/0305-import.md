[Top]() [Prev](./0304-import.md) [Next](./0306-import.md)

```scheme
; ./lib.ss

(library 
  (lib (1)) 
  (export value-1 value-2)
  (import (chezscheme))
  (define value-1 42)
  (define value-2 73))
```

```
Chez Scheme Version 10.4.0-pre-release.2
Copyright 1984-2025 Cisco Systems, Inc.

> (import (rename (lib) (value-1 value-x)))
> value-x
42
```
