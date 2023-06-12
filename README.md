# Learn C# Basics
From Youtube video [C# Tutorial For Beginners - Learn C# Basics in 1 Hour](https://youtu.be/gfkTfcpWqAY) by Programming with Mosh

<br>

## Difference between C# and .NET
<ul>
    <li>C# is a programming language</li>
    <li>.NET is a framework for building applications on Windows</li>
    <li>.NET is not limited to C#. There are different languages that can target .NET framework and build applications. Examples are:</li>
    <ul>
        <li>F#</li>
        <li>Visual Basic.NET</li>
    </ul>
    <li>.NET framework consists of two components.</li>
    <ul>
        <li>Common Language Runtime</li>
        <li>Class Library</li>
    </ul>
</ul>

<br>

## Common Language Runtime (CLR)
CLR translates IL Code (Intermediate Language) into Native/Machine Code.

In **C/C++ applications**, compilers translate code into native code for the machine on which it was running. 

![C/C++ Code into Machine Code](/images/C_to_Machine.png)

Which means if I wrote an application in C++ on a Windows machine with 8086 processor architecture, the compiler would translate my code into the native code for that machine that is — a Windows with an 8086 processor.

We all have different hardware. We have different operating systems.

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

A namespace is a container for related classes. For example, in .NET framework, we have namespaces each containing tens of related classes. We have namespaces for working with data, like databases. We also have namespaces for working with graphics and images. We have namespaces for working with security.

In real world implementation, as these namespaces grow, we need a different way of partitioning an application. That is where we use an assembly.

An assembly is a container for related namespaces.

![Structure of an Assembly](/images/Assembly_Structure.png)

It is a file on the disk which can either be an executable or a DLL (Dynamically Linked Library).

So when you compile your application, the compiler builds one or more assemblies depending on how you partition your code.

![Structure of an Application](/images/Application_Structure.png)

<br>

## Your First C# Program
We can build different kinds of applications with C# — desktop apps, web apps, apps for cloud, mobile, services, workflows and various kinds of things but your first build will be a **console application.**

```dotnet new``` - Creates a new project, configuration file, or solution based on the specified template. Check this [documentation](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-new) for more info.

Create a console app by running ```dotnet new console -o "HelloWorld"``` in the command line. This will create a HelloWorld folder in your current directory with the console application inside.

![HelloWorld using dotnet new command](/images/Hello_World_dotnet_new_console.png)

This version of console app is abstracted compared to most tutorials seen on the internet. But, the commonly seen version is the one created in Visual Studio and it looks like this:

![HelloWorld common version](/images/Hello_World.png)

While the two variants have different structure, their function remain the same. 

To explain what is happening particularly on the second part, we look closely at the contents of Program.cs.
The .cs file name extension on Program.cs means it is a C# file. On the top you see a bunch of ```using``` statements but what are all these about?

Our project is called HelloWorld so by default, Visual Studio creates a namespace called HelloWorld. When we write code in this namespace, we have access to any class defined in this namespace. If you want to use a class that is defined in a different namespace, we need to import it in our code file and that is why we use the ```using``` statement.

Also by default, Visual studio placed these five ```using``` statements.

```System``` is a namespace in .NET framework where we have all these basic utility classes and primitive data types.

```System.Collections.Generic``` is used to work with lists, collections, and so on.

```System.Linq``` is used to work with data and is a comprehensive topic.

```Sytem.Text``` contains classes representing various character encoding and conversions, as well as providing helper classes for manipulating and formatting String objects.

```System.Threading``` is used to build multi-threaded applications.

The HelloWorld application is very simple that it only uses the ```System``` namespace. Since the application uses only one out of the five imported namespaces, it is safe to remove the other four namespaces to make the code cleaner.

Now, on the ```HelloWorld``` namespace, inside it by default we have a class called ```Program```.

Every console application you create with Visual Studio has a class called ```Program```.

Inside ```Program```, by default we have a method or function called ```Main``` and this is the entry point to the application.

When you run the application, the CLR executes the code inside the ```Main``` method. This method is declared as ```static```.

Methods have input and output. What goes inside the parenthesis is the input to the method which we call parameter or argument. Note that parameters are optional but in the default template, the Main method has a parameter called args which is of type string array. 

What you see before the method name is the return type or the output of the method. Void in C# means nothing. That means this method does not return any value. It just contains some code. That's it.

Also, note that C# is a case sensitive language so this ```Main``` has to be with capital "M". Otherwise, CLR is not going to find this method as the entry point of the application.

One last thing to note are these curly braces. Where we have a block of code, we need to surround it with curly braces and this is applicable for methods, for classes, and for namespaces.

We have a class called ```Console``` which is used to read data from console or write data to it. It has a bunch of methods. We can access this method using the dot notation.

On the HelloWorld application, we used the ```WriteLine``` method. This method can optionally take a parameter. We passed the string ```"Hello World"``` into it.

Note that statements in C# terminate with a semicolon.

Then, we run the application.

![Console Output for HelloWorld](/images/Console_Output_Hello_World.png)

This window that you see here is what we call the console. This is the reason why this kind of project is called a console application. 

<br>

## Variables and Constants
<li>Variable — a name given to a storage location in memory.</li>
<li>Constant — an immutable value.</li>

<br>

In C#, to declare a variable, we start with the type followed by an identifier and finally semicolon.

![Declaring Variables/Constants](/images/Declaring_Variables.png)

You can not use a variable until you initialize it. For example, I wanted to use ```int number;``` in its current state in an application. My application will not compile because I have to assign it a value before I can use/read it.

There are a few things we have to know about identifiers. 
<li>The identifier cannot start with a number.</li>
<li>An identifier cannot include whitespace</li>
<li>An identifier cannot be a reserved keyword</li>

<br>

List of the most commonly used primitive types in C# : <br>
![Primitive Types](/images/Primitive_Types.png)

Most of these data types are pretty straight forward but there is something tricky about real numbers.

In this table we have data types for real numbers — float, double, and decimal. <br>
![Real Numbers](/images/Real_Numbers.png)

The **double** row is highlighted because it is the default data type used by C# compiler when using real numbers.

If you want to declare a float, you need to explicitly tell the compiler to treat the number you have as a float.

In C#, we also have a few other types which are not considered primitive types. These are: <br>
![Non-Primitive Types](/images/NonPrimitive_Types.png)