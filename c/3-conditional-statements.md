# Week 3: Conditional Statements and Switch Statements

## 1. If Statement

### Basic If Statement

The `if` statement is used to make decisions based on a condition.

```c
#include <stdio.h>

int main() {
  int age;

  printf("Enter your age: ");
  scanf("%d", &age);

  if (age >= 18) {
    printf("You are eligible to vote.");
  }

  return 0;
}
```

**Output**
```
Enter your age: 21
You are eligible to vote.
```

### If-Else Statement

The `if-else` statement allows specifying an alternative action.

```c
#include <stdio.h>

int main() {
  int age = 15;

  if (age >= 18) {
    printf("You are eligible to vote.");
  } else {
    printf("Sorry, you are not eligible to vote.");
  }

  return 0;
}
```

**Output**
```
Sorry, you are not eligible to vote.
```

## 2. Switch Statement

### Basic Switch Statement

The `switch` statement is used to select one code block from many based on a specified condition.

```c
#include <stdio.h>

int main() {
  int number;

  printf("Enter a number between 1 to 7: ");
  scanf("%d", &number);

  switch (number) {
    case 1:
      printf("Sunday");
      break;
    case 2:
      printf("Monday");
      break;
    case 3:
      printf("Tuesday");
      break;
    case 4:
      printf("Wednesday");
      break;
    case 5:
      printf("Thursday");
      break;
    case 6:
      printf("Friday");
      break;
    case 7:
      printf("Saturday");
      break;
    default:
      printf("Invalid Number");
  }

  return 0;
}
```

**Output**
```
Enter a number between 1 to 7: 4
Wednesday
```

### Switch with Multiple Cases

```c
#include <stdio.h>

int main() {
  int number;

  printf("Enter a number between 1 to 7: ");
  scanf("%d", &number);

  switch (number) {
    case 2:
    case 3:
    case 4:
    case 5:
    case 6:
      printf("Weekday");
      break;
    case 1:
    case 7:
      printf("Weekend");
      break;
    default:
      printf("Invalid Number");
  }

  return 0;
}
```

**Output**
```
Enter a number between 1 to 7: 7
Weekend
```

## 3. Calculator Example

Simple calculator using `if-else` and `switch` statements:

```c
#include <stdio.h>

int main() {
  double num1, num2;
  char op;

  printf("Enter a number: ");
  scanf("%lf", &num1);
  printf("Choose an operator [+ , - , * , / ]: ");
  scanf(" %c", &op);
  printf("Enter a number: ");
  scanf("%lf", &num2);

  double result;

  switch (op) {
    case '+':
      result = num1 + num2;
      break;
    case '-':
      result = num1 - num2;
      break;
    case '/':
      if (num2 != 0) {
        result = num1 / num2;
      } else {
        printf("Division by zero is not allowed.");
        return 1; // Exit the program with an error code
      }
      break;
    case '*':
      result = num1 * num2;
      break;
    default:
      printf("Invalid Operator");
      return 1; // Exit the program with an error code
  }

  printf("Result: %lf", result);

  return 0;
}
```

**Output**
```
Enter a number: 10
Choose an operator [+ , - , * , / ]: /
Enter a number: 0
Division by zero is not allowed.
```
