# Week 9-1: Abstract Base Classes

## Pure Virtual Functions

   - A pure virtual function is a function with no implementation in the base class.
   - It is declared as `virtual Type identifier(parameters) = 0;`.
   - It serves as a placeholder for a function that must be implemented by derived classes.
   - Pure virtual functions are used to create abstract classes.

## Abstract Classes

   - An abstract class is a class that contains or inherits at least one pure virtual function.
   - Abstract classes cannot be instantiated and any attempt to do so results in a compiler error.
   - Abstract classes are used to define interfaces and provide a common set of functions for derived classes.
   - Abstract classes can have data members but usually don't provide implementations for functions.

**Example: Abstract Class and Pure Virtual Function**

```cpp
#include <iostream>

// Abstract Base Class for the Person Hierarchy
class iPerson {
public:
    virtual void display(std::ostream&) const = 0;
};

class Person : public iPerson {
    char name[30 + 1];
public:
    Person();
    Person(const char*);
    void display(std::ostream&) const;
};

class Student : public Person {
    int no;
    float grade[20];
    int ng;
public:
    Student();
    Student(int);
    Student(const char*, int, const float*, int);
    void display(std::ostream&) const;
};

// Implementation of functions
// ...

int main() {
    iPerson* p = new Student("Jane Doe", 1234, new float[]{45.6, 67.8, 89.5}, 3);
    p->display(std::cout);
    delete p;
    return 0;
}
```

- `iPerson` is an abstract class with a pure virtual function `display`.
- `Person` and `Student` derive from `iPerson` and provide their implementations of the `display` function.
- An object of the `Student` class is created and stored in a pointer of type `iPerson`, allowing for dynamic dispatch.

## Array of Pointers

   - A systematic technique for accessing objects of different dynamic type within the same hierarchy is through an array of pointers of their static type.
   - The executable code dereferences each pointer at run time based on its object's dynamic type.

```cpp
iPerson* p[NP];  // Array of pointers
p[0] = new Person();
p[1] = new Student();
```

## Concrete Class Definitions
   - Concrete classes are derived from abstract base classes and provide implementations for pure virtual functions.

```cpp
// Concrete classes derived from `iPerson`:
class Person : public iPerson {
    // Implement the display function
};
class Student : public Person {
    // Implement the display function
};
```

## Unit Tests on an Interface
   - Unit tests should be written for the interface, not specific implementations.
   - Unit tests do not need to change as new implementations are added.

**Example of a unit test for an interface:**
```cpp
// Sorter Interface
// iSorter.h

class iSorter {
public:
    virtual void sort(float*, int) = 0;
    virtual const char* name() const = 0;
};

iSorter* CreateSorter(int);
int noOfSorters();

// Sorter Concrete Classes
// Sorter.h

#include "iSorter.h"

class SelectionSorter : public iSorter {
public:
    void sort(float*, int);
    const char* name() const;
};

class BubbleSorter : public iSorter {
public:
    void sort(float*, int);
    const char* name() const;
};

iSorter* CreateSorter(int);
int noOfSorters();

// Sorter Hierarchy - Implementation
// Sorter.cpp

#include "Sorter.h"

void SelectionSorter::sort(float* a, int n) {
    int i, j, max;
    float temp;

    for (i = 0; i < n - 1; i++) {
        max = i;
        for (j = i + 1; j < n; j++)
            if (a[max] > a[j])
                max = j;
        temp = a[max];
        a[max] = a[i];
        a[i] = temp;
    }
}

const char* SelectionSorter::name() const {
    return "Selection Sorter";
}

void BubbleSorter::sort(float* a, int n) {
    int i, j;
    float temp;

    for (i = n - 1; i > 0; i--) {
        for (j = 0; j < i; j++) {
            if (a[j] > a[j+1]) {
                temp = a[j];
                a[j] = a[j+1];
                a[j+1] = temp;
            }
        }
    }
}

const char* BubbleSorter::name() const {
    return "Bubble Sorter";
}

iSorter* CreateSorter(int i) {
    iSorter* sorter = nullptr;
    switch (i) {
        case 0:
            sorter = new SelectionSorter();
            break;
        case 1:
            sorter = new BubbleSorter();
            break;
    }
    return sorter;
}

int noOfSorters() {
    return 2;
}
```

**Unit Tester:**
```cpp
// Test Main for the iSorter Interface
// Test_Main.cpp

#include <iostream>
#include <ctime>
#include "iSorter.h"

void populate(float* a, int n) {
    srand(time(nullptr));
    float f = 1.0f / RAND_MAX;
    for (int i = 0; i < n; i++)
        a[i] = rand() * f;
}

void test(iSorter* sorter, float* a, int n) {
    sorter->sort(a, n);
    bool sorted = true;
    for (int i = 0; i < n - 1; i++)
        if (a[i] > a[i+1]) sorted = false;
    if (sorted)
        std::cout << sorter->name()
        << " is sorted" << std::endl;
    else
        std::cout << sorter->name()
        << " is not sorted" << std::endl;
}

int main() {
    int n;
    std::cout << "Enter no of elements : ";
    std::cin >> n;
    float* array = new float[n];

    for (int i = 0; i < noOfSorters(); i++) {
        iSorter* sorter = CreateSorter(i);
        populate(array, n);
        test(sorter, array, n);
        delete sorter;
    }

    delete [] array;
}
```

**Output:**
```
Enter no of elements : 200
Selection Sorter is sorted
Bubble Sorter is sorted
```
