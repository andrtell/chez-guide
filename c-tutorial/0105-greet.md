[Up]() [Prev](./0104-greet.md) [Next]()

----

```c
// greet.c

#include <stdio.h>
#include <stdlib.h>

int main() {
	char* name = malloc(100 * sizeof(char)); // 100 chars allocated on Heap

	if (name == NULL) {
		fprintf(stderr, "Memory allocation failed\n");
		return 1;
	}

	scanf("%s", name);
	printf("Hello, %s!\n", name);

	free(name); // Should free the memory at some point.
}
```

```
$ cc -W -Wall -pedantic -o greet greet.c
./greet
Bob
Hello, Bob!
```
