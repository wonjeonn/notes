# Week 10: Pointers and Functions

## 1. **Pointer Basics**

### Pointer Variable and Address

```c
#include <stdio.h>

int main() {

  int age = 21;
  printf("Address of age: %p\n", &age);

  int* p = &age;
  printf("Pointer value: %p", p);

  return 0;
}
```

**Output**
```c
Address of age: 0x7ffee1e8a9dc
Pointer value: 0x7ffee1e8a9dc
```

### Accessing Values through Pointers

```c
#include <stdio.h>

int main() {

  int age = 21;
  int* p = &age;

  printf("Address: %p\n", p);
  printf("Value: %d", *p);

  return 0;
}
```

**Output**
```c
Address: 0x7ffee1e8a9dc
Value: 21
```

### Modifying Values using Pointers

#### Example 1

```c
#include <stdio.h>

int main() {

  int age = 21;
  int* p = &age;

  *p = 24;

  printf("%d", age);

  return 0;
}
```

**Output**
```c
24
```

#### Example 2

```c
#include <stdio.h>

int main() {
    
  double price;
  printf("Enter item price: ");
  scanf("%lf", &price);
  
  double* p = &price;
  printf("Item price: %.2lf\n", *p);
  
  double taxPrice = *p * 0.13;
  printf("Taxes: %.2lf\n", taxPrice);
  
  double totalPrice = *p + (*p * 0.13);
  printf("Total: %.2lf", totalPrice);
}
```

**Output**
```
Enter item price: 3.98
Item price: 3.98
Taxes: 0.52
Total: 4.50
```

## 2. **Pointer and Arrays**

### Pointer Arithmetic

```c
#include <stdio.h>

int main() {

  int numbers[5] = {1, 2, 3, 4, 5};

  for (int i = 0; i < 5; ++i) {
    printf("%d = %p\n", numbers[i], (numbers + i));
  }

  return 0;
}
```

**Output**
```c
1 = 0x7ffee1e8a9c0
2 = 0x7ffee1e8a9c4
3 = 0x7ffee1e8a9c8
4 = 0x7ffee1e8a9cc
5 = 0x7ffee1e8a9d0
```

### Accessing Array Elements with Pointers

```c
#include <stdio.h>

int main() {

  int numbers[5] = {1, 2, 3, 4, 5};

  for (int i = 0; i < 5; ++i) {
    printf("%d = %p\n", *(numbers + i), (numbers + i));
  }

  return 0;
}
```

**Output**
```c
1 = 0x7ffee1e8a9c0
2 = 0x7ffee1e8a9c4
3 = 0x7ffee1e8a9c8
4 = 0x7ffee1e8a9cc
5 = 0x7ffee1e8a9d0
```

### Modifying Array Elements using Pointers

```c
#include <stdio.h>

int main() {

  int numbers[5] = {1, 2, 3, 4, 5};

  *numbers = 0;          // numbers[0]
  *(numbers + 4) = 6;    // numbers[4]

  printf("First Element: %d\n", *numbers);
  printf("Last Element: %d\n", *(numbers + 4));

  return 0;
}
```

**Output**
```c
First Element: 0
Last Element: 6
```

## 3. **Pointers and Functions**

### Passing Pointers to Functions

```c
#include <stdio.h>

void findValue(int* num) {
  *num = 24;
}

int main() {

  int number = 21;

  findValue(&number);
  
  printf("Number: %d", number);

  return 0;
}
```

**Output**
```c
Number: 24
```

### Returning Pointers from Functions

#### Example 1

```c
#include <stdio.h>

int* findSquare(int* num) {
  
  int square = *num * *num;

  *num = square;

  return num;
}

int main() {

  int num = 15;

  int* result = findSquare(&num);
  
  printf("Square: %d", *result);

  return 0;
}
```

**Output**
```c
Square: 225
```

#### Example 2

```c
#include <stdio.h>

int* addNumbers(int* num1, int* num2, int* sum) {

  *sum = *num1 + *num2;

  return sum;
}

int main() {

  int number1 = 21;
  int number2 = 24;
  
  int sum;

  int* result = addNumbers(&number1, &number2, &sum);
  
  printf("%d + %d = %d", number1, number2, *result);

  return 0;
}
```

**Output**
```c
21 + 24 = 45
```
