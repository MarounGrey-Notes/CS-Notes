# C# vs .NET
* C# is a programming language
* .Net is a framework for building applications on Windows
.Net consists of two components: CLR (Common Language Runtime) and Class Library

# CLR (Common Language runtime)
The CLR is like a virtual machine that runs .NET applications. It takes care of important tasks like managing memory, handling errors, and making sure that the application runs securely. It also helps improve performance by compiling the code just before it is executed. All in all, the CLR is an essential part of the .NET framework that makes it easier and safer to develop applications.

When you compile an application, C# compiler compiles your code to IL (Intermediate Language) code. IL code is platform agnostics, which makes it possible to a take a C# program on a different computer with different hardware architecture and operating system and run it. For this to happen, we need CLR. When you run a C# application, CLR compiles the IL code into the native machine code for the computer on which it is running. This process is called Just-in-time Compilation (JIT).

# Architecture of .NET Applications
Applications consists of classes. **Class** is a container for some data (attributes) and functions (methods). Data represents the state of the application and functions are representing behaviour. For example: Car have attributes: model, color, etc; Car also have some functions: we can start it, we can move it, etc. <br><br>
**Namespace** - is a container for related classes. In .NET applications we have different namespaces for working with Databases, Graphics, Security, etc. <br><br>
**Assembly** - is a container for related namespaces. Physically it's a file on the disk, which can either be an EXE (executable) or DLL (dynamically linked library).

# Variables / Constants
**Variable** - a name given to a storage location in memory. <br>
**Constant** - an immutable value.

### Declaring Variables / Constants 
`int number;` - We declare variable by starting with the type (int) followed by identifyer (number). <br>
`int Number = 1;` -  When declaring the variable we can assign the value. Also, C# is a case sensitive language, so `Number != number`. <br>

### Identifiers
* Cannot start with the number
* Connot include whitespace
* Cannot be a reserved keyword

### Primitive Types

|                  | C# Type    | .NET Type   | Bytes | Range    |
| :---:            | :--------: | :---------: | :---: | :----:   |
| Integral Numbers | byte       | Byte        | 1     | 0 to 255 |
|                  | short      | Int16       | 2     | -32,768 to 32,768 |
|                  | int        | Int32       | 4     | -2.1B to 2.1B |
|                  | long       | Int64       | 8     | ... |
| Real Numbers     | float      | Single      | 4     | -3.4 x 10^38 to 3.4 x 10^38 |
|                  | double     | Double      | 8     | ... |
|                  | decimal    | Decimal     | 16    | -7.9 x 10^38 to 7.9 x 10^38 |
| Character        | char       | Char        | 2     | Unicode Characters |
| Boolean          | bool       | Boolean     | 1     | True / False |

# Overflowing
**Overflowing** - exeeding the boundary of the data type.

Example:
```
byte number = 255;

number = number + 1; //0
```
To prevent overflowing at runtime we can add `checked { }`:
```
checked { 
  byte number = 255;

  number = number + 1; //0
}
```
In this case an exception will be thrown and the program will crash, unless you handle the exception.

# Scope
**Scope** - is where a variable / constant has meaning.
```
{
  byte a = 1;
    {
      byte b = 2;
        {
          byte c = 3;
         }
     }
 }
 ```
 a is accessible everywhere in the scope, however c is only accessible within its own block. If I try to access a variable outside the scope I will get the compile error.

# Type conversion
### Implicit type conversion
Implicit type conversion: Implicit type conversion is an automatic conversion of a lower data type to a higher data type. It is done by the C# compiler automatically. This means that you do not need to explicitly specify the conversion.

For example, if you assign an integer value to a double variable, the compiler will automatically convert the integer value to a double value. Here's an example:

```
int num1 = 10;
double num2 = num1; // implicit conversion from int to double

```

### Explicit type conversion (casting)
Explicit type conversion: Explicit type conversion is a manual conversion of a higher data type to a lower data type. This is done by the programmer explicitly specifying the conversion using a cast operator.

For example, if you assign a double value to an integer variable, you will need to explicitly convert the double value to an integer value using a cast operator. Here's an example:

```
double num1 = 10.5;
int num2 = (int)num1; // explicit conversion from double to int using cast operator

```
It's important to note that when performing explicit type conversion, there is a risk of losing data or precision. Therefore, you should use explicit type conversion only when necessary and make sure to handle any potential loss of data or precision.


### Conversion between non-compatible types
In C#, there are cases where you may need to convert between non-compatible types. This can be done using various methods provided by the language, such as the Convert class, parsing methods, and user-defined conversion operators.

##### String to Integer: You can convert a string to an integer using the Parse method of the Int32 class, as follows:
```
string strNum = "123";
int num = Int32.Parse(strNum);
```
##### Integer to String: You can convert an integer to a string using the ToString method of the Int32 class, as follows:
```
int num = 123;
string strNum = num.ToString();
```
##### Enum to String: You can convert an enum to a string using the ToString method, as follows:
```
enum Days {Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday};
Days day = Days.Monday;
string dayStr = day.ToString();
```
##### String to Enum: You can convert a string to an enum using the Enum.Parse method, as follows:
```
string dayStr = "Monday";
Days day = (Days)Enum.Parse(typeof(Days), dayStr);
```
##### User-defined conversion operators: You can also define your own conversion operators for user-defined types. For example, if you have a class called MyClass, you can define a conversion operator to convert an instance of MyClass to an integer as follows:
```
class MyClass
{
    private int num;

    public MyClass(int num)
    {
        this.num = num;
    }

    public static explicit operator int(MyClass myObj)
    {
        return myObj.num;
    }
}

// Usage:
MyClass myObj = new MyClass(123);
int num = (int)myObj;
```
In general, it's important to be careful when converting between non-compatible types, as there may be loss of data or precision. You should always handle any potential errors that may occur during type conversion.

# Operators
### Arithmetic Operators
|                  | Operator   | Example   |
| :------: | :---: | :-------: | 
| Add      | + | a + b |
| Subtract | - | a - b |
| Multiply | * | a * b |
| Divide   | / | a / b |
| Remainder | % | a % b |

|  | Operator | Example | Same As |
| :---: | :---: | :---: | :---: |
| Increment | ++ | a++ | a = a + 1 |
| Decrement | -- | a-- | a = a-1 |

##### Postfix Increment
```
int a = 1;
int b = a++;

// a = 2, b = 1
```
##### Prefix Increment
```
int a = 1;
int b = ++a;

// a = 2, b = 2
```

### Comparison Operators

|  | Operator   | Example   |
| :------: | :---: | :-------: | 
| Equal    | == | a == b |
| Not Equal | != | a != b |
| Greater than | > | a > b |
| Greater than or equal to | >= | a >= b |
| Less than | < | a < b |
| Less than or equal to | <= | a <= b |


### Assignment Operators

|  | Operator | Example | Same As |
| :---: | :---: | :---: | :---: |
| Assignment | = | a = 1 |  |
| Addition Assignment | += | a += 3 | a = a + 3 |
| Subtraction Assignment | -= | a -= 3 | |
| Multiplication Assignment | \*= | a \*= 3 | |
| Division Assignment | /= | a /= 3 | |


### Logical Operators

|  | Operator   | Example   |
| :------: | :---: | :-------: | 
| And | && | a && b |
| Or | \|\| | a \|\| b |
| Not | ! | !a |

### Bitwise Operators

|  | Operator   | Example   |
| :------: | :---: | :-------: | 
| And | & | a & b |
| Or | \| | a | b |


# Classes
### Declaring Class
```
public class Person {  // access modifier( who can access this class), class keyword, identifier (Person)
  // Inside this code block we can have variables (fields)
  public string Name;
  // Classes can also contain methods:
  public void Introduce()
  {
    Console.WriteLine("Hi, my name is " + Name);
   }
}
```
### Declaring Objects
```
// Start with the type and identifier, then allocate memory for that object (new operator)
var person = new Person();
person.Name = "Maroun";
person.Introduce();
```
### Static Modifier
```
public class Calculator
{
  public static int Add(int a, int b)
  {
    return a+b;
  }
}
int result = Calculator.Add(1, 2);
// static is accessible from class, but not the object
```
Best practice is to have one class per file.

# Struct
### Declaring Struct
```
public struct RgbColor
{
  public int Red;
  public int Green;
  public int Blue;
}
```
There is not much difference between Classes and Structures, so use Struct when declaring a small lightweight object (like this rgb color).

# Array

**Array** - A data structure to store a collection of variables of the same type.

### Declaring array
```
int[] numbers = new int[3];
var numbers = new int[3]; { 1, 2, 3 } // if we already know the values we want to put in array;
```

# Strings

**String** - a sequence if characters.

## Creating strings
```
string firstName = "Maroun"; //using string literal
string name = firstName + " " + lastName; //using string concatenation
string name = string.Format("{0} {1}", firstName, lastName); //using string format

var numbers = new int[3] {1, 2, 3};
string list = string.Join(",", numbers);   //using string join
```

## String Elements
```
string name = "Maroun";
char firstChar = name[0]; //firstChar = "M"
```

### Strings are immutable - Once you created them, you can't change them.

| Char | Description |
| :---: | :---: | 
| \n | New Line | 
| \t | Tab |
| \\\ | Backslash |
| \\' | Single Quotation Mark |
| \\" | Double Quotation Mark |

### Verbatim Strings
```
string path = "c:\\projects\\project1\\folder1"; //when you have case like this
string path = @"c:\projects\project1\folder1"    //do this
```

### Enum

**Enum** - A set name/value pairs (constants)

Use enum where you see a number of related constants. For example:
```
// instead of this:
const int RegularMail = 1;
const int RegisteredAirMail = 2;
const int Express = 3;

//use this:
public enum ShippingMethod
{
   RegularMail = 1;
   RegisteredAirMail = 2;
   Express = 3;
}
```
# Parsing
**Parcing** - converting the string to another type.
The int.TryParse() method has two parameters:
  1. The first parameter is the string to be parsed as an integer.
  2. The second parameter is an output parameter that is used to store the parsed integer value if the parse is successful.


Example of parsing the string as integer:
```
string input = "42";
int number;

if (int.TryParse(input, out number))
{
    Console.WriteLine("Parsed number: " + number);
}
else
{
    Console.WriteLine("Invalid input.");
}
```


# Conditional Statements
### if / else
```
if (condition)
{
  someStatement
 } 
else if (condition)
{ 
 anotherStatement
}
else 
{
  someOtherStatement
}
```
### Switch / Case
Use switch instead of bunch 'else if' statements.
```
switch(role)
{
  case Role.Admin:
    ...
    break;
  case Role.Moderator:
    ...
    break;
  default:
    ...
    break;
}
```
### Conditional operator: a ? b : c
If `a` is true then do `b`, else `c`

# Iteration Statements
### For
```
for (var i = 0; i < 10; i++) {
  ...
}
```
### Foreach
Used to iterate over elements of an innumerable object (anything that has some kind of list or array)
* Local temporary variable (number)
* List or object that we are iterating (numbers)
```
foreach (var number in numbers)
{
  ...
}
```
### While
```
while (i<10) 
{
...
i++;
}
```
### Do-while
```
do 
{
  ...
  i++;
} while (i < 10);
```
### Break and Continue 
* Break: jump out of the loop
* continue: jump to the next iteration

# Random Class
```
{ 
 var random = new Random(); 
 random.Next(); 
}
```

# Arrays
**Array** - Represents a fixed number of variables of a particular type.

### Single Dimention Arrays 
```
var numbers = new int[5];
var numbers = new int[5]{1, 2, 3, 4, 5};
```
### Multi Dimentional Arrays
##### Rectangular
```
0 1 2 3 4
0 1 2 3 4        3x5
0 1 2 3 4
```
Syntax:
```
//Rectangular 2D
var matrix = new int[3, 5];
var matrix = new int[3, 5]
{
  { 1, 2, 3, 4, 5 },
  { 6, 7, 8, 9, 10},
  { 11, 12, 13, 14, 15 }
};

var element = matrix[0, 0]; //To access elemet from array

//Rectangular 3D
var colors = new int[3, 5, 4];

```
##### Jagged
```
0 1 2 3
0 1 2 3 4
0 1 2
```
Syntax:
```
var array = new int[3][];

array[0] = new int[4];
array[1] = new int[5];
array[2] = new int[3];

//To access elemet in the array:
array[0][0] = 1;
```
### Some of the Array methods
```
var numbers = new[] { 1, 2, 3, 4, 5, };

//Length
//Returns number of elements in Array
Console.WriteLine(numbers.Length); //5

//IndexOf
//Returns the index of the element in array
var index = Array.IndexOf(numbers, 3);
Console.WriteLine(index); //2

//Clear()
//Clears elements in array: sets numbers to 0, booleans to false, strings to null
Array.Clear(numbers, 0, 2); //name of the array, starting index, number of items to clear
foreach (var n in numbers) Console.WriteLine(n);  //0 0 3 4 5

//Copy
//Copies elements of one array to another
int[] another = new int[3];
Array.Copy(numbers, another, 3); //src array, destination, num of elements to copy
foreach (var n in another) Console.WriteLine(n); //0 0 3

//Sort()
//Sorts elements in ascending order
Array.Sort(numbers);
foreach (var n in numbers) Console.WriteLine(n); //0 0 3 4 5

//Reverse()
//Sorts elements in descending order
Array.Reverse(numbers);
Array.Sort(numbers);
foreach (var n in numbers) Console.WriteLine(n); //5 4 3 0 0       
            
```

# Lists
Lists are similar to arrays, however while arrays have fixed sizes, lists have dynamic sizes
