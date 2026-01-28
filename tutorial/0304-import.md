[Top]() [Prev](./0303-import.md) [Next](./0305-import.md)

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

> (import (except (lib) value-1))
> value-2
73
> value-1
Exception: variable value-1 is not bound
```
