# Week 6: Input and Output Operators in C++

## Standard I/O

- `std::istream`: Used for processing input from the standard input device.
- `std::ostream`: Used for processing output to the standard output devices.

## Overloading Stream Operators

- To work with custom classes, overload the insertion (`<<`) and extraction (`>>`) operators.
- The typical form of these overloading functions for a class named `Type` is:

```cpp
std::istream& operator>>(std::istream&, Type&);
std::ostream& operator<<(std::ostream&, const Type&);
```

- Example with a `Student` class:

```cpp
class Student {
    int no;
    float grade[NG];
    int ng;
public:
    // ...
};

std::istream& operator>>(std::istream& is, Student& s);
std::ostream& operator<<(std::ostream& os, const Student& s);
```

## Member Functions for istream

1. **ignore()**
   - `ignore()` extracts bytes from the input buffer and discards them without skipping whitespace.
   - Two versions of `ignore()`:
     - No arguments: Discards a single byte.
     - Two arguments: Removes and discards up to the specified number of bytes or up to the specified delimiting character, whichever occurs first.

2. **get()**
   - `get()` extracts either a single character or a string from the input buffer.
   - Three versions:
     - `get()` (no arguments): Extracts a single character.
     - `get(char)`: Extracts a single character.
     - `get(char*, int)`: Extracts a string with a newline delimiter.
     - `get(char*, int, char)`: Extracts a string with a specified delimiter.

3. **getline()**
   - `getline()` behaves like `get()` but extracts the delimiting character from the input buffer.
   - Two versions:
     - `getline(char*, int)`: Extracts a string with a newline delimiter.
     - `getline(char*, int, char)`: Extracts a string with a specified delimiter.

## Output Objects

- An output object is an instance of the `ostream` class.
- `ostream` objects transfer data from system memory into an output stream, converting it into a sequence of characters.
- Three standard output objects:
  - `cout`: Transfers a buffered sequence of characters to the standard output device.
  - `cerr`: Transfers an unbuffered sequence of characters to the standard error output device.
  - `clog`: Transfers a buffered sequence of characters to the standard error output device.

## Inserting Data

- To insert data into an output stream, use the `<<` insertion operator.
- Format: `output << identifier`, where `output` is an `ostream` object, `<<` is the insertion operator, and `identifier` holds the data.
- Data in the `identifier` is converted into a sequence of characters based on its type.

```cpp
int i = 6;
char c = ' ';
double x = 9.75;
char s[] = "Harry";
cout << i << c << x << c << s << endl;
cerr << "Data has been written";
```

- `endl` inserts a newline character and flushes the stream's buffer.

## Whitespace Handling
- Input objects skip leading whitespace for numeric, string and character types.
- They treat whitespace as delimiters for these data types.
- Trailing whitespace is added to C-style null-terminated strings.
- Using `getline()` for more control over whitespace handling.

## Cascading
Multiple extraction operations can be combined into a single compound expression:

```cpp
cin >> i >> c >> x >> s;
```

## Member Functions
- Output objects (`ostream`) offer member functions for formatting control.
- These functions include `width()`, `fill()`, `setf()`, `unsetf()` and `precision()`.

## Manipulators
- Manipulators are elegant alternatives to member function calls for both input and output.
- They include functions like `skipws`, `setw()`, `fixed`, `scientific`, `left` and `right`, among others.
- Some manipulators can be used directly in combination with variables for compound expressions. E.g., `cin >> setw(5) >> a >> setw(2) >> b`.

- **Input Manipulators**:
  - `skipws`: Skips whitespace during extraction.
  - `noskipws`: Turns off skipping whitespace.
  - `setw(int)`: Sets the field width for the next input.

- **Output Manipulators**:
  - `fixed`: Outputs floating-point numbers in fixed-point format.
  - `scientific`: Outputs floating-point numbers in scientific format.
  - `left`: Left-justifies output.
  - `right`: Right-justifies output.
  - `endl`: Outputs a newline and flushes the buffer.
  - `setprecision(int)`: Sets the precision of output.
  - `setfill(int)`: Sets the fill character for field width.
  - `setbase(int)`: Sets the base of the number system for int output.
  - `flush`: Flushes the output buffer.

## Input State Functions

- **`good()`:** Checks if the stream is in a valid state, e.g., no errors have occurred during the previous operations.
- **`fail()`:** Returns true if a previous operation failed (e.g., when an attempt to read an integer from a character fails).
- **`eof()`:** Returns true if the end-of-file (EOF) has been encountered.
- **`bad()`:** Returns true if a fatal error (like a memory allocation failure) has occurred.
- **`clear()`:** Resets the state of the stream, allowing further extraction operations.

## Robust Validation Techniques

**Clearing Failed State:**
```cpp
if(cin.fail()) {
    cin.clear(); // Reset the stream state to good
    cin.ignore(2000, '\n'); // Clear the input buffer
}
```

**Robust Validation Function:**
```cpp
int getPosInt(int max) {
    int value;
    int keepreading;

    keepreading = 1;
    do {
        cout << "Enter a positive integer (<= " << max << ") : ";
        cin  >> value;

        if (cin.fail()) {
            cerr << "Invalid character. Try Again." << endl;
            cin.clear();
            cin.ignore(2000, '\n');
        } else if (value <= 0 || value > max) {
            cerr << value << " is outside the range [1," << max << ']' << endl;
            cerr << "Invalid input. Try Again." << endl;
            cin.ignore(2000, '\n');
        } else if (char(cin.get()) != '\n') {
            cerr << "Trailing characters. Try Again." << endl;
            cin.ignore(2000, '\n');
        } else {
            keepreading = 0; // Valid input, stop reading
        }
    } while(keepreading == 1);

    return value;
}
```

## String Class

C++ provides the `std::string` class to handle character strings, offering member functions like `length()` and `c_str()` for versatile string operations.

  ```cpp
  #include <iostream>
  #include <string>

  int main() {
      char* s;
      std::string str;

      std::cout << "Enter a string: ";
      if (std::getline(std::cin, str)) {
          s = new char[str.length() + 1];
          std::strcpy(s, str.c_str());
          std::cout << "The string entered is: >" << s << '<' << std::endl;
          delete[] s;
      }
  }
  ```

### A Complete Student Class Example

- Example of a `Student` class with input and output operator overloads:

```cpp
#include <iostream>
#include <string>

const int NG = 20;

class Student {
    int no;
    float grade[NG];
    int ng;
    std::string comment;
public:
    Student();
    Student(int);
    Student(int, const float*, int, const std::string&);
    void read(std::istream&);
    void display(std::ostream&) const;
};

std::istream& operator>>(std::istream& is, Student& s);
std::ostream& operator<<(std::ostream& os, const Student& s);
```

- Implementation:

```cpp
#include "Student.h"
using namespace std;

Student::Student() {
no = 0;
ng = 0;
}

Student::Student(int n) {
*this = Student(n, nullptr, 0, "");
}

Student::Student(int sn, const float* g, int ng_, const string& c) {
bool valid = sn > 0 && g != nullptr && ng_ >= 0;
if (valid)
for (int i = 0; i < ng_ && valid; i++)
    valid = g[i] >= 0.0f and g[i] <= 100.0f;

if (valid) {
// Accept the client's data
no = sn;
ng = ng_ < NG ? ng_ : NG;
for (int i = 0; i < ng; i++)
    grade[i] = g[i];
comment = c;
} else {
*this = Student();
}
}

void Student::read(istream& is) {
int no;          // Will hold the student number
int ng;          // Will hold the number of grades
float grade[NG]; // Will hold the grades
string comment;  // Will hold comments

cout << "Student Number: ";
is >> no;
cout << "Number of Grades: ";
is >> ng;
if (ng > NG) ng = NG;
for (int i = 0; i < ng; i++) {
cout << "Grade " << i + 1 << ": ";
is >> grade[i];
}
is.ignore(); // Extract newline
cout << "Comments: ";
getline(is, comment, '\n');

// Construct a temporary Student
Student temp(no, grade, ng, comment);
// If data is valid, copy the temporary object into the current object
if (temp.no != 0)
*this = temp;
}

void Student::display(ostream& os) const {
if (no > 0) {
os << no << ":\n";
os.setf(ios::fixed);
os.precision(2);
for (int i = 0; i < ng; i++) {
    os.width(6);
    os << grade[i] << endl;
}
os.unsetf(ios::fixed);
os.precision(6);
os << "Comments:\n" << comment << endl;
} else {
os << "no data available" << endl;
}
}

ostream& operator<<(ostream& os, const Student& s) {
s.display(os);
return os;
}

istream& operator>>(istream& is, Student& s) {
s.read(is);
return is;
}
```
