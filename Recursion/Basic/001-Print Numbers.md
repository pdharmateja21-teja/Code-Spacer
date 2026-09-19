# 🔹 Recursion — Print Numbers from 1 to 9

## 📝 What This Code Does

This program uses **recursion** to print numbers from `1` to `9`.

The method `recursion()` keeps calling itself after increasing `count` by `1`. When `count` becomes `10`, the base condition stops the recursion.

## 💻 Complete Code

```java
import java.util.*;

public class Main {
    static void recursion(int count) {
        if (count == 10) {
            return;
        }

        System.out.print(count + "\n");
        count++;
        recursion(count);
    }

    public static void main(String[] args) {
        recursion(1);
    }
}
```

---

## 💡 Core Logic

> **Print the current number → increase it → call the function again → stop when `count` reaches 10.**

The two most important parts are:

```java
if (count == 10) {
    return;
}
```

This is the **base condition** that stops the recursion.

```java
count++;
recursion(count);
```

This increases the value and makes the next recursive call.

---

## 🔄 Code Flow

### Step 1: `main()` starts

```java
recursion(1);
```

The function starts with:

`count = 1`

### Step 2: Check the base condition

```java
if (count == 10)
```

For `count = 1`:

`1 == 10` → `false`

So execution continues.

### Step 3: Print the value

```java
System.out.print(count + "\n");
```

Prints:

`1`

### Step 4: Increment

```java
count++;
```

Now:

`count = 2`

### Step 5: Recursive call

```java
recursion(count);
```

Calls:

`recursion(2)`

The same process repeats until `count` becomes `10`.

---

## 🧠 Important Variable

| Variable | Purpose                                                                   |
| -------- | ------------------------------------------------------------------------- |
| `count`  | Stores the current number being printed and controls when recursion stops |

---

## ▶️ Example Flow

Starting with:

```text
recursion(1)
```

The execution becomes:

```text
recursion(1)
    ↓
print 1
    ↓
count = 2
    ↓
recursion(2)
    ↓
print 2
    ↓
count = 3
    ↓
recursion(3)
    ↓
...
    ↓
recursion(9)
    ↓
print 9
    ↓
count = 10
    ↓
recursion(10)
    ↓
count == 10 → return
```

### Output

```text
1
2
3
4
5
6
7
8
9
```

---

## 🔑 Remember

### Execution Pattern

```text
Check → Print → Increment → Recursive Call
```

### Base Condition

```java
count == 10
```

### Quick Recall

> Start with `1`, print it, increment `count`, and call the same function again. When `count` reaches `10`, `return` stops the recursion.
