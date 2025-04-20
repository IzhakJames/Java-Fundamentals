# 01 – JVM and Java Architecture

## 🧠 Key Concepts

- Java source code (`.java`) is compiled into **bytecode** (`.class`).
- Bytecode is executed by the **Java Virtual Machine (JVM)**.
- This makes Java **platform-independent** (Write Once, Run Anywhere).
- JVM abstracts away the operating system, allowing the same bytecode to run anywhere.
- JVM provides memory safety, exception handling, and automatic garbage collection.

---

## 🧩 Java Runtime Components

- **Compiler (`javac`)**: Converts source code into bytecode.
- **JVM**: Executes bytecode using interpretation and/or JIT compilation.
- **JRE (Java Runtime Environment)**: Includes JVM + standard libraries (like `java.lang`, `java.util`).
- **JDK (Java Development Kit)**: Includes JRE + development tools such as:
    - `javac` – Compiler
    - `javadoc` – Documentation generator
    - `javap` – Bytecode disassembler
    - `jshell` – Interactive REPL (Java 9+)

---

## 📦 Java Execution Flow

       ┌────────────────────┐
       │   Class Loader     │  <- Loads .class bytecode
       └────────────────────┘
               ↓
       ┌────────────────────┐
       │  Bytecode Verifier │  <- Ensures .class is valid & secure
       └────────────────────┘
               ↓
       ┌────────────────────┐
       │   JVM Runtime      │
       │   Interpreter      │  <- Executes instructions
       │   JIT Compiler     │  <- Speeds up execution (hot code)
       └────────────────────┘
               ↓
       ┌────────────────────┐
       │ Memory (Heap/Stack)│
       └────────────────────┘

- **Class Loader**: Loads `.class` files into memory when required.
- **Bytecode Verifier**: Ensures that the bytecode is valid and won't violate memory access rules.
- **Interpreter**: Executes bytecode line-by-line (slower but quick to start).
- **JIT Compiler**: Compiles hot code paths into native machine code for faster execution.
- **Memory**: JVM allocates memory in different areas (stack for methods, heap for objects, etc.).

```java
// HelloWorld.java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, JVM!");
    }
}

```
```shell
// Bash
$ javac HelloWorld.java   # Compile to HelloWorld.class
$ java HelloWorld         # Run via JVM
```

## 🚀 JVM Responsibilities

### Memory management (Heap & Stack):
- **Stack** → stores method frames and local variables
- **Heap** → stores objects and class instances

### Garbage collection:
- Reclaims memory automatically for unreachable objects
- Uses algorithms like **G1**, **ZGC**, **Parallel GC**

### Bytecode execution:
- Executes compiled `.class` bytecode either via **interpreter** or **JIT**

### Class loading:
- Dynamically loads required classes at runtime

### Security & sandboxing:
- Enforces permission restrictions on untrusted code

### Performance optimization:
- Uses **JIT compiler** and adaptive optimizations

---

## 🔒 What is Sandboxing?

JVM uses **sandboxing** to isolate and restrict code execution:

### Prevents untrusted code (e.g., downloaded applets) from:
- Accessing file systems
- Opening network connections
- Calling native OS commands

### Enforced through:
- ClassLoader hierarchy
- `SecurityManager` (deprecated in Java 17+)
- Bytecode verification

---

## ⚡ JIT Compiler

- **JIT (Just-In-Time)** compiler is part of the JVM runtime
- Translates frequently-used **bytecode into native machine code**
- Works during program execution (**not ahead-of-time**)

### 🔹 Benefits:
- Faster execution after initial warm-up
- Optimized loop unrolling, inlining, branch prediction
- Java performance can rival **C/C++** in long-running apps

---

## 🧠 Class Loader Phases

### Loading
- Loads `.class` files into memory

### Linking
- **Verification** – Ensures bytecode is valid and secure
- **Preparation** – Allocates memory for class variables
- **Resolution** – Converts symbolic references to actual references

### Initialization
- Runs static initializers
- Assigns static fields

```java
static {
    System.out.println("Static block initialized");
}
```

## 🧠 Metaspace (Java 8+)

- Replaces **PermGen** from Java 7 and earlier
- Stores **class metadata**, including:
  - Class names, method signatures, field types
  - String constants (in constant pool)
  - Reflection metadata (`Class`, `Field`, `Method`)
- Grows automatically depending on available system memory

---

## 🧪 Metaspace Example

```java
class Dog {
  String name;
  void bark() {
    System.out.println(name + " barks!");
  }
}
```
- Structure of the class (its name, methods, fields) is stored in **Metaspace**
- String literals like `" barks!"` are stored in the **constant pool**, which also resides in Metaspace

---

## 🛠 Common JVM Implementations

- **HotSpot (Oracle/OpenJDK)** – Most common, default in standard JDK
- **OpenJ9 (Eclipse)** – Lightweight JVM optimized for cloud environments
- **GraalVM** – Supports AOT (ahead-of-time) compilation and multiple languages (Java, JS, Python, etc.)
- **Amazon Corretto**, **Zulu**, **Liberica** – Alternate OpenJDK builds for different platforms and use cases

---

## 🧠 Key JVM Concepts

| Concept         | Description                                      |
|-----------------|--------------------------------------------------|
| **Bytecode**     | Platform-independent `.class` format             |
| **ClassLoader**  | Dynamically loads classes into memory            |
| **Metaspace**    | Stores class-level metadata                      |
| **JIT Compiler** | Converts bytecode into native machine code       |
| **GC**           | Garbage Collector for heap cleanup               |
| **Stack**        | Method frames, local variables, LIFO             |
| **Heap**         | Object memory shared across threads              |

---

## 🔁 Summary

- Java is compiled to **bytecode**, which runs on the **JVM**
- JVM handles **execution, memory, garbage collection**, and **security**
- **JDK = JRE + tools**; **JRE = JVM + libraries**
- **JIT** improves performance by compiling bytecode to native code
- **Metaspace** holds class metadata and grows as needed
- JVM abstracts OS/hardware to make Java truly **cross-platform**