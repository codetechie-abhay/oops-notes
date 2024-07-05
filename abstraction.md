# Abstraction in Object-Oriented Programming (OOP)

## Introduction
- Abstraction is a key concept in OOP.
- It involves showing important information while hiding complex details.
- Example used: Coffee machine (simple interface vs. complex internal process).

## Real-Life Example of Abstraction
- **Coffee Machine**:
  - User interface: Add coffee and water, press a button.
  - Internal complexity: How the machine processes and brews the coffee is hidden.

## Importance of Abstraction
- Simplifies the user experience.
- Users interact with a simple interface without needing to understand the complex underlying mechanisms.

## Abstraction in Programming
- In programming, abstraction helps in:
  - Hiding complex implementation details.
  - Providing a simple interface for other developers.
- **Example**: Using a smartphone (simple actions like taking a selfie) without knowing the internal workings.

## Implementing Abstraction in C++
- Use abstract classes and pure virtual functions.
- An abstract class in C++ contains at least one pure virtual function.
- Example: Creating an abstract class `Smartphone` with a pure virtual function `takeSelfie()`.

## Example Code

### Abstract Class
```cpp
class Smartphone {
public:
    virtual void takeSelfie() = 0; // Pure virtual function
};
```

### Derived Classes
- **Android Class**:
  ```cpp
  class Android : public Smartphone {
  public:
      void takeSelfie() override {
          std::cout << "Android takes a selfie";
      }
  };
  ```

- **iPhone Class**:
  ```cpp
  class iPhone : public Smartphone {
  public:
      void takeSelfie() override {
          std::cout << "iPhone takes a selfie";
      }
  };
  ```

## Benefits of Abstraction
- **Modularity**: Different developers can work on different parts of the code without needing to know the details of other parts.
- **Maintainability**: Changes in the internal implementation do not affect the users of the abstraction.
- **Scalability**: New functionalities can be added with minimal changes to existing code.

## Example Usage
- Creating objects of derived classes using pointers to the abstract class:
  ```cpp
  Smartphone* s1 = new Android();
  s1->takeSelfie(); // Output: Android takes a selfie

  s1 = new iPhone();
  s1->takeSelfie(); // Output: iPhone takes a selfie
  ```

## Extending the Abstraction
- Adding new functionalities:
  - Example: Adding a `makeCall()` function to the `Smartphone` class.
  - Both `Android` and `iPhone` classes must implement the new function.

### Updated Abstract Class
```cpp
class Smartphone {
public:
    virtual void takeSelfie() = 0;
    virtual void makeCall() = 0; // New pure virtual function
};
```

### Updated Derived Classes
- **Android Class**:
  ```cpp
  class Android : public Smartphone {
  public:
      void takeSelfie() override {
          std::cout << "Android takes a selfie";
      }
      void makeCall() override {
          std::cout << "Android calling";
      }
  };
  ```

- **iPhone Class**:
  ```cpp
  class iPhone : public Smartphone {
  public:
      void takeSelfie() override {
          std::cout << "iPhone takes a selfie";
      }
      void makeCall() override {
          std::cout << "iPhone calling";
      }
  };
  ```

## Conclusion
- Abstraction hides complex details and provides a simple interface.
- It enhances code modularity, maintainability, and scalability.
- Using abstract classes and pure virtual functions in C++ is an effective way to implement abstraction.
