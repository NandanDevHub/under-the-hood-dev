# C# Programming – Basics Level 2

### ✅ 1. What is a **variable** in C#?

**Answer:**  
A **variable** is a **named memory location** used to store data temporarily during the execution of a program.

It is created **inside a method or block** and used only **within that scope**.

---

**Example:**
```csharp
void Greet()
{
    string name = "Nandan"; // variable
    Console.WriteLine("Hello " + name);
}
```

- `name` is a **local variable**
- It **lives only while the method is running**
- It gets stored on the **stack** (for value types) or points to the heap (for reference types)

---

**Analogy:**  
A variable is like a **whiteboard** you write on during a meeting. Once the meeting is over (method ends), the whiteboard is wiped clean.

---

### ✅ 2. What is a **parameter** in C#?

**Answer:**  
A **parameter** is like a **variable** that’s used to **receive a value from the caller** when a method is invoked.

It's defined inside the method **signature**.

---

**Example:**
```csharp
void Greet(string name) // 'name' is a parameter
{
    Console.WriteLine("Hi " + name);
}

Greet("Nandan");  // "Nandan" is the argument
```

- A **parameter** is like a **placeholder**
- The **value passed in** is called an **argument**
- Parameters exist **only during method execution**

---

**Analogy:**  
Think of parameters like **airport boarding passes**. Each flight (method) has a slot for your name (parameter), and when you check in (call the method), you fill it with your name (argument).

---

### ✅ 3. What is a **field** in C#?

**Answer:**  
A **field** is a **variable declared inside a class** but **outside any method**.

It belongs to the **object** (if non-static) or to the **class itself** (if static).

---

**Example:**
```csharp
class Person
{
    public string name;  // field

    public void Introduce()
    {
        Console.WriteLine("My name is " + name);
    }
}
```

- `name` here is a **field** of the class `Person`
- It lives **as long as the object exists**
- Stored on the **heap** (because objects are reference types)

---

**Key difference from variable:**
- Variables = local to methods (short-lived)
- Fields = part of the class or object (longer-lived)

---

**Analogy:**  
A field is like a **permanent tag** attached to every object — like a name tag on a backpack. Variables are like **stickers on a notepad** used only during a session.

---

### 🧠 Summary Table

| Term      | Where it's declared     | Lives how long?        | Belongs to?            |
|-----------|--------------------------|-------------------------|-------------------------|
| Variable  | Inside method/block       | Until method ends       | Method                  |
| Parameter | In method signature       | Until method ends       | Method call             |
| Field     | In class (outside method) | As long as object lives | Object or class (static)|

---

### ✅ 4. What is a **method** in C#? Is it the same as a function?

**Answer:**  
In C#, a **method** is a **named block of code** that performs a task.  
It can take inputs (parameters) and return a result.

---

**Example:**
```csharp
int Add(int a, int b)
{
    return a + b;
}
```

---

✅ **Is it same as a function?**  
Yes — but in C#, we usually call them **methods** because they belong to a **class**.  
In other languages like Python or JavaScript, **functions can exist independently**.  
In C#, **every method must belong to a class or struct**.

---

**Analogy:**  
Think of a method like a **machine in a factory**. You give it input (parameters), it processes, and gives you an output (return value).

---

### ✅ 5. What is a **member** in C#?

**Answer:**  
A **member** is **anything defined inside a class or struct**.  
It includes:
- **Fields**
- **Methods**
- **Properties**
- **Events**
- **Constructors**
- **Indexers**, etc.

---

**Example:**
```csharp
class Car
{
    // Members:
    public string model;         // Field
    public void Drive() { }      // Method
    public int Speed { get; set; } // Property
}
```

---

**Why this matters:**  
When people say:  
> "That class has 3 members."  
They mean it has 3 things inside it — which could be **methods, fields, or properties**.

---

### ✅ 6. What is the difference between a **property** and a **field**?

| Feature         | Field                          | Property                        |
|-----------------|-------------------------------|----------------------------------|
| What is it?     | A direct variable              | A method-like wrapper over a field  
| Access control  | Public/private directly        | Uses `get`/`set` accessors      |
| Purpose         | Stores data                    | Controls how data is accessed   |
| Encapsulation   | Weak                           | Strong                          |
| Syntax          | `public int age;`              | `public int Age { get; set; }`  |

---

**Example with a field:**
```csharp
public int age; // Anyone can modify freely
```

---

**Example with a property:**
```csharp
private int age;  // hidden field

public int Age    // controlled access
{
    get { return age; }
    set 
    {
        if (value >= 0)
            age = value;
    }
}
```

---

**Why use a property instead of a field?**
- To **validate** or **control** the value
- To later **change internal logic** without changing external code
- Properties are preferred in real-world C# apps

---

**Analogy:**  
A **field** is like a raw storage box anyone can open.  
A **property** is like a **vending machine** — you press a button (get/set), and it controls access safely.

---

### ✅ 7. What is a **class** in C#?

**Answer:**  
A **class** is a **blueprint or template** used to create objects.

It defines:
- **What data** an object can hold (fields/properties)
- **What actions** it can perform (methods)

But a class **by itself does nothing** — it must be used to **create an object**.

---

**Example:**
```csharp
class Person
{
    public string Name;
    public void Greet()
    {
        Console.WriteLine("Hi " + Name);
    }
}
```

---

**Analogy:**  
A class is like a **blueprint of a house** — it tells you how the house should look, but it’s not a house yet.

---

### ✅ 8. What is an **object** or **instance**?

**Answer:**  
An **object** is a **real thing created using a class**.  
It has its **own copy of fields** and can use the methods defined by the class.

Creating an object = creating an **instance of a class**.

---

**Example:**
```csharp
Person p = new Person(); // p is an object (instance)
p.Name = "Nandan";
p.Greet();               // Output: Hi Nandan
```

- `p` is an object of type `Person`
- It holds its own data (`Name`) and can act (`Greet()`)

---

**Analogy:**  
If a class is a **cookie cutter**, then the object is the **actual cookie** made from it.

---

### ✅ 9. What is the difference between **class** and **object**?

| Concept   | Class                                  | Object (Instance)                    |
|-----------|-----------------------------------------|--------------------------------------|
| Role      | Blueprint                              | Real-world item based on blueprint   |
| Memory    | No memory until object is created      | Has memory (heap) when created       |
| Usage     | Defines structure                      | Holds data and behavior              |
| Example   | `Person`                               | `Person p = new Person();`           |

---

### ✅ 10. What does **static** mean in C#?

**Answer:**  
A `static` member (field, method, or class) **belongs to the class itself**, not to any object.

- You can call it **without creating an object**
- There’s only **one copy** of it shared across everything

---

**Example:**
```csharp
class MathUtils
{
    public static int Square(int n)
    {
        return n * n;
    }
}

int result = MathUtils.Square(5);  // No object needed
```

---

**Use static when:**
- The value or method is **common** to all objects
- You don’t need to store per-object data

---

**Analogy:**  
A `static` method is like a **public calculator on a wall** — anyone can walk up and use it, no one “owns” it.


### ✅ 11. What is a **type** in C#?

**Answer:**  
A **type** defines what kind of data a variable can hold and what operations can be performed on it.

In C#, everything has a **type**:
- `int`, `string`, `bool` → primitive types
- `List<string>`, `DateTime`, `Person` → complex types
- `void` → means no return value

---

**Example:**
```csharp
int age = 25;           // type is int
string name = "Nina";   // type is string
Person p = new Person();// type is Person
```

Even when you create your own class (`Person`), you're creating a **new type**.

---

**Analogy:**  
Think of types as **labels on boxes**.  
A box labeled `int` can only carry numbers. A box labeled `Person` can carry people-like information.

---

### ✅ 12. What is a **reference** in C#?

**Answer:**  
A **reference** is like a **pointer or address** that tells the program where the actual object is stored in memory (usually on the heap).

When you assign an object to a variable, you're assigning a **reference**, not the actual object.

---

**Example:**
```csharp
Person p1 = new Person();
Person p2 = p1; // both point to the same object

p2.Name = "Amit";
Console.WriteLine(p1.Name); // Output: Amit
```

- `p1` and `p2` **both refer to the same object**
- Changing one reflects in the other

---

✅ This only applies to **reference types** (like classes).  
For **value types** (like `int`, `bool`, `struct`), the value itself is copied.

---

**Analogy:**  
A reference is like a **home address**. If two people share the same address, they're both pointing to the **same place**.

---

### ✅ 13. So, what’s the difference between a **type**, a **reference**, and an **instance**?

| Term       | Means...                                 | Example                              |
|------------|-------------------------------------------|--------------------------------------|
| Type       | Blueprint/definition                      | `Person`, `int`, `string`            |
| Reference  | A pointer to an instance in memory        | `p1`, `p2` (both pointing to same `Person`) |
| Instance   | The actual object in memory               | Created using `new Person()`         |

---

**Example to tie them together:**
```csharp
Person p1 = new Person();  // Person = type, p1 = reference, new Person() = instance
```

### ✅ 14. What is the **`this`** keyword in C#?

**Answer:**  
`this` refers to the **current instance of the class** — the object on which a method or property is being called.

It helps:
- Distinguish between class fields and parameters
- Refer to the current object from within itself

---

**Example:**
```csharp
class Person
{
    private string name;

    public Person(string name)
    {
        this.name = name;  // 'this.name' = field, 'name' = parameter
    }

    public void Introduce()
    {
        Console.WriteLine("Hi, I'm " + this.name);
    }
}
```

---

**Analogy:**  
`this` is like saying "me" inside a WhatsApp message — it means “this person sending the message”.

---

### ✅ 15. What does the `new` keyword do?

**Answer:**  
`new` is used to **create a new instance** (object) of a class, struct, or array.

It tells the runtime to:
1. Allocate memory on the **heap** (for reference types)
2. Call the class’s **constructor**
3. Return a **reference** to that memory

---

**Example:**
```csharp
Person p = new Person("Nandan");  // creates a new object
```

---

**Why `new` is important:**  
- Without it, you just have a reference pointing to `null`
- With it, you actually create an object

---

**Analogy:**  
`new` is like swiping your card to book a cab. You get a **fresh ride**, not someone else's.

---

### ✅ 16. What is `null`?

**Answer:**  
`null` means “**no object**” or “**no value assigned**”.

It applies only to **reference types** — it means the reference doesn’t point to anything yet.

---

**Example:**
```csharp
Person p = null;

if (p == null)
{
    Console.WriteLine("No one is here yet.");
}
```

---

**Danger of null:**  
If you try to use a `null` reference, you get a **NullReferenceException**.

```csharp
p.Name = "John"; // ❌ error if p is null
```

✅ Always check for `null` before using an object — or use **null-safe operators** (`?.` or `??` in modern C#).

---

**Analogy:**  
`null` is like having **someone’s name on a list**, but they never showed up — their chair is empty.

---

### ✅ 17. What is the difference between **compile time** and **runtime**?

| Phase         | Happens When?           | Checks For                        | Example Issue                     |
|---------------|--------------------------|------------------------------------|-----------------------------------|
| Compile Time  | Before program runs      | Syntax, type correctness           | Missing semicolon, type mismatch |
| Runtime       | While program is running | Logic errors, user input issues    | Divide by 0, file not found      |

---

**Compile Time Errors:**
```csharp
int x = "hello"; // ❌ Compile-time error: Type mismatch
```

**Runtime Errors:**
```csharp
int x = 10 / 0;  // ❌ Runtime error: DivideByZeroException
```

---

**Why this matters:**  
You fix **compile-time errors** before the program runs.  
You must handle **runtime errors** gracefully using **try-catch**, validation, etc.

---

**Analogy:**  
Compile time is like **checking your luggage before the flight** — if it’s overweight, you’re stopped early.  
Runtime is like the **flight itself** — turbulence may still happen.

---

### ✅ 18. What does `void` mean in C#?

**Answer:**  
`void` means the method **does not return any value**.  
You call it just to **perform an action**, not to get a result back.

---

**Example:**
```csharp
void SayHello()
{
    Console.WriteLine("Hello!");
}
```

- This method prints something but doesn’t return anything.
- If you try to use `var result = SayHello();` → ❌ Error!

---

**Analogy:**  
A `void` method is like **sending a message** to someone. You don’t expect a reply — you just inform.

---

### ✅ 19. What is a return type and how does it differ from `void`?

**Answer:**  
A method’s **return type** tells you **what kind of value it gives back**.

If it’s not `void`, it **must use a `return` statement**.

---

**Examples:**

✅ `int Add(int a, int b)` returns an integer:
```csharp
int Add(int a, int b)
{
    return a + b;
}
```

✅ `string GetName()` returns a string:
```csharp
string GetName()
{
    return "Nandan";
}
```

---

**Why return values matter:**
- You can **use them in expressions**
- They allow your program to **compute and pass information around**

---

**Analogy:**  
A method with a return type is like **asking someone a question**. You wait for a reply, and use it.

---

### ✅ 20. What is **method overloading**?

**Answer:**  
**Method Overloading** allows you to define **multiple methods with the same name** but **different parameters**.

C# decides which one to call based on:
- Number of parameters
- Type of parameters
- Order of parameters

---

**Example:**
```csharp
void Print() { Console.WriteLine("Nothing"); }

void Print(string message) { Console.WriteLine(message); }

void Print(int number) { Console.WriteLine(number); }
```

---

✅ All these are valid because their **signatures differ**

---

**Why it's useful:**
- It helps create **intuitive APIs**
- Keeps methods **semantically grouped** under one name

---

**Analogy:**  
It’s like pressing different **buttons on a vending machine**. Each button is called “Select” but works differently based on the snack code you type.

---

### ✅ 21. What are **access modifiers** and why do we need them?

**Answer:**  
**Access modifiers** control **who can see or use** a member (like a method or field).

They enforce **encapsulation and safety** in your code.

---

| Modifier    | Who can access?                                 |
|-------------|--------------------------------------------------|
| `public`    | Anyone, anywhere                                 |
| `private`   | Only inside the same class                       |
| `protected` | Inside the class and its child (derived) classes |
| `internal`  | Only within the same assembly/project            |
| `protected internal` | Derived classes in same assembly        |
| `private protected`  | Only in derived classes in the same class |

---

**Examples:**
```csharp
public int age;        // globally accessible
private string name;   // accessible only in the class
protected void Talk()  // accessible in subclasses
```

---

**Why care about this?**
- To **hide implementation details**
- To **prevent misuse** by other parts of your program
- To support **modularity** and **security**

---

**Analogy:**  
Think of access modifiers as **door locks**:
- `public` = open gate
- `private` = locked drawer
- `protected` = secret family box
- `internal` = office-only access

---

### ✅ 22. What is the difference between `const` and `readonly`?

| Feature         | `const`                               | `readonly`                              |
|----------------|----------------------------------------|------------------------------------------|
| Value Set       | At compile-time only                  | At runtime (in constructor or declaration) |
| Modifiable?     | ❌ Cannot change ever                 | ✅ Can set once in constructor           |
| Type            | Always static implicitly              | Can be instance-level                   |
| Use Case        | Fixed values like Pi, maxSize         | Configurable values set at creation     |

---

**Example:**
```csharp
const double Pi = 3.14159;
readonly int userId;

public User(int id)
{
    userId = id; // valid only in constructor
}
```

---

**Analogy:**  
- `const` is like a **printed label** — it can never change  
- `readonly` is like a **whiteboard** that you write on **once** and never touch again

---

### ✅ 23. What’s the difference between `static` and instance members?

| Feature            | `static`                                 | instance (non-static)                  |
|--------------------|-------------------------------------------|----------------------------------------|
| Belongs to         | The class itself                          | An object created from the class       |
| Memory             | One copy shared by all                    | Each object gets its own copy          |
| Access             | `ClassName.Member`                        | `object.Member`                        |
| Use Case           | Utility methods, shared config            | Per-user data, behavior per object     |

---

**Example:**
```csharp
class Counter
{
    public static int count = 0; // shared
    public string name;          // per-object
}
```

```csharp
Counter.count++;       // shared across all
Counter c1 = new Counter();
c1.name = "One";        // only for c1
```

---

**Analogy:**  
- `static` is like a **shared document** on Google Drive  
- `instance` is like **your personal copy**

---

### ✅ 24. What is the difference between class-level and method-level declarations?

| Scope         | Declared Inside           | Lives Until               | Accessed By                  |
|---------------|---------------------------|---------------------------|------------------------------|
| Method-level  | Inside a method           | Method ends               | Only inside that method      |
| Class-level   | Inside a class (outside methods) | Object/class lives      | Across multiple methods      |

---

**Example:**
```csharp
class Example
{
    int number = 10;   // class-level field

    void Show()
    {
        int temp = 5;  // method-level variable
        Console.WriteLine(temp + number);
    }
}
```

- `temp` exists only while `Show()` is running  
- `number` exists as long as the object exists

---

**Analogy:**  
- Class-level = **permanent record** in a file  
- Method-level = **sticky note** during a task

---

### ✅ 25. What is a **namespace** in C#?

**Answer:**  
A **namespace** is like a **folder** for your classes. It helps organize code and avoid name conflicts.

---

**Why use namespaces?**
- Prevents clashes when different libraries use the same class names.
- Helps organize code logically (by feature, layer, module, etc.).

---

**Example:**
```csharp
namespace SchoolApp.Teachers
{
    class Teacher { }
}

namespace SchoolApp.Students
{
    class Student { }
}
```

You can use:
```csharp
using SchoolApp.Students;
```

---

**Analogy:**  
Think of namespaces like **file directories**. You might have two files named `Notes.txt` in different folders — no conflict.

---

### ✅ 26. What is the `Main()` method in C#?

**Answer:**  
`Main()` is the **entry point** of a C# program. It’s the first method that runs when your app starts.

---

**Example:**
```csharp
class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Hello, World!");
    }
}
```

- It can be `void` or return `int`
- Can have parameters like `string[] args` to accept command-line input

---

✅ **Important Notes:**
- There can only be **one `Main()` method** as entry point.
- In newer C# versions (like C# 9+), **top-level statements** let you skip writing `Main()` explicitly.

---

**Analogy:**  
It’s like the **starting gate** of a race — your program enters through here.

---

### ✅ 27. What’s the difference between a **Solution**, **Project**, **DLL**, and **EXE**?

| Term       | Meaning                                                             |
|------------|---------------------------------------------------------------------|
| **Solution** | A container that holds multiple projects                          |
| **Project**  | A unit of code that compiles into an output (DLL or EXE)          |
| **DLL**      | Dynamic Link Library (shared code, not directly executable)       |
| **EXE**      | Executable file (runs as an application)                          |

---

**Example in Visual Studio:**
- Solution: `InventorySystem`
  - Project 1: `InventoryApp` → builds into `InventoryApp.exe`
  - Project 2: `InventoryLib` → builds into `InventoryLib.dll`

---

**Analogy:**
- **Solution** = folder containing multiple notebooks
- **Project** = a notebook
- **DLL** = a reference book used by others
- **EXE** = a standalone report you can run

---

### ✅ 28. What is the **compilation flow** in C#?

**Answer:**  
C# is a **compiled language**. Your code goes through several steps before it runs.

---

1. **C# code (.cs)**  
   ↓  
2. **C# Compiler (csc)** compiles it to  
   → **IL (Intermediate Language)**  
   ↓  
3. **CLR** uses **JIT (Just-In-Time)** to compile IL to  
   → **Machine Code**  
   ↓  
4. **Your CPU executes it**

---

**Visual Diagram:**
```
C# Code → IL → JIT → Machine Code → CPU runs it
```

---

**Why is this done?**
- IL makes .NET code **platform-independent**
- JIT compiles for **your machine's architecture** on the fly
- Ensures performance and portability

---

**Analogy:**  
It’s like writing in English → translating to a middle language → then converting to regional dialect before speaking.

### ✅ 29. What is the **CLI** (Common Language Infrastructure)?

**Answer:**  
CLI is a standard defined by Microsoft that says:

> “If you're making a language or runtime for the .NET ecosystem, follow **these rules** so everything works together.”

It defines things like:
- How code is compiled (to IL)
- How memory is managed
- How languages interoperate (C#, VB.NET, F#)

---

**Analogy:**  
Think of CLI as a **set of international rules** — any .NET language must follow them to work well in the same ecosystem.

---

### ✅ 30. What is the **CLR** (Common Language Runtime)?

**Answer:**  
The CLR is the **engine** that runs your .NET program.

It does:
- **Memory management** (allocates stack/heap)
- **Garbage collection**
- **Security checks**
- **JIT compilation**
- **Exception handling**

---

**Visual Flow:**
```
C# Code → IL → CLR → Machine Code → CPU
```

---

**Analogy:**  
CLR is like the **manager** at runtime — it handles resources, supervises memory, and translates code to machine-understandable form.

---

### ✅ 31. What is the **JIT** (Just-In-Time Compiler)?

**Answer:**  
JIT is part of the CLR. It **translates IL (Intermediate Language)** into **machine code**, just before the code runs.

- Makes execution platform-specific
- Runs *once per method* (unless optimized)
- Stores compiled output for faster reuse

---

**Types of JIT in .NET:**
- **Normal JIT**: Converts as needed (default)
- **Pre-JIT (Ngen)**: Converts everything ahead of time
- **Tiered JIT**: Adaptive and performance-tuned in .NET Core+

---

**Analogy:**  
JIT is like a **live translator** in a courtroom — interprets what’s said into a form the judge (CPU) can understand.

---

### ✅ 32. What are **CTS** and **CLS** in .NET?

| Term | Full Form                  | Meaning                                                                 |
|------|-----------------------------|-------------------------------------------------------------------------|
| CTS  | Common Type System         | Defines how **types** should behave across .NET languages               |
| CLS  | Common Language Specification | A **subset of CTS** that all .NET languages **must support**          |

---

**Example:**
- CTS supports `unsigned int` (`uint`), but CLS doesn't — so avoid `uint` if you want your code to work in **any .NET language**

---

**Why it matters:**
- Ensures **interoperability**
- Prevents language-specific confusion

---

**Analogy:**  
- CTS = full **dictionary** of types  
- CLS = shared **vocabulary** all speakers must use

---

### ✅ 33. What is the difference between **statement**, **expression**, and **block**?

| Term        | Meaning                                 | Example                              |
|-------------|-----------------------------------------|--------------------------------------|
| Expression  | Any piece of code that gives a value    | `5 + 3`, `"Hi".ToUpper()`, `a > b`   |
| Statement   | A complete action (often ends with `;`) | `int x = 5 + 3;`, `Console.WriteLine("Hi");` |
| Block       | Group of statements inside `{}`         | Used in methods, loops, `if`, etc.   |

---

**Example:**
```csharp
int x = 5 + 3;  // statement with expression
if (x > 5)      // expression in condition
{
    Console.WriteLine(x); // block with a statement
}
```

---

**Analogy:**
- Expression = a **word**
- Statement = a **sentence**
- Block = a **paragraph**

---

### ✅ 34. What are the different types of **comments** in C#?

| Type         | Syntax                   | Usage                                 |
|--------------|--------------------------|----------------------------------------|
| Single-line  | `// comment`             | Brief notes or inline explanations    |
| Multi-line   | `/* comment */`          | Larger blocks of comments             |
| XML docs     | `/// <summary>...</summary>` | Used to generate documentation       |

---

**Example:**
```csharp
// This is a single-line comment

/* This is a
   multi-line comment */

/// <summary>
/// Says hello to the user
/// </summary>
void SayHello() { ... }
```

---

**Best practice:**
- Use meaningful comments only where needed  
- Don't explain *what*, explain *why* when it’s not obvious

---

### ✅ 35. What are `.cs` files, folders, and how is code organized in C# projects?

**Answer:**  
In a C# project:

- `.cs` files contain **C# source code**
- **Folders** help organize files logically (features, layers, etc.)
- A single `.cs` file may contain:
  - A class or struct
  - Enums or interfaces
  - `namespace` declaration
  - Method definitions

---

**Example Structure:**
```
/ProjectName
  └── Models/
        └── User.cs
  └── Services/
        └── EmailService.cs
  └── Program.cs
```

---

**Analogy:**  
- `.cs` files = pages of a book
- Folders = chapters or categories
- Whole project = one book (or app)

---

### ✅ 36. What happens when you **build** a C# project?

**Answer:**  
The build process transforms your `.cs` code into a **binary output** (DLL or EXE).

---

**Steps during build:**
1. All `.cs` files are **compiled** into **Intermediate Language (IL)**
2. The compiler checks for **errors** (syntax, types, etc.)
3. An output file (like `MyApp.dll` or `MyApp.exe`) is generated
4. Dependencies are also bundled

---

**Tool used:**  
- C# compiler: `csc.exe`
- In Visual Studio: the Build button automates it
- In CLI: `dotnet build`

---

**Output Types:**
- `Console App` → EXE
- `Class Library` → DLL

---

### ✅ 37. What is the difference between **compile-time errors** and **runtime errors**?

| Type            | Happens When?              | Caught By?         | Example                              |
|-----------------|----------------------------|--------------------|--------------------------------------|
| Compile-time    | When building the code      | Compiler           | Missing semicolon, wrong type        |
| Runtime         | When executing the program  | Runtime/CLR        | Divide by zero, file not found       |

---

**Compile-time error example:**
```csharp
int x = "hello";  // ❌ Type mismatch
```

**Runtime error example:**
```csharp
int y = 0;
int z = 10 / y;    // ❌ DivideByZeroException
```

---

**Why this matters:**
- Compile-time errors must be fixed before running the program
- Runtime errors must be handled using `try-catch`

---

### ✅ 38. What is the **build output folder** and why is it used?

**Answer:**  
When a C# project is built, the result is stored in the **`bin` folder** inside:

```
/bin/Debug/net6.0/
```

Here, you’ll find:
- The compiled `DLL` or `EXE`
- Config files
- Dependencies (.dll)

---

This folder is what gets **executed or published** for deployment.

---

### ✅ 39. What is the difference between `dotnet build` and `dotnet run`?

| Command         | What it does                                  |
|-----------------|-----------------------------------------------|
| `dotnet build`  | Compiles code and creates DLL/EXE (doesn’t run it) |
| `dotnet run`    | Builds **and then runs** the app              |

---

**Use cases:**
- Use `build` to check for errors or prepare binaries
- Use `run` during development/testing

---

Let me know when you’re ready to move to **Set 11** — which will be the **final wrap-up of Phase 0.5**, including:
- What is a solution explorer?
- What is the role of `.csproj`, `.sln`, `.dll`?
- Debug vs Release mode


### ✅ 40. What is the **Solution Explorer** in Visual Studio?

**Answer:**  
The **Solution Explorer** is a panel in Visual Studio that shows:

- The entire **solution structure**
- All **projects** inside the solution
- Project **files, folders, references**, and settings

---

**Why it’s useful:**
- Navigate between code files quickly
- Add or remove files/projects
- Manage references, properties, and NuGet packages

---

**Analogy:**  
It’s like a **table of contents** for your codebase, showing everything your app uses and includes.

---

### ✅ 41. What is the `.csproj` file in a C# project?

**Answer:**  
`.csproj` is an **XML configuration file** that defines the structure and settings for a **single C# project**.

---

**It contains:**
- Target framework (e.g., `net6.0`)
- Project references
- NuGet dependencies
- Build settings
- Output type (DLL/EXE)

---

**Example:**
```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net6.0</TargetFramework>
  </PropertyGroup>
</Project>
```

---

**Note:**  
Do **not edit manually** unless necessary — Visual Studio manages this.

---

### ✅ 42. What is the `.sln` file?

**Answer:**  
`.sln` stands for **Solution File** — it ties together **multiple projects** under one umbrella.

- Keeps track of project order
- Stores build configurations
- Opened by Visual Studio

---

**Analogy:**  
`.sln` is like a **playlist** of projects — Visual Studio reads it to know what all to load.

---

### ✅ 43. What is a `.dll` vs `.exe` file in output?

| File Type | Meaning                             | Use Case                               |
|-----------|--------------------------------------|----------------------------------------|
| `.exe`    | Executable file (runs an application) | Console or Windows app                 |
| `.dll`    | Dynamic Link Library (reusable code) | Shared libraries, utility functions    |

---

**Important Note:**
- A **class library** always builds into a `.dll`
- A **console app or web app** builds into an `.exe` (with other dependencies)

---

**Example:**
```bash
/bin/Debug/net6.0/
  - MyApp.exe     ← executable
  - MyApp.dll     ← main compiled code
  - Newtonsoft.Json.dll  ← external library
```

---

### ✅ 44. What is the difference between **Debug** and **Release** mode?

| Mode    | Purpose                        | Output Characteristics                       |
|---------|--------------------------------|----------------------------------------------|
| Debug   | Development and testing        | Includes debug info (symbols), slower, bigger |
| Release | Final published version        | Optimized, no debug info, faster              |

---

**When to use:**
- Use `Debug` when writing and testing code
- Use `Release` for production/publishing

---

**Command-Line:**
```bash
dotnet build -c Debug    # default
dotnet build -c Release  # optimized output
```

---

**Analogy:**
- `Debug` = **practice run with notes**
- `Release` = **final stage performance**

---

