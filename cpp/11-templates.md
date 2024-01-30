# Week 11: Function Templates and Constrained Casts

## Function Templates:
1. **Template Syntax:**
   - A template definition resembles a global function with angle brackets replacing parentheses.
   - `template <Type identifier[, ...]>`
   - typename: To identify a type (fundamental or compound)
   - class: To identify a type (fundamental or compound)
   - int, long, short, char: To identify a non floating-point fundamental type a template parameter

2. **Template Examples:**
   ```cpp
   template <typename T>
   void swap(T& a, T& b) {
       T c;
       c = a;
       a = b;
       b = c;
   }
   ```

3. **Calling a Templated Function:**
   ```cpp
   double a = 2.3, b = 4.5;
   long d = 78, e = 567;

   swap(a, b);  // compiler generates swap(double, double)
   swap(d, e);  // compiler generates swap(long, long)
   ```

## Class Templates:
1. **Template Syntax for Classes:**
   ```cpp
   template <class T, int N>
   class Array {
       T a[N];
   public:
       T& operator[](int i) { return a[i]; }
   };
   ```
   - Class templates can have multiple parameters, both types and non-type.

2. **Using Class Templates:**
   ```cpp
   Array<int, 5> a, b;

   for (int i = 0; i < 5; i++)
       a[i] = i * i;

   b = a;

   for (int i = 0; i < 5; i++)
       std::cout << b[i] << ' ';
   // Output: 0 1 4 9 16
   ```

## Constrained Casts:
1. **Static Cast:**
   ```cpp
   double hours;
   int minutes;
   hours = static_cast<double>(minutes) / 60;
   ```
   - Used for related types.
   - Performs limited type checking.

2. **Reinterpret Cast:**
   ```cpp
   int x = 2;
   int* p = reinterpret_cast<int*>(x);
   ```
   - Used for unrelated types.
   - Minimal type checking.
   - Often used for raw data evaluation.

3. **Const Cast:**
   ```cpp
   const int x = 3;
   const int* a = &x;
   int* b = const_cast<int*>(a);
   ```
   - Removes const status.
   - Minimal type checking.

4. **Dynamic Cast:**
   ```cpp
   Base* b = new Base;
   Derived* d = dynamic_cast<Derived*>(b);
   ```
   - Used for upcasting and downcasting within class hierarchies.
   - Performs runtime type checking.
   - Requires polymorphism for downcasting.

### Compile-Time Checking:
- `dynamic_cast<Type>(expression)` performs some compile-time checking.
- It rejects conversions from a base class pointer to a derived class pointer if the object is monomorphic.
