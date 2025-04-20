# 05 – Operators and Expressions

## 🧠 Key Concepts

- **Operators** are special symbols used to perform operations on variables and values.
- **Expressions** are combinations of variables, values, and operators that are evaluated to produce a result.

---

## ➕ Arithmetic Operators

| Operator | Description       | Example        |
|----------|-------------------|----------------|
| `+`      | Addition           | `a + b`        |
| `-`      | Subtraction        | `a - b`        |
| `*`      | Multiplication     | `a * b`        |
| `/`      | Division           | `a / b`        |
| `%`      | Modulus (remainder)| `a % b`        |

```java
int a = 10, b = 3;
System.out.println(a % b);  // 1
```
---
## 🧮 Assignment Operators

| Operator | Description         | Example     |
|----------|---------------------|-------------|
| `=`      | Assign              | `a = 5`     |
| `+=`     | Add and assign      | `a += 2`    |
| `-=`     | Subtract and assign | `a -= 3`    |
| `*=`     | Multiply and assign | `a *= 4`    |
| `/=`     | Divide and assign   | `a /= 2`    |
| `%=`     | Modulus and assign  | `a %= 2`    |

---

## ⚖️ Comparison (Relational) Operators

| Operator | Description       | Example     |
|----------|-------------------|-------------|
| `==`     | Equal to          | `a == b`    |
| `!=`     | Not equal to      | `a != b`    |
| `>`      | Greater than      | `a > b`     |
| `<`      | Less than         | `a < b`     |
| `>=`     | Greater or equal  | `a >= b`    |
| `<=`     | Less or equal     | `a <= b`    |

```java
int x = 10;
System.out.println(x > 5);  // true
```
---
## 🔁 Logical Operators

| Operator | Description             | Example         |
|----------|-------------------------|-----------------|
| &&       | Logical AND             | `a > 0 && b > 0` |
| ll       | Logical OR              | `a > 0 ll b > 0` |
| !        | Logical NOT (negation)  | `!(a > 0)`      |

- Here in the table the ll refers to || (pipe operator)
```java
int age = 20;
boolean isAdult = (age >= 18 && age < 65);
boolean isTeenOrSenior = (age < 18 || age > 64);
```
---
## 🧠 Unary Operators

| Operator | Description   | Example         |
|----------|---------------|-----------------|
| `+`      | Unary plus    | `+a`            |
| `-`      | Unary minus   | `-a`            |
| `++`     | Increment     | `a++` or `++a`  |
| `--`     | Decrement     | `a--` or `--a`  |

---

## 🔀 Ternary Operator

A shorthand for `if-else`:
```java
String result = (score >= 50) ? "Pass" : "Fail";
```
---
## 🧩 Bitwise Operators (Advanced)

| Operator   | Description  |
|------------|--------------|
| `&`        | AND          |
| `l` (pipe) | OR           |
| `^`        | XOR          |
| `~`        | Complement   |
| `<<`       | Left shift   |
| `>>`       | Right shift  |

---

## 🎯 Operator Precedence (Top to Bottom)

1. `()` – Parentheses
2. `++` / `--` – Unary
3. `*`, `/`, `%` – Multiplicative
4. `+`, `-` – Additive
5. `<`, `>`, `<=`, `>=` – Relational
6. `==`, `!=` – Equality
7. `&&` – Logical AND
8. `||` – Logical OR
9. `?:` – Ternary
10. `=`, `+=`, `-=` – Assignment

---

## 🔁 Summary

- Operators allow manipulation of values and control logic.
- Java supports **arithmetic**, **relational**, **logical**, **assignment**, **unary**, and **bitwise** operators.
- Use the **ternary operator** for concise conditions.
- Understand **operator precedence** to avoid bugs in complex expressions.
