# C# vs .NET
* C# is a programming language
* .Net is a framework for building applications on Windows
.Net consists of two components: CLR (Common Language Runtime) and Class Library

# CLR (Common Language runtime)
The CLR is like a virtual machine that runs .NET applications. It takes care of important tasks like managing memory, handling errors, and making sure that the application runs securely. It also helps improve performance by compiling the code just before it is executed. All in all, the CLR is an essential part of the .NET framework that makes it easier and safer to develop applications.

# Architecture of .NET Applications
Applications consists of classes. **Class** is a container for some data (attributes) and functions (methods). Data represents the state of the application and functions are representing behaviour. For example: Car have attributes: model, color, etc; Car also have some functions: we can start it, we can move it, etc. <br><br>
**Namespace** - is a container for related classes. In .NET applications we have different namespaces for working with Databases, Graphics, Security, etc. <br><br>
**Assembly** - is a container for related namespaces. Physically it's a file on the disk, which can either be an EXE (executable) or DLL (dynamically linked library).