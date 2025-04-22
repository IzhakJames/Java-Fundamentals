# 08 – Constructors

## 🧠 What is a Constructor?

- A **constructor** is a special method in Java used to initialize objects.
- It is called automatically when a new object is created.
- Constructors have the same name as the class and do not have a return type.

---

## 🧱 Syntax of a Constructor

```java
class ClassName {
    // Constructor
    ClassName() {
        // initialization code
    }
}
```

- The constructor name must match the class name.
- Constructors do not have a return type, not even `void`.

---

## 🔹 Types of Constructors

### 1. Default Constructor

- Provided by Java if no constructor is defined.
- Initializes object with default values.

```java
class Car {
    String model;
    int year;

    // No constructor defined

    public static void main(String[] args) {
        Car car = new Car();
        System.out.println(car.model); // Outputs: null
        System.out.println(car.year);  // Outputs: 0
    }
}
```
### 2. No-Argument Constructor

- A constructor without parameters.
- Used to set default values.

```java
class Car {
    String model;
    int year;

    // No-argument constructor
    Car() {
        model = "Toyota";
        year = 2020;
    }

    public static void main(String[] args) {
        Car car = new Car();
        System.out.println(car.model); // Outputs: Toyota
        System.out.println(car.year);  // Outputs: 2020
    }
}
```
### 3. Parameterized Constructor

- Accepts parameters to set initial values.

```java
class Car {
    String model;
    int year;

    // Parameterized constructor
    Car(String m, int y) {
        model = m;
        year = y;
    }

    public static void main(String[] args) {
        Car car = new Car("Honda", 2021);
        System.out.println(car.model); // Outputs: Honda
        System.out.println(car.year);  // Outputs: 2021
    }
}
```
### 4. Copy Constructor

- Creates a new object by copying another object.
- Java doesn't provide a default copy constructor; it must be defined manually.

```java
class Car {
    String model;
    int year;

    // Parameterized constructor
    Car(String m, int y) {
        model = m;
        year = y;
    }

    // Copy constructor
    Car(Car c) {
        model = c.model;
        year = c.year;
    }

    public static void main(String[] args) {
        Car car1 = new Car("Ford", 2019);
        Car car2 = new Car(car1);
        System.out.println(car2.model); // Outputs: Ford
        System.out.println(car2.year);  // Outputs: 2019
    }
}
```
---

## 🔁 Constructor Overloading

- Multiple constructors with different parameter lists.

```java
class Car {
    String model;
    int year;

    // No-argument constructor
    Car() {
        model = "Default";
        year = 2000;
    }

    // Parameterized constructor
    Car(String m, int y) {
        model = m;
        year = y;
    }

    public static void main(String[] args) {
        Car car1 = new Car();
        Car car2 = new Car("BMW", 2022);
        System.out.println(car1.model); // Outputs: Default
        System.out.println(car2.model); // Outputs: BMW
    }
}
```
---

## 🔐 Access Modifiers in Constructors

- Constructors can have access modifiers to control object creation.

```java
class Car {
    String model;
    int year;

    // Private constructor
    private Car() {
        model = "Private";
        year = 2020;
    }

    public static void main(String[] args) {
        // Car car = new Car(); // Error: constructor is private
    }
}
```
- Private constructors are used in Singleton patterns to restrict object creation.

---

## 🧠 Summary

- Constructors initialize new objects.
- Types: Default, No-Argument, Parameterized, Copy.
- Constructors can be overloaded.
- Access modifiers control the visibility of constructors.
