# 03 – Access Modifiers in Java

## 🧠 Key Concepts

- Access modifiers control the **visibility** of classes, fields, constructors, and methods.
- Java provides **four access levels**:
    - `public`
    - `protected`
    - (default) no modifier — also called *package-private*
    - `private`
- Proper use of access modifiers improves **encapsulation** and **code security**.

---

## 🔓 Access Modifier Levels

| Modifier     | Class | Package | Subclass | World |
|--------------|-------|---------|----------|--------|
| `public`     | ✅    | ✅      | ✅       | ✅     |
| `protected`  | ✅    | ✅      | ✅       | ❌     |
| *(default)*  | ✅    | ✅      | ❌       | ❌     |
| `private`    | ✅    | ❌      | ❌       | ❌     |

---

## 🔑 public

- Accessible **from anywhere** (same class, package, subclass, outside world)
- Used for APIs and shared utilities

```java
public class Car {
    public void startEngine() {
        System.out.println("Engine started");
    }
}
```
---
## 🔐 private

- Accessible **only within the same class**
- Most **restrictive access level**
- Commonly used for:
  - Internal variables
  - Helper methods
  - Full encapsulation
```java
public class User {
  private String password;

  private void hashPassword() {
    // logic hidden from outside
  }
}
```
---
## 🏠 (default) — Package-Private

- No keyword = visible **only to other classes in the same package**
- Cannot be accessed from other packages, even in subclasses
- Used for internal logic that shouldn't be exposed externally

```java
class PackageService {
  void internalLogic() {
    System.out.println("Internal use only");
  }
}
```
> This class and method are **not visible outside their package**.
---
## 🧬 protected

- Accessible within:
  - The **same package**
  - **Subclasses**, even in different packages
- Commonly used in **inheritance hierarchies**
```java
public class Animal {
    protected void makeSound() {
        System.out.println("Animal sound");
    }
}

public class Dog extends Animal {
    public void bark() {
        makeSound(); // ✅ allowed
    }
}
```
---
## 🚫 Common Pitfall
```java
package a;
public class A {
    private int x = 10;
}

package b;
public class B extends A {
    void print() {
        System.out.println(x); // ❌ Cannot access private field 'x'
    }
}
```
> Even though `B` is a subclass of `A`, it **cannot access private members**.
---
## 🧠 Use Case Summary

| Use This When...                  | Modifier     |
|----------------------------------|--------------|
| Utility method available to all  | `public`     |
| Sensitive internal logic         | `private`    |
| Share only within the package    | *(default)*  |
| Allow subclass access/override   | `protected`  |

---
## 🔁 Summary
- ✅ Use `private` to **encapsulate** and hide implementation details.
- ✅ Use `public` to expose only the **intended interface** of your class.
- ✅ Use *(default)* for **internal package-level** collaboration.
- ✅ Use `protected` for **extensibility in subclasses**.
- ✅ Choosing the right access level enforces **good design**, **security**, and **maintainability**.