# **Move Semantics**

## **Overview**
In modern C++, move semantics is a powerful feature that allows efficient resource transfer between objects. It is especially useful when dealing with objects that manage dynamic memory or other heavy resources. In this lab, students will explore how move semantics work, understand the difference between copy and move operations, and implement move constructors and move assignment operators in their own classes.

By the end of the lab, students will have a concrete understanding of when and why move semantics matter, and how to apply them to write more efficient and modern C++ code.

---

## **Learning Goals**
By the end of this lab, you will be able to:

✅ Explain the concept of move semantics and rvalue references in C++  
✅ Implement a move constructor and move assignment operator  
✅ Compare the behavior and performance of copy vs. move operations  
✅ Identify scenarios where move semantics are particularly beneficial  
✅ Use std::move appropriately to enable moves  

---

## **Part 1: Introduction to Copy vs. Move**
### ✅ **Task 1.1 Reading and Discussion**

Read the following code snippet:

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> v1 = {1, 2, 3, 4};
    std::vector<int> v2 = v1;        // Copy
    std::vector<int> v3 = std::move(v1); // Move

    std::cout << "v1 size: " << v1.size() << std::endl;
    std::cout << "v2 size: " << v2.size() << std::endl;
    std::cout << "v3 size: " << v3.size() << std::endl;

    return 0;
}
```

Questions:

•	What is the output of this program?  
•	Why does v1.size() return 0 after the move?  
•	What does std::move do?  
•	Why is v1 still in a valid but unspecified state?  

## **Part 2: Implementing Move Semantics**

### ✅ **Task 2.1 Define a Simple Resource-Managing Class**
Implement a class Buffer that manages a dynamically allocated array of integers.

```cpp
class Buffer {
private:
    int* data;
    size_t size;

public:
    Buffer(size_t s) : size(s), data(new int[s]) {
        std::cout << "Constructor called\n";
    }

    ~Buffer() {
        delete[] data;
        std::cout << "Destructor called\n";
    }

    // TODO: Add copy constructor and assignment operator
    // TODO: Add move constructor and move assignment operator
};
```

### ✅ **Task 2.2 Add Copy Constructor and Assignment**
Implement the copy constructor and copy assignment operator.

```cpp
Buffer(const Buffer& other) : size(other.size), data(new int[other.size]) {
    std::copy(other.data, other.data + other.size, data);
    std::cout << "Copy constructor called\n";
}

Buffer& operator=(const Buffer& other) {
    if (this != &other) {
        delete[] data;
        size = other.size;
        data = new int[size];
        std::copy(other.data, other.data + size, data);
        std::cout << "Copy assignment called\n";
    }
    return *this;
}
```

### ✅ **Task 2.3 Add Move Constructor and Assignment**
Implement the move constructor and move assignment operator.

```cpp
Buffer(Buffer&& other) noexcept : data(other.data), size(other.size) {
    other.data = nullptr;
    other.size = 0;
    std::cout << "Move constructor called\n";
}

Buffer& operator=(Buffer&& other) noexcept {
    if (this != &other) {
        delete[] data;
        data = other.data;
        size = other.size;

        other.data = nullptr;
        other.size = 0;
        std::cout << "Move assignment called\n";
    }
    return *this;
}
```


## **Part 3: Using Your Class**
### ✅ **Task 3.1 Create Instances and Observe Behavior**
Write a main function that uses the Buffer class:

```cpp
int main() {
    Buffer b1(100);
    Buffer b2 = b1;           // Should call copy constructor
    Buffer b3 = std::move(b1); // Should call move constructor

    Buffer b4(50);
    b4 = b2;                  // Should call copy assignment
    b4 = std::move(b2);       // Should call move assignment
    return 0;
}
```

Questions:
•	What constructors and assignments are called and when?
•	What happens to the source object after a move?
•	What would happen if you didn’t define the move constructor/assignment?


## **Part 4: Performance Comparison**
### ✅ **Task 3.1 Measure Performance**

Wrap a loop around operations with large buffers (e.g., size 10,000,000) and measure time taken when copying vs. moving. Write down your findings.

Use <chrono> for timing.

```cpp
#include <chrono>

auto start = std::chrono::high_resolution_clock::now();
// Operation
auto end = std::chrono::high_resolution_clock::now();
std::cout << "Duration: " << std::chrono::duration_cast<std::chrono::milliseconds>(end - start).count() << " ms\n";
```

## **Part 5: Summary**
Questions

•	What did you learn about move semantics?  
•	In what kinds of projects do you think this would matter?  
•	What are some risks of using std::move incorrectly?  