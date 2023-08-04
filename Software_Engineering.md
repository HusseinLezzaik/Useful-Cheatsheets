## Primitives
- Primitive concept is popular in computing, science, etc
- Are simple/basic objects/datatype that can be used to build more complex objects
- In computers, primitives are made up of single object called a NAND gate (binary operation)
- You can build all sorts of logic operations and math operations using the NAND gate
- Focus on building codebases using primitives

## Callbacks
- function that calls another function that runs a thread and returns a value

## Decorators
- used to pass function into another functino, creating a new function

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
- Secure Hash Algorithm SHA is a hash function whicn takes an input and produces a 20-byte hash value known as a message digest. 
- Designed by NSA, but it's been cryptographically broken but still widely used.

## Linter
- Not always easy to configure
- Time consuming
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

## Operator Overloading
- It's one of the advantages of `OOP`, where you can run operations on classes that's part of the object definition
- Giving extended meaning beyond their predefined operational meaning
- Example
```
$ class A:
      def __init__(self, a):
          self.a = a

      # adding two objects
      def __add__(self, o):
          return self.a + o.a

$ ob1 = A(1)
$ ob2 = A(2)
$ ob3 = A("Geeks")
$ ob4 = A("For")
 
$ print(ob1 + ob2)
$ print(ob3 + ob4)
```

## Nested Loops
- A nested loop is a loop inside a loop.

## Characteristics of Codebase
- Portability
- Correctness
- Reliability (asess trust/risk about `cross-dependencies`)
- Trusted Code Base (TCB)

## Debugging Lessons
- Debug by tracing back lines of code and check how things are connected
- In classes you'll find them defined in the .h files
- Always compile libraries
- Use print() statements for debugging
- Use "break" command in C++ for debugging
- Check if there's an online solution for your problem, or if someone has already solved it online
- Fill your unworking script with print statements after each instant where it might get stuck, that helps debugging your code a lot
- When a framework of several layers of software isn't working, turn them all off and start using one by one to see which one is failing .. start from the raw data and upwards
- Root cause the problem then work on a solution. ROS has strict configuration files at the beginning and check for people who've used stereo launch files before
- Draw flowcharts everytime you want to debug code, design code/systems, and get an overview of what the flow of data is.
- How do we know that what we think is happening is actually happening? In other words, if we said that we have a whole pipeline working together, how are we sure that all the subsystems are actually working together?
- When solving a problem, alway's think in terms of the "delta". What changed? When solving your problem.
- when debugging a problem, go through baby steps one by one and comment out everything else.
- start with the most basic/simple design, make sure that whatever you think is happening is actually happening
- don't write full lines of codes and test at that stage
- One useful trick for improving performance is just using the print statement from the top to the bottom. When you find which function is spending the most time, go inside the function and repeat until you find where's your time getting lost. Sort of a Binary Search Trick

## Profiling for Debugging
- Most programming languages have dedicated libraries for them to do profiling .. so just google what the language has and use that instead

## Bugs
- off-by-one bug
