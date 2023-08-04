## Concepts
- Cpp is exactly like C, but an increment (internal joke of how they got the name) the same way we define a variable as x++ 
- Windows: compile c++, myApp.exe (executable) || Linux doesn't care
- Static (.lib) and Dynamic (.dll) Linking
- Stack and Heap in C++, usually used for memory allocation and dynamic memory allocations. Memory leaks happens usually when dynamic memory keeps on storing.
- Classes are like the example of Fruit and an Apple
- If you're not including a standard library, run #include<library/name.h>
- STL: Standard Template Library
- C is faster than cpp by small ms .. cpp is used for gaming, kernels design, OS, .. Also cpp is useful for virtual functions/vtables that have to do with designing kernels
- Most compilers are designed in C
- A lot of code in c++ packages are encapsulated, but the meat of it is usually a function that you can easily use
- there's primitive data types and complex classes/structures

## C++ file management
1) Header file:
_ .h or .hxx (include) for all the libraries

2) Source code:
_ .cc or .cpp or .cxx (src)

## Libraries
1) Eigen:
- Eigen is a C++ template library for linear algebra: matrices, vectors, numerical solvers, and related algorithms.

## Includes
```c++
$ include <boost/thread/mutex.hpp>
$ include <cmath>
$ include <algorithm>
$ include <vector>
$ include <iostream>
$ include <vector>
```

## In C++ there are two ways to add comments
```c++
$ //single-line comment
$ /* block comment */
```
## Global vs. Local Variables
In order to access the global variable, we make use of a “scope resolution operator (::)”.
```c++
$ cout<<”Global Variable x = “<<::x;
```

## Constants Declaration
```c++
$ #define PI 3.142
$ const int pi = 3.142;
```

## Sizes
- int is of 2 bytes, long int is 4 bytes
- float is 4 bytes
- bi = 2
- dec = 10
- oct = 8
- hex = 16
- 0 1 2 3 4 5 6 7 8 9 A B C D E F

## UML (Unified Modeling Language)
- The Unified Modeling Language (UML) is a general-purpose, developmental, modeling language in the field of software engineering that is intended to provide a standard way to visualize the design of a system.
- Can be very helpful for representing classes in c++

## Float
- floats are usually 4 bytes (32 bits)

## Variables Declaration:
- string name;
- int age;

## Commands
- for commenting: either `/* Hello World */` or `// Hello World`
- for printing statements: 
```c++
    // Print output
    cout << "Name : " << name << endl;
    cout << "Age : " << age << endl;
```

- for reading statements: 
```c++
    // Take multiple input using cin
    cin >> name >> age;
```

## Debugging tips
- Debug by tracing back lines of code and check how things are connected
- For classes, you'll find them defined in .h files
- Always compile libraries whenever you make changes
- Use print() for debugging
- Use "break" command in c++ for debugging

## Binary files
- a lot of company hide their code with binary files

## Spaces
- spaces don't really matter in cpp like in python
- you can have lots of spaces in If statements for examples without them being aligned and that's not a problem

## Define Constants
```c++
$ #define PI 3.1415
```

## Mutex: Definition for thread-safe code
- to be thread-safe, you can read/write in the same thread if only one exists, but in ROS the way the sub/pub works is that there is multiple threads running
```c++
$ boost::mutex mtx_radar;
$ mtx_radar.lock()
$ radar_full = radar_front;
$ mtx_radar.unlock()
```

## Arrays
- when we type array[o], it's more of a pointer than a actually variable
- Can use Booleans to capture a specific condition

## Classes
- private variables
- public variables

## Modulus
- A smart way to control the upper bound of something like the lidar points from the array because 361 for example doesn't exist
```c++
$ LIDAR_TOTAL_POINTS = 360;
$ angle = (i)%LIDAR_TOTAL_POINTS;
```

## Namespaces
```c++
$ #include <iostream>
$ using namespace std; # to specify which namespaces defined inside <iostream>, computer needs to know the code for the cout, cin functionalities and it needs to know which namespace they are defined.
```

## Segmentation Fault
- A segmentation fault occurs when your program attempts to access an area of memory that it is not allowed to access. 
- In other words, when your program tries to access memory that is beyond the limits that the operating system allocated for your program.

1) When you try to write to a portion of memory that was marked as read-only:
```
char *str = "Foo"; // Compiler marks the constant string as read-only
*str = 'b'; // Which means this is illegal and results in a segfault
```
2) A common way to get a segfault is to dereference a null pointer:
```c++
int *p = NULL;
*p = 1;
```

## Add Space:
```c++
$ << endl
```
