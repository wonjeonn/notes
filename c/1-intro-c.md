# Week 1: Introduction to C Programming

## 1. **Output with Printf**

### Hello, World!

```c
#include <stdio.h>

int main() {
  printf("Hello, World!");
  return 0;
}
```

**Output**
```
Hello, World!
```

- The `printf` function is used to display text on the console.
- Include the `<stdio.h>` library to use `printf`.
- The `int main()` function is the starting point of a C program.
- `return 0;` is used to indicate a successful program execution.

## 2. **Variables and Data Types**

### Variables

```c
#include <stdio.h>

int main() {
  int age = 21;
  printf("Age: %d", age);
  return 0;
}
```

**Output**
```
Age: 21
```

- Variables in C must be declared before use.
- The `%d` format specifier is used to print integer variables.
- Demonstrates the concept of variable initialization.

### Data Types
- C data types:
  - `int` (for integers)
  - `double` (for double-precision floating-point numbers)
  - `float` (for single-precision floating-point numbers)
  - `char` (for characters)

## 3. **Input with Scanf**

### User Input

```c
#include <stdio.h>

int main() {
  int age;
  printf("Enter your age: ");
  scanf("%d", &age);
  printf("You are %d years old.", age);
  return 0;
}
```

**Output**
```
Enter your age: 21
You are 21 years old.
```

- `scanf` is used to receive user input.
- The format specifier, `%d`, is used to read integers.
- The `&` operator is used to store input in a variable.

### Taking Double Input

```c
#include <stdio.h>

int main() {
  double gpa;
  char grade;
  printf("Enter your GPA: ");
  scanf("%lf", &gpa);
  printf("Enter your grade: ");
  scanf(" %c", &grade);
  printf("Your GPA is %.1lf\n", gpa);
  printf("Your grade is %c.", grade);
  return 0;
}
```

**Output**
```
Enter your GPA: 4.0
Enter your grade: A
Your GPA is 4.0
Your grade is A.
```

- Use `%lf` for reading `double` values and `%c` for reading characters.
- Adding a space before `%c` in the format string consumes any newline characters left in the input buffer.
