# 13 – SOLID Principles (Bonus Lesson)

## 🧠 Overview

**SOLID** is an acronym for five core design principles that help make object-oriented software:

- Easier to maintain
- More scalable
- Less prone to bugs

Developed by **Robert C. Martin (Uncle Bob)**, these principles guide developers in creating flexible, extensible, and robust applications.

---

## 🔹 S – Single Responsibility Principle (SRP)

> A class should have **only one reason to change**.

- Each class should do **one thing**, and do it well.
- Promotes separation of concerns.

**Bad Example:**

```java
class Report {
    void generate() {}
    void print() {}         // ❌ Printing should not be here
    void saveToFile() {}    // ❌ File I/O responsibility
}
```
**Good Example:**

```java
class ReportGenerator {
    void generate() {}
}

class ReportPrinter {
    void print() {}
}

class ReportSaver {
    void saveToFile() {}
}
```
---

## 🔹 O – Open/Closed Principle (OCP)

> Software entities should be **open for extension**, but **closed for modification**.

- Add new features via extension, not by changing existing code.

**Bad Example:**

```java code
class PaymentProcessor {
    void pay(String type) {
        if (type.equals("CreditCard")) { /* ... */ }
        else if (type.equals("PayPal")) { /* ... */ }
    }
}
```
**Good Example:**

```java
interface PaymentMethod {
    void pay();
}

class CreditCardPayment implements PaymentMethod {
    public void pay() { /* ... */ }
}

class PayPalPayment implements PaymentMethod {
    public void pay() { /* ... */ }
}

class PaymentProcessor {
    void process(PaymentMethod method) {
        method.pay();
    }
}
```
---

## 🔹 L – Liskov Substitution Principle (LSP)

> Subtypes must be substitutable for their base types **without breaking the program**.

**Bad Example:**
```java
class Bird {
    void fly() {}
}

class Ostrich extends Bird {
    void fly() { throw new UnsupportedOperationException(); } // ❌ Not substitutable
}
```
**Good Example:**

```java
interface Bird {}

interface FlyingBird extends Bird {
    void fly();
}

class Sparrow implements FlyingBird {
    public void fly() { /* ... */ }
}

class Ostrich implements Bird {}
```
---

## 🔹 I – Interface Segregation Principle (ISP)

> Clients should **not be forced to implement methods they don't use**.

**Bad Example:**

```java code
interface Machine {
    void print();
    void scan();
    void fax();
}

class OldPrinter implements Machine {
    public void print() {}
    public void scan() {}   // ❌ Not needed
    public void fax() {}    // ❌ Not needed
}
```
**Good Example:**
```java
interface Printer {
    void print();
}

interface Scanner {
    void scan();
}

class OldPrinter implements Printer {
    public void print() {}
}
```
---

## 🔹 D – Dependency Inversion Principle (DIP)

> High-level modules should not depend on low-level modules.  
> Both should depend on **abstractions**.

**Bad Example:**
```java
class LightBulb {
    void turnOn() {}
    void turnOff() {}
}

class Switch {
    LightBulb bulb;

    Switch(LightBulb bulb) {
        this.bulb = bulb;
    }

    void operate() {
        bulb.turnOn();  // ❌ High-level module depends on low-level
    }
}
```
**Good Example:**
```java
interface Switchable {
    void turnOn();
    void turnOff();
}

class LightBulb implements Switchable {
    public void turnOn() {}
    public void turnOff() {}
}

class Switch {
    Switchable device;

    Switch(Switchable device) {
        this.device = device;
    }

    void operate() {
        device.turnOn();
    }
}
```
---

## 🧠 Summary

| Principle | Purpose                                    |
|-----------|--------------------------------------------|
| SRP       | One class = One responsibility             |
| OCP       | Add features via extension, not modification |
| LSP       | Subclasses must be substitutable           |
| ISP       | Avoid fat interfaces                       |
| DIP       | Depend on abstractions, not concretions    |

---

✅ Mastering SOLID is key to writing clean, maintainable, and scalable OOP code!
