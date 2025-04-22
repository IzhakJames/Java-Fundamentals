# 09 – Inheritance

## 🧠 What is Inheritance?

- **Inheritance** is a fundamental concept in Object-Oriented Programming (OOP) that allows a class (called a subclass or child class) to inherit fields and methods from another class (called a superclass or parent class).
- It promotes **code reusability** and establishes a natural hierarchy between classes.

---

## 🧩 Syntax of Inheritance

```java
class Superclass {
// fields and methods
}

class Subclass extends Superclass {
// additional fields and methods
}
```
- The `extends` keyword is used to establish inheritance.
- The subclass inherits all non-private members of the superclass.

---

## 🔹 Example: Basic Inheritance

```java
class Animal {
    void eat() {
        System.out.println("This animal eats food.");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("The dog barks.");
    }
}

class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();  // Inherited method
        dog.bark(); // Subclass method
    }
}
```
---

## 🧬 Types of Inheritance in Java

1. **Single Inheritance**: A subclass inherits from one superclass.

```java
class Parent {
// code
}

class Child extends Parent {
// code
}
```
2. **Multilevel Inheritance**: A subclass inherits from a superclass, and another subclass inherits from that subclass.

```java
class Grandparent {
// code
}

class Parent extends Grandparent {
// code
}

class Child extends Parent {
// code
}
```
3. **Hierarchical Inheritance**: Multiple subclasses inherit from a single superclass.

```java
class Parent {
// code
}

class Child1 extends Parent {
// code
}

class Child2 extends Parent {
// code
}
```
*Note*: Java does **not** support **multiple inheritance** (a class inheriting from more than one class) to avoid ambiguity.

---

## 🔁 Method Overriding

- A subclass can provide a specific implementation of a method that is already defined in its superclass.
- This is known as **method overriding**.

```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
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
        Animal myDog = new Dog();
        myDog.makeSound(); // Outputs: Dog barks
    }
}
```
---

## 🧠 Key Points

- **`super` Keyword**: Used to refer to the immediate parent class object.
    - Can be used to call superclass methods and constructors.

```java
class Animal {
    Animal() {
    System.out.println("Animal constructor");
    }
}

class Dog extends Animal {
    Dog() {
        super(); // Calls Animal constructor
        System.out.println("Dog constructor");
    }
}
```
- **Access Modifiers**:
    - `private` members are **not** inherited.
    - `protected` members are accessible in subclasses.
    - `public` members are accessible everywhere.

---

## 🧠 Summary

- Inheritance allows a class to acquire properties and behaviors of another class.
- Promotes code reusability and establishes a hierarchical relationship.
- Java supports single, multilevel, and hierarchical inheritance.
- Method overriding enables a subclass to provide a specific implementation of a method.
- The `super` keyword is used to access superclass members.

