
# Encapsulation in C++

## Definition

- **Encapsulation** is an OOP principle that:
  - Combines data and methods into a single unit (class).
  - Restricts direct access to some components.
  - Exposes only necessary parts through public methods.
  - Keeps internal details private.
  
## Benefits

- **Data Hiding:** Protects object integrity by preventing unauthorized access.
- **Increased Security:** Limits how data is accessed and modified.
- **Improved Maintainability:** Internal implementation changes do not affect external code.
- **Ease of Use:** Simplifies interaction with objects through a defined interface.

## Example

### YouTubeChannel Class

```cpp
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class YouTubeChannel {
private:
    string Name;
    string OwnerName;
    int SubscribersCount;
    vector<string> PublishedVideoTitles;

public:
    YouTubeChannel(string name, string ownerName)
        : Name(name), OwnerName(ownerName), SubscribersCount(0) {}

    void Subscribe() {
        SubscribersCount++;
    }

    void Unsubscribe() {
        if (SubscribersCount > 0) {
            SubscribersCount--;
        }
    }

    void PublishVideo(string title) {
        PublishedVideoTitles.push_back(title);
    }

    void GetInfo() const {
        cout << "Name: " << Name << endl;
        cout << "OwnerName: " << OwnerName << endl;
        cout << "SubscribersCount: " << SubscribersCount << endl;
        cout << "Videos: " << endl;
        for (const string& videoTitle : PublishedVideoTitles) {
            cout << videoTitle << endl;
        }
    }
};
```

### Main Function

```cpp
int main() {
    YouTubeChannel ytChannel("0xA13H4Y", "codetechie-abhay");

    ytChannel.Subscribe();
    ytChannel.Subscribe();
    ytChannel.Subscribe();
    ytChannel.GetInfo();

    ytChannel.Unsubscribe();
    ytChannel.GetInfo();

    ytChannel.PublishVideo("C++ for beginners");
    ytChannel.PublishVideo("HTML & CSS");
    ytChannel.PublishVideo("C++ OOP");
    ytChannel.GetInfo();

    return 0;
}
```

### Output

```
Name: 0xA13H4Y
OwnerName: codetechie-abhay
SubscribersCount: 3
Videos:

Name: 0xA13H4Y
OwnerName: codetechie-abhay
SubscribersCount: 2
Videos:

Name: 0xA13H4Y
OwnerName: codetechie-abhay
SubscribersCount: 2
Videos:
C++ for beginners
HTML & CSS
C++ OOP
```

## Summary

- **Encapsulation** ensures:
  - Private properties.
  - Modification only through public methods.
  - Better data control.
  - Prevention of unauthorized changes.
  - Maintenance of object state integrity.

