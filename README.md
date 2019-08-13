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

String seems to be like the C++ string type or similar to java maybe.  "" or @"" are two ways of expressing quotes.  You can use the \ to extend lines.  The string replacement for WriteLine use similar syntax to python format string calls.  It uses {0} for first parameter, {1} for second, and so on..

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

# Visibility

public, private, and protected seem similar to C++.  internal is new and allows any function or class within the given file to access the member???

# Passing parameters

If you specify the keyword "out" in a function parameter declaration, modifying the parameters in the function will modify them externally (like passing an object by pointer or reference in C).  "ref" seems to do something similar.

# Operator differences

null == NULL, ?? is a coalescing operator
