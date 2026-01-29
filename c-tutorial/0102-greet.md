[Up]() [Prev](./0101-hello.md) [Next]()

----

```c
// greet.c

#include <stdio.h>

int main() {
	char name[100];     // Stack allocation of 100 chars on each call (automatic storage).

	scanf("%s", name);  // Array (char[]) decays into a pointer (char *) to its first element.

	printf("Hello, %s!\n", name);
}
```

```
$ cc -W -Wall -pedantic -o greet greet.c
$ ./greet
Peter
Hello, Peter!
```
