# Object Oriented Paradigm

## Classes and Objects:
  - **Class**: Defines the structure and behavior of objects.
  - **Object**: Instance of a class, with its own state (values of attributes).

## Three Core Concepts
1. **Encapsulation**:
   - **Definition**: Couples data with the logic that manipulates it.
   - **Types**:
     - **Weak Encapsulation**: Couples state and logic without privacy.
     - **Strong Encapsulation**: Includes privacy, protecting the object's data.

2. **Inheritance**:
   - **Definition**: Enables one class to inherit the structure and behavior of another class.
   - **Base Class**: Original class providing inherited features.
   - **Derived Class**: New class adding features to the base class.

3. **Polymorphism**:
   - **Definition**: Allows multiple behaviors for a single identifier based on the object's dynamic type.
   - **Dynamic Type**: Determines the specific behavior at runtime.

## Modularity
- **Definition**: Divides source code into modules (self-contained units).
- **Advantages**: 
  - Independent compilation of modules.
  - Only affected modules need recompilation after changes.

## Building Blocks of OOP Languages
- **Values, Objects, Variables, References, Functions, Types, Class Members, Templates, Namespaces**:
  - **Object**: Memory region with a value, may or may not have a name.
  - **Variable**: Named object.

## Types
- **Categories**:
  - **Fundamental Types**: Directly correspond to hardware.
  - **Built-in Types**: Reflect hardware capabilities.
  - **User-Defined Types**:
    - **Concrete Types**: Known representation.
    - **Abstract Types**: Unknown representation.

## Declarations and Scope
- **Declarations**: Introduce names and associate them with types.
- **Scope**: Defines where a name is valid within the code (local, class, namespace, global).
- **Linkage**: Determines if a name can refer to an identical name in another scope.

## Compilers
- **Function**: Translate source code into binary code.
- **Language Standards**: Ensure portability across different compilers.
- **Type System**: Provides consistency and admissibility checks for operations.

## Compiling, Linking, and Executing
- **Verification**: Checks compliance with the type system at compile-time, link-time, and run-time.

## Memory Distinctions
- **Memory Segments**:
  - **Code Segment**: Stores program instructions.
  - **Data Segments**: Store persistent data.
  - **Stack Segment**: Stores statically allocated local data.
  - **Heap Segment**: Stores dynamically allocated local data.

## Building Blocks

1. **Entities**: Include values, variables, objects, references, functions, types, class members, templates, and namespaces.
2. **Translation Units**: Consist of a header file and an implementation file. The compiler processes each module as an independent translation unit.

## Declarations and Definitions

- **Declaration**: Introduces a name into a translation unit.
- **Definition**: Associates a meaning with a name. A definition is also a declaration but not vice versa.
- **One Definition Rule**: Each definition must appear only once across all translation units.

## Scope

- **Block Scope**: Local to the block; extends from declaration to block end.
- **Class Scope**: Extends from object construction to destruction.
- **Global Scope**: Visible throughout the entire program.
- **Shadowing**: A local name can hide a broader scope name.

## Linkage

- **External Linkage**: Allows a name to be shared across multiple translation units using `extern`.
- **Internal Linkage**: Restricts a name to its translation unit using `static`.

## Types and cv-Qualifiers

- **cv-Qualifiers**: 
  - `const`: Unmodifiable.
  - `volatile`: Subject to side-effects.
  - `const volatile`: Unmodifiable and subject to side-effects.

- **Type Definition**: 
  - `typedef`: Creates an alias for a type.
  - Example: `typedef const int constInt;`

## Namespaces

- **Declaration**:
  ```cpp
  namespace identifier {
      // declarations
  }
  ```
- **Anonymous Namespaces**: Restrict visibility to the translation unit.

## Storage Duration

- **Automatic**: Lifetime from declaration to the end of scope.
- **Static**: Lasts the entire program duration.
- **Dynamic**: Managed via `new` and `delete`.
- **Thread**: Lifetime of the thread, using `thread_local`.

**Block Scope with Selection Constructs Example**
```cpp
#include <iostream>

int main() {
    int i;
    std::cout << "Enter i: ";
    std::cin >> i;
    if (int j = i % 10; j < 5) {
        i -= j;  // round down
    } else {
        i += 10 - j;  // round up
    }
    std::cout << i << std::endl;

    std::cout << "Enter i: ";
    std::cin >> i;
    switch (int j = i % 10; j / 5) {
      case 0: // round down
        i -= j;
        break;
      case 1: // round up
        i += 10 - j;
    }
    std::cout << i << std::endl;
}
```

**External Linkage Example**
```cpp
// Module_a.cpp
#include <iostream>
extern int share_me; // external linkage declaration

void display() {
    std::cout << "Module A: share_me at " << &share_me << '\n';
    std::cout << "Module A: share_me is " <<  share_me++ << '\n';
}

// Module_b.cpp
#include <iostream>
void display();
int share_me = 0; // variable definition

int main() {
    display();
    display();
    std::cout << "Module B: share_me at " << &share_me << '\n';
    std::cout << "Module B: share_me is " <<  share_me++ << '\n';
}
```

**Static Duration Example**
```cpp
#include <iostream>

void display() {
    static int n = 1;
    std::cout << "n is " << n++ << std::endl;
}

int main() {
    display();
    display();
}
```

**Namespaces Example**
```cpp
// dot.h
namespace dot {
    const char* leader(char*);
    const int ML = 15;
}

// dot.cpp
#include "dot.h"
namespace dot {
    const char* leader(char* s) {
        for (int i = 0; i < ML; i++)
            s[i] = '.';
        s[ML] = '\0';
        return s;
    }
}

// main.cpp
#include "dot.h"
int main() {
    char s[51];
    std::cout << dot::leader(s) << std::endl;
}
```

## Compilation Process

1. **Pre-Processing Stage**:
   - **Function**: Creates a translation unit for each module.
   - **Process**: Inserts header files into implementation files and expands macros.
   - **Output**: Pre-processed source file.

2. **Compilation Stage**:
   - **Function**: Compiles each translation unit into a binary file.
   - **Process**: Converts source code into machine code.
   - **Output**: Object file (.obj or .o).

3. **Linking Stage**:
   - **Function**: Combines all object files and libraries into a single executable.
   - **Process**: Resolves references between object files.
   - **Output**: Relocatable executable file.

### Running the Executable
- **Loader**: Loads the executable into memory, arranges storage, and transfers control to the `main()` function.

## Platforms and Compilers
- **Windows**: Uses Microsoft Visual Studio (cl compiler).
  - **Compiler Options**:
    - `/c`: Compile only.
    - `/E`: Pre-process only, output to stdout.
    - `/P`: Pre-process only, output to file.
    - `/Wall`: Enable all warnings.
  - **Example**: Disable warning for unsafe functions using `#define _CRT_SECURE_NO_WARNINGS`.

- **Linux**: Uses GNU Compiler Collection (gcc).
  - **Compiler Options**:
    - `-c`: Compile without linking.
    - `-E`: Pre-process only.
    - `-g`: Produce debugging information.
  - **Example**: Access specific GCC version and compile with `g++`.

### Interface with the Operating System
- **Entry Point**: `main()` function with return type `int`.
  - **Prototypes**:
    - `int main();`
    - `int main(int argc, char *argv[]);`
  - **Command-Line Arguments**:
    - `argc`: Number of arguments.
    - `argv[]`: Array of C-style strings representing arguments.

- **Example**: Command-line arguments processing.
  ```cpp
  #include <iostream>

  int main (int argc, char *argv[]) {
      std::cout << "Application: " << argv[0] << std::endl;
      for (int i = 1; i < argc; i++)
          std::cout << "- " << argv[i] << std::endl;
  }
  ```

## Compile-Time Evaluations
- **Constant Expressions**: `constexpr` for values known at compile-time.
  - **Example**: Factorial calculation.
  ```cpp
  constexpr int factorial(int i) {
      return i > 1 ? i * factorial(i - 1) : 1;
  }
  ```

- **Static Assertions**: `static_assert()` for compile-time checks.
  - **Example**: Check value of `N`.
  ```cpp
  static_assert (N >  0, "N <=  0");
  static_assert (N < 20, "N >= 20");
  ```
