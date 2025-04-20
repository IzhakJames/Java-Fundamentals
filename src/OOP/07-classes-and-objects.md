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
