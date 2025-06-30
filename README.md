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

**The Common Language Runtime(CLR) it's what actually executes your .NET applications, and it manages the execution of .net code**

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

![image](https://github.com/user-attachments/assets/343af643-dff4-4e00-8770-2808db83823f)

## ⚙ Debug vs Release

Debug and Release are build modes.

> 💡 Use Debug when you are in development
> 💡 Use Release when you need to go on production or you need to push your .DLL or .EXE

**The difference is that in Debug mode the code is not optimized, while in Release it is optimized. The Release mode doesn't not print any stack errors, and ignore debug symbols `#if DEBUG`.** 

## 🔶 dotnet publish 

`dotnet publish` is used for deploying your application. The output of dotnet publish includes the compiled IL, dependencies, and other required files to run the application.
It is used to prepare your application for deployment. It compiles your code, copies dependencies, and generates all the files needed to run your app on a target system. It's the final step before deploying a .NET application to production or another environment.

| Option                           | Description                                                                   |
| -------------------------------- | ----------------------------------------------------------------------------- |
| `-c Release`                     | Publishes in Release mode (instead of Debug).                                 |
| `-o <output-folder>`             | Sets a custom output folder.                                                  |
| `--self-contained`               | Publishes the .NET runtime with the app (so .NET isn’t required on the host). |
| `--runtime <RID>`                | Targets a specific OS/architecture (e.g. `win-x64`, `linux-arm`).             |
| `--self-contained true` | Used to bundle the .NET runtime with your app, so it runs even on those that don’t have .NET installed.|
| `--no-restore`                   | Skips dependency restore (faster if already done).                            |
| `p:PublishSingleFile=true` |This output a single file |


#  Global using in C#
 
> You can import a namespace in one .cs file and it will be available throughout all .cs files instead of having to import the namespace at the top of every file that needs it. You could put  the global using statements in the GlobalUsings.cs with the contents being all your global using statements. 

---

### 🚀 Types

In C# every type can be **categorized as a class, struct, enum, interface, delegate**. For example, the C# keyword string is a class, but int is struct from `System.Int32` where int is an *allias*.

### 🎊 Verbatim literal string

A literal string prefixed with `@` to disable escape characters so that a backslash is a backslash. It also allows the string value to span multiple lines because the whitespace characters are treated as themselves instead of instructions to the compiler.
<code>string filePath = @"C:\test\projects"</code>

### 🎎 Raw string literals

Raw string literals are convenient for entering any arbitrary text without needing to escape the contents. They make it easy to define literals containing other languages like `XML`, `HTML`, or `JSON`.

```c#
string xml = """
             <person age="50">
               <first_name>Mark</first_name>
             </person>
             """; 
```

You can also use **raw interpolated string literals** : 
```c#
var person = new { FirstName = "Alice", Age = 5
 string json = $$"""
              {
                "first_name": "{{person.FirstNa
                "age": {{person.Age}},
                "calculation": "{{{ 1 + 2 }}}"
              }
              """;
 Console.WriteLine(json); 
 ```

 # Numbers 

> You can use `0b_number` to write a number in binary.
> You can use `0x_number` to write a number in hexadecimal.
> You can use `_` as digit seperator.

> In C# the special type named object can store any type of data.

Suffixes for numbers :
* **L**: Compiler infers long
* **M**: Compiler infers decimal
* **D**: Compiler infers double
* **F**: Compiler infers float

### 🙏 Null Forgiving operator `!`

It tells the compiler that it won't return null, but you need to ensure it.

### 🧲 Switch expressions for reference types 

```c#
message = animal switch
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
}; 
```

### Foreach :

The `foreach` statement can be used with any type that implements the following pattern:

- The type must have a `GetEnumerator` method that returns an enumerator object.
- The enumerator object must have:
    - A `Current` property, which provides access to the current element in the collection.
    - A `MoveNext` method, which advances to the next element and returns `true` if there are more elements, or `false` if the end of the collection has been reached.

This allows `foreach` to iterate over arrays, collections, and any custom types that follow this pattern.


### Casting :

**Implicit casting** happens automatically, and it is safe, meanwhile **explicit  casting** must be performed manually because it may lose information.

## 🧪 Unit testing

**Unit testing** is a practice where you test a small unit before they are integrated together or seen by user acceptance testers. The principle where you create the unit tests before you write the code is called **Test-Driven Development (TDD)**. 

**Types of testing :**

- **Unit** : Tests the smallest unit of code, typically a method or function. Unit testing is performed on a unit of code isolated from its dependencies by mocking them if needed. Each unit should have multiple tests: some with typical inputs and expected outputs, some with extreme input values to test boundaries, and some with
deliberately wrong inputs to test exception handling.
- **Integration** : Tests if the smaller units and larger components work together as a single piece of software. Sometimes involves integrating with external components for which you do not have source code.
- **End to end testing(E2E)** : End-to-end testing is a process that tests the entire application flow—from start to finish—simulating real user scenarios to ensure all parts of the system work together correctly.

> A **class library** is a package of code that can be distributed and referenced by other .NET applications.

## Writing unit tests:

**A well-written unit test will have three parts:**
* **Arrange** : This part will declare and instantiate variables for input and output.
* **Act** : This part will execute the unit that you are testing. In our case, that means calling the method that we want to test.
* **Assert** : This part will make one or more assertions about the output. An assertion is a belief that, if not true, indicates a failed test. For example, when adding 2 and 2, we would expect the result to be 4

### How to throw errors

Instead of using an if and throwing an exception you can just the static methods of 
``ArgumentException,  ArgumentOutOfRangeException, ArgumentNullException`` static classes. For example :
```c#
ArgumentException.ThrowIfNullOrWhiteSpace(parameter, paramName);
```

### Testing throwed exceptions:

You can test a method that throws an exception :

```c#
[Fact]
public void ProfileRepository_GetSettingsForUserIDWithInvalidArguments_ThrowsArgumentException()
{
    //arrange
    ProfileRepository profiles = new ProfileRepository();
    //act
    Action act = () => profiles.GetSettingsForUserID("");
    //assert
    ArgumentException exception = Assert.Throws<ArgumentException>(act);
    //The thrown exception can be used for even more detailed assertions.
    Assert.Equal("expected error message here", exception.Message);
}
```

## .NET Components

- **Language Compilers** : These turn your source code into **intermediate language (IL)** code stored in assemblies. The compiler is **Roslyn**.
- **Common Language Runtime(CLR)** : This runtime loads assemblies, compiles the IL code stored in them into native code instructions for your computer’s CPU, and executes the code within an environment that manages resources, such as threads and memory.
- **Base Class Libraries** : These are prebuilt assemblies of types packaged and distributed using NuGet to perform common tasks when building applications. 

> An **assembly** is where a type is stored in the filesystem. Assemblies are a mechanism for deploying code. For example, the System.Data.dll assembly contains types to manage data. To use types in other assemblies, they must be referenced. Assemblies can be static (pre-created) or dynamic (generated at runtime). Assemblies are distributed as NuGet packages, which are files that are downloadable from public online feeds and can contain multiple assemblies and other resources.

If an assembly is compiled as a class library and provides types for other assemblies to use, then it has the file extension .dll (dynamic link library), and it cannot be executed standalone. Likewise, if an assembly is compiled as an application, then it has the file extension .exe (executable) and can be executed standalone.

> By default .net applications have a dependency in the .NET SDK.

## .NET CLI

When you install the .NET SDK, it includes a command-line interface (CLI) named dotnet.

| Command | Description |
|---------|-------------|
| `dotnet new sln` | Create a new solution in the current folder, you can specify the `-o` to name it|
| `dotnet new typeofproject` | Creates a new project, you can the `-o` option to name it |
| `dotnet sln add projectnaem` | Add a project to the solution |
| `dotnet add package packagename` | Add a new nuget package |
| `dotnet new gitignore` | Create a .gitignore file with all the removed files |

| Commmand | Description |
|----------|-------------|
| `dotnet help` | This shows the command-line help.|
| `dotnet new` | This creates a new .NET project or file |
| `dotnet tool` | This installs or manages tools that extend the .NET experience |
| `dotnet restore` | This downloads dependencies for the project, e.x.g: nuget packages |
| `dotnet build` | This builds, aka compiles, a .NET project |
| `dotnet clean` | This removes the temporary outputs from a build |
| `dotnet test` | This builds and then runs unit tests for the project. |
| `dotnet run` | This builds and then runs the project. |
| `dotnet pack` | This creates a NuGet package for the project. |
| `dotnet publish` | This builds and then publishes the project, either with dependencies or as a self-contained application. In .NET 7 and earlier, this published the Debug configuration by default. In .NET 8 and later, it now publishes the Release configuration by default |
| `dotnet add` | This adds a reference to a package or class library to the project e.xg : a nuget package. |
| `dotnet remove` | This removes a reference to a package or class library from the project |
| `dotnet list` | This lists the package or class library references for the project |
| `dotnet package search` | This allows you to search one or more package sources for packages that match a search term |

## Regular Expressions

- The `@` symbol character switches off the ability to use escape characters in the string. 
- The `\d` means digit. e.x.g: 
```c# 
Regex x = new (@"\d"); x.check(input); // this checks the input if it has a digit inside, not if it is a digit , for example : input = jsd123 this is correct.
```
- The `^` symbol indicates the start of the input.
- The `$` symbol indicates the end of the input.
```c#
Regex ageChecker = new(@"^\d$"); // checks if the input starts and end with a digit
```

| Symbol | Meaning|
|--------|--------|
|`^` | Start of the input |
| `\d` | A single digit |
| `\s` | Whitespace |
| `\w` | Word characters |
| `[A-Za-z0-9]` | Range of characters |
| `[aeiou]` | Set of characters |
| `.` | Any single character |
| `$` | End of the input |
| `\D` | A single non digit |
| `\S` | A non whitespace |
| `\W` | Non word characters|
| `\^` | caret(^) character|
| `[^aeiou]` | Not in a set of characters |
| `\.` | A dot . character |

### Aditional regular expressions that affect previous symbols

| Symbol | Meaning |
|--------|---------|
|`+` | One or more |
|`{3}` | Exactly three |
|`{3, }` | At least three |
|`?` |  One or none |
|`{3, 5}` | Three to five |
|`{, 3}` | Up to three |
| `(x|y)` | Can have x or y|

### Exampes of regular expressions 

| Expression | Meaning |
|------------|---------|
| `\d` | A single digit somewhere in the input |
| `a` | The character “a” somewhere in the input |
| `Bob` | The word “Bob” somewhere in the input |
| `^Bob` | The word “Bob” at the start of the input |
| `Bob$` | The word “Bob” at the end of the input |
| `^\d{2}$` |  Exactly two digits |
| `^[0-9]{2}$` |  Exactly two digits |
| `[A-Z]{4,}$` | At least four uppercase English letters in the ASCII character set only |
| `[A-Za-z]{4,}$` | At least four upper or lowercase English letters in the ASCII character set only |
| `^[A-Z]{2}\d{3}$` |  Two uppercase English letters in the ASCII character set and three digits only |
| `^[A-Zaz\u00c0\u017e]+$` | At least one uppercase or lowercase English letter in the ASCII character set or European letters in the Unicode character set |
| `^d.g$` | The letter d, then any character, and then the letter g, so it would match both single character between the dig and dog or any d and g. |
| `^d\.g$` | The letter d, then a dot ., and then the letter g, so it would match d.g only |

**You can test the regular expressions at this website : <a href="https://regex101.com/">https://regex101.com/**

# 🔷 Reflection 

Reflection enables you to analyze, inspect, and interact with the metadata of types, objects, and assemblies during runtime.

```c#
using System.Reflection; // the namespace you need to import to use reflection
```

**All types in C# derive from the System.Object class, which has four methods directly connected to reflection.**

1. `GetType()`: Gets the `Type` of the current instance.
2. `MemberwiseClone()`: Creates a shallow copy of the current object.
3. `GetHashCode()`: Generates a hashcode for the current object.
4. `ToString()`: Returns a string representation of the current object.

🔸 The most critical reflection method here is `GetType()`.
```c#
int someNumber = 42;
Type numberType = someNumber.GetType();
Console.WriteLine(numberType.FullName); // System.Int32
```
> By using `GetType()` on the someNumber variable, we can get the `Type` object associated with it `(System.Int32)`, providing a gateway to further reflection possibilities.

### 🔴 Get Method Name and Class Information

To extract or manipulate metadata from a Type object, use the properties and methods provided by the `Type` class.

```c#
// Using typeof keyword
Type exampleType = typeof(String);
Console.WriteLine(exampleType.FullName); // System.String

// Get properties & methods from Type
PropertyInfo[] properties = exampleType.GetProperties();
MethodInfo[] methods = exampleType.GetMethods();

// Display property names
foreach (PropertyInfo prop in properties)
{
    Console.WriteLine(prop.Name);
}

// Get the method name in C#
foreach (MethodInfo method in methods)
{
    Console.WriteLine(method.Name);
}
```
### 🟠 Get Assembly Details in C#

To load an assembly and extract its metadata, you can use the `Assembly` class and its various methods.

```c#
// Get the current assembly
Assembly currentAssembly = Assembly.GetExecutingAssembly();

// Get the assembly details
Console.WriteLine($"FullName: {currentAssembly.FullName}");
Console.WriteLine($"Location: {currentAssembly.Location}");

// Getypes from assembly
Type[] assemblyTypes = currentAssembly.GetTypes();
foreach (Type type in assemblyTypes)
{
    Console.WriteLine(type.FullName);
}
```
### 🟡 Create Instance of Class Dynamically

Creating instances of objects during runtime can be an essential part of reflection. To create an instance of a class without knowing its type at compile-time, you can use the `Activator.CreateInstance()` method.
```c#
Type exampleType = typeof(List<int>);
object exampleInstance = Activator.CreateInstance(exampleType);
```

> The `Activator` class plays a crucial role in reflection when you need to instantiate an object for an unknown type at compile-time. It provides methods to create types of objects locally or remotely, or obtain references to existing remote objects. You can create instances of objects with specific constructor arguments, in a different application domain, or with specific activation attributes – all thanks to Activator’s methods.

### 🟢 Invoking Methods Dynamically

```c#
public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }
}

// Get Type of Calculator class
Type calculatorType = typeof(Calculator);

// Create an instance of Calculator
object calculatorInstance = Activator.CreateInstance(calculatorType);

// Get the Add method
MethodInfo addMethod = calculatorType.GetMethod("Add");

// Invoke the Add method dynamically
object result = addMethod.Invoke(calculatorInstance, new object[] { 10, 20 });
Console.WriteLine($"10 + 20 = {result}"); // 10 + 20 = 30
```

In this example, we have a Calculator class with an Add method. We create an instance of the Calculator using `Activator.CreateInstance()`. Then, we get the Add method using `GetMethod("Add")`, and finally, we invoke the `Add` method dynamically, passing the required parameters and displaying the result on the console.

### 🔵 Add Property to Dynamic Object Using Reflection

```c#
using System.Dynamic;

// Create a dynamic object
dynamic expando = new ExpandoObject();

// Add properties using dynamic keyword
expando.FirstName = "John";
expando.LastName = "Doe";

// Use PropertyInfo to add properties by reflection
Type expandoType = expando.GetType();
PropertyInfo ageProperty = expandoType.GetProperty("Age");
if (ageProperty == null)
{
    IDictionary<string, object> expandoDict = (IDictionary<string, object>)expando;
    expandoDict["Age"] = 30;
}

Console.WriteLine($"{expando.FirstName} {expando.LastName}, {expando.Age} years old");
```

In this example, we demonstrate how to add property to a dynamic object using reflection. We create a dynamic object using ExpandoObject and add properties using the dynamic keyword. For reflection usage, we get the ExpandoObject type, check if the “Age” property exists, and add it to the dynamic object if it doesn’t exist already. Finally, we display the properties on the console.

### 🟣 Loading Assemblies and Types

```c#
// Load an assembly (replace with actual assembly file)
Assembly externalAssembly = Assembly.LoadFile(@"C:\path\to\your\assembly.dll");

// Get all the types in the assembly
Type[] assemblyTypes = externalAssembly.GetTypes();

// Find a specific type by its name
Type targetType = assemblyTypes.FirstOrDefault(t => t.Name == "TargetTypeName");

// Create an instance of the targetType (if found)
if (targetType != null)
{
    object targetInstance = Activator.CreateInstance(targetType);
}
```
In this example, we load an external assembly from a file path (replace with an actual assembly file path) using Assembly.LoadFile(). Afterward, we retrieve all types within the assembly, find a specific type by its name using LINQ FirstOrDefault(), and then create an instance of the target type using Activator.CreateInstance().

## 🟥 Advanced C# Reflection Techniques

**Custom Attributes and Metadata**

Attributes are nothing but metadata applied to programs. They allow you to add extra information to types, members or assemblies that can later be queried, validated, or manipulated through reflection.
```c#
// Custom attribute definition
public class MyCustomAttribute : Attribute
{
    public string Description { get; }

    public MyCustomAttribute(string description)
    {
        Description = description;
    }
}

[MyCustomAttribute("This is a custom attribute applied to a class.")]
public class ExampleClass
{
    // ...
}

// Get the custom attribute from ExampleClass
Type exampleType = typeof(ExampleClass);
object[] attributes = exampleType.GetCustomAttributes(typeof(MyCustomAttribute), false);
if (attributes.Length > 0)
{
    MyCustomAttribute customAttribute = (MyCustomAttribute)attributes[0];
    Console.WriteLine($"Custom Attribute: {customAttribute.Description}");
}
```
In this example, we create a `MyCustomAttribute` class inheriting from the `Attribute` class. We then apply this custom attribute to an `ExampleClass` and later query it using the `GetCustomAttributes()` method. Once retrieved, we cast the attribute to its specific type and access its properties.

### 🟤 Using Reflection in C# to Generate Code

You can inspect types, objects, or assemblies, and based on their metadata, generate code snippets or whole classes/structures during runtime.
```c#
public class Customer
{
    public string FirstName { get; set; }
    public int BirthYear { get; set; }
}

public static void GenerateObjectInitializer(Type targetType)
{
    StringBuilder builder = new StringBuilder($"new {targetType.Name}\n{{\n");
    PropertyInfo[] properties = targetType.GetProperties();

    foreach (PropertyInfo property in properties)
    {
        builder.AppendLine($"{property.Name} = default({property.PropertyType.Name}),");
    }

    builder.AppendLine("};");
    string generatedCode = builder.ToString();
    Console.WriteLine(generatedCode);
}

// Call the GenerateObjectInitializer method
GenerateObjectInitializer(typeof(Customer));

// Output:
// new Customer
// {
//     FirstName = default(String),
//     BirthYear = default(Int32),
// };
```

The `GenerateObjectInitializer()` method takes a `Type` parameter and generates the corresponding object initializer code for that type. We then call this method, passing `typeof(Customer)` in, and see the generated code printed on the console.

Key aspects when using reflection for code generation :                                                                                              
- **Performance**:  Reflection can be slower compared to conventional coding practices. Excessive usage or relentless iteration may lead to performance bottlenecks. Optimize your code and use caching whenever possible.
- **Security**: Reflection may expose private members, providing inappropriate access, or expose sensitive information.

  

  
