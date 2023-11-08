# Week 9-0: Polymorphism, Virtual Functions in C++

## Types and Memory Representation

- Raw memory stores information as bit strings, which represent variables, objects, addresses, instructions, constants, etc.
- Associating a type with a region of memory tells the compiler how to interpret the bit string in that memory region.

```cpp
// Raw memory representation
struct Student {
    int id;             // 4 bytes
    float grades[3];    // 12 bytes (3 floats)
    int age;            // 4 bytes
};
```

## C++ Pointers for Polymorphism

- Polymorphic objects are represented using pointers syntax.
- A pointer's type indicates the static type of the object in the inheritance hierarchy.
- Static type is known at compile time.
- The pointer holds the memory address of the polymorphic object.

```cpp
// Creating polymorphic objects using pointers
Person jane("Jane");
float grades[] = {54.6f, 67.7f, 89.6f};
Student john("John", 1234, grades, 3);

Person* pJane = &jane;    // pJane points to a Person object
Person* pJohn = &john;    // pJohn points to a Student object
```

## Static and Dynamic Types

- Static type is known at compile time and defined by the pointer type.
- Dynamic type is the actual type of the object at runtime.
- Dynamic type is set when the object is created.

```cpp
// Static and dynamic types
void show(const Person*);

show(pJohn);  // Calls show() with a Student object (dynamic type)
show(pJane);  // Calls show() with a Person object (dynamic type)
```

## Function Bindings

- Function calls are bound to function definitions based on the object's type.
- Two types of binding:
    1. Early Binding (Static Binding): Based on the object's static type.
    2. Dynamic Dispatch (Dynamic Binding): Based on the object's dynamic type.

## Early Binding

- Early binding is based on the static type.
- Calls the function definition associated with the static type.
- Compile-time binding is the default in C++.
- No shadowing occurs when calling functions with early binding.

```cpp
// Early Binding
#include <iostream>

class Base {
public:
    void display() {
        std::cout << "Base::display()" << std::endl;
    }
};

class Derived : public Base {
public:
    void display() {
        std::cout << "Derived::display()" << std::endl;
    }
};

int main() {
    Base baseObj;
    Derived derivedObj;

    Base* ptr1 = &baseObj;     // Pointer to Base object
    Base* ptr2 = &derivedObj;  // Pointer to Derived object

    ptr1->display();  // Calls Base::display() (early binding)
    ptr2->display();  // Calls Base::display() (early binding)
    
    return 0;
}
```

In this example, even though `ptr2` points to a `Derived` object, the `display` function call is resolved at compile time and binds to the `Base::display()` method because the pointer's static type is `Base`. This is early binding.

## Dynamic Dispatch

- Dynamic dispatch postpones function binding until runtime.
- Achieved by using the `virtual` keyword in the base class.
- Calls the most derived version of the function based on the object's dynamic type.
- Enables different execution paths for different dynamic types.
- Useful for polymorphic behavior.

```cpp
// Dynamic Dispatch
#include <iostream>

class Base {
public:
    virtual void display() {
        std::cout << "Base::display()" << std::endl;
    }
};

class Derived : public Base {
public:
    void display() {
        std::cout << "Derived::display()" << std::endl;
    }
};

int main() {
    Base baseObj;
    Derived derivedObj;

    Base* ptr1 = &baseObj;     // Pointer to Base object
    Base* ptr2 = &derivedObj;  // Pointer to Derived object

    ptr1->display();  // Calls Base::display() (dynamic dispatch)
    ptr2->display();  // Calls Derived::display() (dynamic dispatch)
    
    return 0;
}
```

In this example, by marking the `display` function as `virtual` in the base class, we enable dynamic dispatch. Now, when `ptr2` points to a `Derived` object, the `display` function call is determined at runtime and it binds to `Derived::display()` because of the object's dynamic type.

## Overriding Dynamic Dispatch

- To override dynamic dispatch with early binding, resolve the scope explicitly.
```cpp
void show(const Person& p) {
    p.Person::display(std::cout);
}
```

## Polymorphic Objects

- Polymorphic objects can change their dynamic type during their lifetime.
- Static type is specified using pointer declarations or receive-by-address/receive-by-reference parameters.
- Dynamic type is set when the object is created.

```cpp
// Polymorphic Objects - Static Type
Person* p = nullptr;  // Static type specified by pointer declaration
p = new Person("Jane Doe");  // Dynamic type set at runtime

// Polymorphic Objects - Dynamic Type
p = new Student("Harry", 1234, grades, 3);  // Dynamic type changed at runtime
```

## Good Design

- Declare base class destructors as virtual, even if no class is derived from the base class.
- This ensures that the most derived destructor is called at destruction time.

```cpp
// Good Design - Using a virtual destructor
class Base {
public:
    virtual ~Base() {
        // Destructor code
    }
};

class Derived : public Base {
public:
    ~Derived() override {
        // Derived destructor code
    }
};
```

## Reusability and Flexibility

- Inclusion polymorphism with virtual functions improves reusability and flexibility.
- Reduces code size as one function works on references of any type in the hierarchy.
- Easily add new derived classes without altering existing client code.

```cpp
// Reusability and Flexibility - Using virtual functions
void show(const Person& p) {
    p.display(std::cout);  // Calls the most derived version of display()
}
```
