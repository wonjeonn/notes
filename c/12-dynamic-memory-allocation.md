# Week 12: Dynamic Memory Allocation in C

## 1. **`malloc()` and `free()` Functions**

### Example 1: Allocating and Using Memory

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  int n = 3;
  int* p = (int*) malloc(n * sizeof(int));

  if (p == NULL) {
    printf("Error! Memory not allocated.");
    return 0;
  }

  printf("Enter input values:\n");
  for (int i = 0; i < n; ++i) {
    scanf("%d", p + i);
  }

  printf("Input values:\n");
  for (int i = 0; i < n; ++i) {
    printf("%d\n", *(p + i));
  }

  free(p);
  return 0;
}
```

### Example 2: Allocating and Summing Elements

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  int n, *p, sum = 0;

  printf("Enter number of elements: ");
  scanf("%d", &n);

  p = (int*) malloc(n * sizeof(int));

  if (p == NULL) {
    printf("Error! Memory not allocated.");
    exit(0);
  }

  printf("Enter elements: ");
  for (int i = 0; i < n; ++i) {
    scanf("%d", p + i);
    sum += *(p + i);
  }

  printf("Sum: %d", sum);

  free(p);
  return 0;
}
```

## 2. **`calloc()` Function**

### Example 3: Allocating and Summing Elements with `calloc()`

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  int n, *p, sum = 0;

  printf("Enter number of elements: ");
  scanf("%d", &n);

  p = (int*) calloc(n, sizeof(int));

  if (p == NULL) {
    printf("Error! Memory not allocated.");
    exit(0);
  }

  printf("Enter elements: ");
  for (int i = 0; i < n; ++i) {
    scanf("%d", p + i);
    sum += *(p + i);
  }

  printf("Sum: %d", sum);

  free(p);
  return 0;
}
```

## 3. **`realloc()` Function**

### Example 4: Resizing Allocated Memory

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  int n = 4;
  int* p = (int*) malloc(n * sizeof(int));

  if (p == NULL) {
    printf("Memory cannot be allocated");
    return 0;
  }

  printf("Allocated Memory\n");
  for (int i = 0; i < n; ++i) {
    printf("%p\n", p + i);
  }

  n = 6;

  p = realloc(p, n * sizeof(int));

  printf("Newly Allocated Memory\n");
  for (int i = 0; i < n; ++i) {
    printf("%p\n", p + i);
  }

  return 0;
}
```
