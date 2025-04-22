# 10 – Polymorphism

## 🧠 What is Polymorphism?

- **Polymorphism** means "many forms".
- It allows objects of different types to be treated as instances of a common super type (usually a parent class or interface).
- Enables flexibility and extensibility in code.

---

## 🔹 Types of Polymorphism in Java

1. **Compile-time Polymorphism** (a.k.a. **Method Overloading**)
2. **Runtime Polymorphism** (a.k.a. **Method Overriding**)

---

## ⚙️ Compile-time Polymorphism (Method Overloading)

- Same method name but different parameters (signature).
- Decided at **compile time**.

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```
---

## 🕒 Runtime Polymorphism (Method Overriding)

- A subclass provides its own implementation of a method that is already defined in the parent class.
- Determined at **runtime** via dynamic method dispatch.

```java
class Animal {
    void makeSound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Dog barks");
    }
}

class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Dog(); // Upcasting
        myAnimal.makeSound(); // Outputs: Dog barks
    }
}
```
---

## 🔄 Upcasting and Downcasting

- **Upcasting**: Subclass object is assigned to a parent class reference.
    - Allowed implicitly.
- **Downcasting**: Parent reference is cast back to subclass.
    - Must be done manually with caution.

```java
Animal a = new Dog();       // Upcasting
Dog d = (Dog) a;            // Downcasting
```
---

## 🧠 instanceof Operator

- Used to check an object’s type before casting.

```java
if (a instanceof Dog) {
    Dog d = (Dog) a;
    d.makeSound();
}
```
---

## 🧪 Real-world Analogy

- A **remote control** (parent class) can operate a **TV**, **AC**, or **Fan** (subclasses).
- The remote exposes a common interface (`powerOn()`), but each device implements it differently.

---

## ✅ Benefits of Polymorphism

- Promotes **code reuse** and **extensibility**
- Enables **dynamic behavior** at runtime
- Simplifies **code maintenance** by relying on a common interface
- Enhances **modular design**

---

## 🧠 Summary

- **Overloading** = same method name, different parameters (**compile-time**)
- **Overriding** = subclass method replaces superclass version (**runtime**)
- Use **upcasting** to treat child class as parent
- Use **instanceof** to safely **downcast**
- Polymorphism enables flexible and scalable application design
