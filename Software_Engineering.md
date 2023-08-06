## SOLID
- SOLID principles are generally applied to object-oriented programming (OOP), not databases. The acronym SOLID stands for five design principles:
- These principles help in creating a more maintainable, flexible, and robust codebase.
  
**1) S: Single Responsibility Principle (SRP)**
- A class should have only one reason to change.
```python
# Bad
class Report:
    def generate(self):
        # Code to generate report
        pass
    def save(self):
        # Code to save report to file
        pass

# Good
class Report:
    def generate(self):
        # Code to generate report
        pass

class ReportSaver:
    def save(self, report):
        # Code to save report to file
        pass
```

**2) O: Open-Closed Principle (OCP)**
- Software entities should be open for extension but closed for modification.
```python
# Bad
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

class AreaCalculator:
    def area(self, rectangle):
        return rectangle.width * rectangle.height

# Good
class Shape:
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

class AreaCalculator:
    def area(self, shape):
        return shape.area()
```

**3) L: Liskov Substitution Principle (LSP)**
- Subtypes must be substitutable for their base types.
```python
# Good
class Bird:
    def fly(self):
        pass

class Sparrow(Bird):
    def fly(self):
        # Implementation for Sparrow
        pass

class Penguin(Bird):
    def fly(self):
        raise NotImplementedError("Penguins can't fly!")

# Using the bird class
bird = Sparrow()
bird.fly()  # Works fine
bird = Penguin()
bird.fly()  # Raises an error
```

**4) I: Interface Segregation Principle (ISP)**
- A client should not be forced to depend on interfaces it doesn't use.

```python
# Bad
class MultiFunctionPrinter:
    def print(self):
        pass
    def scan(self):
        pass

# Good
class Printer:
    def print(self):
        pass

class Scanner:
    def scan(self):
        pass

class MultiFunctionPrinter(Printer, Scanner):
    pass
```

**5) D: Dependency Inversion Principle (DIP)**
- High-level modules should not depend on low-level modules. Both should depend on abstractions.
```python
# Bad
class LightBulb:
    def turn_on(self):
        pass

class Switch:
    def __init__(self, bulb):
        self.bulb = bulb

# Good
class Switchable:
    def turn_on(self):
        pass

class LightBulb(Switchable):
    def turn_on(self):
        # Turn on the bulb
        pass

class Switch:
    def __init__(self, device):
        self.device = device
```

## Four Pillars of OOP
**1. Encapsulation:**
- Encapsulation is the bundling of data and the methods that operate on that data, restricting access to some of the object's components
```python
class Car:
    def __init__(self, brand):
        self.__brand = brand  # Private attribute

    def get_brand(self):  # Public method to access private attribute
        return self.__brand

my_car = Car('Toyota')
print(my_car.get_brand())  # Outputs 'Toyota'
```

**2. Inheritance:**
- Inheritance is the mechanism that allows a class to inherit attributes and methods from another class. It promotes code reusability.

```python
class Vehicle:
    def move(self):
        print('Moving...')

class Car(Vehicle):
    pass

my_car = Car()
my_car.move()  # Outputs 'Moving...'
```

**3. Polymorphism:**
- Polymorphism refers to the ability of different objects to be treated as instances of the same class. It allows objects to be processed in a way that's appropriate to their individual types.
```python
class Dog:
    def sound(self):
        return 'Woof!'

class Cat:
    def sound(self):
        return 'Meow!'

def animal_sound(animal):
    print(animal.sound())

dog = Dog()
cat = Cat()
animal_sound(dog)  # Outputs 'Woof!'
animal_sound(cat)  # Outputs 'Meow!'
```

**4. Abstraction:**
- Abstraction means hiding the complex reality while exposing only the essential parts. It helps to reduce complexity by hiding unnecessary details.   
```python
from abc import ABC, abstractmethod

class Shape(ABC):  # Abstract class
    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

rect = Rectangle(5, 10)
print(rect.area())  # Outputs 50
```

## Operator Overloading
- It's one of the advantages of `OOP`, where you can run operations on classes that's part of the object definition
- Giving extended meaning beyond their predefined operational meaning
- Example
```python
class A:
      def __init__(self, a):
          self.a = a

      # adding two objects
      def __add__(self, o):
          return self.a + o.a

ob1 = A(1)
ob2 = A(2)
ob3 = A("Geeks")
ob4 = A("For")
 
print(ob1 + ob2)
print(ob3 + ob4)
```

## Overriding
- Overriding in Python refers to the ability of a subclass to provide a specific implementation of a method that is already defined in its superclass. This allows the subclass to inherit the properties and behaviors from the superclass but also gives the ability to modify or extend specific behaviors.
```python
class Animal:
    def sound(self):
        return "Some generic animal sound"

class Dog(Animal):
    def sound(self):
        return "Woof"
```

## Functional Programming
- Functional programming is a programming paradigm that treats computation as the evaluation of mathematical functions and avoids changing state and mutable data. The primary pillars of functional programming are:
**1. Immutability:**
- Data cannot be changed once created. This leads to more predictable code.
- Example:
```python
x = (1, 2, 3)  # Using a tuple, which is immutable
```
**2. Pure Functions:**
- A function is pure if its return value is only determined by its input values, and it doesn't have side effects like modifying global variables.
```python
def add(a, b):
    return a + b  # Pure function, no side effects
```
**3. First-Class Functions:**
- Functions can be assigned to variables, passed as arguments, and returned from other functions.
```python
def apply_function(func, a, b):
    return func(a, b)

result = apply_function(add, 5, 3)  # Passing the 'add' function
```
**4. Higher-Order Functions:**
- These are functions that take one or more functions as arguments or return a function as a result.
```python
def multiply_by(factor):
    def multiply(number):
        return number * factor
    return multiply

times_two = multiply_by(2)
print(times_two(4))  # Outputs 8
```
**5. Recursion:**
- Instead of using loop constructs, functional programming often utilizes recursion to iterate.
```python
def factorial(n):
    return 1 if n == 0 else n * factorial(n - 1)

print(factorial(5))  # Outputs 120
```
**6. Referential Transparency:**
- An expression is called referentially transparent if it can be replaced with its value without changing the behavior of the program.
```python
# You can replace 'add(2, 3)' with '5' anywhere in the code without changing behavior
y = add(2, 3)
```


## Primitives
- Primitive concept is popular in computing, science, etc
- Are simple/basic objects/datatypes that can be used to build more complex objects
- In computers, primitives are made up of a single object called a NAND gate (binary operation)
- You can build all sorts of logic operations and math operations using the NAND gate
- Focus on building codebases using primitives

## Callbacks
- a function that calls another function that runs a thread and returns a value

## Decorators
- used to pass a function into another function, creating a new function

## Codebase
- great code is written 3 times, like hardware iterations

## Portable
- easily portable into new environments

## Modular
- Modular languages is one that supports the concept of modularity, which refers to the separation of a computer program into discrete, self-contained modules that can be independently created, modified, and reused. 
- Modular programming languages typically provide mechanisms for defining and using modules, such as import statements, module definitions, and module interfaces. 

## Bootstrap
- Starting up a computer system or application by loading a small program into memory that then loads the rest of the operating system or application
- Term can refer to the process of starting up any complex system or process, such as a business organization

## Comments
- Write comments that explain why code is written, not how

## SHA-1
- Secure Hash Algorithm SHA is a hash function which takes an input and produces a 20-byte hash value known as a message digest. 
- Designed by NSA, but it's been cryptographically broken but still widely used.

## Linter
- Not always easy to configure
- Time-consuming
- Lots of False Positives
- Triggers unnecessary work like refactoring code to make the tool stop complaining
- Focus on ISO + POSIX specs using proof from Standards is often better

## Logs
- Try to always keep logs directories inside software projects, especially important for deep learning

## Dynamic Link Library | Dll
- A dynamic-link library (DLL) is a file that contains compiled code and data that can be used by multiple programs at the same time. 
- There are two types of DLLs: static and dynamic. Static DLLs are linked to a program at compile time, while dynamic DLLs are linked to a program at runtime.
- Examples of static linking include C and C++,  and those that support dynamic linking include Python and Java.

## OOP
- Classes are made up of `constructor` and `method`. These are later called `attributes`

## Nested Loops
- A nested loop is a loop inside a loop.

## Characteristics of Codebase
- Portability
- Correctness
- Reliability (assess trust/risk about `cross-dependencies`)
- Trusted Code Base (TCB)

## Debugging Lessons
- Debug by tracing back lines of code and check how things are connected
- In classes, you'll find them defined in the .h files
- Always compile libraries
- Use print() statements for debugging
- Use the "break" command in C++ for debugging
- Check if there's an online solution for your problem, or if someone has already solved it online
- Fill your unworking script with print statements after each instant where it might get stuck, that helps debug your code a lot
- When a framework of several layers of software isn't working, turn them all off and start using them one by one to see which one is failing .. start from the raw data and upwards
- Root cause the problem then work on a solution. ROS has strict configuration files at the beginning and checks for people who've used stereo launch files before
- Draw flowcharts every time you want to debug code, design code/systems, and get an overview of what the flow of data is.
- How do we know that what we think is happening is actually happening? In other words, if we said that we have a whole pipeline working together, how are we sure that all the subsystems are actually working together?
- When solving a problem, always think in terms of the "delta". What changed? When solving your problem.
- when debugging a problem, go through baby steps one by one and comment out everything else.
- start with the most basic/simple design, and make sure that whatever you think is happening is actually happening
- don't write full lines of codes and test at that stage
- One useful trick for improving performance is just using the print statement from the top to the bottom. When you find which function is spending the most time, go inside the function and repeat until you find where's your time getting lost. Sort of a Binary Search Trick

## Profiling for Debugging
- Most programming languages have dedicated libraries for them to do profiling .. so just google what the language has and use that instead

## Bugs
- off-by-one bug
