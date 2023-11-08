# Week 4: Encapsulation, Classes and Resources

## Dynamic Allocation of Resources

- Resources can be dynamically allocated, meaning they are allocated and deallocated during the program's execution.

- In C++, dynamic allocation of resources typically involves using pointers to manage memory for those resources.

## Example: Student Class with Dynamic Grades

```cpp
class Student {
private:
    int no;          // Student number
    float* grade;    // Pointer to dynamically allocated grades array
    int ng;          // Number of grades

public:
    Student();
    Student(int);
    Student(int, const float*, int);
    ~Student();
    void display() const;
};
```

- In this `Student` class, the `grade` array is dynamically allocated using a float pointer.

- The constructors initialize the object and the destructor is responsible for releasing the dynamically allocated memory when the object is destroyed.

## Deep Copy:
- Deep copying involves allocating new memory for the resource and copying its data from the source to the destination.
- Non-resource instance variables are shallow copied (copied as-is). In the `Student` class, this means copying the student number (`no`) and the number of grades (`ng`) but not the address stored in the `grade` pointer.

## Copy Constructor

- The copy constructor copies data from a source object to a newly created object of the same type.

```cpp
class Student {
public:
    Student(const Student&);  // Copy constructor
};
```

- The copy constructor performs a deep copy of the data, allocating new memory for the resource and copying its contents.

```cpp
Student::Student(const Student& src) {
    // Shallow copy non-resource instance variables
    no = src.no;
    ng = src.ng;
    
    // Allocate dynamic memory for grades
    if (src.grade != nullptr) {
        grade = new float[ng];
        for (int i = 0; i < ng; i++)
            grade[i] = src.grade[i];
    }
    else {
        grade = nullptr;
    }
}
```

## Copy Assignment Operator

- The copy assignment operator copies data from an existing object to another existing object.

```cpp
class Student {
public:
    Student& operator=(const Student&);  // Copy assignment operator
};
```

- The copy assignment operator checks for self-assignment (e.g., `a = a`), performs a deep copy and deallocates any previously allocated memory for the resource.

```cpp
Student& Student::operator=(const Student& source) {
    if (this != &source) {  // Check for self-assignment
        no = source.no;
        ng = source.ng;

        // Deallocate previously allocated dynamic memory
        delete[] grade;

        // Allocate new dynamic memory, if needed
        if (source.grade != nullptr) {
            grade = new float[ng];
            for (int i = 0; i < ng; i++)
                grade[i] = source.grade[i];
        }
        else {
            grade = nullptr;
        }
    }
    return *this;
}
```

## Prohibiting Copies

- In some class designs, it is necessary to prohibit client code from copying or assigning objects.
- By using `= delete`, making it clear that copying or assignment is not allowed for objects of this class.

```cpp
class Student {
public:
    Student(const Student&) = delete;            // Delete copy constructor
    Student& operator=(const Student&) = delete; // Delete copy assignment operator
};
```
