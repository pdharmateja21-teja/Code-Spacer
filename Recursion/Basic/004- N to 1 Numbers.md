# 🔹 Recursion — Print N to 1

## 📝 What This Code Does

This program takes `n` as input and uses recursion to print numbers from **`n` down to `1`**.

The number is printed **before** making the recursive call. Then `n` is decreased by `1` until it reaches `0`.

## 💻 Complete Code

```java
import java.util.*;

public class Main {
    static void recursion(int n) {
        if (n == 0) {
            return;
        }

        System.out.print(n + " ");
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

The key idea is:

> **Print `n` → decrease `n` → call the function again → stop when `n` becomes 0.**

The important order is:

```java
System.out.print(n + " ");
recursion(n - 1);
```

Since `print` comes **before** the recursive call, the printing happens while **going down** through the recursive calls.

---

## 🔄 Code Flow

Suppose the input is:

```text
5
```

### Going Down

```text
recursion(5)
↓
print 5
↓
recursion(4)
↓
print 4
↓
recursion(3)
↓
print 3
↓
recursion(2)
↓
print 2
↓
recursion(1)
↓
print 1
↓
recursion(0)
```

At `n = 0`:

```java
if (n == 0) {
    return;
}
```

The function stops.

### Output

```text
5 4 3 2 1
```

---

## ▶️ Example Walkthrough

### Input

```text
5
```

### Step-by-Step

| Call           | Action    | Next Call      |
| -------------- | --------- | -------------- |
| `recursion(5)` | Print `5` | `recursion(4)` |
| `recursion(4)` | Print `4` | `recursion(3)` |
| `recursion(3)` | Print `3` | `recursion(2)` |
| `recursion(2)` | Print `2` | `recursion(1)` |
| `recursion(1)` | Print `1` | `recursion(0)` |
| `recursion(0)` | Return    | Stop           |

Final output:

```text
5 4 3 2 1
```

---

## 🧠 Important Variable

| Variable | Purpose                                                        |
| -------- | -------------------------------------------------------------- |
| `n`      | Current number being printed and controls when recursion stops |

---

## 🔑 Most Important Concept

Compare this code with the previous one:

### Print Before Recursion

```java
System.out.print(n + " ");
recursion(n - 1);
```

**Output:**

```text
5 4 3 2 1
```

### Print After Recursion

```java
recursion(n - 1);
System.out.print(n + " ");
```

**Output:**

```text
1 2 3 4 5
```

So remember:

> **Before recursive call → action happens while going DOWN.**
> **After recursive call → action happens while coming BACK.**

---

## 🔑 Quick Recall

```text
Check → Print → Decrease → Recursive Call
```

**Base Case:**

```text
n == 0
```

**Quick Recall:**

> Start from `n`, print it immediately, decrease it by `1`, and repeat until `n` becomes `0`. Because printing happens before recursion, the output is `N → 1`.
