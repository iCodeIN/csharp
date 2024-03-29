# csharp
My attempt at understanding csharp

# Differences between C# and C/C++

# Using vs include

In C/C++ you might include a header file.

```c
#include <stdio.h>
```

In C#, the using keyword using is used.  using is significantly more than #include.  It is similar to the using keyword in C++ in the sense that if you indicate "using System;", you mean that your code in that file will search the System namespace.  using allows for aliasing namespaces like "using S=System;".  In this case, if you wanted to call Console.WriteLine(...), you would need to prefix it with S. (S.Console.WriteLine(...)).  using allows for forward usage.  For example...

```csharp
using System;
using namespace A=Apple;

namespace Apple {
  class Animal {
      void Print() {
          Console.WriteLine("Hello World");
      }
  }
}
/* Comments are the same as C */
namespace Orange {  // These are comments as well
  class Animal {
    void Print() {
      A.Animal.Print();
    }
  }
}
```

Not sure about this syntax

```csharp
using (var font1 = new Font("Arial", 10.0f))
{
    byte charset = font1.GdiCharSet;
}
```

# Data type differences

decimal is introduced as a 128 bit version of double<br/>
byte == unsigned char<br/>
sbyte == char<br/>
char == 16-bit Unicode character<br/>
uint == unsigned int<br/>
ulong == unsigned long<br/>
ushort == unsigned short<br/>
bool == True or False<br/>

# sizeof works the same

# Dynamic types

object allows for compiled dynamic typing.  It's called boxing when a type is converted to an object.  Unboxing is when an object is converted back to a type.

dynamic allows for runtime dynamic typing.  It works as you might expect in other languages.

# Strings

String seems to be like the C++ string type or similar to java maybe.  "" or @"" are two ways of expressing quotes.  You can use the \ to extend lines.  The string replacement for WriteLine use similar syntax to python format string calls.  It uses {0} for first parameter, {1} for second, and so on..  The string keyword is an alias for the System.String class.

https://www.tutorialspoint.com/csharp/csharp_strings.htm

# Structures

struct is more like C++ than C, definitely just read this...

https://www.tutorialspoint.com/csharp/csharp_struct.htm

# Enums

Work similar to C (I rarely use them anyways).

https://www.tutorialspoint.com/csharp/csharp_enums.htm

# Pointers

Pointers are similar to C in how they are declared.

```csharp
byte* ptr;
```

Working with pointers is considered unsafe (not that it's unsafe, but there is a keyword unsafe).

# Type conversion stuff

Type conversions happen in a similar manner to C.  They can happen implicitly or through casting.  You can also use type conversion methods.

typeof() returns the type of a class.

is is used to determine if an object is of a certain type.

```csharp
if(Cat is Animal) ...
```

as is used to up-convert an object?

```csharp
void TreatAnimalAsCat(Animal a) {
  Cat c = a as Cat;
}
```

# Loops and Control

loops and if logic generally seems the same as C.


```csharp
int[] n = new int[10] { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
foreach (int j in n ) {
}
```

# Visibility and polymorphism

public, private, and protected seem similar to C++.  internal is new and allows any function or class within the given file to access the member???

static works the same as C++.  

Inheritance is similar to C++, except no support for multiple inheritance (makes me like C# a little more :-)).  

A bit to read here...
https://www.tutorialspoint.com/csharp/csharp_polymorphism.htm

# interface

Allows you to define a series of public method signatures which must be implemented in a derived class.

# namespace

Works like C++, allows nested namespaces.

# directives

Mostly similar, but a few new ones.

https://www.tutorialspoint.com/csharp/csharp_preprocessor_directives.htm

# Operator overloading

Makes me like C# a little less :-)

https://www.tutorialspoint.com/csharp/csharp_operator_overloading.htm

# Passing parameters

If you specify the keyword "out" in a function parameter declaration, modifying the parameters in the function will modify them externally (like passing an object by pointer or reference in C).  "ref" seems to do something similar.

# Operator differences

null == NULL, ?? is a coalescing operator

# Arrays

Assigning Values to an Array
You can assign values to individual array elements, by using the index number, like −

```csharp
double[] balance = new double[10];
balance[0] = 4500.0;
```

You can assign values to the array at the time of declaration, as shown −

```csharp
double[] balance = { 2340.0, 4523.69, 3421.0};
```

You can also create and initialize an array, as shown −

```csharp
int [] marks = new int[5]  { 99,  98, 92, 97, 95};
```

You may also omit the size of the array, as shown −

```csharp
int [] marks = new int[]  { 99,  98, 92, 97, 95};
```

You can copy an array variable into another target array variable. In such case, both the target and source point to the same memory location −

```csharp
int [] marks = new int[]  { 99,  98, 92, 97, 95};
int[] score = marks;
```

When you create an array, C# compiler implicitly initializes each array element to a default value depending on the array type. For example, for an int array all elements are initialized to 0.

Multidimensional arrays are like the following...

```csharp
int [,] a = new int [3,4] {
   {0, 1, 2, 3} ,   /*  initializers for row indexed by 0 */
   {4, 5, 6, 7} ,   /*  initializers for row indexed by 1 */
   {8, 9, 10, 11}   /*  initializers for row indexed by 2 */
};
```

An element in 2-dimensional array is accessed by using the subscripts. That is, row index and column index of the array. For example,

```csharp
int val = a[2,3];
```

More C/C++ like...
```csharp
int[][] scores;
scores = new int[5][];
for (int i = 0; i < scores.Length; i++) {
   scores[i] = new int[4];
}
```

params allows expansion

```csharp
   public int AddElements(params int[] arr) {
      foreach (int i in arr)
      ...

    int sum = app.AddElements(512, 720, 250, 567, 889);
```

https://www.tutorialspoint.com/csharp/csharp_array_class.htm
