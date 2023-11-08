# Week 5: Encapsulation, Helper Functions and Friendship in C++

## Helper Functions

- **Helper Functions:** Support a class from outside, providing additional logic.
- Access class objects solely through parameters, maintaining encapsulation.
- Can be free functions or friend functions.

### Free Helper Functions

- **Free Helper Functions:** Use public member functions, do not access private members.
- Example: A function comparing two objects of the same class.

```cpp
bool areIdentical(const Student&, const Student&);
```

### Helper Function Usage

```cpp
float gh[] = {89.4f, 67.8f, 45.5f};
Student harry(1234, gh, 3), harry_(1234, gh, 3);
if (areIdentical(harry, harry_))
    cout << "are identical" << endl;
else
    cout << "are different" << endl;
```

## Helper Operators

- **Helper Operators:** Overloaded operators as free functions.
- Do not change the values of their operands.
- Example: Overloading the equality operator for the Student class.

```cpp
bool operator==(const Student&, const Student&);
```

## Overloading Operators

- **Operator Overloading:** Giving new meanings to operators for user-defined types.
- Can be member functions or free functions.
- Example: Overloading `+` operator for Student class.

```cpp
Student operator+(const Student&, float);
Student operator+(float, const Student&);
```

## Friendship in C++

- **Friend Functions:** Access private members of a class.
- Declared inside the class with `friend` keyword.
- Provides direct access to class internals without compromising encapsulation.

```cpp
class Student {
    int no;
    float grade[NG];
    int ng;
public:
    // ...
    friend bool areIdentical(const Student&, const Student&);
};
```
