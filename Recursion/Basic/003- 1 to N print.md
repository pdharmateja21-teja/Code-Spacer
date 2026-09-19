# 🔹 Recursion — Print Numbers 1 to N

## 📝 What This Code Does

This program takes `n` as input and uses **recursion to print numbers from `1` to `n`**.

The important point is that the recursive call happens **before** the `print` statement. So the function first goes all the way down to `0`, and only then starts printing while returning from the recursive calls.

## 💻 Complete Code

```java
import java.util.*;

public class Main {
    static void recursion(int n) {
        if (n == 0) {
            return;
        }

        recursion(n - 1);
        System.out.print(n + " ");
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

> **First keep calling the function with `n - 1` until `n` becomes 0, then print `n` while returning back.**

Notice the order:

```java
recursion(n - 1);
System.out.print(n + " ");
```

Because `print` comes **after** the recursive call, printing happens during the **returning phase** of recursion.

---

## 🔄 Code Flow

Suppose:

```text
n = 5
```

The first call is:

```text
recursion(5)
```

### Going Down

The function keeps calling itself:

```text
recursion(5)
    ↓
recursion(4)
    ↓
recursion(3)
    ↓
recursion(2)
    ↓
recursion(1)
    ↓
recursion(0)
```

At `n = 0`:

```java
if (n == 0) {
    return;
}
```

The function stops going deeper.

### Coming Back Up

Now the recursive calls start returning.

```text
recursion(1) → print 1
recursion(2) → print 2
recursion(3) → print 3
recursion(4) → print 4
recursion(5) → print 5
```

So the output is:

```text
1 2 3 4 5
```

---

## ▶️ Example Walkthrough

### Input

```text
5
```

### Step-by-Step

```text
recursion(5)
    ↓
    recursion(4)
        ↓
        recursion(3)
            ↓
            recursion(2)
                ↓
                recursion(1)
                    ↓
                    recursion(0)
                    ↓
                    return
                print 1
            print 2
        print 3
    print 4
print 5
```

### Final Output

```text
1 2 3 4 5
```

---

## 🧠 The Most Important Concept

Compare these two:

### Print Before Recursive Call

```java
System.out.print(n + " ");
recursion(n - 1);
```

Output:

```text
5 4 3 2 1
```

### Print After Recursive Call

```java
recursion(n - 1);
System.out.print(n + " ");
```

Output:

```text
1 2 3 4 5
```

So remember:

> **Before recursion → action happens while going down.**
> **After recursion → action happens while coming back.**

---

## 🔑 Quick Recall

**Pattern:**

```text
Go Down → Reach Base Case → Come Back → Print
```

**Base Case:**

```text
n == 0
```

**Quick Recall:**

> The function first reaches `0` by repeatedly calling `recursion(n-1)`. After reaching the base case, it returns upward and prints each `n`, producing `1` to `N`.
