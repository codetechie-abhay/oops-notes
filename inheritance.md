# 👹 Introduction to Inheritance

Inheritance is a fundamental concept in object-oriented programming where a new class (derived class) is created from an existing class (base class). This allows the derived class to inherit the properties and behaviors of the base class, facilitating code reuse and promoting a hierarchical structure in your program.

### 😶‍🌫️Base Class: YouTubeChannel👹

Here's a base class `YouTubeChannel` designed for managing YouTube channels:

- **Private Properties:** `name`, `owner_name`, `subscribers_count`, `published_video_titles`.
  
- **Public Methods:**
  - **Constructor:** Initializes the channel with `name` and `owner_name`.
  - `getInfo()`: Displays channel information.
  - `subscribe()`, `unsubscribe()`: Manages subscriber interactions.
  - `publishVideo(string title)`: Adds new videos to the channel.

### Creating a Derived Class: CookingYouTubeChannel

To specialize our channel, such as for a cooking channel, we extend `YouTubeChannel`:

```cpp
class CookingYouTubeChannel : public YouTubeChannel {
public:
    // Constructor inheriting base class's constructor
    CookingYouTubeChannel(string name, string owner_name)
        : YouTubeChannel(name, owner_name) {}

    // Additional method specific to CookingYouTubeChannel
    void practice() {
        cout << "Practicing cooking, learning new recipes, and experimenting with spices!" << endl;
    }
};
```

### Using Inherited and Specific Methods

Let's demonstrate inheritance with instances of `CookingYouTubeChannel`:

```cpp
CookingYouTubeChannel amyChannel("Amy's Kitchen", "Amy");
amyChannel.publishVideo("Apple Pie");
amyChannel.publishVideo("Chocolate Cake");
amyChannel.subscribe();
amyChannel.getInfo();
amyChannel.practice();

CookingYouTubeChannel johnChannel("John's Kitchen", "John");
johnChannel.practice();
```

### Understanding Access Modifiers

Access modifiers (`public`, `protected`, `private`) manage member visibility. `protected` allows derived classes to access base class members, ensuring flexibility in object-oriented design.

## Conclusion

Inheritance enhances code reusability and promotes a structured approach in object-oriented programming. It allows for the creation of specialized classes while maintaining a clear hierarchy, facilitating easier maintenance and extension of software systems.



# 🦉👁️ Understanding Access Specifiers in C++ Inheritance

In C++, there are three main access specifiers: `public`, `protected`, and `private`. These specifiers determine how members (variables and methods) of a class are accessible from other parts of the program, including derived classes.

### 1. Public Access Specifier

- **Usage:** Public members are accessible from outside the class as well as within the class and its derived classes.
- **Inheritance Effect:** Public inheritance makes public members of the base class public in the derived class. Protected members remain protected.

#### Example:

```cpp
class Base {
private:
    int privateVar = 1;

protected:
    int protectedVar = 2;

public:
    int publicVar = 3;
};

class PublicDerived : public Base {
public:
    int getPrivateVar() { return privateVar; }  // Error: privateVar is not accessible
    int getProtectedVar() { return protectedVar; }  // Accessible
    int getPublicVar() { return publicVar; }  // Accessible
};
```

### 2. Protected Access Specifier

- **Usage:** Protected members are accessible within the class and its derived classes, but not from outside.
- **Inheritance Effect:** Protected inheritance makes both public and protected members of the base class protected in the derived class.

#### Example:

```cpp
class ProtectedDerived : protected Base {
public:
    int getPrivateVar() { return privateVar; }  // Error: privateVar is not accessible
    int getProtectedVar() { return protectedVar; }  // Accessible
    int getPublicVar() { return publicVar; }  // Accessible
};
```

### 3. Private Access Specifier

- **Usage:** Private members are only accessible within the class itself, not even by derived classes.
- **Inheritance Effect:** Private inheritance makes both public and protected members of the base class private in the derived class.

#### Example:

```cpp
class PrivateDerived : private Base {
public:
    int getPrivateVar() { return privateVar; }  // Error: privateVar is not accessible
    int getProtectedVar() { return protectedVar; }  // Error: protectedVar is not accessible
    int getPublicVar() { return publicVar; }  // Accessible
};
```
# 🐼Types of Inheritance
### 1. Single Inheritance
A **Vehicle** class and a **Car** class. The **Car** class inherits properties from the **Vehicle** class.

```cpp
#include <iostream>
using namespace std;

class Vehicle {
public:
    void start() {
        cout << "Vehicle started" << endl;
    }
};

class Car : public Vehicle {
public:
    void drive() {
        cout << "Car is driving" << endl;
    }
};

int main() {
    Car myCar;
    myCar.start(); // Inherited from Vehicle
    myCar.drive(); // Defined in Car
    return 0;
}
```
🚌 ➡️ 🚗  
- `Vehicle` ➡️ `Car`

### 2. Multiple Inheritance
A **Person** class and **Employee** and **Athlete** classes. A **Manager** class can inherit from both **Employee** and **Athlete**.

```cpp
#include <iostream>
using namespace std;

class Employee {
public:
    void work() {
        cout << "Employee is working" << endl;
    }
};

class Athlete {
public:
    void train() {
        cout << "Athlete is training" << endl;
    }
};

class Manager : public Employee, public Athlete {
public:
    void manage() {
        cout << "Manager is managing" << endl;
    }
};

int main() {
    Manager myManager;
    myManager.work(); // Inherited from Employee
    myManager.train(); // Inherited from Athlete
    myManager.manage(); // Defined in Manager
    return 0;
}
```
👨‍💼 ➡️ 👨‍💼 🏋️‍♂️ ➡️ 🧑‍💼  
- `Employee` ➡️ `Manager`  
- `Athlete` ➡️ `Manager`

### 3. Multilevel Inheritance
A **LivingBeing** class, a **Human** class, and a **Student** class. **Human** inherits from **LivingBeing**, and **Student** inherits from **Human**.

```cpp
#include <iostream>
using namespace std;

class LivingBeing {
public:
    void breathe() {
        cout << "LivingBeing is breathing" << endl;
    }
};

class Human : public LivingBeing {
public:
    void speak() {
        cout << "Human is speaking" << endl;
    }
};

class Student : public Human {
public:
    void study() {
        cout << "Student is studying" << endl;
    }
};

int main() {
    Student myStudent;
    myStudent.breathe(); // Inherited from LivingBeing
    myStudent.speak(); // Inherited from Human
    myStudent.study(); // Defined in Student
    return 0;
}
```
🌳 ➡️ 👨 ➡️ 📚  
- `LivingBeing` ➡️ `Human` ➡️ `Student`

### 4. Hierarchical Inheritance
A **Device** class, and **Smartphone** and **Laptop** classes, both inheriting from **Device**.

```cpp
#include <iostream>
using namespace std;

class Device {
public:
    void powerOn() {
        cout << "Device is powered on" << endl;
    }
};

class Smartphone : public Device {
public:
    void makeCall() {
        cout << "Smartphone is making a call" << endl;
    }
};

class Laptop : public Device {
public:
    void code() {
        cout << "Laptop is coding" << endl;
    }
};

int main() {
    Smartphone myPhone;
    Laptop myLaptop;

    myPhone.powerOn(); // Inherited from Device
    myPhone.makeCall(); // Defined in Smartphone

    myLaptop.powerOn(); // Inherited from Device
    myLaptop.code(); // Defined in Laptop

    return 0;
}
```
📱 ➡️ 💻  
- `Device` ➡️ `Smartphone`  
- `Device` ➡️ `Laptop`

### 5. Hybrid (Virtual) Inheritance
A **Person** class, **Doctor** and **Teacher** classes, and a **MedicalTeacher** class that inherits from both **Doctor** and **Teacher**.

```cpp
#include <iostream>
using namespace std;

class Person {
public:
    void eat() {
        cout << "Person is eating" << endl;
    }
};

class Doctor : virtual public Person {
public:
    void treatPatient() {
        cout << "Doctor is treating a patient" << endl;
    }
};

class Teacher : virtual public Person {
public:
    void teach() {
        cout << "Teacher is teaching" << endl;
    }
};

class MedicalTeacher : public Doctor, public Teacher {
public:
    void research() {
        cout << "MedicalTeacher is researching" << endl;
    }
};

int main() {
    MedicalTeacher myMedTeacher;
    myMedTeacher.eat(); // Inherited from Person
    myMedTeacher.treatPatient(); // Inherited from Doctor
    myMedTeacher.teach(); // Inherited from Teacher
    myMedTeacher.research(); // Defined in MedicalTeacher

    return 0;
}
```
👨‍⚕️ ➡️ 👨‍🏫 ➡️ 🧑‍⚕️  
- `Person` ➡️ `Doctor`  
- `Person` ➡️ `Teacher`  
- `Doctor` ➡️ `MedicalTeacher`  
- `Teacher` ➡️ `MedicalTeacher`

