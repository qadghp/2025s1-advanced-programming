# **Lab: Template Functions in C++**

## **Overview**
In this lab, you will explore the basics of template functions in C++, including **function templates**, **concepts**, **variadic templates**, and **template metaprogramming**. Templates are a powerful feature in C++ that enable generic programming, allowing you to write more flexible and reusable code.

This lab is designed to be completed in approximately **two hours**. 

---

## **Learning Goals**
By the end of this lab, you will be able to:
✅ Understand the syntax and purpose of template functions in C++  
✅ Write generic functions using templates  
✅ Use **concepts** to restrict template parameters  
✅ Create and use **variadic templates**  
✅ Apply **template metaprogramming** techniques  

---

## **Part 1: Basic Template Functions**
### ✅ **Task 1.1: Write a Simple Template Function**
1. Create a template function called `maxValue` that takes two arguments of the same type and returns the maximum value.
2. Test the function with different types, including `int`, `double`, and `std::string`.

### 📝 **Example**
```cpp
#include <iostream>
using namespace std;

template <typename T>
T maxValue(T a, T b) {
    return (a > b) ? a : b;
}

int main() {
    cout << maxValue(5, 10) << endl;          // Should print 10
    cout << maxValue(3.5, 2.1) << endl;       // Should print 3.5
    cout << maxValue(string("apple"), string("orange")) << endl; // Should print "orange"
}
```

## ✅ Task 1.2: Overload a Template Function
1.	Create an overloaded version of the maxValue template that takes three parameters.
2.	Test the function with integers and floating-point numbers.

### 📝 **Example**
```cpp
template <typename T>
T maxValue(T a, T b, T c) {
    return maxValue(a, maxValue(b, c));
}

int main() {
    cout << maxValue(1, 5, 3) << endl;          // Should print 5
    cout << maxValue(2.1, 3.7, 1.9) << endl;    // Should print 3.7
}
```

## **Part 2: Concepts**

✅ Task 2.1: Create a Template with a Concept
	1.	Create a concept called Numeric that allows only integral or floating-point types.
	2.	Write a template function add that accepts two parameters constrained by the Numeric concept.


### 📝 **Example**

```cpp
#include <iostream>
#include <concepts>

template <typename T>
concept Numeric = std::integral<T> || std::floating_point<T>;

template <Numeric T>
T add(T a, T b) {
    return a + b;
}

int main() {
    cout << add(3, 4) << endl;       // Should print 7
    cout << add(2.5, 3.1) << endl;   // Should print 5.6
    // cout << add("a", "b");        // Should fail at compile time
}
```

## **Part 2: Variadic Templates**
### ✅ Task 3.1: Write a Variadic Template Function
	1.	Write a variadic template function called printAll that accepts any number of parameters and prints them separated by spaces.
	2.	Test it with different types of arguments.

### 📝 **Example**
```cpp
#include <iostream>

template <typename T>
void printAll(T t) {
    std::cout << t << std::endl;
}

template <typename T, typename... Args>
void printAll(T t, Args... args) {
    std::cout << t << " ";
    printAll(args...);
}

int main() {
    printAll(1, 2.5, "Hello", 'c'); // Should print: 1 2.5 Hello c
}
```
## ✅ Task 3.2: Variadic Template for Summation
	1.	Write a variadic template function called sum that returns the sum of all arguments.
	2.	Test it with integers and floating-point values.

```cpp
template <typename T>
T sum(T t) {
    return t;
}

template <typename T, typename... Args>
T sum(T t, Args... args) {
    return t + sum(args...);
}

int main() {
    cout << sum(1, 2, 3, 4, 5) << endl;             // Should print 15
    cout << sum(1.1, 2.2, 3.3) << endl;             // Should print 6.6
}
```

## **Part 2: Template Metaprogramming**
### ✅ Task 4.1: Compile-Time Factorial Using Templates
	1.	Write a recursive template that calculates the factorial of a number at compile time using template metaprogramming.
	2.	Test it with a constexpr value.

### 📝 **Example**
```cpp
#include <iostream>

template <int N>
struct Factorial {
    static constexpr int value = N * Factorial<N - 1>::value;
};

template <>
struct Factorial<0> {
    static constexpr int value = 1;
};

int main() {
    constexpr int result = Factorial<5>::value;
    std::cout << result << std::endl;  // Should print 120
}
```

### ✅ Task 4.2: Fibonacci Series Using Template Metaprogramming
	1.	Write a recursive template that calculates the nth Fibonacci number at compile time.
	2.	Test it with constexpr values.

### 📝 **Example**
```cpp
template <int N>
struct Fibonacci {
    static constexpr int value = Fibonacci<N - 1>::value + Fibonacci<N - 2>::value;
};

template <>
struct Fibonacci<0> {
    static constexpr int value = 0;
};

template <>
struct Fibonacci<1> {
    static constexpr int value = 1;
};

int main() {
    constexpr int result = Fibonacci<10>::value;
    std::cout << result << std::endl; // Should print 55
}
```