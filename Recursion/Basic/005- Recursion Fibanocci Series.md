# 🔹 Recursion — Fibonacci Series

## 📝 What This Code Does

This program takes `n` as input and prints the **first `n` Fibonacci numbers**.

It uses a recursive function `fibanocci()` to calculate each Fibonacci number.

The Fibonacci sequence follows:

```text
0 1 1 2 3 5 8 13 ...
```

Each number is calculated as:

> **Current Fibonacci number = previous number + number before previous**

---

## 💻 Complete Code

```java
import java.util.*;

public class Main {
    static int fibanocci(int n) {
        if (n == 0) {
            return 0;
        }

        if (n == 1) {
            return 1;
        }

        return fibanocci(n - 1) + fibanocci(n - 2);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        for (int i = 0; i < n; i++) {
            System.out.print(fibanocci(i) + " ");
        }
    }
}
```

---

## 💡 Core Logic

There are **two important parts** in this code.

### 1. Fibonacci Base Cases

```java
if (n == 0) {
    return 0;
}

if (n == 1) {
    return 1;
}
```

These are the values from which the recursion starts building the sequence.

```text
fib(0) = 0
fib(1) = 1
```

### 2. Recursive Formula

```java
return fibanocci(n - 1) + fibanocci(n - 2);
```

This follows the Fibonacci formula:

```text
fib(n) = fib(n-1) + fib(n-2)
```

---

## 🔄 Code Flow

Suppose the input is:

```text
5
```

The `for` loop runs:

```java
for(int i = 0; i < 5; i++)
```

So `i` takes:

```text
0 → 1 → 2 → 3 → 4
```

For every `i`, the program calls:

```java
fibanocci(i)
```

### `i = 0`

```text
fibanocci(0)
```

Base case:

```text
return 0
```

Output:

```text
0
```

### `i = 1`

```text
fibanocci(1)
```

Base case:

```text
return 1
```

Output:

```text
0 1
```

### `i = 2`

```text
fibanocci(2)
```

Since `2` is neither `0` nor `1`:

```text
fibanocci(1) + fibanocci(0)
```

```text
1 + 0 = 1
```

Output:

```text
0 1 1
```

### `i = 3`

```text
fibanocci(3)
```

```text
fibanocci(2) + fibanocci(1)
```

We already know:

```text
fibanocci(2) = 1
fibanocci(1) = 1
```

Therefore:

```text
1 + 1 = 2
```

Output:

```text
0 1 1 2
```

### `i = 4`

```text
fibanocci(4)
```

```text
fibanocci(3) + fibanocci(2)
```

```text
2 + 1 = 3
```

Final output:

```text
0 1 1 2 3
```

---

## ▶️ Example — Recursive Flow

For:

```text
fibanocci(4)
```

The function breaks it down like this:

```text
fibanocci(4)
       ↓
fibanocci(3) + fibanocci(2)
       ↓              ↓
fib(2) + fib(1)    fib(1) + fib(0)
       ↓              ↓
   1 + 1            1 + 0
       ↓              ↓
       2              1
        \            /
         \          /
          2 + 1
            ↓
            3
```

Therefore:

```text
fibanocci(4) = 3
```

---

## 🧠 Important Variables

| Variable | Purpose                                                  |
| -------- | -------------------------------------------------------- |
| `n`      | Determines which Fibonacci number needs to be calculated |
| `i`      | Controls how many Fibonacci numbers are printed          |

### Important distinction

Inside:

```java
fibanocci(int n)
```

`n` means **which Fibonacci number** we want.

Inside:

```java
for(int i = 0; i < n; i++)
```

`i` controls **how many Fibonacci numbers we generate**.

---

## 🔑 Most Important Concept

For Fibonacci:

```text
fib(0) = 0
fib(1) = 1
fib(n) = fib(n-1) + fib(n-2)
```

The recursive function keeps splitting into **two recursive calls** until it reaches the base cases `0` and `1`.

---

## ⚠️ Important Observation

This implementation recalculates the same Fibonacci values many times.

For example, calculating:

```text
fibanocci(5)
```

will calculate `fibanocci(3)`, `fibanocci(2)`, etc. multiple times.

So this is a **basic recursive implementation**, mainly useful for understanding recursion and the Fibonacci recurrence. It is not the efficient approach for large `n`.

---

## 🔑 Quick Recall

### Flow

```text
for loop
   ↓
fibanocci(i)
   ↓
Check n == 0 or n == 1
   ↓
If not → fib(n-1) + fib(n-2)
   ↓
Return value
   ↓
Print
```

### One-Line Memory Trick

> **Fibonacci recursion = two branches: `n-1` and `n-2`, with base cases `0 → 0` and `1 → 1`.**

For `n = 5`, the program prints:

```text
0 1 1 2 3
```
