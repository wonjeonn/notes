# Week 7-1: Arrays and Multidimensional Arrays

## 1. **Arrays**

Arrays are collections of elements of the same data type.

### Assign Values to an Array

```c
#include <stdio.h>

int main() {
  int num[5] = {1, 2, 3, 4, 5};

  for(int i = 0; i < 5; ++i) {
    printf("%d ", num[i]);
  }

  return 0;
}
```

**Output**
```c
1 2 3 4 5
```

### Taking Input and Assigning to an Array

```c
#include <stdio.h>

int main() {
  int num[5];

  printf("Enter 5 input values: ");

  for(int i = 0; i < 5; ++i) {
    scanf("%d", &num[i]);
  }

  for(int i = 0; i < 5; ++i) {
    printf("%d ", num[i]);
  }

  return 0;
}
```

**Output**
```c
Enter 5 input values: 1 2 3 4 5
1 2 3 4 5
```

### Modifying Array Elements

```c
#include <stdio.h>

int main() {
  int num[5] = {1, 2, 3, 4, 5};

  num[2] = 6;

  for(int i = 0; i < 5; ++i) {
    printf("%d ", num[i]);
  }

  return 0;
}
```

**Output**
```c
1 2 6 4 5
```

## 2. **Loop and Array**

### Example 1: Reading and Printing Array Using a Loop

```c
#include <stdio.h>

int main() {
  int num[5];

  printf("Enter 5 input values: ");

  for(int i = 0; i < 5; ++i) {
    scanf("%d", &num[i]);
  }

  for(int i = 0; i < 5; ++i) {
    printf("%d ", num[i]);
  }

  return 0;
}
```

**Output**
```c
Enter 5 input values: 1 2 3 4 5
1 2 3 4 5
```

### Example 2: Calculating the Average of an Array

```c
#include <stdio.h>

int main() {
  double marks[5];
  double sum = 0;

  printf("Enter marks: ");

  for(int i = 0; i < 5; ++i) {
    scanf("%lf", &marks[i]);
    sum += marks[i];
  }

  double averageMark = sum / 5;
  printf("Average mark: %.2lf", averageMark);

  return 0;
}
```

**Output**
```c
Enter marks: 100 96 98 100 100
Average mark: 98.80
```

## 3. **Multidimensional Arrays**

Multidimensional arrays are arrays of arrays, often used to represent tables of values or matrices.

### Declaration, Initialization and Accessing Elements

```c
#include <stdio.h>

int main() {
  int arr[2][3] = { {1, 3, 5}, {2, 4, 6} };

  printf("%d\n", arr[0][1]);
  printf("%d\n", arr[1][2]);

  arr[0][2] = 7;
  arr[1][1] = 8;

  printf("%d\n", arr[0][2]);
  printf("%d\n", arr[1][1]);

  for(int i = 0; i < 2; ++i) {
    for(int j = 0; j < 3; ++j) {
      printf("%d    ", arr[i][j]);
    }
    printf("\n");
  }

  return 0;
}
```

**Output**
```c
3
6
7
8
1    3    7    
2    8    6  
```
