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


