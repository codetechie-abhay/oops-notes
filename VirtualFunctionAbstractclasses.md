# Virtual Functions, Pure Virtual Functions, and Abstract Classes 🎵🎹

## Virtual Functions 💻

### Definition
Virtual functions allow a function in a base class to be overridden in derived classes.

### Purpose
Enable runtime polymorphism, where the correct derived class function is executed when invoked through a base class pointer or reference.

### Example

#### Base Class: `Instrument`
```cpp
#include <iostream>

class Instrument {
public:
    // Virtual function
    virtual void makeSound() {
        std::cout << "Instrument is making a sound." << std::endl;
    }
};
```

#### Derived Class: `Accordion`
```cpp
class Accordion : public Instrument {
public:
    // Override virtual function
    void makeSound() override {
        std::cout << "Accordion is playing." << std::endl;
    }
};
```

#### Derived Class: `Piano`
```cpp
class Piano : public Instrument {
public:
    // Override virtual function
    void makeSound() override {
        std::cout << "Piano is playing." << std::endl;
    }
};
```

## Pure Virtual Functions 🌟

### Definition
Functions declared as virtual and set to `= 0` in the base class, forcing derived classes to implement their own versions.

### Purpose
Make a class abstract, ensuring all derived classes provide specific implementations.

### Example

#### Abstract Base Class: `Instrument`
```cpp
class Instrument {
public:
    // Pure virtual function
    virtual void makeSound() = 0;
};
```

#### Derived Class: `Accordion`
```cpp
class Accordion : public Instrument {
public:
    // Override pure virtual function
    void makeSound() override {
        std::cout << "Accordion is playing." << std::endl;
    }
};
```

#### Derived Class: `Piano`
```cpp
class Piano : public Instrument {
public:
    // Override pure virtual function
    void makeSound() override {
        std::cout << "Piano is playing." << std::endl;
    }
};
```

## Abstract Classes 🎨

### Definition
Classes containing at least one pure virtual function, making them unable to instantiate objects.

### Purpose
Define a common interface for derived classes while enforcing specific behavior.

### Example

#### Abstract Base Class: `Instrument`
```cpp
class Instrument {
public:
    // Pure virtual function
    virtual void makeSound() = 0;
};
```

#### Derived Class: `Accordion`
```cpp
class Accordion : public Instrument {
public:
    // Override pure virtual function
    void makeSound() override {
        std::cout << "Accordion is playing." << std::endl;
    }
};
```

#### Derived Class: `Piano`
```cpp
class Piano : public Instrument {
public:
    // Override pure virtual function
    void makeSound() override {
        std::cout << "Piano is playing." << std::endl;
    }
};
```

## Polymorphic Behavior 🔄

### Definition
Ability to treat objects of derived classes as objects of their base class, invoking overridden methods dynamically.

### Example

```cpp
#include <iostream>

int main() {
    // Example with polymorphic behavior
    Instrument* instruments[] = { new Accordion(), new Piano() };

    for (int i = 0; i < 2; ++i) {
        instruments[i]->makeSound();
    }

    // Clean up allocated memory
    for (int i = 0; i < 2; ++i) {
        delete instruments[i];
    }

    return 0;
}
```

## Conclusion 📝

### Usage
Virtual functions allow flexibility in object-oriented designs, enabling polymorphic behavior crucial for managing varied implementations across derived classes.

### Practical Example
Demonstrated using `Instrument`, `Accordion`, and `Piano` classes to showcase how polymorphism operates with virtual and pure virtual functions.

### Note
Ensure proper memory management when using polymorphic objects, especially when allocated dynamically as shown in the example.


# Runtime vs Compile-time Polymorphism and Difference Between Override and Overridden 🔄🔍

## Runtime Polymorphism

### What is it?
Runtime polymorphism happens when the specific function that gets called is decided when the program runs, not when it's being written. It allows different classes that inherit from a base class to have their own versions of the same function.

### Key Points
- **Decided Later:** The exact function used is chosen when the program runs.
- **Using Virtual Functions:** In C++, this is done using virtual functions which allow different classes to have their own implementations.

### Example

#### Base Class: `Instrument`
```cpp
#include <iostream>

class Instrument {
public:
    // Virtual function
    virtual void makeSound() {
        std::cout << "Instrument is making a sound." << std::endl;
    }
};
```

#### Derived Class: `Accordion`
```cpp
class Accordion : public Instrument {
public:
    // Override virtual function
    void makeSound() override {
        std::cout << "Accordion is playing." << std::endl;
    }
};
```

#### Derived Class: `Piano`
```cpp
class Piano : public Instrument {
public:
    // Override virtual function
    void makeSound() override {
        std::cout << "Piano is playing." << std::endl;
    }
};
```

## Compile-time Polymorphism

### What is it?
Compile-time polymorphism happens when the function that's called is decided when the program is being written, not when it runs. It's achieved through function overloading and templates in C++.

### Key Points
- **Decided Earlier:** The specific function used is chosen when the program is being written.
- **Using Function Overloading:** Functions with the same name but different parameters can be resolved at compile-time.

### Example

#### Function Overloading Example
```cpp
#include <iostream>

// Function overloading
void display(int a) {
    std::cout << "Integer: " << a << std::endl;
}

void display(double b) {
    std::cout << "Double: " << b << std::endl;
}

int main() {
    display(5);       // Calls display(int)
    display(3.14);    // Calls display(double)

    return 0;
}
```