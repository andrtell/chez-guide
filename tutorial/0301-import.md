[Top]() [Prev](./0205-repl.md) [Next](./0302-import.md)

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

> (import (lib))
> value
42
```
