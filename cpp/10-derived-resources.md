# Week 10: Derived Classes and Resources

## Constructors and Destructors

- **Constructor Behaviour:**
  - Each constructor of a derived class automatically calls a constructor of its base class.
  - By default, that constructor is the no-argument constructor. 
  - To override this default, insert an explicit call to the base class constructor.

- **Destructor Behaviour:**
  - Destructors in an inheritance hierarchy do not need explicit intervention.
  - Each class in the hierarchy has but one destructor and each destructor calls its sole base class counterpart automatically.

    ```cpp
    #include <iostream>

    class Base {
    public:
        Base() { std::cout << "Base Constructor\n"; }
        ~Base() { std::cout << "Base Destructor\n"; }
    };

    class Derived : public Base {
    public:
        Derived() { std::cout << "Derived Constructor\n"; }
        ~Derived() { std::cout << "Derived Destructor\n"; }
    };

    int main() {
        Derived derivedObject;
        return 0;
    }
    ```

## Copy Constructor

- **Default Behaviour:**
  - The copy constructor of a derived class calls the base class's no-argument constructor by default.
  - To override this default, explicitly call the base class constructor of specific choice.

- **Copy Constructor Definition:**
    ```cpp
    Derived(const Derived& identifier) : Base(identifier) {
        // ...
    }
    ```
  - The parameter receives an unmodifiable reference to an object of the derived class. The argument in the call to the base class' constructor is the parameter's identifier.

- **Copying Stages:**
    1. Copy the base class part of the existing object.
        1. Allocate memory for the instance variables of the base class in the order of their declaration
        2. Execute the base class' copy constructor
    2. Copy the derived class part of the existing object.
        1. Allocate memory for the instance variables of the derived class in the order of their declaration
        2. Execute the derived class' copy constructor

    ```cpp
    #include <iostream>

    class Base {
    public:
        Base() { std::cout << "Base Constructor\n"; }
        Base(const Base& other) { std::cout << "Base Copy Constructor\n"; }
        ~Base() { std::cout << "Base Destructor\n"; }
    };

    class Derived : public Base {
    public:
        Derived() { std::cout << "Derived Constructor\n"; }
        Derived(const Derived& other) : Base(other) { std::cout << "Derived Copy Constructor\n"; }
        ~Derived() { std::cout << "Derived Destructor\n"; }
    };

    int main() {
        Derived derivedObject;
        Derived copiedObject = derivedObject; // Copy constructor called
        return 0;
    }
    ```

## Copy Assignment Operator

- **Default Behaviour:**
  - The default copy assignment operator of a derived class calls the copy assignment operator of its base class.
  - Custom copy assignment operators in derived classes do not automatically call the base class's copy assignment operator.

- **Explicit Call:**
  - Custom copy assignment operator in a derived class with a resource requires an explicit call to the base class copy assignment operator.
  - Forms of the call: Functional Form (`Base::operator=`) or Cast Assignment Form (`(Base&)*this = identifier`).

    ```cpp
    #include <iostream>

    class Base {
    public:
        Base& operator=(const Base& other) {
            std::cout << "Base Copy Assignment Operator\n";
            // Perform assignment logic for Base class
            return *this;
        }
    };

    class Derived : public Base {
    public:
        Derived& operator=(const Derived& other) {
            std::cout << "Derived Copy Assignment Operator\n";
            // Explicitly call the base class's copy assignment operator
            Base::operator=(other);
            // Perform assignment logic for Derived class
            return *this;
        }
    };

    int main() {
        Derived derivedObject1, derivedObject2;
        derivedObject1 = derivedObject2; // Custom copy assignment operator called
        return 0;
    }
    ```

## Direct Call Copy Constructor

- **Default Behaviour:**
  - The alternative to sharing a private member function is a direct call from the copy constructor to the copy assignment operator.
  - In a direct call, the assignment operator copies the base class part of the object and any call to the base class copy constructor is redundant.

    ```cpp
    #include <iostream>

    class Base {
    public:
        Base() { std::cout << "Base Constructor\n"; }
        Base(const Base& other) { std::cout << "Base Copy Constructor\n"; }
        ~Base() { std::cout << "Base Destructor\n"; }

        Base& operator=(const Base& other) {
            std::cout << "Base Copy Assignment Operator\n";
            // Perform assignment logic for Base class
            return *this;
        }
    };

    class Derived : public Base {
    public:
        Derived() { std::cout << "Derived Constructor\n"; }
        Derived(const Derived& other) : Base(other) {
            std::cout << "Derived Copy Constructor\n";
            // Directly call the copy assignment operator
            Base::operator=(other);
        }
        ~Derived() { std::cout << "Derived Destructor\n"; }
    };

    int main() {
        Derived derivedObject1, derivedObject2;
        derivedObject1 = derivedObject2; // Direct call to copy assignment operator
        return 0;
    }
    ```
