# Class

## Class Basics

A **class** in C++ is a blueprint for creating objects, representing a set of data and functions that operate on that data. Classes can include multiple types of data, unlike arrays that contain elements of the same type. The functions within a class define its logic. Classes do not guarantee contiguous memory storage for their data members due to alignment requirements, leading to potential padding by the compiler.

### Class Keys

1. **class**: Members are private by default, promoting encapsulation.
2. **struct**: Members are public by default, facilitating information sharing.
3. **union**: Members share the same memory location, with only one active at a time.

### Class Definitions
A class definition introduces a type and declares its sub-objects and member functions.

```cpp
class-key Identifier {
    sub-object declarations
    member function declarations
};
```

Example:

```cpp
class Subject {
    unsigned number;
    char desc[41];
    Subject* prerequisite; // OK - pointer to Subject
};
```

### Forward Declarations
Forward declarations introduce a class name without defining its members.

```cpp
class Identifier;
```

### Instance Definitions
You can define an instance within the class definition.

```cpp
class Subject {
    unsigned number;
    char desc[41];
} subject, *pSubject;
```

### Default Member Initialization
Data members can be initialized directly within the class definition.

```cpp
class Item {
    int item = ++nItems;               // default initializer
    const std::string name{"empty"};   // default initializer
public:
    Item() {}
    Item(const char* n) : name{n} {}
    Item(const char* n, int i) : name{n}, item{i} {}
};
```

### Member List Initializers
Constructors can initialize data members using member-list initializers.

```cpp
Item(const char* n, int i) : name{n}, item{i} {}
```

## Copying

### Copy Construction and Copy Assignment
Classes manage resources using user-defined copy constructors and copy-assignment operators. 

Example:

```cpp
class Array {
    int* a = nullptr;
    unsigned n = 0u;
    int dummy = 0;

public:
    Array() {}
    Array(unsigned no) : a(new int[no]), n(no) {}
    Array(const Array& src) { *this = src; }

    Array& operator=(const Array& src) {
        if (this != &src) {
            delete[] a;
            n = src.n;
            a = new int[src.n];
            for (unsigned i = 0u; i < src.n; ++i)
                a[i] = src.a[i];
        }
        return *this;
    }

    ~Array() { delete[] a; }

    int& operator[](unsigned i) {
        return n > 0u && i < n ? a[i] : dummy;
    }

    int operator[](unsigned i) const {
        return n > 0u && i < n ? a[i] : dummy;
    }

    unsigned size() const { return n; }
};
```

## Move Semantics

### Move Construction and Move Assignment
Move constructors and move-assignment operators efficiently transfer resources from a temporary object that is about to be destroyed.

```cpp
class Array {
    // ...
public:
    Array(Array&& src) { *this = std::move(src); }
    Array& operator=(Array&& src) {
        if (this != &src) {
            delete[] a;
            n = src.n;
            a = src.a;
            src.a = nullptr;
        }
        return *this;
    }
    // ...
};
```

## Class Members

### Class Variables
Class variables are shared among all instances and declared using the `static` keyword. They are defined and initialized outside the class.

```cpp
class Horse {
    unsigned age;
    unsigned id;
public:
    static unsigned noHorses;
    Horse(unsigned a);
    ~Horse();
};

unsigned Horse::noHorses = 0;

Horse::Horse(unsigned a) : age{a}, id{++noHorses} {}
Horse::~Horse() { --noHorses; }
```

## Structs
Structs are similar to classes but with public members by default.

```cpp
struct Subject {
    unsigned number;
    char desc[41];
};
```

## Unions
Unions allow different members to share the same memory location.

```cpp
union Product {
    int sku;
    char upc[13];
};

int main() {
    Product cereal, tissue;
    cereal.sku = 4789;
    std::strcpy(tissue.upc, "0360002607555");
    std::cout << cereal.sku << std::endl;
    std::cout << tissue.upc << std::endl;
}
```

## Plain Enumerations

Plain enumerations are defined using the `enum` keyword, followed by the enumeration type and a list of symbolic constants. By default, the underlying type is `int`.

**Syntax:**
```cpp
enum Type {
    symbolic_constant_1,
    symbolic_constant_2,
    symbolic_constant_3,
    ...
};
```

**Example:**
```cpp
#include <iostream>
#include <string>

enum Colour { white, red, green, blue };

std::ostream& operator<<(std::ostream& os, const Colour& colour) {
    std::string str;
    switch(colour) {
        case white: str = "white"; break;
        case red: str = "red"; break;
        case green: str = "green"; break;
        case blue: str = "blue"; break;
        default: str = "none";
    }
    os << str;
    return os;
}

int main() {
    Colour wall = red, ceiling = white, door = green;
    std::cout << wall << ' ' << ceiling << ' ' << door << std::endl;
}
```

**Output:**
```
red white green
```

### Tracking Access in Unions Using Structs and Enumerations

To track which member of a union was last accessed, wrap the union in a struct and use an enumeration to record the accessed member.

**Example:**
```cpp
#include <iostream>
#include <cstring>

enum ProductId { sku, upc };

struct Product {
    ProductId id;
    union {
        int sku;
        char upc[13];
    } code;
    char desc[100];
};

int main() {
    Product p[2];
    p[0].id = sku;
    p[0].code.sku = 4789;
    std::strcpy(p[0].desc, "A history book about ancient Rome.");

    p[1].id = upc;
    std::strcpy(p[1].desc, "A universal remote control for TVs.");
    std::strcpy(p[1].code.upc, "0360002607555");

    for (int i = 0; i < 2; i++) {
        switch(p[i].id) {
            case sku: std::cout << p[i].code.sku << std::endl; break;
            case upc: std::cout << p[i].code.upc << std::endl; break;
        }
    }
}
```

**Output:**
```
4789
0360002607555
```

### Scoped Enumerations

Scoped enumerations (enum classes) limit the scope of their enumerators, reducing namespace pollution and providing stronger type safety.

**Syntax:**
```cpp
enum class Type {
    symbolic_constant_1,
    symbolic_constant_2,
    symbolic_constant_3,
    ...
};
```

**Example:**
```cpp
#include <iostream>
#include <string>

enum class Colour { white, red, green, blue };

std::ostream& operator<<(std::ostream& os, const Colour& colour) {
    std::string str;
    switch(colour) {
        case Colour::white: str = "white"; break;
        case Colour::red: str = "red"; break;
        case Colour::green: str = "green"; break;
        case Colour::blue: str = "blue"; break;
        default: str = "none";
    }
    os << str;
    return os;
}

int main() {
    Colour wall = Colour::red, ceiling = Colour::white, door = Colour::green;
    std::cout << wall << ' ' << ceiling << ' ' << door << std::endl;
}
```

**Output:**
```
red white green
```

### Underlying Types

Enumerators can have custom underlying types, allowing you to assign specific values.

**Example:**
```cpp
enum class Colour {
    white = 0x01,
    red   = 0x02,
    green = 0x04,
    blue  = 0x08
};
```

### Modifying an Enumeration

You can easily add new enumerators to an enumeration without affecting the existing values.

**Example:**
```cpp
#include <iostream>
#include <string>

enum class Colour { white, yellow, red, green, blue };

std::ostream& operator<<(std::ostream& os, const Colour& colour) {
    std::string str;
    switch(colour) {
        case Colour::white: str = "white"; break;
        case Colour::yellow: str = "yellow"; break;
        case Colour::red: str = "red"; break;
        case Colour::green: str = "green"; break;
        case Colour::blue: str = "blue"; break;
        default: str = "none";
    }
    os << str;
    return os;
}

int main() {
    Colour wall = Colour::red, ceiling = Colour::white, door = Colour::green, window = Colour::yellow;
    std::cout << wall << ' ' << window << ' ' << ceiling << ' ' << door << std::endl;
}
```

**Output:**
```
red yellow white green
```
