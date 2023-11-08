# Week 3: Encapsulation, The Current Object and Member Operators

## The Current Object

- Distinguishing Member Function's Access

    - Member functions operate on a specific object, referred to as the **current object**.
    - Access to instance variables and client variables is distinguished within member functions.

- Accessing the Current Object

    - The **`this`** keyword holds the address of the current object.
    - **`*this`** refers to the current object itself, representing its complete set of instance variables.
    - Member functions can access the current object's data through implicit parameters.

- Member Function Parameters

    1. Explicit parameters: These parameters access the client code and are explicitly defined in the function's parameter list.
    2. Implicit parameters: These parameters access the instance variables of the current object. They are not explicitly defined but are available to the member function.

```cpp
class Student {
private:
    int no;
    float grade[NG];
    int ng;

public:
    Student();
    Student(int sn, const float* g, int ng_);
    void display() const;
    Student& operator+=(float g);
};

Student& Student::operator+=(float g) {
    if (no != 0 && ng < NG && g >= 0.f && g <= 100.f)
        grade[ng++] = g;
    return *this;
}

int main() {
    float gh[] = {89.4f, 67.8f, 45.5f};
    Student harry(1234, gh, 3);
    harry += 78.23f;
    harry.display();
}
```

- Return Types and Assignments

    - Member functions can return copies of the current object or references to it.
    - Assigning to the current object involves using **`*this`** in an assignment expression.

## Type Conversion Operators

- Type conversion operators allow implicit conversion of class objects to other types, including fundamental types.
- In this example, a `bool` conversion operator is defined to allow a `Student` object to be used in a condition as if it were a `bool`.

```cpp
class Student {
public:
    operator bool() const;
};

Student::operator bool() const {
    return no != 0;
}
```

## Cast Operator

- Casting operations for a class type are defined using a single-argument constructor.
- In this example, a constructor with a single `int` argument allows the implicit conversion of an `int` to a `Student` object.

```cpp
class Student {
public:
    Student(int);
};

Student::Student(int sn) {
    float g[] = {0.0f};
    set(sn, g, 0);
}
```

## Binary Operators

Binary operators work on two operands and can be overloaded as member functions.

```cpp
class Student {
public:
    Student& operator+=(float g);
};

Student& Student::operator+=(float g) {
    if (no != 0 and ng < NG and g >= 0.f and g <= 100.f)
        grade[ng++] = g;
    return *this;
}
```

## Unary Operators

Unary operators work on a single operand and can be overloaded for pre-fix and post-fix operations.

1. Pre-fix operators, like `++x` or `--x`, modify the current object directly and return a reference to it.
2. Post-fix operators, like `x++` or `x--`, modify the current object after returning its original value.

```cpp
class Student {
public:
    Student& operator++();     // Pre-fix
    Student operator++(int);   // Post-fix
};

Student& Student::operator++() {
    for (int i = 0; i < ng; i++)
        if (grade[i] < 99.0f) grade[i] += 1.f;
    return *this;
}

Student Student::operator++(int) {
    Student s = *this;  // Save the original
    ++(*this);          // Call the pre-fix operator
    return s;           // Return the original
}
```
