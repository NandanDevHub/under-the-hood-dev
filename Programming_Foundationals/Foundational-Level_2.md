# C# Programming – Foundational Level 2

Continuing from the earlier sets, this file explains **loops** and **functions** in C# with complete clarity, beginner-focused structure, and real-world analogies.

---

## Loops and Repetition

### 21. Why do we need loops in programming?

**Explanation:**  
Loops are used when you want to **repeat a block of code multiple times**. Without loops, you’d have to copy-paste the same code again and again — which is inefficient and error-prone.

**Real-world analogy:**  
Imagine writing names on 100 invitation cards. You wouldn’t write one sentence 100 times manually — you'd use a loop to automate it.

**Example:**
```csharp
for (int i = 0; i < 100; i++)
{
    Console.WriteLine("Sending invitation to person " + i);
}
```

---

### 22. What is a `for` loop and when do we use it?

**Explanation:**  
A `for` loop is used when you know exactly **how many times** you want to repeat something.

**Structure:**
```csharp
for (initialization; condition; update)
{
    // repeat this block
}
```

**C# Example:**
```csharp
for (int i = 1; i <= 5; i++)
{
    Console.WriteLine("Line " + i);
}
```

---

### 23. What is a `while` loop and how is it different?

**Explanation:**  
A `while` loop runs **as long as the condition is true**. It’s best when you don’t know how many times you need to repeat something — you just wait for a certain situation to stop the loop.

**Example:**
```csharp
int i = 1;
while (i <= 5)
{
    Console.WriteLine("Line " + i);
    i++;
}
```

---

### 24. What is a `do-while` loop?

**Explanation:**  
A `do-while` loop is similar to `while`, but it **always runs at least once**, because the condition is checked **after** the loop block.

**C# Example:**
```csharp
int i = 1;
do
{
    Console.WriteLine("Line " + i);
    i++;
} while (i <= 5);
```

**When to use it?**  
When the block must execute **once**, even if the condition is false initially.

---

### 25. How do you stop a loop or skip one cycle?

**Explanation:**
- `break` → exits the loop completely.
- `continue` → skips the current iteration and moves to the next one.

**Examples:**
```csharp
for (int i = 1; i <= 5; i++)
{
    if (i == 3)
        continue; // skip when i = 3

    if (i == 5)
        break; // exit when i = 5

    Console.WriteLine(i);
}
```

---

## Functions and Code Reuse

### 26. What is a function and why do we use it?

**Explanation:**  
A function is a **block of code** that performs a specific task. Instead of writing the same logic again and again, we define it once and reuse it.

**Benefits:**
- Code reuse
- Easier debugging
- Better readability

**Real-world analogy:**  
A washing machine has a “wash” function. You press a button, and it does the job. Similarly, you “call” a function to do work.

**C# Example:**
```csharp
void Greet()
{
    Console.WriteLine("Hello!");
}

Greet();  // Calling the function
```

---

### 27. What is the `Main()` method?

**Explanation:**  
In C#, `Main()` is the **starting point** of the program. It's where the program begins execution.

**Why is it special?**
The compiler looks for `Main()` to know where to start running the code.

**Example:**
```csharp
class Program
{
    static void Main()
    {
        Console.WriteLine("Program started");
    }
}
```

---

### 28. What are parameters in functions?

**Explanation:**  
Parameters are **inputs** passed to a function so it can act on different data each time.

**Example:**
```csharp
void Greet(string name)
{
    Console.WriteLine("Hello " + name);
}

Greet("Alice");  // Output: Hello Alice
Greet("Bob");    // Output: Hello Bob
```

---

### 29. What is a return value?

**Explanation:**  
A return value is the **output** a function gives back to the code that called it.

**C# Example:**
```csharp
int Add(int a, int b)
{
    return a + b;
}

int result = Add(3, 4);  // result = 7
```

**Why useful?**
It lets you store and use the result of a function’s work.

---

### 30. Why is breaking code into functions a good practice?

**Explanation:**
- Keeps code organized and readable
- Avoids duplication
- Makes debugging and testing easier

**Example:**  
Instead of copying the logic to calculate area everywhere, define one function:
```csharp
double GetArea(double radius)
{
    return Math.PI * radius * radius;
}
```

You can now call `GetArea(5)` from anywhere.

---
# Errors, Scope, and Booleans

### 31. What are syntax errors and why do they happen?

**Explanation:**  
A **syntax error** means you've written code that doesn't follow the rules of the language. The compiler reads your code line by line, and if something breaks the grammar, it won’t allow the program to compile.

**Why do they happen?**
- Missing semicolons
- Misplaced brackets or parentheses
- Incorrect spelling of keywords
- Invalid statements

**C# Example:**
```csharp
int number = 5  // ❌ Error: missing semicolon
Console.WriteLine(number)
```

**Fix:**
```csharp
int number = 5;
Console.WriteLine(number);
```

**Real-world analogy:**  
Like saying in English: “Go to store I.” It makes no sense grammatically. Syntax errors are similar — they prevent the code from making sense to the compiler.

---

### 32. What is a runtime error and how is it different from a syntax error?

**Explanation:**  
A **runtime error** occurs **while the program is running** — even if there are no syntax errors. It happens when something unexpected or invalid occurs during execution.

**Common causes:**
- Dividing by zero
- Using an uninitialized variable
- Trying to convert "abc" into an integer
- Accessing an element outside array bounds

**C# Example:**
```csharp
int age = int.Parse("abc");  // ❌ FormatException at runtime
```

**Difference from syntax error:**
- **Syntax error:** Code doesn’t compile at all
- **Runtime error:** Code compiles, but fails when it runs

**Analogy:**  
A plane built correctly (no syntax issues) crashes mid-flight due to engine failure (runtime error). Everything looked okay, but something went wrong while it was working.

---

### 33. What is exception handling and why is it necessary?

**Explanation:**  
**Exception handling** is how you tell your program what to do **when something goes wrong at runtime** — instead of crashing, it handles the error gracefully.

**Why it's needed:**
- Prevent program from crashing
- Show meaningful messages to the user
- Allow recovery or alternate action

**C# Example:**
```csharp
try
{
    int age = int.Parse("abc");
}
catch (FormatException ex)
{
    Console.WriteLine("Invalid input. Please enter a number.");
}
```

**Analogy:**  
Like wearing a seatbelt in a car — it doesn’t stop the crash but prevents serious consequences. Exception handling is your code’s seatbelt.

---

### 34. What is the `finally` block and when does it run?

**Explanation:**  
The `finally` block is used to execute code **no matter what** — whether there was an exception or not.

**When to use it:**
- To clean up resources (like closing a file or connection)
- To ensure some actions always run (e.g., logging, freeing memory)

**C# Example:**
```csharp
try
{
    int num = int.Parse("abc");
}
catch (Exception)
{
    Console.WriteLine("Something went wrong.");
}
finally
{
    Console.WriteLine("This runs no matter what.");
}
```

**Analogy:**  
After every movie, you roll the credits — whether the movie was a hit or a flop. The `finally` block is the credit roll.

---

### 35. What is the difference between an error and an exception?

**Explanation:**

| Feature       | Error                             | Exception                         |
|---------------|------------------------------------|------------------------------------|
| Definition    | Serious problem during execution   | Specific issue handled by program |
| Catchable?    | Often not (e.g., memory error)     | Yes, using try-catch               |
| Severity      | More severe                        | Less severe and expected           |

**C# Example:**
- StackOverflowError (like infinite recursion) is an **error**
- FormatException, NullReferenceException are **exceptions**

**Why important to know?**  
You can catch exceptions and handle them — but most errors are fatal and uncatchable.

---

