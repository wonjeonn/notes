# The Basics of Python Programming

### Interpreted vs Compiled Languages
- **Python** operates as both an interpreted and compiled language.
  - Python code is first **compiled** into **bytecode** (a lower-level, platform-independent representation).
  - This bytecode is then **interpreted** by the Python interpreter, unlike C/C++ where the code is compiled directly into a machine-specific executable.

---

### Comments

```python
# This is a comment in Python
```

---

### Basic Types and Variables

#### Variables
- **C** requires explicit type declarations for variables, while **Python** dynamically assigns types:
  ```python
  x = 5      # x is an integer
  y = "text" # y is a string
  ```

#### Naming Rules and Conventions
- Must start with a **letter** or an **underscore**.
- Use **snake_case** for variables and functions, **CamelCase** for class names, and **ALL_CAPS** for constants.

#### Strings
- Strings can be enclosed in single (`'`) or double (`"`) quotes:
  ```python
  "This is a string"
  'This is also a string'
  ```
- To include both quotes, use the escape character `\`:
  ```python
  "\"It's still magic even if you know how it's done\" - Terry Pratchett"
  ```

#### Numbers
- **Integers** and **floats** are represented without explicitly specifying their bit size.
  ```python
  x = 5   # Integer
  y = 5.0 # Floating-point number
  ```

---

### Numeric Operators

- Arithmetic operations include `+`, `-`, `*`, `/`, `//`, `%`, and `**`.
- **Division**:
  - `/` results in a float.
  - `//` performs integer division (floor).
  ```python
  14 / 5  # Output: 2.8
  14 // 5 # Output: 2
  ```
- **Modulo with Negative Numbers**:
  ```python
  -9 % 5  # Output: 1
  ```

---

### Selection (Conditionals)

#### Boolean Expressions and Operators
- Comparisons: `==`, `!=`, `<`, `<=`, `>`, `>=`.
- Logical operators: `and`, `or`, `not`.

#### Lazy Evaluation
- **Short-circuit evaluation**:
  - In an `and` expression, if the left operand is **False**, the right operand is **not evaluated**.
  - In an `or` expression, if the left operand is **True**, the right operand is **not evaluated**.

#### Syntax for Conditionals
```python
if condition:
    # Block of code
elif another_condition:
    # Another block
else:
    # Default block
```

---

### Lists

- **Lists** are dynamic and can contain mixed data types:
  ```python
  my_list = [1, 2, "hello", 1.5]
  ```
- Access elements by index, starting from `0`.

#### List Assignments
- Assigning one list to another creates a reference, not a copy.

---

### Dictionaries

- **Dictionaries** store key-value pairs:
  ```python
  my_dict = {"key1": 5, "key2": 6}
  ```
- Access values by keys:
  ```python
  my_dict["key1"]  # Output: 5
  ```

---

### Iteration

#### For Loops
- Iterate over ranges or lists:
  ```python
  for i in range(5):
      print(i)
  ```

#### While Loops
- Execute as long as the condition is true:
  ```python
  i = 1
  while i < 10:
      print(i)
      i += 1
  ```

---

### Functions

- Defined using the `def` keyword:
  ```python
  def function_name(parameters):
      # Code block
  ```
- Called by using the function name:
  ```python
  function_name(arguments)
  ```

---

### Classes

#### Class Definition
- Define classes with the `class` keyword, using `self` to refer to the instance:
  ```python
  class MyClass:
      def __init__(self, attribute):
          self.attribute = attribute
  ```

#### Inheritance
- Use `super()` to access methods from the base class:
  ```python
  class DerivedClass(BaseClass):
      def __init__(self, argument):
          super().__init__(argument)
  ```
