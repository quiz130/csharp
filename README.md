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
