# Week 6: Scope and Storage Classes

## 1. Scope

### Local Scope

- Variables declared inside a function are called local variables.
- They are accessible only within the function where they are declared.
- Once the function execution is over, local variables are destroyed.
  
#### Example:

```c
#include <stdio.h>

int addNumbers(int num1, int num2) {
  int result = num1 + num2;
  return result;
}

int main() {
  int sum = addNumbers(10, 20);
  printf("Result = %d", sum);
  return 0;
}
```

- `result` is a local variable of the `addNumbers` function and it is accessible only within that function.

### Global Scope

- Variables declared outside of all functions are called global variables.
- They are accessible from any function within the program.
- Global variables have a lifetime throughout the program's execution.

#### Example:

```c
#include <stdio.h>

int result;  // global variable

void addNumbers(int num1, int num2) {
  result = num1 + num2;
}

int main() {
  addNumbers(10, 20);
  printf("Result = %d", result);
  return 0;
}
```

- `result` is a global variable and can be accessed from both `addNumbers` and `main` functions.

## 2. Storage Classes

### Auto Storage Class

- Variables declared inside a function without any storage class keyword have auto storage class.
- They are local to the block they are declared in.
- They are initialized to garbage values if not explicitly initialized.

#### Example:

```c
#include <stdio.h>

int main() {
  auto int num = 10;  // auto storage class
  printf("Number: %d", num);
  return 0;
}
```

- `num` has auto storage class and is local to the `main` function.

### Static Storage Class

- Variables declared with the `static` keyword have static storage class.
- They retain their values between function calls.
- They are initialized to zero if not explicitly initialized.

#### Example:

```c
#include <stdio.h>

void increment() {
  static int counter = 0;  // static storage class
  counter++;
  printf("Counter: %d\n", counter);
}

int main() {
  increment();
  increment();
  increment();
  return 0;
}
```

- `counter` has static storage class and retains its value between function calls.

### Extern Storage Class

- Variables declared with the `extern` keyword have external storage class.
- They are defined in one source file and can be used in another source file.
- They are declared in a source file and can be used in multiple files.

#### Example:

Source File 1 (file1.c):

```c
int globalVar = 10;  // extern storage class
```

Source File 2 (file2.c):

```c
#include <stdio.h>

extern int globalVar;  // declaration of globalVar from file1.c

int main() {
  printf("Global Variable: %d", globalVar);
  return 0;
}
```

- `globalVar` is declared as `extern` in file2.c and is defined in file1.c. This allows it to be used in file2.c.

### Register Storage Class

- Variables declared with the `register` keyword have register storage class.
- They are stored in the CPU registers for faster access.
- They cannot have the address-of (`&`) operator applied to them.

#### Example:

```c
#include <stdio.h>

int main() {
  register int num = 10;  // register storage class
  printf("Number: %d", num);
  return 0;
}
```

- `num` has register storage class and is stored in a CPU register for faster access.
