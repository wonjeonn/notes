# Pointers, References, and Arrays

## Pointers
A pointer type holds an address as its value, allowing direct manipulation of memory locations. Each type in C++, whether fundamental, built-in, or user-defined, has an associated pointer type.

```cpp
signed char* p1;
int* p2;
double* p3;
```

## Null Address Constant
The `nullptr` keyword represents a null pointer constant, indicating that the pointer does not point to any object. 

### Good Design Practice
- **The null address cannot be dereferenced**; any attempt to dereference a pointer that holds the value `nullptr` causes a run-time error.
- Initialize pointers to `nullptr` to avoid wild pointers, which can cause undefined behavior when dereferenced.

    ```cpp
    int* ptr = nullptr;
    ```

## Synonym Pointer Types

```cpp
typedef unsigned long long int ullint;
ullint* p;

typedef unsigned long long int* ullint_ptr;
ullint_ptr p; // a pointer to ullint

unsigned long long int* pp, * qq;  // we need * before each identifier
ullint_ptr p, q;                   // no need for a repeated *
```

## Generic Pointer Type
A generic pointer type can hold the address of any object type without storing type information. The `void*` type is used for generic pointers.

```cpp
void* p; // generic pointer type
```

### Generic Pointer Type Example
```cpp
#include <iostream>

int main() {
    int i;
    void* v = &i;
    int* j = static_cast<int*>(v);  // OK - j now holds the address of i
    std::cout << &i << std::endl;
    std::cout << j << std::endl;
    return 0;
}
```

### Converting from one pointer type to another requires an explicit cast
```cpp
int* i;
char* c;
i = c; // ERROR - Incompatible: Different Pointer Types

int* i;
char* c;
i = static_cast<int*>(static_cast<void*>(c)); // OK
```

## Hexadecimal Dump Example
The `hexDump` function displays memory contents in hexadecimal format.

```cpp
#include <iostream>
#include <iomanip>

void hexDump(void* a, int n) {
    unsigned char* c = static_cast<unsigned char*>(a);
    auto oldFill = std::cout.fill('0');
    std::cout << std::hex;
    for (int i = 0; i < n; i++)
        std::cout << std::setw(2) << static_cast<int>(c[i]) << ' ';
    std::cout.fill(oldFill);
    std::cout << std::dec;
}

int main() {
    int i;
    double x;
    std::cout << "Integer value: ";
    std::cin >> i;
    std::cout << "is : ";
    hexDump(&i, 4);
    std::cout << std::endl;
    std::cout << "Floating-point value: ";
    std::cin >> x;
    std::cout << "is : ";
    hexDump(&x, 8);
    std::cout << std::endl;
    return 0;
}
```

# References
A reference is an alias for an existing object, providing an alternative name for the entity defined elsewhere.

## `lvalue` References: denoted by `&`
An `lvalue` reference refers to an accessible region of memory and generally requires an initializer unless it:
    - Has external linkage
    - Is a class member within a class definition
    - Is a function parameter or a function return type

```cpp
int x = 10;
int& ref = x;
```

## `rvalue` References: denoted by `&&`
An `rvalue` reference refers to an object that is near the end of its lifetime, a temporary object, or a value not associated with an object. They are commonly used in move semantics.

```cpp
int&& rref = 10;
```

### lvalue and rvalue References Example
```cpp
#include <iostream>

class A {
    int a;
public:
    A(int aa) : a(aa) {}
    void display(const char* str) const {
        std::cout << str << ' ' << a << std::endl;
    }
};

void print(const A& a) { a.display("lvalue"); }
void print(A&& a) { a.display("rvalue"); }

int main() {
    A a(10);
    print(a);
    print(A(20));
    return 0;
}
```

## Array Types

An array type in C++ is a built-in type that consists of elements of identical type arranged contiguously in memory. Each element is a subobject of the array type. An array can be constructed from various types, including:

- Fundamental types (except `void`)
- Pointer types
- Pointer to member types
- Class types
- Enumeration types

An array cannot be constructed directly from reference types.

## One-Dimensional Array

- **Stack Allocation**: `Type identifier[c];`
- **Heap Allocation**: `Type* identifier = new Type[n];`

Where:
- `Type` is the type of each element in the array.
- `c` is the number of elements in the array, which must be an integer constant or constant integer expression.
- `n` is the number of elements in the array, which can be an integer variable, integer constant, or constant integer expression.

## Aggregate Initialization 

- `Type identifier[c] = { initializer-list };`
- `Type identifier[c] = {};`
- `Type identifier[c] { initializer-list };`
- `Type identifier[c] { };`
- `Type identifier[] = { initializer-list };`
- `Type identifier[] { initializer-list };`
- `Type* identifier = new Type[n] { initializer-list };`
- `Type* identifier = new Type[n] { };`

`initializer-list` is a comma-separated list of initial values. If the list is present, `c` is optional. If `c` exceeds the number of values in the list, the compiler initializes the remaining elements to 0. If the initialization list is absent, `c` is required. If the braces are present but empty, the compiler initializes all elements to 0.

### Example of Aggregate Initialization

```cpp
// Aggregate Initialization
// initializers.cpp
#include <iostream>

int main() {
    const int n = 6;
    int a[] = { 1, 2, 3 };
    int b[] { 1, 2, 3 };
    int c[5] { 1, 2, 3 };
    int d[5] {};
    int* f = new int[n] { 1, 2, 3 };
    int* g = new int[n] {};

    for (int e : a) // range-based for loop
        std::cout << e;
    std::cout << '|' << std::endl;

    for (int e : b)
        std::cout << e;
    std::cout << '|' << std::endl;

    for (int e : c)
        std::cout << e;
    std::cout << '|' << std::endl;

    for (int e : d)
        std::cout << e;
    std::cout << '|' << std::endl;

    for (int i = 0; i < n; ++i) // cannot use range-based for with pointers
        std::cout << f[i];
    std::cout << '|' << std::endl;

    for (int i = 0; i < n; ++i)
        std::cout << g[i];
    std::cout << '|' << std::endl;

    delete[] f;
    delete[] g;
}
```

#### Output
```
123|
123|
12300|
00000|
123000|
000000|
```

## Range-Based for Loop

A range-based for loop is an iteration construct designed for use with collections. It steps sequentially through the elements of a collection, which must carry information about its size or have a mechanism to detect when the boundary has been reached. Statically allocated array types carry such information, but pointers do not.

### Example of Range-Based for Loop

```cpp
// Range-Based for
// for_each.cpp
#include <iostream>

int main() {
    int a[]{1, 2, 3, 4, 5, 6};

    for (int& e : a)
        std::cout << e << ' ';
    std::cout << std::endl;
}
```

#### Output
```
1 2 3 4 5 6
```

### Range-Based for Loop with Type Inference

A range-based for loop can infer the type of each element in the array from the array declaration itself.

```cpp
// Range-Based for with Type Inference
// for_each_auto.cpp
#include <iostream>

int main() {
    int a[]{1, 2, 3, 4, 5, 6};

    for (auto& e : a) // the type of an element will be inferred by the compiler
        std::cout << e << ' ';
    std::cout << std::endl;
}
```

#### Output
```
1 2 3 4 5 6
```
