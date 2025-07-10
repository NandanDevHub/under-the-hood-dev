# C# Programming – Basics Level 1

### 1. What happens when we compile a C# program?

**Answer:**  
When you write a C# program and click "Build" or "Run", several things happen behind the scenes — more than just "running code".

Here’s the step-by-step breakdown:

---

**Step 1: Compilation to IL (Intermediate Language)**  
- Your `.cs` files are passed to the **C# compiler (`csc`)**
- The compiler checks your code for **syntax errors**
- If all is good, it converts your code into something called **IL** (Intermediate Language)
- IL is **not machine code**, but a special format understood by the .NET runtime

---

**Step 2: IL is stored in an Assembly (.exe or .dll)**  
- The IL code is stored in a file — usually `.exe` or `.dll`
- This file also contains **metadata** (like type definitions, version, references)

---

**Step 3: CLR and JIT Compilation**  
- When you run the program, the **CLR (Common Language Runtime)** takes over
- The CLR uses **JIT (Just-In-Time)** compilation to convert IL → **native machine code**
- This native code is what actually runs on your processor

---

**Summary Flow:**
```
Your C# Code (.cs)
     ↓ compile
Intermediate Language (.exe/.dll)
     ↓ run with CLR
Machine Code (executed by CPU)
```

---

**Why does this two-step process exist?**
- It makes your code **cross-platform** (IL can run on any system with a CLR)
- It allows .NET to do **optimizations at runtime**
- It supports **security checks**, **memory management**, and **error handling** via CLR

---

**Analogy:**  
Imagine writing a recipe (C# code) in English.  
The compiler translates it into a universal kitchen language (IL).  
When a chef (JIT) receives it, they translate just the steps they need, in their local language (machine code), and then cook the dish (execute).

---

### 2. What is the CLR and why does C# depend on it?

**Answer:**  
The **Common Language Runtime (CLR)** is the **engine** that runs your C# code.

Think of it like a virtual machine (like JVM for Java) that handles all the tough work for you.

---

**The CLR is responsible for:**
- **Loading your program**
- **Compiling IL to machine code (JIT)**
- **Managing memory** (allocating and freeing up space)
- **Handling exceptions**
- **Running security checks**
- **Managing threads and execution flow**

---

**Why C# depends on it:**
- Because C# targets the .NET platform, and the CLR **is** the .NET runtime
- It provides a safe and managed environment
- Without it, your C# code would be nothing more than IL that the OS can’t directly understand

---

**Analogy:**  
The CLR is like the engine of a car — you write code (steer, accelerate), but the engine makes everything work safely, efficiently, and powerfully underneath.

---
### 3. What is Intermediate Language (IL) and why is it used?

**Answer:**  
**Intermediate Language (IL)** is the **low-level, platform-independent code** that your C# code gets compiled into before it's turned into actual machine code.

You might also see it called:
- **MSIL** (Microsoft Intermediate Language)
- **CIL** (Common Intermediate Language)

---

**Why use IL instead of directly compiling to machine code?**
- It allows your program to **run on any system** with a .NET runtime
- It enables the CLR to do **runtime optimizations**
- It helps with **security**, **portability**, and **cross-language support** (e.g., VB.NET and F# also compile to IL)

---

**Example:**
When you write:
```csharp
int x = 5;
```

IL might contain something like:
```
ldc.i4.5      // Load constant integer 5
stloc.0       // Store it in local variable 0
```

This is not machine code — it's IL, and the CLR understands and translates it at runtime.

---

**Analogy:**  
IL is like writing instructions in a universal script (like Latin).  
Each region (Windows, Linux, Mac) can read and interpret it using their local accents (machine code).

---

### 4. What is JIT compilation and how does it work in .NET?

**Answer:**  
**JIT (Just-In-Time)** compilation happens **at runtime**.  
It’s how the CLR translates IL → machine code **just before** the code is needed.

---

**How it works:**
1. Your IL `.exe` is loaded by the CLR
2. When a method is called for the first time, JIT translates **only that method** into machine code
3. That compiled machine code is cached and reused if the method is called again

---

**Advantages of JIT:**
- Only translates code that’s actually used
- Can optimize based on the **actual hardware**
- Keeps the IL file smaller than full native code

---

**Disadvantages:**
- Slight delay the first time a method runs
- Heavier load at runtime compared to ahead-of-time compiled programs

---

**Analogy:**  
Imagine having a recipe written in Latin.  
Instead of translating the entire book up front, you only translate the current page **just before cooking** — and reuse the translation next time.

---

**Bonus:**  
.NET also supports **AOT (Ahead-of-Time)** compilation in some cases (e.g., Blazor WebAssembly, .NET Native) to avoid JIT overhead.

---

### 5. What is the difference between Stack and Heap memory in C#?

**Answer:**  
C# uses **two main memory regions** during execution:

- **Stack**: Stores simple, short-lived values (like local variables, method calls)
- **Heap**: Stores larger, more complex data (like objects, arrays)

---

| Feature        | Stack                              | Heap                               |
|----------------|-------------------------------------|------------------------------------|
| Lifetime       | Short (per method call)             | Long (until no longer used)       |
| Speed          | Very fast                           | Slower                            |
| Managed by     | Automatically by compiler           | Managed by Garbage Collector      |
| Stores         | Value types, method frames          | Reference types, objects, arrays  |
| Size           | Small (fixed size)                  | Large (flexible size)             |

---

**Example:**
```csharp
int a = 5;                      // stored on the stack
Person p = new Person();        // 'p' is on stack, but Person object is on heap
```

In the above:
- `a` is stored directly in the stack
- `p` (the reference) is in the stack, but the actual `Person` object lives in the heap

---

**Why two types of memory?**
- Stack is optimized for speed and simplicity
- Heap allows flexible, long-lived, shared data — but needs more management

---

**Analogy:**
- Stack = Your desk workspace: quick access, small items, cleaned after every task
- Heap = A filing cabinet: large, organized storage — slower to access, but holds more

---

### 6. What happens to variables when a method is called?

**Answer:**  
Each time a method is called:
1. A **new frame** is pushed onto the **stack**
2. That frame holds the method’s **local variables** and **parameters**
3. When the method finishes, the frame is **popped off** the stack — variables are gone

---

**Example:**
```csharp
void Calculate()
{
    int x = 10; // stored in stack
}
```

When `Calculate()` is called:
- Stack allocates space for `x`
- When method ends, space is freed — `x` is gone

---

If inside that method you create an object:
```csharp
Person p = new Person();
```
- Stack holds `p` (the reference)
- Heap stores the actual `Person` object
- Even after the method ends, the object **may remain in heap** (if referenced elsewhere)

---

**Why is this important?**
Understanding this helps with:
- Performance tuning
- Debugging memory leaks
- Knowing what lives where (value vs reference types)

---

**Analogy:**
Calling a method is like opening a notebook for a task:
- You use a fresh page (stack frame)
- Write notes (variables)
- When done, you tear out the page (frame is cleared)

But if you created a sticky note and left it on your monitor (heap), it stays until removed manually (via garbage collection).

---

### 7. What is a value type and how does it behave in memory?

**Answer:**  
A **value type** holds the **actual data directly**.  
When you assign a value type to another variable, the data is **copied**.

---

**Common value types:**
- `int`, `double`, `bool`, `char`
- `struct` (user-defined)
- `enum`

---

**Example:**
```csharp
int a = 5;
int b = a;
b = 10;

Console.WriteLine(a); // Output: 5
```

Here, `b = a` copies the value of `a`. Changing `b` doesn’t affect `a`.

---

**Memory:**  
- Stored in the **stack**
- Each variable gets its **own copy**
- Very fast to access

---

**Analogy:**  
A value type is like giving someone a **photocopy** of a document. They can write on it, but your original remains unchanged.

---

### 8. What is a reference type and how is it different?

**Answer:**  
A **reference type** holds a **reference (memory address)** to the actual data stored in the **heap**.

When you assign one reference variable to another, both variables **point to the same object**.

---

**Common reference types:**
- `class` (like `string`, `Person`, `List<T>`)
- `interface`, `delegate`, `object`

---

**Example:**
```csharp
int[] x = { 1, 2, 3 };
int[] y = x;
y[0] = 99;

Console.WriteLine(x[0]); // Output: 99
```

Here, `y = x` means both point to the **same array in heap**. Changing one changes both.

---

**Memory:**
- The **reference** is on the **stack**
- The **actual object** is in the **heap**
- Multiple variables can point to the **same object**

---

**Analogy:**  
A reference type is like sharing a **link to a shared document**. If anyone edits the content, everyone sees the change.

---

**Summary Table:**

| Feature         | Value Type         | Reference Type       |
|------------------|---------------------|------------------------|
| Stored in         | Stack               | Stack (ref) + Heap (data) |
| Assignment        | Copies value        | Copies reference       |
| Examples          | `int`, `float`, `bool` | `class`, `string`, arrays |
| Behavior          | Independent copy    | Shared reference       |

---

### 9. What is boxing in C# and when does it happen?

**Answer:**  
**Boxing** is the process of **converting a value type into a reference type**, specifically into an `object`.

This happens when:
- A value type is assigned to an `object` variable
- A value type is passed into a method that expects an `object` parameter

---

**Example:**
```csharp
int num = 42;
object boxed = num;  // Boxing happens here
```

Here’s what really happens:
- `num` is copied from the stack
- That value is **wrapped in a heap-allocated object**
- `boxed` now holds a reference to that object in the heap

---

**Why does this exist?**
- Because in C#, everything derives from `object`
- Value types can’t behave like objects unless boxed

---

**Analogy:**  
Boxing is like putting a **gift (value)** into a **box (object)** so it can be handled like any other boxed item — but now it takes more space and time.

---

### 10. What is unboxing and what are its risks?

**Answer:**  
**Unboxing** is the process of **extracting a value type from an object**.

It’s the reverse of boxing.

---

**Example:**
```csharp
object boxed = 100;           // boxing
int number = (int)boxed;      // unboxing
```

---

**Rules of unboxing:**
- You must explicitly cast the object back to the correct value type
- If the cast is wrong, you get a **runtime error**

---

**Example of incorrect unboxing:**
```csharp
object boxed = 100;
double wrong = (double)boxed; // ❌ InvalidCastException
```

---

**Why unboxing is risky:**
- It involves casting
- It slows down performance
- It can cause runtime exceptions if not handled properly

---

**Analogy:**  
Unboxing is like opening a box and **expecting a book** inside — but if it turns out to be a brick, you get hurt (error).

---

**When to avoid boxing/unboxing:**
- In performance-critical applications
- Inside loops or large data operations
- When using collections like `ArrayList` (before generics existed)

---

**Modern solution:**  
Use **generics** (like `List<int>`) instead of collections like `ArrayList`, which required boxing for value types.

---

### 11. What is managed code in C# and why is it safer?

**Answer:**  
**Managed code** is code that runs under the **control of the CLR (Common Language Runtime)**.  
This means the .NET runtime **manages memory, type safety, security, and error handling** for you.

---

**What the CLR does for managed code:**
- Allocates memory for objects
- Frees memory automatically (garbage collection)
- Checks for unsafe type conversions
- Catches and handles exceptions

---

**Example of managed code:**
```csharp
int x = 10;
string name = "Alice";
```

You don’t have to manually allocate or free memory for these variables — the CLR handles it.

---

**Why is it safer?**
- No memory leaks (if used properly)
- No invalid pointer access
- No manual freeing of memory (like `free()` in C/C++)

---

**Analogy:**  
Managed code is like flying on autopilot — the system takes care of engine checks, speed, altitude, and safety. You focus only on navigation (business logic).

---

### 12. What is unmanaged code and when do we use it?

**Answer:**  
**Unmanaged code** is code that **runs outside the control of the CLR**, usually written in languages like C or C++.

You, the programmer, are responsible for:
- Allocating and freeing memory
- Handling memory addresses (pointers)
- Preventing memory corruption and leaks

---

**When would you use unmanaged code in a C# project?**
- To call into OS-level APIs (like Windows API)
- To use legacy code or high-performance native libraries
- To do low-level hardware interaction (e.g., with sensors)

---

**How does C# work with unmanaged code?**
By using **Interop/Platform Invocation Services (P/Invoke)** or the `unsafe` keyword.

**Example:**
```csharp
[DllImport("user32.dll")]
static extern int MessageBox(IntPtr hWnd, string text, string caption, uint type);
```

This lets you call unmanaged Windows APIs from C#.

---

**Why is unmanaged code risky?**
- Memory leaks if you forget to free memory
- Dangling pointers or buffer overflows
- System crashes from incorrect memory access

---

**Analogy:**  
Unmanaged code is like flying a plane manually — you have full control, but also full responsibility. If something goes wrong, there’s no safety net.

---

### 13. What is garbage collection in C# and why is it important?

**Answer:**  
**Garbage Collection (GC)** is the automatic process of **finding and freeing memory** that your program no longer uses.

It runs in the background and reclaims heap memory that:
- Was allocated for objects
- Is no longer referenced (i.e., nothing points to it anymore)

---

**Why is GC important?**
- Prevents memory leaks
- Saves you from manually freeing memory (like in C/C++)
- Makes your code safer and more reliable

---

**Example:**
```csharp
Person p = new Person();
p = null;  // The object is no longer reachable

// Eventually, GC will detect this and free the memory
```

You don’t need to say `delete p;` — the GC takes care of it.

---

**Analogy:**  
Garbage collection is like a janitor who walks around the building (heap), looking for abandoned desks (objects) and clearing them out.

---

### ✅ 14. When does garbage collection run, and can we control it?

**Answer:**  
The **GC decides on its own** when to run — based on:
- Amount of memory used
- Available system resources
- Generational tracking of objects

It tries to **avoid slowing down** your program and runs when it thinks it’s optimal.

---

**Can we force it?**
Yes — but it’s not recommended unless necessary.

```csharp
GC.Collect();  // Forces garbage collection
```

Use this only in special scenarios (like memory benchmarking), as it interrupts normal program flow.

---

**How does GC know what to collect?**
- It keeps track of all **active references**
- If no variable or object refers to a given object anymore, it's marked as **"unreachable"**
- Unreachable objects are collected

---

**Bonus: Generations in GC:**
- .NET divides objects into **3 generations**: `Gen 0`, `Gen 1`, `Gen 2`
- Objects that live longer are moved to higher generations
- GC collects younger objects more frequently, as they are more likely to be garbage

---

**Analogy:**  
Think of it like a smart cleaning crew:
- Checks rooms frequently that are used often (Gen 0)
- Checks rooms occasionally that are still occupied (Gen 1, Gen 2)
- Cleans only when necessary, without disturbing active users

---

### ✅ 15. What is a `struct` in C# and how is it different from a `class`?

**Answer:**  
A **`struct`** is a value type that you can use to create lightweight objects.  
It’s similar to a `class`, but:
- It lives in the **stack**, not the heap
- It does **not support inheritance**
- It’s **copied** when assigned or passed around (like value types)

---

**Basic syntax:**
```csharp
struct Point
{
    public int X;
    public int Y;

    public void Print()
    {
        Console.WriteLine($"({X}, {Y})");
    }
}
```

---

**Differences from `class`:**

| Feature              | `struct` (value type)         | `class` (reference type)           |
|----------------------|-------------------------------|------------------------------------|
| Memory               | Stack                         | Heap                              |
| Assignment           | Copies entire struct          | Copies reference only             |
| Inheritance          | No inheritance allowed        | Supports inheritance              |
| Default constructor  | Not allowed (must be parameterless) | Allowed                        |
| Use case             | Lightweight, short-lived data | Complex, shared data              |

---

**Example:**
```csharp
Point p1 = new Point { X = 1, Y = 2 };
Point p2 = p1;
p2.X = 10;

Console.WriteLine(p1.X); // Output: 1 — p1 is unaffected
```

---

**When should I use `struct` instead of `class`?**
- When you want **performance** and **copy-based behavior**
- When the object has **no need for inheritance**
- When the data is small and simple (like coordinates, RGB color, etc.)

---

**Analogy:**  
A `struct` is like giving someone a copy of a document.  
A `class` is like giving them a link to a shared document. Changes in one affect the other.

---

### ✅ 16. When should we avoid using `struct`?

**Answer:**  
Avoid using `struct` when:
- Your object has **a lot of data** (large memory footprint)
- You want to use **inheritance or polymorphism**
- You expect the object to be **shared or modified** across parts of the program
- You want **consistent behavior across method calls** (since structs are copied)

---

**Why?**
Because:
- Structs are **copied**, which can lead to bugs if you expect shared behavior
- Passing large structs can hurt performance more than classes

---

**Problem example:**
```csharp
struct Counter
{
    public int Value;

    public void Increment()
    {
        Value++;
    }
}

Counter c = new Counter();
c.Increment();   // This actually does nothing!
```

**Why?**  
`c.Increment()` works on a **copy** of the struct, not the original — so `Value` doesn’t change in the original `c`.

---

**Summary:**  
Use `struct` when you want:
- Small, immutable, performance-friendly value types  
Use `class` when you want:
- Shared, reference-based, object-oriented behavior

---

### ✅ 17. What is a string in C# and how is it stored?

**Answer:**  
A `string` in C# is a **sequence of characters**, used to store and manipulate text (like names, sentences, inputs).

---

**Key facts:**
- Strings are **reference types**, but behave like value types in some ways (because they are immutable)
- A string is stored in the **heap**, but variables referencing it live on the **stack**
- Strings are **immutable**, meaning once created, their content **cannot be changed**

---

**Example:**
```csharp
string name = "Alice";
```

If you try:
```csharp
name = name + " Smith";
```

You’re not modifying the original string — you're creating a **new one**.

---

**Analogy:**  
A string is like a sealed envelope — if you want to change what’s inside, you must make a **new envelope**.

---

### ✅ 18. What are common string methods and properties?

**Answer:**  
Here are some **common string operations** you’ll use often:

---

**Length** – total number of characters
```csharp
string name = "Alice";
Console.WriteLine(name.Length); // 5
```

---

**ToUpper / ToLower** – change case
```csharp
Console.WriteLine(name.ToUpper()); // "ALICE"
Console.WriteLine(name.ToLower()); // "alice"
```

---

**Contains / StartsWith / EndsWith**
```csharp
Console.WriteLine(name.Contains("li"));     // true
Console.WriteLine(name.StartsWith("Al"));   // true
Console.WriteLine(name.EndsWith("ce"));     // true
```

---

**IndexOf / LastIndexOf**
```csharp
string sentence = "Hello world";
Console.WriteLine(sentence.IndexOf("o"));       // 4
Console.WriteLine(sentence.LastIndexOf("o"));   // 7
```

---

**Substring** – get part of a string
```csharp
Console.WriteLine(name.Substring(1, 3)); // "lic"
```

---

**Replace**
```csharp
Console.WriteLine(name.Replace("A", "E")); // "Elice"
```

---

**Split**
```csharp
string fullName = "John Michael Doe";
string[] parts = fullName.Split(' ');
Console.WriteLine(parts[0]); // "John"
Console.WriteLine(parts[1]); // "Michael"
Console.WriteLine(parts[2]); // "Doe"
```

---

**Trim / TrimStart / TrimEnd**
```csharp
string messy = "   Hello!   ";
Console.WriteLine(messy.Trim()); // "Hello!"
```

---

**Analogy:**  
Think of strings as powerful Lego blocks of characters. These methods help you **slice, transform, or inspect** them without manually looping over each character.

---

### ✅ 19. What is an exception in C# and why do we need `try-catch`?

**Answer:**  
An **exception** is an error that occurs **while your program is running** — not during compilation.  
For example:
- Dividing by zero
- Accessing a file that doesn’t exist
- Parsing invalid input like `int.Parse("abc")`

If not handled, an exception will **crash your program**.

---

**To prevent this, we use:**
- `try` → for the code that might fail
- `catch` → to handle the failure gracefully
- `finally` → (optional) to run cleanup code

---

**Example:**
```csharp
try
{
    int x = int.Parse("abc");  // This will throw FormatException
}
catch (FormatException)
{
    Console.WriteLine("Input was not a valid number.");
}
```

---

**Why use this?**
- It lets your program recover from errors
- It prevents crashes and improves user experience
- You can log errors, retry operations, or give meaningful messages

---

**Analogy:**  
It’s like trying to open a file. If the file isn’t there, you don’t die — you show a message and try another file.

---

### ✅ 20. What is the role of `finally`, and when is it useful?

**Answer:**  
The `finally` block contains code that runs **no matter what** — whether an exception was thrown or not.

It’s used for **cleanup**, like:
- Closing files
- Releasing resources
- Ending a database connection

---

**Example:**
```csharp
try
{
    Console.WriteLine("Trying risky code...");
}
catch (Exception)
{
    Console.WriteLine("Something went wrong.");
}
finally
{
    Console.WriteLine("This always runs.");
}
```

---

**Output:**
```
Trying risky code...
This always runs.
```

Even if the `try` block fails or the `catch` is skipped, `finally` still runs.

---

**When not to use it?**
- If you have no cleanup or post-processing logic
- If it adds unnecessary complexity

---

**Analogy:**  
`finally` is like locking your house every time — even if nothing bad happened, **you still do it as a habit** before leaving.

---

### ✅ 21. What is a `switch` statement and how is it different from `if-else`?

**Answer:**  
A `switch` statement is a cleaner and more readable way to write multiple `if-else` conditions based on the **same variable**.

Use it when:
- You’re comparing a variable to several known constant values
- You want a simpler alternative to long `if-else-if` chains

---

**Basic syntax:**
```csharp
switch (day)
{
    case "Monday":
        Console.WriteLine("Start of the week.");
        break;
    case "Friday":
        Console.WriteLine("Almost weekend!");
        break;
    default:
        Console.WriteLine("Just another day.");
        break;
}
```

---

**Key rules:**
- Each `case` must end with a `break;` (or `return`)
- `default` is optional — it runs if no `case` matches
- You cannot compare ranges (`>`, `<`) — only discrete values

---

**When not to use `switch`:**
- When you need to compare multiple different variables
- When your logic is more complex than a simple value match

---

**Analogy:**  
A `switch` is like a vending machine:
- You choose a code
- The machine checks its internal list
- It returns the exact item, or says “invalid choice”

---

### ✅ 22. Can `switch` be used with non-strings or numbers?

**Answer:**  
Yes. In C#, `switch` supports multiple types including:
- `int`, `char`, `string`, `bool` (from C# 7), and `enum`

---

**Examples:**

With `int`:
```csharp
int number = 2;
switch (number)
{
    case 1:
        Console.WriteLine("One");
        break;
    case 2:
        Console.WriteLine("Two");
        break;
}
```

With `char`:
```csharp
char grade = 'B';
switch (grade)
{
    case 'A':
        Console.WriteLine("Excellent");
        break;
    case 'B':
        Console.WriteLine("Good");
        break;
}
```

With `enum`:
```csharp
enum Status { Pending, Approved, Rejected }

Status s = Status.Approved;
switch (s)
{
    case Status.Pending:
        Console.WriteLine("Wait...");
        break;
    case Status.Approved:
        Console.WriteLine("Go ahead!");
        break;
}
```

---

**Modern bonus (C# 8+):**
You can use **switch expressions** and `when` filters — we’ll explore that in advanced C#.

---

### ✅ 23. What is a `List<T>` in C# and why is it better than an array?

**Answer:**  
A `List<T>` is a **generic, dynamic collection** that allows you to:
- Add or remove elements at any time
- Automatically resize itself
- Store elements of any type (`T` stands for type)

It’s part of `System.Collections.Generic` and is widely used in real-world development.

---

**How is it better than an array?**
| Feature         | Array                      | List<T>                         |
|------------------|----------------------------|----------------------------------|
| Size             | Fixed after creation       | Grows/shrinks automatically     |
| Adding/removing  | Manual with copying        | Built-in methods like `Add()`   |
| Search/filter    | Manual                     | Easy with LINQ or methods       |
| Flexibility      | Low                        | High                            |

---

**Basic example:**
```csharp
using System.Collections.Generic;

List<string> fruits = new List<string>();
fruits.Add("Apple");
fruits.Add("Banana");

Console.WriteLine(fruits[0]); // Output: Apple
Console.WriteLine(fruits.Count); // Output: 2
```

---

**Why use it in real apps?**
- It simplifies storage and iteration
- It supports advanced operations (searching, sorting, filtering)
- It plays nicely with LINQ

**Analogy:**  
If an array is a fixed-size egg carton, a `List<T>` is a flexible shopping basket — you can keep adding/removing items as you need.

---

### ✅ 24. What are some useful methods available in `List<T>`?

**Answer:**

Here are some commonly used methods:

---

`Add()` – adds an item
```csharp
fruits.Add("Mango");
```

`Insert(index, value)` – adds item at a specific position
```csharp
fruits.Insert(1, "Pineapple");
```

`Remove(value)` – removes the first matching item
```csharp
fruits.Remove("Apple");
```

`RemoveAt(index)` – removes item at a given index
```csharp
fruits.RemoveAt(0);
```

`Contains(value)` – checks if item exists
```csharp
Console.WriteLine(fruits.Contains("Banana")); // true or false
```

`Clear()` – removes all items
```csharp
fruits.Clear();
```

`Count` – total number of items
```csharp
int total = fruits.Count;
```

---

**Looping through a list:**
```csharp
foreach (string fruit in fruits)
{
    Console.WriteLine(fruit);
}
```

---

**Important:**  
- Lists are **zero-indexed** like arrays
- You can use `.Count` instead of `.Length`

---