# 07 – Classes and Objects

## 🧠 Key Concepts

- A **class** is a blueprint for creating objects.
- An **object** is an instance of a class — it holds actual data and behaviors.
- Java is an **object-oriented language**, so classes and objects are essential.

---

## 🧱 Defining a Class

- A class contains:
    - Fields (variables)
    - Methods (functions)
    - Optionally: constructors, blocks, inner classes

```java
public class Person {  
    String name;  
    int age;

    void sayHello() {  
        ("Hi, I’m " + name);  
    }  
}
```

---

## 🧪 Creating an Object

- Use the `new` keyword to instantiate a class.
```java
Person p = new Person();  
p.name = "Izhak";  
p.age = 25;  
p.sayHello();  // Output: Hi, I’m Izhak
```
---

## 📦 Fields and Methods

### Fields (Attributes):
- Represent **state**
- Can be `public`, `private`, etc.

### Methods:
- Represent **behavior**
- Can take parameters and return values

```java
public class Calculator {  
    int add(int a, int b) {  
        return a + b;  
    }  
}
```
---

## 🛠 Accessing Members

- Use **dot (`.`)** notation to access fields or methods of an object.

```java
Calculator calc = new Calculator();  
int sum = calc.add(10, 5);  
System.out.println(sum);  // Output: 15
```
---

## 🧱 Multiple Objects

- You can create multiple instances of a class.

```java 
Person a = new Person();  
Person b = new Person();

a.name = "Alice";  
b.name = "Bob";

a.sayHello();  // Hi, I’m Alice  
b.sayHello();  // Hi, I’m Bob
```
---

## 🔁 Summary

- A **class** defines the structure and behavior of objects.
- An **object** is created using `new` and holds data separately.
- Fields = **data**, Methods = **actions**
- Use the **dot operator** to access members of an object.
- You can create **multiple independent objects** from one class.

# Encapsulation

## 🧠 What is Encapsulation?

- **Encapsulation** is an object-oriented programming principle that bundles data (fields) and the methods that operate on that data within a single class.
- It hides internal details from the outside world to prevent misuse and protect the integrity of the object.
- Encapsulation = **data hiding + controlled access**

---

## 🔐 How to Achieve Encapsulation in Java

1. Declare fields as `private`
2. Provide public **getter** and **setter** methods to access/modify them

---

## 🧱 Example: Encapsulation in Action

```java
class Person {
    private String name;
    private int age;

    // Getter for name
    public String getName() {
        return name;
    }

    // Setter for name
    public void setName(String newName) {
        this.name = newName;
    }

    // Getter for age
    public int getAge() {
        return age;
    }

    // Setter for age
    public void setAge(int newAge) {
        if (newAge > 0) {
            this.age = newAge;
        }
    }
}

class Main {
    public static void main(String[] args) {
      Person person = new Person();
      person.setName("Alice");
      person.setAge(30);

      System.out.println("Name: " + person.getName());
      System.out.println("Age: " + person.getAge());
    }
}
```
---

## ✅ Benefits of Encapsulation

- **Data Hiding**: Internal state is protected from outside interference.
- **Security**: Sensitive fields cannot be accessed directly.
- **Control**: You can apply logic in setters to validate or modify inputs.
- **Flexibility & Maintainability**: Internal code can change without affecting external code.
- **Code Reusability**: Self-contained components are easier to test and reuse.

---

## 🧠 Summary

- Encapsulation binds data and behavior together inside a class.
- Use `private` access for fields and provide `public` getters/setters.
- It enables secure, clean, and modular code.
