# 12 – Static, Final, and Nested Classes

## 🧠 Overview

This lesson covers three key modifiers/features in Java OOP:
- `static`: Belongs to the class rather than instances
- `final`: Prevents modification (used with classes, methods, and variables)
- Nested classes: Classes defined inside other classes

---

## 🔹 static Keyword

- A `static` member (variable or method) belongs to the **class**, not to instances.
- Shared across all instances of the class.

```java
class Counter {
    static int count = 0;

    Counter() {
        count++;
    }

    static void showCount() {
        System.out.println("Total objects: " + count);
    }
}

class Main {
    public static void main(String[] args) {
        new Counter();
        new Counter();
        Counter.showCount();  // Output: Total objects: 2
    }
}
```
---

## 🔹 final Keyword

### Final Variables

- Value **cannot be changed** once assigned.
- Must be initialized either inline or in the constructor.

```java code
class Config {
    final int MAX_USERS = 100;
}
```
### Final Methods

- Cannot be overridden in subclasses.

```java
class Parent {
    final void greet() {
        System.out.println("Hello!");
    }
}

class Child extends Parent {
    // void greet() {} // ❌ Error: Cannot override final method
}
```
### Final Classes

- Cannot be extended by any subclass.

```java code
final class Utility {
    static void log(String msg) {
        System.out.println("LOG: " + msg);
    }
}

// class SubUtility extends Utility {} // ❌ Error
```
---

## 🧬 Nested Classes

Java supports four types of nested classes:

1. **Static Nested Class** – Like a static member of the outer class
2. **Non-static Inner Class** – Tied to an instance of the outer class
3. **Local Inner Class** – Declared within a method
4. **Anonymous Inner Class** – Instantiated without a class name (used with interfaces or abstract classes)

---

### 1. Static Nested Class

- Can access only static members of the outer class

```java
class Outer {
    static int data = 42;

    static class Nested {
        void display() {
            System.out.println("Data: " + data);
        }
    }
}

class Main {
    public static void main(String[] args) {
        Outer.Nested obj = new Outer.Nested();
        obj.display();  // Output: Data: 42
    }
}
```
---

### 2. Non-static Inner Class

- Needs an instance of the outer class to be created

```java code
class Outer {
    int data = 10;

    class Inner {
        void show() {
            System.out.println("Data: " + data);
        }
    }
}

class Main {
    public static void main(String[] args) {
        Outer outer = new Outer();
        Outer.Inner inner = outer.new Inner();
        inner.show();  // Output: Data: 10
    }
}
```
---

## 🧠 Summary

- `static`: Belongs to the class; shared among instances
- `final`: Prevents modification (used on vars, methods, and classes)
- Nested classes improve code organization:
    - **Static Nested**: Can exist without an outer instance
    - **Inner Classes**: Need an outer instance
