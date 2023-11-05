# Week 7-0: Recursion and Factorial

## 1. **Recursion**
```c
#include <stdio.h>

int sum(int n);

int main() {
  int number, result;

  printf("Enter a positive integer: ");
  scanf("%d", &number);

  result = sum(number);

  printf("Sum = %d", result);
  return 0;
}

int sum(int n) {
  if (n != 0) {
      return n + sum(n - 1);
  }
  else {
      return n;
  }
}
```

**Output**
```c
Enter a positive integer: 5
Sum = 15
```

- The `sum` function calculates the sum of integers from 1 to `n` using recursion.
- It calls itself with a decreasing value of `n` until `n` becomes 0.

## 2. **Factorial**

```c
#include <stdio.h>

int fact(int n);

int main() {
  int number;

  printf("Enter a positive integer: ");
  scanf("%d", &number);
  
  if(number > 0) {
      int result = fact(number);
      printf("Factorial of %d is %d", number, result);
  }
  else {
      printf("Enter a positive value");
  }
  
  return 0;
}

int fact(int n) {
  if(n == 1 || n == 0) {
      return 1;
  }
  else {
      return n * fact(n - 1);
  }
}
```

**Output**
```c
Enter a positive integer: 5
Factorial of 5 is 120
```

- The `fact` function computes the factorial of an integer `n` using recursion.
- It checks for the base cases (0 and 1) and recursively multiplies the number by `n-1`.
