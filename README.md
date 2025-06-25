# 📦 .NET SDK vs .NET RUNTIME

---

## 🧰 What is the .NET SDK?

The **.NET SDK (Software Development Kit)** is used do **build and develop** .NET applications.

### The .NET SDK includes : 
 - The **.NET Runtime**
 - **Compilers**
 - **.NET CLI tools** (`dotnet` command)
 - **Project templates**
 - **Build tools**

### When do you need it?
 - Creating new projects: `dotnet new console`
 - Building apps: `dotnet build`
 - Running apps during development: `dotnet run`

> 📌 Install the SDK if you are a **developer**.

---

## ⚙ What is the .NET Runtime 

The **.NET Runtime** is what is required to **run a .NET application** after is build.  It is required so that an operating system can **run a .NET application**. It **does not include build tools**, so it's meant for **running applications**, not for developing them.


### It includes :
 - The **Common Language Runtime (CLR)**
 - Base libraries 

### ❌ It does **not include** :
 - Compilers 
 - SDK tools 
 - Project Templates 

### When do you need it?
If you have a pre-built app (e.g., `dll`) and just want to run it: ``dotnet MyApp.dll``

---

The C# compiler (named Roslyn) used by the dotnet CLI tool converts your C# source code into intermediate language (IL) code and stores the IL in an assembly (a DLL or EXE file)

**The Common Language Runtime(CLR) it's what actually executes your .NET applications.**

# ⚙️ Common Language Runtime (CLR)

The **Common Language Runtime(CLR)** it's what actually executes your .NET applications, managing critical services like memory, security, and exception handling.

---

## 🚀 What Does the CLR Do?

| Feature                 | Description |
|------------------------|-------------|
| 🔄 Code Execution       | Runs Intermediate Language (IL) code by converting it to native code using **JIT (Just-In-Time)** compilation. |
| 🗑️ Memory Management    | Uses **Garbage Collection (GC)** to automatically free unused memory. |
| 🔐 Security             | Enforces code access permissions and sandboxing where needed. |
| 🧪 Type Safety          | Ensures that data types are used correctly and safely. |
| 📦 Exception Handling   | Provides a unified error-handling mechanism across all .NET languages. |
| 🌐 Interoperability     | Allows .NET code to interact with unmanaged code (e.g., C++, COM). |
| 🔍 Metadata & Reflection | Supports runtime inspection of types and assemblies. |

---

## 🛠️ How It Works

1. ✅ You write code in C# (or any .NET-supported language)
2. 🧱 It is compiled into **IL (Intermediate Language)**
3. ⚙️ The **CLR** loads the IL code at runtime
4. 🧠 The **JIT Compiler** translates IL into native machine code
5. 🧩 The code runs on your operating system with full runtime services


#  Global using in C#
 
> You can import a namespace in one .cs file and it will be available throughout all .cs files instead of having to import the namespace at the top of every file that needs it. You could put  the global using statements in the GlobalUsings.cs with the contents being all your global using statements. 

---

### Types

In C# every type can be **categorized as a class, struct, enum, interface, delegate**. For example, the C# keyword string is a class, but int is struct from System.Int32 where int is an allias.

### Verbatim literal string

A literal string prefixed with @ to disable escape characters so that a backslash is a backslash. It also allows the string value to span multiple lines because the whitespace characters are treated as themselves instead of instructions to the compiler.
<code>string filePath = @"C:\test\projects"</code>

### Raw string literals

Raw string literals are convenient for entering any arbitrary text without needing to escape the contents. They make it easy to define literals containing other languages like XML, HTML, or JSON.

``string xml = """
             <person age="50">
               <first_name>Mark</first_name>
             </person>
             """; ``

**You can also use raw interpolated string literals : 
``var person = new { FirstName = "Alice", Age = 5
 string json = $$"""
              {
                "first_name": "{{person.FirstNa
                "age": {{person.Age}},
                "calculation": "{{{ 1 + 2 }}}"
              }
              """;
 Console.WriteLine(json); ```

 # Numbers 

> You can use ``0b_number`` to write a number in binary.
> You can use ``0x_number`` to write a number in hexadecimal.
> You can use _ as digit seperator.

> In C# the special type named object can store any type of data.

Suffixes for numbers :
* L: Compiler infers long
* M: Compiler infers decimal
* D: Compiler infers double
* F: Compiler infers float

### Null Forgiving operator ``!``

It tells the compiler that it won't return null, but you need to ensure it.

### Switch expressions for reference types 

`` message = animal switch
  {
    Cat fourLeggedCat when fourLeggedCat.Legs == 4
        => $"The cat named {fourLeggedCat.Name} 
    Cat wildCat when wildCat.IsDomestic == false
        => $"The non-domestic cat is named {wildCat}",
    Cat cat
        => $"The cat is named {cat.Name}.",
    Spider spider when spider.IsVenomous
        => $"The {spider.Name} spider is venomous."
    null =>
           $"The animal is null."'
    _ =>
           $"Nothing"
  }; ``

### Foreach :

The `foreach` statement can be used with any type that implements the following pattern:

- The type must have a `GetEnumerator` method that returns an enumerator object.
- The enumerator object must have:
    - A `Current` property, which provides access to the current element in the collection.
    - A `MoveNext` method, which advances to the next element and returns `true` if there are more elements, or `false` if the end of the collection has been reached.

This allows `foreach` to iterate over arrays, collections, and any custom types that follow this pattern.


### Casting :

Implicit casting happens automatically, and it is safe, meanwhile explicit  casting must be performed manually because it may lose information.
