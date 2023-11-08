# Week 2: Encapsulation, Member Functions and Privacy

## Member Functions
- **Queries (Accessor Methods):** Report the state of the object.
- **Modifiers (Mutator Methods):** Change the state of the object.
- **Special (Manager Methods):** Create, assign and destroy an object.

## Class
- A class is a blueprint for creating objects.
- Instance variables can have various data types (fundamental, compound, pointer, reference).
- Member functions are shared among all objects of a class.

```cpp
class Student {
    int no;
    float grade[NG];
    int ng;
public:
    void set(int, const float*, int);
    void display() const;
};
```
- **Object Creation:**
```cpp
Student harry;
```

## Encapsulation and Data Hiding
- Member functions can access private members of the class they belong to.
- Privacy in C++ is applied at the class level, not at the object level.

```cpp
class Student {
    int no;
    float grade[NG];
    int ng;
public:
    // ...
};
```

## Constructors
- Constructors are special member functions called at an object's creation.
- Default constructor is invoked without arguments.

**Default Constructor:**
```cpp
class Student {
public:
    Student();
};

Student::Student() {
    no = 0;
    ng = 0;
}
```

**Parameterized Constructor:**
```cpp
Student::Student(int sn, const float* g, int ng_) {
    set(sn, g, ng_);
}
```

## Destructors
- Destructors are special member functions called when an object goes out of scope.
- Used for cleanup like deallocating memory.
- Cannot be overloaded or explicitly called.
- Order of destruction is opposite to order of construction.

```cpp
class Student {
public:
    ~Student();  // Destructor
};

Student::~Student() {
    // Cleanup logic
}
```

## Safe Empty State
- Initializing objects in constructors ensures they have a well-defined state.
- Objects are in a safe empty state until explicitly initialized.
- Calling member functions on objects in safe empty states is safe.

## Overloading Constructors
- Overloading allows creating objects with different sets of arguments.

```cpp
class Student {
public:
    Student();  // Default constructor
    Student(int sn, const float* g, int ng);  // Overloaded constructor
};

Student::Student(int sn, const float* g, int ng) {
    // Overloaded constructor logic
}
```

## Formatting Output
- `width(int):` Sets the field width.
- `fill(char):` Sets the padding character.
- `setf(...) / unsetf(...):` Sets/unsets formatting flags.
- `precision(int):` Sets the decimal precision.

```cpp
double pi = 3.141592653;
cout.width(10);
cout.setf(ios::fixed);
cout.precision(2);
cout << pi << endl;  // Outputs: "      3.14"
```

**Display Function with Formatting:**
```cpp
void Student::display() const {
    if (no > 0) {
        cout << no << ":\n";
        cout.setf(ios::fixed);
        cout.precision(2);
        for (int i = 0; i < ng; i++) {
            cout.width(6);
            cout << grade[i] << endl;
        }
        cout.unsetf(ios::fixed);
        cout.precision(6);
    } else {
        cout << "no data available" << endl;
    }
}
```
