# C++ Coding Challenge: Initialization, References, and Value Categories

## Objective

This challenge will help students practice different initialization methods, references, structured bindings, and value categories (l-values and r-values) in C++. They will also analyze how these concepts interact and identify l-values and r-values in the code.

## Task Description

You will implement a small program that demonstrates:

    1.	Different types of initialization in C++.
    2.	The use of references and pointers to modify values.
    3.	Structured bindings to unpack values from a structure.
    4.	Identification of l-values and r-values in various expressions.


## Part 1: Variable Initialization

Declare and initialize the following variables using different initialization methods:

	- An `int` with an initial value.
	- A `double` with an initial value.
	- A `std::string` with an initial value.
	- A `bool` with an initial value.

Use different types of initialization (i.e., direct initialization, uniform initialization, structured binding)Print all the initialized values.

## Part 3: References
    1.	Declare a reference to a and use it to modify the value of the previously created variables.
    2.	Print the values again to confirm changes.

## Part 4: Structured Binding
	1.	Define a struct Point containing three members (e.g., x, y, z).
	2.	Create an instance of this struct and initialize it.
	3.	Use structured binding to unpack its members into separate variables.
	4.	Print the unpacked values.

## Part 5: Identifying l-values and r-values

Analyze the following expressions and classify each as an l-value or an r-value:
	1.	a = 42;
	2.	int x = a + b;
	3.	&a;
	4.	std::string s = c + " World";
	5.	int& refX = x;
	6.	int&& rref = 100;

Write comments in the code explaining which expressions are l-values and which are r-values.

## Example Output
```
Initial values:
int: 10, double: 3.14, string: Hello, float: 2.5

Modified values:
int: 20, double: 2.71, string: World, float: 1.5

Pointer modification:
int: 100

Structured Binding:
x: 5, y: 10, z: 15

Value Categories (only comments in code):
a = 42; // l-value
int x = a + b; // a and b are l-values, (a + b) is an r-value
&a; // l-value
std::string s = c + " World"; // c is an l-value, "World" is an r-value, (c + " World") is an r-value
int& refX = x; // l-value reference
int&& rref = 100; // r-value reference
```