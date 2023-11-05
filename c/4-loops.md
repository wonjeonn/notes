# Week 4: Loops and Control Statements

## 1. While Loop

### While Loop Syntax

```c
while (condition) {
  // Code to be executed while the condition is true
}
```

- A while loop executes a block of code repeatedly as long as a specified condition is true.

### Infinite While Loop

```c
#include <stdio.h>

int main() {
  while (1 < 5) {
    printf("Infinite while loop\n");
  }
  return 0;
}
```

- This loop will run indefinitely because the condition `1 < 5` is always true.

### Basic While Loop

```c
#include <stdio.h>

int main() {
  int count = 1;

  while (count < 5) {
    printf("While loop in C\n");
    printf("Count = %d\n", count);
    count = count + 1;
  }

  return 0;
}
```

- This loop prints messages and increments the count variable until the condition `count < 5` becomes false.

## 2. Multiplication Table

### Using a While Loop

```c
#include <stdio.h>

int main() {
  int number;
  printf("Enter a number: ");
  scanf("%d", &number);

  int count = 1;

  while (count <= 10) {
    int result = number * count;
    printf("%d * %d = %d\n", number, count, result);
    count = count + 1;
  }

  return 0;
}
```

- This program takes a number as input and uses a while loop to print its multiplication table.

## 3. Do-While Loop

### Do-While Loop Syntax

```c
do {
  // Code to be executed at least once
} while (condition);
```

- A do-while loop is similar to a while loop but guarantees that the code block is executed at least once before checking the condition.

### Using a Do-While Loop

```c
#include <stdio.h>

int main() {
  int count = 1;

  do {
    printf("%d\n", count);
    count = count + 1;
  } while (count < 5);

  return 0;
}
```

- This do-while loop prints numbers and increments the count variable. It will run at least once.

## 4. For Loop

### For Loop Syntax

```c
for (initializationExpression; testExpression; updateExpression) {
  // Code to be executed in the loop
}
```

- A for loop is used to execute a block of code a specific number of times.

### Using a For Loop

```c
#include <stdio.h>

int main() {
  for (int i = 0; i < 10; i++) {
    printf("%d ", i);
  }

  return 0;
}
```

- This for loop prints numbers from 0 to 9.

### Example: Sum of Numbers

```c
#include <stdio.h>

int main() {
  int sum = 0;

  for (int i = 1; i <= 100; i++) {
    sum = sum + i;
  }

  printf("Sum: %d", sum);
  return 0;
}
```

- This program calculates the sum of numbers from 1 to 100 using a for loop.

## 5. Break and Continue Statements

### Break Statement

- The `break` statement is used to exit a loop prematurely.

### Using Break in a For Loop

```c
#include <stdio.h>

int main() {
  for (int i = 1; i <= 5; i++) {
    printf("%d\n", i);
    break;
  }

  return 0;
}
```

- This loop will execute only once because of the `break` statement.

### Continue Statement

- The `continue` statement is used to skip the current iteration and continue with the next one.

### Using Continue in a For Loop

```c
#include <stdio.h>

int main() {
  for (int i = 1; i <= 5; i++) {
    if (i == 4) {
      continue;
    }
    printf("%d\n", i);
  }

  return 0;
}
```

- This loop skips printing the number 4 due to the `continue` statement.

### Using Break and Continue Together

```c
#include <stdio.h>

int main() {
  while (1) {
    int number;
    printf("Enter a number: ");
    scanf("%d", &number);

    if (number <= 0) {
      break;
    }

    if (number % 2 != 0) {
      continue;
    }

    printf("%d\n", number);
  }

  return 0;
}
```
