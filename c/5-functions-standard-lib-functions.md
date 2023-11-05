# Week 5: Functions and Standard Library Functions

## 1. Functions

### Function Syntax

```c
returnType functionName() {
  // body of the function
}
```

- Functions in C are used to group a set of statements into a block and give it a name.

### Example: Simple Function

```c
#include <stdio.h>

void greet() {
  printf("Good Morning!\n");
}

int main() {
  greet();
  greet();
  greet();
  return 0;
}
```

- The `greet()` function is defined and then called three times from the `main()` function.

### Function Parameters

- Functions can take parameters (inputs) and return a value (output).

### Example: Function with Parameters

```c
#include <stdio.h>

void calculateSquare(int num) {
  int square = num * num;
  printf("Square of %d is %d\n", num, square);
}

int main() {
  calculateSquare(5);
  return 0;
}
```

- The `calculateSquare()` function takes an integer parameter, calculates its square and prints the result.

### Function Return Types

- Functions can return a value using the `return` keyword.

### Example: Function with Return Type

```c
#include <stdio.h>

int addNumbers(int num1, int num2) {
  int sum = num1 + num2;
  return sum;
}

int main() {
  int result = addNumbers(10, 20);
  printf("Result = %d", result);
  return 0;
}
```

- The `addNumbers()` function takes two integers as parameters, calculates their sum and returns the result.

### Function Prototypes

- Function prototypes declare the function before its actual definition, allowing the compiler to recognize the function before it is called.

### Example: Function Prototype

```c
#include <stdio.h>

int addNumbers(int num1, int num2);

int main() {
  int result = addNumbers(10, 20);
  printf("Result = %d", result);
  return 0;
}

int addNumbers(int num1, int num2) {
  int sum = num1 + num2;
  return sum;
}
```

- The `addNumbers()` function prototype is declared before `main()`, allowing its usage before its actual definition.

## 2. Standard Library Functions

### Math Header File

- The `math.h` header file provides various mathematical functions.

### Example: Math Functions

```c
#include <stdio.h>
#include <math.h>

int main() {
  int num = 64;
  printf("Square root is %lf", sqrt(num));
  return 0;
}
```

- The `sqrt()` function from `math.h` is used to calculate the square root of a number.

```c
#include <stdio.h>
#include <math.h>

int main() {
  int a = 8;
  int b = 2;
  double result = pow(a, b);
  printf("Power: %lf", result);
  return 0;
}
```

- The `pow()` function from `math.h` calculates the power of a number.

### Ctype Header File

- The `ctype.h` header file provides functions for character handling.

### Example: Character Functions

```c
#include <stdio.h>
#include <ctype.h>

int main() {
  char alph = 'A';
  char upper = toupper(alph);
  printf("%c\n", upper);
  char lower = tolower(upper);
  printf("%c", lower);
  return 0;
}
```

- The `toupper()` function converts a character to uppercase and `tolower()` function converts a character to lowercase.
