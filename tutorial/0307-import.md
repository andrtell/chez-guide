[Top]() [Prev](./0306-import.md) [Next](./0308-import.md)

```scheme
; ./red/green/blue.ss

(library 
  (red green blue (1)) 
  (export value-1 value-2)
  (import (chezscheme))
  (define value-1 42)
  (define value-2 73))
```

```
Chez Scheme Version 10.4.0-pre-release.2
Copyright 1984-2025 Cisco Systems, Inc.

> (import (red green blue))
> value-1
42
```
