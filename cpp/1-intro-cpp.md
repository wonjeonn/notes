# Week 1: Introduction to Object-Oriented Programming (C++)

## Namespaces

- **Namespaces:** Namespaces are used to group application identifiers to prevent naming conflicts.
- Defined using `namespace identifier { }`.
- Access entities within a namespace using `namespace::entity`.
- `using` declaration exposes an identifier to the current namespace.
- `using` directive exposes all identifiers in a namespace.

## Input and Output in C++

- C++ input uses `cin` and the `>>` extraction operator.
- Output utilizes `cout` and the `<<` insertion operator.
- Object-oriented C++ uses `iostream` for input/output.

## Object and Class

- Object-oriented languages emphasize high cohesion and loose coupling.
- Objects are data abstractions with clear boundaries and defined structures.
- A class defines the common structure shared by objects.
- Each object is an instance of a class.

## Fundamental OOP concepts

- **Encapsulation** hides implementation details within a class.
- Clients access objects through a well-defined interface, unaware of internal data and logic.
- **Inheritance** allows one class to inherit the structure of another.
- **Polymorphism** provides different implementations based on an object's type.

### Integral Types

- `bool`: Represents true or false.
- `char`: Represents a single character.
- `int`, `short`, `long`, `long long`: Various integral numeric types.

### Floating Point Types

- `float`: Single-precision floating-point type.
- `double`: Double-precision floating-point type.
- `long double`: Extended-precision floating-point type.

- `bool` is unique as it exclusively holds `true` or `false` and the `!` operator can invert its value.

## Compound Types

Compound types are used to group related variables together.

```cpp
struct Transaction {
    int acct;      // account number
    char type;     // credit 'c' or debit 'd'
    double amount; // transaction amount
};
```

## Declarations and Definitions

- A **declaration** associates an entity with a type, without specifying its meaning. A function prototype like `int add(int, int);` is a declaration.

- A **definition** is a declaration that attaches meaning to an identifier. Defining the struct `Transaction` or a function like `void display(const Transaction* tr)` provides meaning.

- The One-Definition Rule mandates that a definition can only appear once within its scope.

## Function Overloading

- In C++, functions can have multiple meanings through overloading. Functions with the same name but different parameter lists are considered overloaded.
- The C++ compiler distinguishes overloaded functions by matching the argument types in function calls to the parameter types in the function definition.

```cpp
void display(int x);
void display(const int* x, int n);
```

## References

A **reference** is an alias for a variable or object., allows passing variables by reference.

```cpp
void swap(char& a, char& b);
```

## Array of Pointers

Arrays of pointers are data structures used to store memory addresses.

```cpp
struct Student {
    int no;
    double grade;
    char name[N_CHARS];
};

Student john = {1234, 67.8, "john"};
Student* pStudent[NO_STUDENTS]; // Array of pointers

pStudent[0] = &john;
```

## Static Memory

- **Static memory** is allocated at load time, determined at compile time and lasts throughout the application's lifetime.
- When a variable or object goes out of scope, its memory becomes available for new variables or objects.

## Dynamic Memory

- **Dynamic memory** is allocated during program execution and can be expanded or reduced as needed. However, it comes with the responsibility of explicit allocation and deallocation.
- Dynamic memory is managed using pointers. A pointer stores the address of a dynamically allocated memory region.

## Dynamic Allocation

```cpp
int n;                  // the number of students
Student* student = nullptr; // the address of the dynamic array

cout << "How many students in this section? ";
cin >> n;

student = new Student[n]; // allocates dynamic memory
```

## Dynamic Deallocation

```cpp
delete[] student;
student = nullptr;  // good programming style
```

The `delete` operator releases the memory and assigning `nullptr` to the pointer is a good practice to prevent accidental double deallocation.

## A Complete Example

```cpp
#include <iostream>
using namespace std;

struct Student {
    int no;
    double grade[2];
};

int main() {
    int n;
    Student* student = nullptr;

    cout << "Enter the number of students: ";
    cin >> n;
    student = new Student[n];

    for (int i = 0; i < n; i++) {
        cout << "Student Number: ";
        cin >> student[i].no;
        cout << "Student Grade 1: ";
        cin >> student[i].grade[0];
        cout << "Student Grade 2: ";
        cin >> student[i].grade[1];
    }

    for (int i = 0; i < n; i++) {
        cout << student[i].no << ": "
             << student[i].grade[0] << ", " << student[i].grade[1]
             << endl;
    }

    delete[] student;
    student = nullptr;
}
```

## Memory Issues

- **Memory Leaks:** Occur when an application loses the address of dynamically allocated memory before deallocating it.

- **Insufficient Memory:** On platforms with limited memory, the operating system may not fulfill a dynamic memory request.
