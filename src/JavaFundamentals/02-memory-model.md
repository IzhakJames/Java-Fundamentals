# 02 – Java Memory Model

## 🧠 Overview

- The **Java Memory Model (JMM)** defines how memory is structured, accessed, and shared across threads.
- It explains how variables are stored, how method calls are handled, and how threads interact with memory.
- Knowing the JMM helps you understand:
  - Memory leaks
  - Thread safety
  - Performance optimization

---

## 📦 Java Memory Areas at Runtime

### Stack Memory
- Each thread has its own private **stack**.
- Stores:
  - Method call frames
  - Method parameters
  - Local variables
- Stack frames are created when a method is invoked and destroyed when the method returns.

### Heap Memory
- Shared across all threads.
- Stores:
  - Objects
  - Arrays
  - Instance variables (fields)
- Memory is **dynamically allocated** using `new`.

### Metaspace
- Stores:
  - Class metadata (names, methods, field types)
  - Constant pool
  - Reflection data
- Automatically resizes based on class loading.

### Method Area (Pre-Java 8)
- Formerly used to store class structures (now part of Metaspace).

### PC Registers & Native Method Stack
- Internal to the JVM; used for tracking instruction execution and calling native C libraries (JNI).

---

## 📚 Stack vs Heap

| Feature        | Stack                           | Heap                            |
|----------------|----------------------------------|---------------------------------|
| Lifespan       | Short-lived (per method call)    | Long-lived (until GC)           |
| Stores         | Local variables, method calls    | Objects and instance fields     |
| Thread Safety  | Thread-local (safe)              | Shared across threads           |
| Speed          | Very fast                        | Slower                          |
| Managed by     | LIFO structure                   | JVM Garbage Collector           |

---

## 💡 Stack Frame Example

```java
void greet(String name) {
    String message = "Hello " + name;
    System.out.println(message);
}
```
Each method call creates a **stack frame** that includes:
- Parameters (e.g., `name`)
- Local variables (e.g., `message`)
- Return address

Each call to `greet("Izhak")` has its own frame, which is **popped after execution**.

---

## 🔁 Heap: Shared Object Space

- Objects created with `new` are stored in the **heap**.
- All threads can access these objects (with proper synchronization).
- References to heap objects are stored in the **stack**.
```java
String a = new String("hello");  // 'a' in stack, object in heap
```
---

## 🧹 Garbage Collection

- Java automatically frees memory using the **Garbage Collector (GC)**.
- Only objects with **no live references** are eligible for collection.

### GC Algorithms:
- **G1** – Balanced, low-pause time GC (default in modern JVMs)
- **Parallel GC** – High throughput
- **ZGC, Shenandoah** – Ultra-low pause collectors
- **Serial GC** – Simpler, used in low-resource environments

> You **never** need to call `free()` like in C/C++.

---

## ⚠️ Common Pitfall
```java
String name = "Alice";
String copy = name;
name = null;
```
- The object `"Alice"` is still reachable through `copy`.
- GC won’t collect it until **all references are gone**.

---

## 🧠 Metaspace (Java 8+)

- Replaces **PermGen** (used before Java 8)
- Stores:
  - Class metadata
  - Interned strings and constants
  - Reflection data (`Class`, `Field`, `Method`)
- Automatically grows as needed (limited by system memory)

---

## 🔁 Summary

- ✅ Use **stack** for fast, thread-local method execution.
- ✅ Use **heap** for shared object data.
- ✅ JVM handles memory allocation and **GC**.
- ✅ Stack memory is cleaned when methods return.
- ✅ Heap memory is cleaned by the **Garbage Collector**.
- ✅ **Metaspace** handles class metadata and expands as needed.
