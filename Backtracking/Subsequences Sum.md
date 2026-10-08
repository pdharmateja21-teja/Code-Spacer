# 🔹 Subsequences With Sum K

## 📝 What This Code Does

This program finds and prints **all subsequences of an array whose elements add up to `k`**.

For the array:

```text
[1, 2, 1]
```

and:

```text
k = 2
```

the valid subsequences are:

```text
[1, 1]
[2]
```

The code uses **recursion to make two choices for every element**:

> **Take the element OR skip the element.**

It also uses **backtracking** to remove an element after exploring the "take" choice.

---

## 💻 Complete Code

```java
import java.util.*;

public class Main {

    static void printSubsequences(int[] arr, int index, int sum, int k, ArrayList<Integer> current) {

        if (index == arr.length) {
            if (sum == k) {
                System.out.println(current);
            }
            return;
        }

        current.add(arr[index]);
        printSubsequences(arr, index + 1, sum + arr[index], k, current);

        current.remove(current.size() - 1);
        printSubsequences(arr, index + 1, sum, k, current);
    }

    public static void main(String[] args) {

        int[] arr = {1, 2, 1};
        int k = 2;

        printSubsequences(arr, 0, 0, k, new ArrayList<>());
    }
}
```

---

## 💡 Core Logic

For every element, there are exactly **two choices**:

```text
                 Element
                /       \
             Take       Skip
```

For example, for `1`:

```text
Take 1
   OR
Skip 1
```

The code implements this as:

### Choice 1 — Take

```java
current.add(arr[index]);
printSubsequences(arr, index + 1, sum + arr[index], k, current);
```

The current element is added to the subsequence and its value is added to `sum`.

### Choice 2 — Skip

Before making the skip call:

```java
current.remove(current.size() - 1);
```

This is **backtracking**.

Then:

```java
printSubsequences(arr, index + 1, sum, k, current);
```

The element is skipped, so `sum` remains unchanged.

---

# 🔄 Code Flow

There are **5 important things** to track:

| Variable  | Meaning                                   |
| --------- | ----------------------------------------- |
| `arr`     | Original array                            |
| `index`   | Which element we are currently processing |
| `sum`     | Sum of elements currently selected        |
| `k`       | Required target sum                       |
| `current` | Current subsequence being built           |

---

## 1️⃣ Starting Point

From `main()`:

```java
printSubsequences(arr, 0, 0, k, new ArrayList<>());
```

So initially:

```text
arr     = [1, 2, 1]
index   = 0
sum     = 0
k       = 2
current = []
```

---

## 2️⃣ Base Condition

```java
if (index == arr.length)
```

When:

```text
index == 3
```

we have processed every element.

Then:

```java
if (sum == k)
```

checks whether the selected elements have the required sum.

If yes:

```java
System.out.println(current);
```

prints the subsequence.

---

# ▶️ Example Walkthrough

Array:

```text
[1, 2, 1]
```

Target:

```text
k = 2
```

We can visualize the recursion as:

```text
                         []
                    /          \
                 Take 1       Skip 1
                  [1]            []
                /    \          /    \
            Take 2  Skip 2   Take 2  Skip 2
             [1,2]   [1]       [2]     []
             /  \     / \       / \     / \
            ... ...  ... ...   ... ... ... ...
```

Let's follow the important branches.

---

## 🌳 Branch 1: Take `1`

Initially:

```text
current = []
sum = 0
```

Take `1`:

```text
current = [1]
sum = 1
```

Then move to index `1`.

---

### Take `2`

```text
current = [1, 2]
sum = 3
```

Now process the final `1`.

If we take it:

```text
current = [1, 2, 1]
sum = 4
```

`4 != 2`, so nothing is printed.

Then backtrack:

```text
[1, 2, 1] → [1, 2]
```

Skip the final `1`.

Still:

```text
sum = 3
```

`3 != 2`.

So this branch produces nothing.

---

### Backtrack and Skip `2`

We remove `2`:

```text
[1, 2] → [1]
```

Now skip `2`.

So:

```text
current = [1]
sum = 1
```

Now process the final `1`.

Take it:

```text
current = [1, 1]
sum = 2
```

We reach the end:

```text
index == arr.length
```

and:

```text
sum == k
2 == 2
```

So:

```text
[1, 1]
```

is printed.

---

# 🌳 Branch 2: Skip First `1`

After completely exploring the first `1` branch, we return to:

```text
current = []
sum = 0
```

This happens because of:

```java
current.remove(current.size() - 1);
```

Now we skip the first `1`.

```text
current = []
sum = 0
```

---

### Take `2`

```text
current = [2]
sum = 2
```

Now process the final `1`.

If we take it:

```text
current = [2, 1]
sum = 3
```

Not valid.

Backtrack:

```text
[2, 1] → [2]
```

Skip the final `1`.

Now:

```text
current = [2]
sum = 2
```

At the end:

```text
sum == k
2 == 2
```

So:

```text
[2]
```

is printed.

---

# 🔄 Complete Recursion Idea

The entire process can be remembered as:

```text
                    []
                  /    \
               Take    Skip
                1        1
               /          \
            [1]            []
           /   \          /   \
        Take   Skip     Take   Skip
         2       2       2       2
```

Every element creates **two branches**.

Eventually, every possible subsequence is explored.

---

## 🧠 Why Do We Need `remove()`?

This is one of the most important parts of the code:

```java
current.remove(current.size() - 1);
```

Suppose we have:

```text
current = [1, 2]
```

We just finished exploring the branch where `2` was selected.

Before exploring the branch where `2` is skipped, we need to restore:

```text
current = [1]
```

That's exactly what `remove()` does.

This is called **backtracking**:

```text
Choose
  ↓
Explore
  ↓
Undo choice
  ↓
Explore next choice
```

---

## 🔑 Most Important Pattern

This code follows the classic **Take / Not Take** recursion pattern:

```java
current.add(arr[index]);

// Take
printSubsequences(...);

current.remove(current.size() - 1);

// Not Take
printSubsequences(...);
```

Remember it as:

```text
               Element
              /       \
           TAKE       NOT TAKE
            ↓            ↓
         Explore      Explore
            ↓            ↓
        Backtrack
```

---

## 📌 Quick Recall

> At every index, make two choices: **include the element or exclude it**. If included, add it to `current` and `sum`. After exploring that branch, remove it using backtracking and explore the branch where the element is skipped. When all elements are processed, print `current` only if `sum == k`.

### For this example

```text
arr = [1, 2, 1]
k = 2
```

Output:

```text
[1, 1]
[2]
```

### One-line memory trick

> **Take → Explore → Undo → Skip → Explore**

This pattern is extremely important for learning **subsequences, subsets, combination problems, and backtracking**.
