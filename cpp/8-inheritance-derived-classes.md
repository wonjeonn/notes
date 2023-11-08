# Week 8: Inheritance, Derived Classes

## Derived Classes

- Derived classes inherit attributes and behaviors from their base (parent) classes.
- The derived class is the child in an **"is-a"** relationship, while the base class is the parent. The derived class inherits the entire structure of its base class.
- Base Class: Super Class, Parent Class
- Derived Class: Subclass, Heir Class, Child Class

**Terminology and "is-a" Relationship**

- Inheritance establishes an "is-a" relationship between classes.
- E.g., a **`Student` is a kind of `Person`**. The "is-a" relationship defines the derived class as a specialized version of the base class.

**Inherited Structure**

- A derived class contains all the instance variables and normal member functions of its base class.
- It does not inherit special functions like **constructors, destructors, or assignment operators**.

## Definition of a Derived Class

```cpp
class Derived : access Base {
    // ...
};
```

- `Derived`: The name of the derived class.
- `Base`: The name of the base class.
- `access`: Specifies the access that member functions of the derived class have to the non-private members of the base class. The default access is private.

### Example: Student Class

- A `Student` class derived from a `Person` class. The `Person` class includes an instance variable for a person's name.
- A `Student` class inherits from a `Person` class and adds its own attributes.

```cpp
// Student.h

#include <iostream>
const int NC = 30;
const int NG  = 20;

class Person {
    char name[NC+1];
public:
    void set(const char* n);
    void displayName(std::ostream&) const;
};

class Student : public Person {
    int no;
    float grade[NG];
    int ng;
public:
    Student();
    Student(int);
    Student(int, const float*, int);
    void display(std::ostream&) const;
};
```

```cpp
// Derived Classes
// derived.cpp

#include <iostream>
#include "Student.h"

int main() {
    float gh[] = {89.4f, 67.8f, 45.5f};
    Student harry(1234, gh, 3);
    harry.set("Harry");           // Inherited from Person
    harry.displayName(std::cout); // Inherited from Person
    harry.display(std::cout);     // Defined in Student
}
```

## Access

- Private: Bars all access
- Protected: Limits access to derived classes only
- Public: Unlimited access

### Limiting Access with Protected Access:

#### Example Classes:

```cpp
class Person {
    char name[NC + 1];

public:
    void set(const char* n);
    
protected:
    void displayName(std::ostream&) const;
};

class Student : public Person {
    int no;
    float grade[NG];
    int ng;

public:
    Student();
    Student(int);
    Student(int, const float*, int);
    void display(std::ostream&) const;
};
```

- `Person` class has a protected member function, `displayName()`.
- `Student` class is derived from `Person`.

### Usage of `protected` Access:

- The `displayName()` function is marked as `protected`, so it can be accessed within `Student` but not from external code.

### Implementing Derived Class:

```cpp
void Student::display(std::ostream& os) const {
    if (no > 0) {
        displayName(os);
        os << no << ":\n";
        os.setf(ios::fixed);
        os.precision(2);
        for (int i = 0; i < ng; i++) {
            os.width(6);
            os << grade[i] << endl;
        }
        os.unsetf(ios::fixed);
        os.precision(6);
    } else {
        os << "no data available" << endl;
    }
}
```

- In `Student::display()`, the `displayName()` function is directly called, as `Student` can access the protected member.

### Client Code:

```cpp
int main() {
    float gh[] = {89.4f, 67.8f, 45.5f};
    Student harry(1234, gh, 3);
    harry.set("Harry");           // Inherited
    harry.display(std::cout);     // Not inherited
}
```

- In the client code, the `displayName()` function cannot be called directly because it is marked as `protected`. However, it can be used within `Student`'s member functions as demonstrated.

### Avoid Granting Protected Access to Data Members

- Granting protected access to data members can compromise security.
- It allows derived classes to bypass validation procedures in the base class, potentially leading to unintended behavior or corruption of data.
- **Read-Only Queries**: Instead of providing direct access, implement read-only queries that allow derived classes to retrieve information without modifying the data members.

```cpp
class Person {
public:
    const char* getName() const;
};
```
