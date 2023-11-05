# Week 9: Structs and Enumerations

## 1. **Structs**

In C, a struct is a composite data type used to group related variables together under a single name.

### Struct Declaration and Initialization

```c
#include <stdio.h>

struct Person {
  double salary;
  int age;
};

int main() {

  struct Person person1;

  person1.age = 21;
  person1.salary = 70000.00;
  
  printf("Age of person1: %d\n", person1.age);
  printf("Salary of person1: %.2lf", person1.salary);
  
  return 0;
}
```

**Output**
```c
Age of person1: 21
Salary of person1: 70000.00
```

### Initializing Struct Members in the Same Line

```c
#include <stdio.h>

struct Person {
  double salary;
  int age;
};

int main() {

  struct Person person1 = {.age = 21, .salary = 70000.00};
  struct Person person2 = {.age = 24, .salary = 90000.00};

  printf("Age of person1: %d\n", person1.age);
  printf("Salary of person1: %.2lf\n", person1.salary);

  printf("Age of person2: %d\n", person2.age);
  printf("Salary of person2: %.2lf", person2.salary);
  
  return 0;
}
```

**Output**
```c
Age of person1: 21
Salary of person1: 70000.00
Age of person2: 24
Salary of person2: 90000.00
```

## 2. **Typedef in Struct**

The `typedef` keyword allows creating a custom type name for a struct.

```c
#include <stdio.h>

typedef struct Person {
  double salary;
  int age;
} person;

int main() {

  person person1;

  person1.age = 21;
  person1.salary = 70000.00;
  
  printf("Age of person1: %d\n", person1.age);
  printf("Salary of person1: %.2lf", person1.salary);
  
  return 0;
}
```

**Output**
```c
Age of person1: 21
Salary of person1: 70000.00
```

### Using `typedef` with Complex Numbers

```c
#include <stdio.h>

typedef struct Complex {
  double real;
  double imaginary;
} complex;

int main() {

  complex c1 = {.real = 25.55, .imaginary = 25};
  complex c2 = {.real = 24.45, .imaginary = 120.35};

  complex sum;

  sum.real = c1.real + c2.real;
  sum.imaginary = c1.imaginary + c2.imaginary;

  printf("Result: %.2lf + %.2lfi", sum.real, sum.imaginary);

  return 0;
}
```

**Output**
```c
Result: 50.00 + 145.35i
```

### Subtracting Complex Numbers

```c
#include <stdio.h>

typedef struct Complex {
  double real;
  double imaginary;
} complex;

int main() {
    
  complex c1 = {.real = 30, .imaginary = 80.15};
  complex c2 = {.real = 20, .imaginary = 90.35};
  complex subtract;
  
  subtract.real = c1.real - c2.real;
  subtract.imaginary = c1.imaginary - c2.imaginary;
  
  printf("Result: %.2lf + %.2lfi", subtract.real, subtract.imaginary);
  
  return 0;
}
```

**Output**
```c
Result: 10.00 + -10.20i
```

## 3. **Enumerations**

Enumerations in C are used to define a set of integral constants.

### Basic Enumeration

```c
#include <stdio.h>

enum Size {
  Small,
  Medium,
  Large,
  ExtraLarge
};

int main() {

  enum Size topSize;

  topSize = ExtraLarge;

  printf("%d", topSize);

  return 0;
}
```

**Output**
```c
3
```

### Changing the Enum Value

```c
#include <stdio.h>

enum Size {
  Small,
  Medium,
  Large,
  ExtraLarge
};

int main() {

  enum Size topSize;

  topSize = Small;

  printf("%d", topSize);

  return 0;
}
```

**Output**
```c
0
```

### Assigning Custom Values to Enumeration Constants

```c
#include <stdio.h>

enum Size {
  Small = 22,
  Medium = 28,
  Large = 32,
  ExtraLarge = 40
};

int main() {

  enum Size topSize1 = Small;
  enum Size topSize2 = Medium;
  enum Size topSize3 = Large;
  enum Size topSize4 = ExtraLarge;

  printf("%d\n", topSize1);
  printf("%d\n", topSize2);
  printf("%d\n", topSize3);
  printf("%d", topSize4);

  return 0;
}
```

**Output**
```c
22
28
32
40
```

### Creating Enum Variables

### Example 1

```c
#include <stdio.h>

enum Size {
  Small,
  Medium,
  Large,
  ExtraLarge
} topSize;

int main() {
  
  topSize = Small;
  printf("%d", topSize);

  return 0;
}
```

**Output**
```c
0
```

### Example 2

```c
#include <stdio.h>

enum Day {
  Sunday,
  Monday,
  Tuesday,
  Wednesday,
  Thursday,
  Friday,
  Saturday
};

int main() {
  
  enum Day weekend1 = Sunday;
  enum Day weekend2 = Saturday;
  
  printf("%d\n%d", weekend1, weekend2);
  
  return 0;
}
```

**Output**
```c
0
6
```
