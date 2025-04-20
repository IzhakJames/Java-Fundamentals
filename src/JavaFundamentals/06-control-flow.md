# 06 – Control Flow Statements

## 🧠 Key Concepts

- Control flow statements alter the **natural top-to-bottom flow** of execution.
- They enable decisions, repetitions, and early exits in Java programs.

---
## 🔀 Conditional Statements
### `if`, `else if`, `else`
- Used for decision-making based on conditions.
```java
if (score >= 90) {
    System.out.println("Excellent");  
} else if (score >= 60) {
    System.out.println("Pass");  
} else {
    System.out.println("Fail");  
}
```
---

### `switch` Statement
- Used to match a variable against multiple constant values.
```java
switch (day) {  
    case 1: 
        System.out.println("Monday");
        break;  
    case 2: 
        System.out.println("Tuesday");
        break;  
    default: 
        System.out.println("Other day");  
}
```

---

## 🔁 Loops
### `for` Loop
- Best when the number of iterations is known.
```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);  
}
```

---

### `while` Loop
- Executes a block repeatedly **while a condition is true**.
```java
int i = 0;  
while (i < 5) {  
    System.out.println(i);  
    i++;  
}
```

---

### `do-while` Loop
- Executes the block **at least once**, condition is checked after.
```java
int i = 0;  
do {  
    System.out.println(i);  
    i++;  
} while (i < 5);

```
---

## 🧭 Branching Statements
### `break`
- Terminates the loop or `switch` statement.
```java
for (int i = 0; i < 5; i++) {  
    if (i == 3) break;  
    System.out.println(i);  
}
```

---

### `continue`
- Skips the current iteration and moves to the next.
```java
for (int i = 0; i < 5; i++) {  
    if (i == 2) continue;  
    System.out.println(i);  
}
```

---

### `return`
- Exits the current method and optionally returns a value.
```java
int add(int a, int b) {  
    return a + b;  
}
```
---

## 🔁 Summary

- Use `if` / `else` for condition-based logic.
- Use `switch` for multiple fixed-value conditions.
- Use `for`, `while`, or `do-while` for repetition.
- Use `break` to exit loops or switch blocks.
- Use `continue` to skip to the next iteration in a loop.
- Use `return` to exit a method, optionally returning a result.
