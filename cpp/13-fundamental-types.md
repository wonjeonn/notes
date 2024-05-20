# Fundamental Types

## Memory Interpretation and Operations
1. **Interpretation**: How to interpret the bit string in the memory.
2. **Operations**: What operations can be performed on the bit string.

## Integer Types

- **Standard Integers**:
  - **Signed**: Can hold negative and positive values.
  - **Unsigned**: Can only hold non-negative values.
- **Booleans**: Represent true/false values.
- **Character Types**: Represent characters.

## Range Specifiers
- **Signed**: Negative and positive values.
- **Unsigned**: Only positive values.

## Endianness
- **Big-endian**: Stores the highest-order byte first.
- **Little-endian**: Stores the lowest-order byte first.

## Standard Signed Integers

- **signed char**: Typically 1 byte.
- **short int**: Typically at least 2 bytes.
- **int**: Typically 4 bytes.
- **long int**: Typically at least 4 bytes.
- **long long int**: Typically at least 8 bytes.

    ```cpp
    // signed char example
    signed char c; // for possibility of receiving EOF
    signed char k, m, n, p;
    k = '[';    // character
    m = '\133'; // octal - note the leading \
    n = '\x5b'; // hexadecimal - note the leading \x
    p = '\X5B'; // hexadecimal - note the leading \X

    // short int example
    short int s = 32767;

    // int example
    int a, b, c, d;
    a = 91;   // decimal
    b = 0133; // octal - note the leading 0
    c = 0x5b; // hexadecimal - note the leading 0x
    d = 0X5B; // hexadecimal - note the leading 0X

    // long int example
    long int a, b, c, d;
    a = 91L;   // decimal notation
    b = 0133L; // octal notation; note the leading 0
    c = 0x5bL; // hexadecimal notation; note the leading 0x
    d = 0X5BL; // hexadecimal notation; not the leading 0X

    // long long int example
    long long int a, b, c, d;
    a = 91LL;   // decimal
    b = 0133LL; // octal
    c = 0x5bLL; // hexadecimal
    d = 0X5BLL; // hexadecimal
    ```

## Unsigned Standard Integers
Corresponding to the signed types, unsigned integers only hold non-negative values.

    ```cpp
    unsigned int g;
    unsigned long int h;
    unsigned long long int k;
    g = 0x5bU;  // unsigned int: U or u
    h = 0X5BUL; // unsigned long: (U or u) and (L or l) any order
    k = 456789012345ULL; // unsigned long long: (U or u, LL or ll) any order
    ```

## Ranges

| Type               | Minimum                          | Maximum                            |
|--------------------|----------------------------------|------------------------------------|
| signed char        | -128                             | 127                                |
| short int          | -32,768                          | 32,767                             |
| int                | -2,147,483,648                   | 2,147,483,647                      |
| long int           | -2,147,483,648                   | 2,147,483,647                      |
| long long int      | -9,223,372,036,854,775,808       | 9,223,372,036,854,775,807          |
| unsigned char      | 0                                | 255                                |
| unsigned short int | 0                                | 65,535                             |
| unsigned int       | 0                                | 4,294,967,295                      |
| unsigned long int  | 0                                | 4,294,967,295                      |
| unsigned long long int | 0                            | 18,446,744,073,709,551,615         |


## Boolean Type
The `bool` type represents `true` or `false`.

```cpp
bool flag = true;
```

## Six Character Types

- `char`
- `signed char`
- `unsigned char`
- `wchar_t`
- `char16_t`
- `char32_t`

    ```cpp
    // wchar_t example
    wchar_t w = L'[';

    // char16_t example
    char16_t c16 = u'[';

    // char32_t example
    char32_t c32 = U'[';
    ```

## Three Floating-Point Types

- `float`: Typically 4 bytes.
- `double`: Typically 8 bytes.
- `long double`: At least 8 bytes.

    ```cpp
    // float example
    float f = 3.14f;

    // double example
    double d = 3.14;

    // long double example
    long double ld = 3.14L;
    ```

## Void Type
- The `void` type is an incomplete type. A type is incomplete if it is missing some information. C++ does not allow the creation of objects of type void.
- A `void` type is used for the return type of functions that do not return a value and for generic pointers.


## Initialization

```cpp
// Initialization Expressions
#include <iostream>

int main () {
    int n0 = 7;   // C-style
    int n1 = 7.2; // C-style - narrowing
    int n2 {6};   // universal form
    int n3 = {5}; // universal form

    std::cout << "n0 = " << n0 << std::endl;
    std::cout << "n1 = " << n1 << std::endl;
    std::cout << "n2 = " << n2 << std::endl;
    std::cout << "n3 = " << n3 << std::endl;
    return 0;
}
```

## Type Inference
Type inference with `auto` keyword allows the compiler to infer types.

```cpp
#include <iostream>

int main () {
    int a[] {1, 2, 3, 4, 5, 6};
    const auto n = 6;

    for (auto i = 0; i < n; i++)
        std::cout << a[i] << ' ';
    std::cout << std::endl;

    return 0;
}
```

## Type Alignment
C++ types can be aligned in memory using the `alignas` specifier. The `alignof` operator returns the alignment requirement of a type.

```cpp
#include <iostream>

struct A {
    int n;  // size 4, alignment 4
    char c; // size 1, alignment 1
}; // size 8, alignment 4

struct alignas(16) B {
    int n;  // size 4, alignment 4
    char c; // size 1, alignment 1
}; // size 8, alignment 16

int main() {
    std::cout << "align of int: " << alignof(int) << std::endl;
    std::cout << "align of double: " << alignof(double) << std::endl;

    A a;
    B b;

    std::cout << "align of A: " << alignof(A) << std::endl;
    std::cout << "align of B: " << alignof(B) << std::endl;

    return 0;
}
```
