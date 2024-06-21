# Introduction

This lesson will guide you over math:
1. Understand the arithmetic operators in C++
2. Understand the math library in C++
3. Apply mathematical concepts in practical programming exercises: solving equations

# Arithmetic operators
There are several arithmetic operators that allow operate with variables:
* ```+``` addition
* ```*``` multiplication
* ```-``` substraction
* ```/``` division
* ```%``` modulus (reminder of division)

Each arithmetic operator performs a different operation, you can check them using the following program:

```c++
#include <iostream>

int main() {
  int a, b;

  std::cout << "Introduce a number: \n";
  std::cin >> a;
  std::cout << "Introduce another number: \n";
  std::cout << b;
  std::cout << "\n";
  
  // Perform operations
  std::cout << a << " + " << b << " is " << a+b << "\n";
  std::cout << a << " - " << b << " is " << a-b << "\n";
  std::cout << a << " * " << b << " is " << a*b << "\n";
  std::cout << a << " / " << b << " is " << a/b << "\n";
  std::cout << a << " % " << b << " is " << a%b << "\n";  
}
```

# Math Functions
Arithmetic operations allow us to perform basic mathematical operations, but... what about more complex operations? To solve more complex operations a new library must be included ```cmath```. 

```c++
#include <iostream>
#include <cmath>

int main() {
  int a;

  std::cout << "Introduce a number: \n";
  std::cin >> a;
  
  // Perform operations
  std::cout << "The square of " << a << " is " << pow(a, 2) << "\n";
  std::cout << "The square root of " << a << " is " << sqrt(a) << "\n";
}
```

## Exercise: Calculate Factorial
Putting together maths and loops we can calculate factorial of a number.

```c++
#include <iostream>
#include <cmath>

int main() {
  int a;
  int factorial = 1;

  std::cout << "Introduce a number: \n";
  std::cin >> a;

  for (int i = 2; i <= a; i++)
    {
      factorial = factorial * i;
    }

  std::cout << "The factorial of " << a << " is " << factorial;
}
```
Lets put it in a function
```c++
  int factorial (int number)
{
  int factorial = 1;
  for (int i = 2; i <= number; i++)
    {
      factorial = factorial * i;
    }
  return factorial;
}
```

## Exercise: Calculate Fibonacci sequence
The fibonacci sequence is a mathematical sequence calculated adding the 2 previous numbers in the sequence. This suits perfectly to use a loop to calculate the value of a given position in the sequence. As previous exercise a function is a very good way to make the calculus.

```c++
int fibonacci (int number)
{
  if (number == 0) return 0;
  if (number == 1) return 1;
  int fibonacci_1 = 0;
  int fibonacci_2 = 1;

  for (int i = 2; i <= number; i++)
  {
    int temp = fibonacci_1 + fibonacci_2;
    fibonacci_1 = fibonacci_2;
    fibonacci_2 = temp;
  }
  return fibonacci_2;
}
```

## Exercises: Calculate Areas
Other use of maths is calculate areas, maybe triangle, square, rectangle, circle. It is suitable to make a function for each of these calculus, so it can be used as many times as needed juts passing the parameters and getting the result.

```c++
int area_triangle(int base, int height)
{
  return base * height / 2;
}

int area_square(int side)
{
  return side * side;
}

int area_rectangle (int base, int height)
{
  return base * height;
}

int area_circle (int radius)
{
  return 2 * 3.14 * radius;
}
```
These functions can be used in a program as follow
```c++
int main() {
  int a, b;
  
  std::cout << "Introduce a number: \n";
  std::cin >> a;
  std::cout << "Introduce another number: \n";
  std::cin >> b;

  std::cout << "A triangle with base: " << a << " and height " << b;
  std::cout << " has an area of: " << area_triangle(a,b) << "\n";
  std::cout << "A rectangle with base: " << a << " and height " << b;
  std::cout << " has an area of: " << area_rectangle(a,b) << "\n";
  std::cout << "A square with side: " << a;
  std::cout << " has an area of: " << area_square(a) << "\n";
  std::cout << "A circle with radius: " << a;
  std::cout << " has an area of: " << area_circle(a) << "\n";
}
```

## Exercise: Solving Equations
Math and functions can be used to solve problems. There is a common problem in math classes about two trains that start from different cities with different speeds and the point where they meet must be calculated, given the distance between the two cities.

The math behind this problem is not very compex: ```TrainA speed * time = distance - (TrainB speed * time)```. There are 4 variables in the equation, and 3 of them are known, we can calculate the time, and then the disctance.

```c++
int trainMeetingPoint(int trainA_speed, int trainB_speed, int distance)
{
  int time = distance / (trainA_speed + trainB_speed);

  return time * trainA_speed; // Meeting point from City A
}
```
This function will be able to solve any problem of this kind, just needs to receive the correct arguments.
```c++
int main() {
  int a, b, d;
  
  std::cout << "Introduce train A speed: \n";
  std::cin >> a;
  std::cout << "Introduce train B speed: \n";
  std::cin >> b;
  std::cout << "Introduce the distance: \n";
  std::cin >> d;

  std::cout << "The trains will meet " << trainMeetingPoint(a,b,d);
  std::cout << " away from the City A";
}
```

# Float numbers
Integers are not he only numbers, there are also real numbers. The computer uses different data types for each type of numbers, one for integers and another one for real numbers. The data type used to store and handle real numbers is called Float (because of the floating point used to represent it).

Fortunately, all the code and concepts that are valid for integers are also valid for float numbers, it is only needed to change the type. In some previous examples the need of floating numbers is quite obvious. What about the triangle area? what about the area of a circle? Or even the problema about the two trains. These problems are not going to work properly if just using integers.

```c++
float trainMeetingPoint(float trainA_speed, float trainB_speed, float distance)
{
  float time = distance / (trainA_speed + trainB_speed);

  return time * trainA_speed; // Meeting point from City A
}
```
and
```c++
int main() {
  float a, b, d;
  
  std::cout << "Introduce train A speed: \n";
  std::cin >> a;
  std::cout << "Introduce train B speed: \n";
  std::cin >> b;
  std::cout << "Introduce the distance: \n";
  std::cin >> d;

  std::cout << "The trains will meet " << trainMeetingPoint(a,b,d);
  std::cout << " away from the City A";
}
```
Using floats our program is going to admit real numbers, it is going to use them using the calculus, using integers will cause all the results to trunkate (loose the fractional part), and it is going to return a distance in real format.
  