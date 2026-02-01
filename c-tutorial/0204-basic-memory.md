[Up]() [Prev](./0203-basic-memory.md) [Next](./0301-compilation.md)

----

```c
// greet.c

#include <stdio.h>
#include <stdlib.h>

int main() {
	// 100 chars worth of memory allocated on the heap (dynamic allocation)
	// with indeterminate content (not zeroed, unless you use calloc).
	char* name = malloc(100 * sizeof(char)); 

	// check for allocation failure
	if (name == NULL) {
		fprintf(stderr, "Memory allocation failed\n");
		return 1;
	}

	scanf("%s", name);

	printf("Hello, %s!\n", name);

	// at some point the memory should be released (to avoid memory leaks).
	free(name);

	// name is now a dangling pointer, for good measure, set it to NULL.
	name = NULL;
}
```

```sh
# compile

cc -o greet greet.c
```

```sh
# run

./greet
Peter
Hello, Peter!
```

----

From `man 3 malloc`

```
LIBRARY
       Standard C library (libc, -lc)

SYNOPSIS
       #include <stdlib.h>

       void *malloc(size_t size);
       void free(void *_Nullable ptr);

DESCRIPTION
   malloc()
       The  malloc()  function  allocates size bytes and returns a pointer to the allocated memory.
       The memory is not initialized.  If size is 0, then malloc() returns a unique pointer value
       that can later be successfully passed to free().

   free()
       The free() function frees the memory space pointed to by ptr, which must have been returned
       by a previous call to malloc() or related functions.
       Otherwise, or if ptr has already been freed, undefined behavior occurs.
       If ptr is NULL, no operation is performed.
```

