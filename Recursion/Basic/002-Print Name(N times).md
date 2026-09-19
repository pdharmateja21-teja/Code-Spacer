

# 🔹 Recursion — Print "teja" N Times

## 📝 What This Code Does

This program takes a number `n` as input and uses **recursion to print `"teja"` exactly `n` times**.

Each recursive call decreases `n` by `1`. When `n` becomes `0`, the recursion stops.

## 💻 Complete Code

```java
import java.util.*;

public class Main {
    static void recursion(int n) {
        if (n == 0) {
            return;
        }

        System.out.print("teja" + "\n");
        recursion(n - 1);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        recursion(n);
    }
}
```

---

## 💡 Core Logic

The main idea is:

> **Print `"teja"` → decrease `n` by 1 → call the function again → stop when `n` becomes 0.**

The **base condition** is:

```java
if (n == 0) {
    return;
}
```

This stops the recursion.

The recursive part is:

```java
recursion(n - 1);
```

Every call reduces `n`, so eventually it reaches `0`.

---

## 🔄 Code Flow

### Step 1: Take input

```java
int n = sc.nextInt();
```

Suppose the input is:

```text
5
```

So:

```text
n = 5
```

### Step 2: Call recursion

```java
recursion(n);
```

This becomes:

```text
recursion(5)
```

### Step 3: Check base condition

```java
if (n == 0)
```

For `n = 5`:

```text
5 == 0 → false
```

So execution continues.

### Step 4: Print `"teja"`

```java
System.out.print("teja" + "\n");
```

Output:

```text
teja
```

### Step 5: Decrease `n`

```java
recursion(n - 1);
```

So:

```text
5 → 4
```

and the function calls:

```text
recursion(4)
```

The same process continues until `n = 0`.

---

## ▶️ Example Walkthrough

### Input

```text
5
```

### Function Calls

```text
recursion(5)
    ↓
print "teja"
    ↓
recursion(4)
    ↓
print "teja"
    ↓
recursion(3)
    ↓
print "teja"
    ↓
recursion(2)
    ↓
print "teja"
    ↓
recursion(1)
    ↓
print "teja"
    ↓
recursion(0)
    ↓
n == 0 → return
```

### Final Output

```text
teja
teja
teja
teja
teja
```

---

## 🧠 Important Variable

| Variable | Purpose                                                              |
| -------- | -------------------------------------------------------------------- |
| `n`      | Controls how many times `"teja"` is printed and when recursion stops |

---

## 🔑 Remember

### Execution Pattern

```text
Check → Print → Decrease n → Recursive Call
```

### Base Condition

```text
n == 0
```

### Quick Recall

> If `n` is greater than `0`, print `"teja"` and call the same function with `n - 1`. When `n` reaches `0`, return and stop.

**Key idea:** `n` represents the **number of remaining prints**.

