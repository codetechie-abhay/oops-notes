
# Polymorphism 🌟

**Polymorphism** is a core concept in object-oriented programming that allows objects of different classes to be treated as objects of a common base class. This means a single interface can represent different underlying forms (data types). Here's a simplified way to understand and remember it.

### Key Points

1. **Objects can take multiple forms**:
   - A base class can represent various derived class objects.
   - Allows for defining methods in the base class and overriding them in derived classes.

2. **Common Base Class**:
   - Objects of different derived classes can be treated as objects of the common base class.

3. **Method Behavior**:
   - The method in the derived class is executed based on the object type, even when referenced through the base class.

### Example with Simplified Explanation

#### Step 1: Define the Base Class

The base class has a virtual function that can be overridden by derived classes.

```cpp
class YouTubeChannel {
protected:
    string name;
    string ownerName;
public:
    YouTubeChannel(string name, string ownerName) : name(name), ownerName(ownerName) {}
    virtual void practice() = 0; // Pure virtual function
};
```

#### Step 2: Define Derived Classes

Derived classes override the base class method to provide specific behavior.

**CookingYouTubeChannel**:
```cpp
class CookingYouTubeChannel : public YouTubeChannel {
public:
    CookingYouTubeChannel(string name, string ownerName) : YouTubeChannel(name, ownerName) {}
    void practice() override {
        cout << ownerName << " is practicing cooking techniques." << endl;
    }
};
```

**SingerYouTubeChannel**:
```cpp
class SingerYouTubeChannel : public YouTubeChannel {
public:
    SingerYouTubeChannel(string name, string ownerName) : YouTubeChannel(name, ownerName) {}
    void practice() override {
        cout << ownerName << " is practicing singing and dancing skills." << endl;
    }
};
```

#### Step 3: Use Base Class Pointers

By using pointers or references to the base class, we can call the overridden methods in derived classes.

```cpp
int main() {
    CookingYouTubeChannel amy("Amy's Kitchen", "Amy");
    SingerYouTubeChannel john("John Sings", "John");

    YouTubeChannel* youtube1 = &amy;
    YouTubeChannel* youtube2 = &john;

    youtube1->practice(); // Calls CookingYouTubeChannel's practice()
    youtube2->practice(); // Calls SingerYouTubeChannel's practice()

    return 0;
}
```

### Simplified Full Example with Comments

Here's the complete example with comments for better understanding:

```cpp
#include <iostream>
using namespace std;

// Base class
class YouTubeChannel {
protected:
    string name;
    string ownerName;
public:
    YouTubeChannel(string name, string ownerName) : name(name), ownerName(ownerName) {}
    virtual void practice() = 0; // Pure virtual function
};

// Derived class for a cooking channel
class CookingYouTubeChannel : public YouTubeChannel {
public:
    CookingYouTubeChannel(string name, string ownerName) : YouTubeChannel(name, ownerName) {}
    void practice() override {
        cout << ownerName << " is practicing cooking techniques." << endl;
    }
};

// Derived class for a singer's channel
class SingerYouTubeChannel : public YouTubeChannel {
public:
    SingerYouTubeChannel(string name, string ownerName) : YouTubeChannel(name, ownerName) {}
    void practice() override {
        cout << ownerName << " is practicing singing and dancing skills." << endl;
    }
};

int main() {
    CookingYouTubeChannel amy("Amy's Kitchen", "Amy");
    SingerYouTubeChannel john("John Sings", "John");

    YouTubeChannel* youtube1 = &amy; // Base class pointer to CookingYouTubeChannel
    YouTubeChannel* youtube2 = &john; // Base class pointer to SingerYouTubeChannel

    youtube1->practice(); // Calls the overridden method in CookingYouTubeChannel
    youtube2->practice(); // Calls the overridden method in SingerYouTubeChannel

    return 0;
}
```

### Summary

1. **Base Class**: Contains a virtual function to be overridden.
2. **Derived Classes**: Override the base class function to provide specific behavior.
3. **Base Class Pointers**: Used to call the overridden methods, demonstrating polymorphism.

