# Week 2: Operators, Booleans and Type Conversion

## 1. **Arithmetic Operators**

### Addition, Subtraction, Multiplication and Division

```c
#include <stdio.h>

int main() {
  int a = 10, b = 5;
  printf("Addition: %d\n", a + b);
  printf("Subtraction: %d\n", a - b);
  printf("Multiplication: %d\n", a * b);
  printf("Division: %d\n", a / b);
  return 0;
}
```

**Output**
```
Addition: 15
Subtraction: 5
Multiplication: 50
Division: 2
```

- Arithmetic operators are used for common mathematical operations.
- `+` adds two values, `-` subtracts, `*` multiplies and `/` divides.
- Demonstrate operations with integer values.

### Modulus Operator (%)

```c
#include <stdio.h>

int main() {
  int a = 10, b = 3;
  int remainder = a % b;
  printf("Remainder: %d", remainder);
  return 0;
}
```

**Output**
```
Remainder: 1
```

- The modulus operator `%` calculates the remainder of integer division.
- Useful for tasks like checking for even or odd numbers.

## 2. **Comparison Operators**

### Greater Than, Less Than, Equal To, Not Equal To

```c
#include <stdio.h>

int main() {
  int a = 5, b = 10;
  printf("Greater Than: %d\n", a > b);
  printf("Less Than: %d\n", a < b);
  printf("Equal To: %d\n", a == b);
  printf("Not Equal To: %d\n", a != b);
  return 0;
}
```

**Output**
```
Greater Than: 0
Less Than: 1
Equal To: 0
Not Equal To: 1
```

- Comparison operators allow you to compare values.
- `>`, `<`, `==` and `!=` represent greater than, less than, equal to and not equal to, respectively.

## 3. **Booleans and Logical Operators**

### Logical AND, OR, NOT

```c
#include <stdio.h>
#include <stdbool.h>

int main() {
  bool a = true, b = false;
  printf("Logical AND: %d\n", a && b);
  printf("Logical OR: %d\n", a || b);
  printf("Logical NOT: %d\n", !a);
  return 0;
}
```

**Output**
```
Logical AND: 0
Logical OR: 1
Logical NOT: 0
```

- Boolean variables (`bool`) represent true or false.
- `&&` is the logical AND operator, `||` is the logical OR operator and `!` is the logical NOT operator.

## 4. **Ternary Operator**

The ternary operator (`? :`) provides a concise way to write if-else statements.

```c
#include <stdio.h>

int main() {
  int num = 10;
  (num > 0) ? printf("Positive") : printf("Negative or Zero");
  return 0;
}
```

**Output**
```
Positive
```

- The ternary operator is a compact way to write simple if-else conditions.
- It consists of a condition, a `?`, a value if true, a `:` and a value if false.

## 5. **Type Conversion**

### Implicit Type Conversion (Automatic Type Conversion)

```c
#include <stdio.h>

int main() {
  int a = 5;
  double b = 2.5;
  double result = a + b;
  printf("Result: %lf", result);
  return 0;
}
```

**Output**
```
Result: 7.500000
```

- Implicit type conversion occurs when values of different data types are combined in an expression.
- An integer (`a`) and a double (`b`) are added and the result is implicitly converted to a double.

### Explicit Type Conversion (Type Casting)

```c
#include <stdio.h>

int main() {
  double a = 3.14;
  int b = (int)a;
  printf("Casting Double to Int: %d", b);
  return 0;
}
```

**Output**
```
Casting Double to Int: 3
```

- Explicit type conversion or type casting, is done when you want to convert a value from one data type to another.
- A double (`a`) is explicitly cast to an integer (`b`), resulting in the loss of the fractional part.
