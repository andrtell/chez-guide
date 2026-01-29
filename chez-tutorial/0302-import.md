[Top](./index.md) [Prev](./0301-import.md) [Next](./0303-import.md)

----

```scheme
; ./lib.ss

(library 
  (lib (1)) 
  (export value)
  (import (chezscheme))
  (define value 42))
```

```
Chez Scheme Version 10.4.0-pre-release.2
Copyright 1984-2025 Cisco Systems, Inc.

> (import (prefix (lib) lib:))
> lib:value
42
```
