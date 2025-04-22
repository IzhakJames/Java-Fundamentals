# 11 – Abstract Classes & Interfaces

## 🧠 What is Abstraction?

- **Abstraction** is the process of hiding internal implementation and showing only the essential features.
- In Java, abstraction is achieved using **abstract classes** and **interfaces**.

---

## 🔹 Abstract Classes

- Cannot be instantiated directly.
- May contain **abstract methods** (without a body) and **concrete methods** (with implementation).
- Use `abstract` keyword in class definition.

```java
abstract class Animal {
String name;

    Animal(String name) {
        this.name = name;
    }

    abstract void makeSound(); // Abstract method

    void sleep() {
        System.out.println(name + " is sleeping");
    }
}

class Dog extends Animal {
    Dog(String name) {
        super(name);
    }

    @Override
    void makeSound() {
        System.out.println(name + " barks");
    }
}

class Main {
    public static void main(String[] args) {
        Animal dog = new Dog("Rex");
        dog.makeSound();  // Rex barks
        dog.sleep();      // Rex is sleeping
    }
}
```
---

## 🔹 Interfaces

- Defines a contract — what a class **must do**, not how it does it.
- All methods are **abstract by default** (until Java 8+).
- Cannot have constructors or instance fields.

```java
interface Flyable {
    void fly();
}

interface Swimmable {
    void swim();
}

class Duck implements Flyable, Swimmable {
    public void fly() {
        System.out.println("Duck flies");
    }

    public void swim() {
        System.out.println("Duck swims");
    }
}
```
---

## 🧠 Key Differences: Abstract Class vs Interface

| Feature               | Abstract Class           | Interface                     |
|-----------------------|--------------------------|-------------------------------|
| Methods               | Both abstract & concrete | All abstract (Java <8)        |
| Fields                | Can have instance fields | Only `public static final`    |
| Constructors          | Allowed                  | Not allowed                   |
| Multiple Inheritance  | Not supported            | Supported via multiple interfaces |
| Use Case              | Shared code + abstraction| Pure abstraction (contract)   |

---

## 🧩 Java 8+ Interface Enhancements

- **Default methods** (with implementation):

```java
interface Playable {
    default void pause() {
        System.out.println("Paused");
    }
}
```
- **Static methods** in interfaces:

```java
interface MathUtil {
    static int square(int x) {
        return x * x;
    }
}
```
---

## 🚫 Common Pitfall

```java
abstract class A {
    private int x = 10;
}

class B extends A {
    void print() {
        // System.out.println(x); // ❌ private field not accessible
    }
}
```
> Even subclasses cannot access `private` members of the superclass.

---

## 🧠 Summary

- Use **abstract classes** when some shared logic is needed and partial implementation is expected.
- Use **interfaces** to enforce a common structure (contract) across unrelated classes.
- Java 8+ interfaces can include `default` and `static` methods.
- Both tools allow for abstraction but serve different purposes in design.
