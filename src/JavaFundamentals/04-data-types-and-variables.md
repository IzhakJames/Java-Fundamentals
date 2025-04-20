# 04 – Data Types and Variables

## 🧠 Key Concepts

- Every variable in Java has a **type** — either **primitive** or **reference**.
- The type determines:
    - The **kind of data** it can hold
    - The **operations** that can be performed
    - The **memory size** and behavior

---

## 🔢 Primitive Data Types

Java has **8 primitive types**, each with a fixed size:

| Type     | Size     | Default | Example Value     |
|----------|----------|---------|-------------------|
| `byte`   | 8-bit    | `0`     | `byte b = 100;`   |
| `short`  | 16-bit   | `0`     | `short s = 5000;` |
| `int`    | 32-bit   | `0`     | `int x = 10;`     |
| `long`   | 64-bit   | `0L`    | `long l = 123456L;` |
| `float`  | 32-bit   | `0.0f`  | `float f = 5.75f;` |
| `double` | 64-bit   | `0.0d`  | `double d = 19.99;` |
| `char`   | 16-bit   | `\u0000`| `char c = 'A';`   |
| `boolean`| 1-bit    | `false` | `boolean flag = true;` |

> 💡 Primitives are stored in the **stack** or inside objects in the heap (as fields).

---

## 🧾 Reference Data Types

- Reference types store **memory addresses** that refer to objects in the **heap**.
- Includes:
    - **Classes**
    - **Interfaces**
    - **Arrays**
    - **Enums**

```java
String name = "Izhak";           // Reference to a String object
int[] nums = {1, 2, 3};          // Reference to an array in heap
Dog dog = new Dog();             // Reference to a Dog object
```
---
## 🧪 Variable Declaration and Initialization
```java
int age = 25;              // Declare and initialize
String name;               // Declaration only
name = "Izhak";            // Initialized later
```
### 🔹 Rules

- Variables **must be declared before use**
- **Local variables** do **not** have default values
- **Class fields** (instance/static) **do** have default values based on their type
---

## 🧠 Variable Scope

- **Local variables** – Declared inside methods; exist only during method execution
- **Instance variables** – Fields in a class; tied to object instances
- **Static variables** – Shared across all instances of a class
```java
public class Person {
    static int count = 0;         // static variable
    String name;                  // instance variable

    void greet() {
        String message = "Hi";    // local variable
        System.out.println(message + ", " + name);
    }
}
```
---

## 🔁 Summary

- Java has **8 primitive types** and many **reference types**
- **Primitives** store values directly; **references** store pointers to objects
- Use `new` to create objects; primitives **don’t need** `new`
- Local variables must be **explicitly initialized**
- Proper type choice improves **performance**, **clarity**, and **memory usage**