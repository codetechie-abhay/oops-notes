
# 📋 Copy Constructor in C++

## What is a Copy Constructor? 🛠️
A copy constructor in C++ is a special constructor used to create a new object as a copy of an existing object. It is called when:
- An object is initialized from another object of the same type.
- An object is passed by value to a function.
- An object is returned by value from a function.

### Syntax:
```cpp
class ClassName {
public:
    ClassName(const ClassName &old_obj);
};
```

## Example:
```cpp
#include <iostream>
using namespace std;

class Box {
public:
    int length;

    // Default constructor
    Box() {
        length = 0;
    }

    // Parameterized constructor
    Box(int l) {
        length = l;
    }

    // Copy constructor
    Box(const Box &box) {
        length = box.length;
    }

    void display() {
        cout << "Length: " << length << endl;
    }
};

int main() {
    Box box1(10);    // Parameterized constructor call
    Box box2 = box1; // Copy constructor call

    box1.display();
    box2.display();

    return 0;
}
```

## Benefits of Using Copy Constructor 🎯

### 1. Object Cloning 🤖
When you need an exact duplicate of an object, a copy constructor makes it easy and error-free.

### 2. Passing Objects by Value 📤
When an object is passed to a function by value, the copy constructor is called. This preserves the state of the original object and ensures any changes within the function do not affect it.

### 3. Returning Objects by Value 📥
When a function returns an object by value, the copy constructor is used to create a temporary object that holds the same state as the original object.

### Example with Benefits:
```cpp
#include <iostream>
using namespace std;

class Example {
public:
    int* ptr;

    // Constructor
    Example(int x) {
        ptr = new int(x);
    }

    // Copy Constructor
    Example(const Example& old_obj) {
        ptr = new int(*(old_obj.ptr));
    }

    // Destructor
    ~Example() {
        delete ptr;
    }

    void display() {
        cout << "Value: " << *ptr << endl;
    }
};

void func(Example obj) {
    obj.display();
}

int main() {
    Example obj1(10);
    Example obj2 = obj1; // Copy constructor call

    obj1.display();
    obj2.display();

    func(obj1); // Copy constructor call

    return 0;
}
```

## Deep Copy for Safe Memory Management 🛡️
The copy constructor allows you to perform a deep copy, which manages dynamically allocated memory correctly and avoids issues like dangling pointers and shallow copy problems.

Using a copy constructor provides safe and efficient copying operations, especially when working with complex objects.

### Memory Management Example:
```cpp
Example createExample() {
    Example obj(20);
    return obj; // Copy constructor call
}
```

In this case, the copy constructor is used when the object is returned, ensuring proper memory management.
