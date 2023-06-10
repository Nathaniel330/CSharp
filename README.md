# Learn C# Basics
From Youtube video [C# Tutorial For Beginners - Learn C# Basics in 1 Hour](https://youtu.be/gfkTfcpWqAY) by Programming with Mosh

## Common Language Runtime (CLR)
CLR translates IL Code (Intermediate Language) into Native/Machine Code.

In C/C++ applications, compilers translate code into native code for the machine on which it was running. 

![C/C++ Code into Machine Code](/images/C_to_Machine.png)

Which means if I wrote an application in C++ on a Windows machine with 8086 processor architecture, the compiler would translate my code into the native code for that machine that is — a Windows with an 8086 processor.

We all have different machines. We have different operating systems.

If I took the compiled application on a computer with a different architecture, it would not run.

![Compile Problem - Running an app on two different operating systems](/images/C_System_Issue.png)

When Microsoft was designing the C# language and the .NET Framework, they came up with an idea that they borrowed from the Java community.

In Java, compiled code is not directly translated into machine code. It is translated into an intermediate language called ByteCode.

![Java to ByteCode](/images/Java_to_ByteCode.png)

We have the exact same concept in C#. When you compile your C# code, the result is what we call IL or intermediate languade code and it is independent of the computer on which it is running.

Now we need something that would translate that IL code into the native/machine code to run the application. This is the job of CLR or common language runtime.

![C# to IL into Machine Code](/images/C%23_to_IL_to_Machine.png)

CLR is essentially an application that is sitting in the memory whose job is to transalte the IL code into machine code and this process is called just-in-time compilation or JIT.

With this architecture, you can write an application in C# and you don't have to worry about compiling the code into the native code for differenct machines, as long as the machine has CLR that can run your application.

<br>

## Architecture of .NET Applications
At a very high level, when you build an application with C#, your application consists of building blocks called ```classes```. These classes collaborate with each other at runtime and as a result the application provides some functionality.

![C# Application in a high level](/images/C%23_%20Application_High_Level.png)

A ```class``` is a container that has some data which are also called attributes/properties and functions which are also called methods.

```functions``` or ```methods``` have behavior. They execute code, they do things for us.

```data``` or ```properties``` represent the state of the application.

We can think of a car as a class. Its make, model and its color are the attributes. A car also has some functions. We can start it or we can move it.

![car as a class](/images/car_as_class.png)

As the number of classes in an application grows, we need a way to organize these classes. That is where we use a namespace.

A namespace is a container for related classes. For example, in .NET framework, we have namespaces each containing tens of related classes. We have namespaces for with data, like databases. We also have namespaces for working with graphics and images. We have namespaces for working with security.

In real world implementation, as these namespaces grow, we need a different way of partitioning an application. That is where we use an assembly.

An assembly is a container for related namespaces.

![Structure of an Assembly](/images/Assembly_Structure.png)

It is a file on the disk which can either be an executable or a DLL (Dynamically Linked Library).

So when you compile your application, the compiler builds one or more assemblies depending on how your partition your code.

![Structure of an Application](/images/Application_Structure.png)

