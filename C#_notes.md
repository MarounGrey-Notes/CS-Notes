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
