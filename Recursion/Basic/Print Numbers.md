Print Numbers Using Recursion in Java

A simple Java program that demonstrates the fundamentals of recursion by printing numbers from 1 to 9.

📌 Overview

Recursion is a technique where a method calls itself to solve a problem step by step.

In this program, the recursion() method prints the current number, increments it, and calls itself again until it reaches the stopping condition.

💻 Code
public class Main {

    static void recursion(int count) {

        // Base condition
        if (count == 10) {
            return;
        }

        // Print the current number
        System.out.println(count);

        // Increment the count
        count++;

        // Recursive call
        recursion(count);
    }

    public static void main(String[] args) {
        recursion(1);
    }
}

🧠 Main Logic

The program follows these steps:

recursion(1) starts the recursive process with count = 1.

The method checks whether count == 10.

If the condition is false, the current value is printed.

count is incremented by 1.

The method calls itself with the updated value.

This process continues until count becomes 10.

When count == 10, the base condition is satisfied and the method returns.

🔄 Execution Flow
recursion(1)
     ↓
print 1
     ↓
recursion(2)
     ↓
print 2
     ↓
   ...
     ↓
recursion(9)
     ↓
print 9
     ↓
recursion(10)
     ↓
Base condition → return

🔑 Key Concepts

Recursion — A method calling itself.

Base Condition — count == 10 stops the recursive calls.

Recursive Call — recursion(count) calls the method again.

Increment — count++ moves to the next number.

Starting Point — recursion(1) starts the sequence from 1.

📤 Output
1
2
3
4
5
6
7
8
9

⏱️ Complexity

Time Complexity: O(n) — The method is called once for each number.

Space Complexity: O(n) — Each recursive call remains on the call stack until the base condition is reached.

🎯 Key Takeaway

This example demonstrates the basic structure of a recursive function:

Base Condition
      +
Recursive Call
      +
Progress Toward Base Condition


Every recursive solution should have a base condition to stop the recursion and a recursive call that moves the problem toward that condition.
