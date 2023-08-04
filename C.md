## Concepts
- extern
- global
- static : local static, global static
- volatile
- dangling pointer
- memory layout: stack (func call, auto variable), heap, inititialized, uninitialized
- dynamic memory (malloc/alloc/realloc/free)
- bitwise operations (set/clear bits, binary masks, etc)
- stack overflow error
- segmentation fault: illegal access to memory (*0xsomeGargbageAddress)
- memory mapped I/O
- struct Padding
- file.h
- compiling vs. linking

## Compilers
- several c compilers: clang, gcc, etc
1) Preprocessor: 
- takes in (.c), handles #include, #define, strips out comment, outputs a processed file
```
$ gcc -E // start with your c file, pre-process it and then stop
$ clang - E
```

2) Compiler:
- translate c to assembly, doesn't release an executable, (.s)
```
$ gcc -S // start with .c file and compile into assembly
```

3) Assembler:
- translate assembly to object file (compiled file that has been targeted cpu/os but not complete executable) (.o)
```
$ gcc -c // starts with .c file and transofrms into object file .o
```

4) Linker:
- brings together object files and produces an executable  (exec.)
```
$ gcc // with no flag will do through the whole process
```

## Header Files
- c code, for defining constants, variables, etc
- to use, only have to include them in your c code:
```
$ include "gd.h"
```
- inside gd.h:
```
$ double get_double(char *promt, double min, double max);
```

## Includes
```
$ #include <stdio.h> // standard io
$ #include <<stdlib.h> // standard library
$ #include <string.h>
$ #include <math.h>
```

## Constants
```
$ const int num = 5; // cannot be modified
$ int const num = 5; // cannot be modified
```

## Variables
```
$ short age0 = 10; // atleast 16-bits signed integer
$ int age1 = 20; // atleast 16-bits signed integer
$ long age2 = 30; // atleast 32-bits signed integer
$ float age4 = 40; // 
$ double gpa = 3.6; // double
$ char grade = 'A'; 
$ char phrase[] = "Giraffe Academy" // string of characters
$ char characterName[] = "John"; // defining string 
$ const int IS_TALL; // to use as a boolean
```

## Memory
- ends with 0, 4, 8, C // multiples of 4 in word processor
- byte aligned, faster to access

## Comments
```
$ // 
$ /* my comment */
```

## Printf
- Symbols:
```
$ %c 	// character
$ %d 	// integer number (base 10)
$ %e	// exponential floating-point number
$ %f	// floating-point number
$ %i 	// integer (base 10)
$ %o	// octal number (base 8)
$ %s 	// a string of characters
$ %u 	// unsigned decimal (integer) number
$ %x 	// number in hexadecimal (base 16)
$ %% 	// print a percent sign
$ \% 	// print a percent sign
$ */
$ \n 	// new line
```

- printf samples
```
$ printf("Hello World!\n");
$ printf("%s, your grade is %c  \n", name, testGrade);
```

## Scanf
```
$ int age;
$ printf("Enter your age: ");
$ scanf("%d", &age);
```

## Memory Allocation/Deallocatin
- You have to `free()` the allocated memory in exact reverse order of how it was allocated using `malloc()`
- memory allocation for 1D arrays:
```
$ buffer = malloc(num_items*sizeof(double));
```
- memory deallocation for 1D arrays:
```
$ free(buffer);
```
- memory allocation for 2D arrays:
```
$ double **cross_norm=(double**)malloc(150 * sizeof(double *));
$ for(i=0; i<150;i++)
    {
        cross_norm[i]=(double*)malloc(num_items*sizeof(double));
    }
```    
- memory deallocation for 2D arrays:
```
$ for(i=0; i<150;i++)
    {
        free(cross_norm[i]);
    }

$ free(cross_norm);
```

## Pointers (Memory Address)
- Accessing address of variable
```
$ int num = 10;
$ printf("%p \n", &num);
```

- Defining address variable
```
$ int *pNum = &num;
$ printf("%p \n", pNum); // pNum memory adddress
$ printf("%d \n", *pNum); // dereferencing 
```

## Math
```
$ sqrt(x)
$ pow(x, y)
```

## Arrays
```
$ type arrayName [ arraySize ];
$ int luckyNumbers[] = {4, 8, 15, 16, 23, 42};
```

## 2D Arrays
```
$ int numbs[2][2] = {
		{1, 2},
		{3, 4}
		};
```

## Strings
```
$ char name[10];
$ strcmp(s1, s2) // returns FALSE if they are the same
$ !strcmp(s1, s2)
```

## If/else
```
$ if (condition 1){
	statement;
} else if (condition 2){
	statement;
} else {
	statement;
}
```

## While Loops
```
$ while(condition){
	do stuff;
} 
```

## For Loops
```
$ for (int i=0; i<=n; i++)
{ do stuff
}
```

## Functions
```
$ void sayHi() {
	printf("Hello User");
}
```

## Switch Statements
```
$ switch(grade){
case 'A':
	printf("You did great!");
	break;
case 'B':
	printf("You did alright!");
	break;
}
```

## Padding
```
$ %2ld // pad with blank spaces, have min nb of digits to be printed
$ %05ld // padded with 0
```

## Structures
```
$ struct address
{
   char name[50];
   char street[100];
   char city[50];
   char state[20];
   int pin;
};
```

## Files
```
$ FILE * fpointer = fopen("employees.txt", "w"); // r: read, w: write, a: append - can also specific location
$ fprintf(fpointer, "\nKelly, Customer Service");
$ fclose() // always make sure to close files, remove file from memory and save changes etc
```

## Make Files
- automates building, helps linking stuff at the end, builds the whole dependency tree
```
$ make --version
$ make --help
```
- standard format, file is called "Makefile":
```
$ #-*- MakeFile -*- // must be written at first line
$
$ #target: dependencies
$ # 	action
```

- to run makefile to build, use:
```
$ make
$ make clean // clean stuff
```

## gcc
```
$ gcc --help
$ man gcc
$ -o
$ -c
$ -I
$ -D 
$ -l 
$ -L
$ -o2
$ -W // warning flags
```
