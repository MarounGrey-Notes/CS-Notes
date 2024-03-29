# Terms to know
**Procedural Programming** - paradigm based on procedure calls.

# C# vs .NET
* C# is a programming language
* .Net is a framework for building applications on Windows
* .NET consists of two components: CLR (Common Language Runtime) and Class Library.

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

# Enum
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
# Array

**Array** - Represents a fixed number of variables of a particular type. It's a data structure to store a collection of variables of the same type. 

### Declaring Single Dimention Arrays 
```
int[] numbers = new int[3];
var numbers = new int[3]; { 1, 2, 3 } // if we already know the values we want to put in array;
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
Lists are similar to arrays, however while arrays have fixed sizes, lists are used when you're not sure how many objects you are going to store in it.
### Creating Lists
```
var numbers = new List<int>();
var numbers = new List<int>() { 1, 2, 3, 4 };
```
Common methods for the lists:
* Add() [To add an object to the list]
* AddRange() [To add more than 1 object or a list of objects, that can be another list or an array]
* Remove() [To remove an object from the list]
* RemoveAlt() [To remove the object at a given index]
* IndexOf() [returns index of a given object]
* Contains() [Tells if the list contains the given object or not]
* Count [returns the number of the objects in the list]

# Working with Dates
### DateTime
```
var dateTime = new DateTime(2015, 1, 1); //January 1st 2015
var now = DateTime.Now; //Access current date
var today = DateTime.Today; //Access today

Console.WriteLine(now.Hour);
Console.WriteLine(now.Minute);

var tomorrow = now.AddDays(1); //access tomorrow by adding day
var yesterday = now.AddDays(-1);

Console.WriteLine(now.ToString()); // 23/05/2015 12:43:51 PM
Console.WriteLine(now.ToLongDateString()); // Saturday, 23 May 2015
Console.WriteLine(now.ToShortDateString()); // 23/05/2015
Console.WriteLine(now.ToLongTimeDateString()); // 12:43:51 PM
Console.WriteLine(now.ToShortTimeDateString()); // 12:43 PM
```
### TimeSpan
```
var timeSpan = new TimeSpan(1, 2, 3); // 1 hour, 2 minutes, 3 seconds
var timeSpan1 = new TimeSpan(1, 0, 0); // 1hour, 0 min, 0 sec
var timeSpan2 = TimeSpan.FromHours(1);

var start = DateTime.Now;
var end = DateTime.Now.AddMinutes(2);
var duration = end - start; 
Console.WriteLine(duration); // returns time span. In this case 2 min


Console.WriteLine("Minutes: " + timeSpan.Minutes); // returns minutes component of the timeSpan obj. In this case 2 [bcs TimeSpan(1, 2, 3)]
Console.WriteLine("Total Minutes: " + timeSpan.TotalMinutes); // converts TimeSpan obj to minutes. In this case its 62.05 (bcs 1 hour, 2 min, 3 sec = 62 min)


Console.WriteLine("Add Example: " + timeSpan.Add(TimeSpan.FromMinutes(8))); // adding 8 mins to original timeSpan
Console.WriteLine("Subtract Example: " + timeSpan.Subtract(TimeSpan.FromMinutes(2))); // Subtracting 2 mins to original timeSpan


Console.WriteLine("ToString: " + timeSpan.ToString()); //Converting date to string
Console.WriteLine("Parse: " + timeSpan.Parse("01:02:03")); //parsing string into date object
```
# Working Strings
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
### Formatting
```
ToLover() //"hello world"
ToUpper() // "HELLO WORLD"
Trim() // Gets rid of white spaces around the string
```
### Searching
```
//return first or last occurence of the given string
IndexOf("a");
LastIndexOf("Hello");
```
### Substrings
```
Substring(startIndex) //takes startIndex, retrieves all the characters from that point to the end of the string
Substring(startIndex, length) //same thing but it takse length parameter to limit the number of characters to retrieve
```
### Replacing
```
Replace('a', '!')
Replace("maroun", "maroony")
```
### Join 
```
string[] array = { "Hello", "World", "!" };
string joinedString = string.Join(" ", array); //HelloWorld
```

### Null Checking
```
String.IsNullOrEmpty(str)
String.IsNllOrWhiteSpace(str)
```
### Splitting
```
str.Split(' ');
```

## Parsing
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
### Converting Strings to Numbers
```
string s = "1234";
int i = int.Parse(s);
int j = Convert.ToInt32(s);
```
### Converting Numbers to Strings
```
int i = 1234;

string s = i.ToString();       // "1234"
string t = i.ToString("C");    // "$1,234.00"
string t = i.ToString("C0");   // "$1,234"
```
### Format Strings
| Format or Specifier | Description | Example |
| :-----------------: | :---------: | :-----: |
| **c** or **C**      | Currency    | 123456 (C) -> $123,456 |
| **d** or **D**      | Decimal     | 1234 (D6) -> 001234 |
| **e** or **E**      | Exponential | 1052.0329112756 (E) -> 1.052033E+003 |
| **f** or **F**      | Fixed Point | 1234.567 (F1) -> 1234.5 |
| **x** or **X**      | Hexadecimal | 255 (X) -> FF |

### StringBuilder
Represents mutable string, but not optimised for searching

Some of the methods:
```
var builder = new StringBuilder();
builder.Append('-', 10); //repeats - 10 times
builder.AppendLine(); // new line
builder.Append("Header"); //outputs Header

builder.Replace('-', '+'); //replaces all the - above to +
builder.Remove(0, 10); // removes 10 characters
builder.Insert(5, "a") // inserts a at the index 5

Console.WriteLine(builder[0]); // displays 1st character
```

# Working with Files
In .Net we have a namespace that is called System.IO, that's where all these classes to work with files and directories are located. The most common classes include:

####File, FileInfo 
Provide methods for creating, copying, deleting, moving, and opening of files. <br>
**FileInfo** provides **instance** methods, whereas **File** provides **static** methods.
```
Create();
Copy();
Delete();
Exists()
GetAttributes();
Move();
ReadAllText();
```
#### Directory, DirectoryInfo 

**Directory** provides **static** methods, **DirectoryInfo** provides **instance** methods
```
CreateDirectory
Delete();
Exists()
GetCurrentDirectory();
GetFiles();
Move();
GetLogicalDrives();
```
#### Path
```
GetDirectoryName()
GetFileName()
GetExtention()
GetTempPath()
```

# Classes
Class - building block of software application <br>
Object - instance of a class <br>

Creating class:
```
public class Person
{
  public string Name;
  public void Introduce(); //void means it doesnt return anything
  {
  Console.WriteLine("Hi, myy name is " + Name);  //use shortcut  cw+tab
  }
}
```

Creating Object:
```
var person = new Person();  //Or "Person person = new Person();"

person.Name = "Maroun";
person.Introduce();
```

### Class Members
Instance - accessible from an object:
```
var person = new Person();
person.Name = "Maroun"
```
Static - accessible from the class
```
Console.Writeline();
```

# Constructors
Constructor - method which is called when the instance of a class is created. Constructor always has the same name as Class

Why - To put an object in early state
How:
```
 public class Customer
 {
     public Customer() {}
 }
```
Constructor Overloading:
```
public class Customer
{
    public int Id;
    public string Name;
    public List<Order> Orders;   //Generic class for list of objects

    public Customer()
    {
        Orders = new List<Order>();   //initialize the empty list inside the empty constructor
    }
    public Customer(int id)
        : this()   //before the next line executes its going to call empty constructor
    {
        this.Id = id;
    }

    public Customer(int id, string name)
        : this(id)   //before the next line executes its going to call previous constructor
    {
        this.Id = id;
        this.Name = name;
    }
}
```

# Object initializers
Its a syntax for quickly initializing an object without the need to call one of its constructors (to avoid creating multiple constructors)
```
//For example we have a class Person
public class Person
{
  public int Id;
  public string FirstName;
  public string LastName;
  public DateTime Birthdate;
}

//So, we may end up with a bunch of constructors like this:
public class Person
{
  public Person (int Id) {}
  public Person (int Id, string FirstName) {}
  public Person (int Id, string FirstName, string LastName) {}
  public Person (int Id, DateTime Birthdate) {}
}

//With Object initializer we dont need any of these constructors, we can simply initialize object like this:
var person = new Person
                {
                  FirstName = "Maroun";
                  LastName = "Barqawi";
                };
//behind the scenes the default(parameterless) constructor is going to be called and then any properties you set above will be initialized
``` 
