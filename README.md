# C DSA Assignment

**Course:** BCA  
**Subject:** C DSA  
**Assignment:** Stack and Circular Queue Using Arrays  
**Submission Deadline:** 7 October 2026

---

## Contents

- [Question 1 – Stack Using Array](#question-1--stack-using-array)
- [Question 2 – Circular Queue Using Array](#question-2--circular-queue-using-array)
- [How to Compile and Run](#how-to-compile-and-run)
- [Conclusion](#conclusion)

---

# Question 1 – Stack Using Array

## Problem Statement

Design and implement a stack using an array without using any built-in stack library.

The program supports:

- `PUSH(x)`
- `POP()`
- `PEEK()`
- `DISPLAY()`

The program also handles Stack Overflow and Stack Underflow conditions.

## Theory

A **stack** is a linear data structure that follows the **LIFO (Last In, First Out)** principle. The element inserted last is the first element to be removed.

In an array implementation, a variable called `top` keeps track of the top element of the stack.

Initially:

```text
top = -1
```

When an element is pushed, `top` is increased and the element is stored at that position.

When an element is popped, the element at `top` is removed and `top` is decreased.

## Operations

### PUSH(x)

Adds an element to the top of the stack.

If `top == MAX - 1`, the stack is already full and **Stack Overflow** occurs.

### POP()

Removes the top element from the stack.

If `top == -1`, the stack is empty and **Stack Underflow** occurs.

### PEEK()

Displays the top element without removing it.

### DISPLAY()

Displays all elements currently present in the stack from top to bottom.

## Complexity Analysis

| Operation | Time Complexity | Space Complexity |
|---|---:|---:|
| PUSH | O(1) | O(1) |
| POP | O(1) | O(1) |
| PEEK | O(1) | O(1) |
| DISPLAY | O(n) | O(1) |

The overall stack requires **O(n)** space for an array of capacity `n`.

## Fixed Stack Size and Overflow

The stack in this program has a fixed capacity of 5 elements.

If the stack is full and the user attempts to insert another element, the program does not insert the element. Instead, it displays a **Stack Overflow** message.

This happens because an array with fixed size cannot store elements beyond its allocated capacity.

## Source Code

The complete program is available in:

`Q1_Stack/stack.c`

---

# Question 2 – Circular Queue Using Array

## Problem Statement

Implement a circular queue using an array.

The program supports:

- `ENQUEUE(x)`
- `DEQUEUE()`
- `FRONT()`
- `DISPLAY()`

The implementation correctly distinguishes between a full queue and an empty queue.

## Theory

A **queue** is a linear data structure that follows the **FIFO (First In, First Out)** principle. The element inserted first is removed first.

A **circular queue** treats the last position of the array as connected to the first position. Therefore, when `rear` reaches the last index, it can wrap around to the beginning of the array.

The circular movement is implemented using:

```c
(rear + 1) % MAX
```

and:

```c
(front + 1) % MAX
```

## Operations

### ENQUEUE(x)

Adds an element at the rear of the queue.

The queue is considered full when:

```c
(rear + 1) % MAX == front
```

### DEQUEUE()

Removes an element from the front of the queue.

If the queue contains only one element, both `front` and `rear` are reset to `-1`.

### FRONT()

Displays the element currently at the front without removing it.

### DISPLAY()

Displays all elements from `front` to `rear`, including elements that wrap around to the beginning of the array.

## Circular Queue vs Linear Queue

| Feature | Linear Queue | Circular Queue |
|---|---|---|
| Memory utilization | Can leave unused positions at the beginning | Reuses freed positions |
| Movement of rear | Moves only forward | Wraps around |
| ENQUEUE | O(1) | O(1) |
| DEQUEUE | O(1) | O(1) |
| Space | O(n) | O(n) |
| Reuses deleted positions | Not efficiently in a simple array implementation | Yes |

### 1. Why does a circular queue provide better memory utilization?

In a simple linear queue, after elements are removed from the front, those positions may remain unused even though there is free space.

A circular queue solves this problem by allowing `rear` to wrap around to the beginning of the array and reuse those positions.

### 2. Time Complexity

- `ENQUEUE` → **O(1)**
- `DEQUEUE` → **O(1)**
- `FRONT` → **O(1)**
- `DISPLAY` → **O(n)**

### 3. Space Complexity

A circular queue using an array of capacity `n` requires **O(n)** space.

### 4. Problem in a Linear Queue

Suppose a linear queue has five positions:

```text
[10][20][30][40][50]
```

After removing the first three elements:

```text
[ ][ ][ ][40][50]
```

The first three positions are unused, but `rear` is already at the last index.

In a simple linear array implementation, another element cannot be inserted even though free positions exist at the beginning. This is the **false overflow / wasted-space problem** that a circular queue avoids.

## Source Code

The complete program is available in:

`Q2_Circular_Queue/circular_queue.c`

---

# How to Compile and Run

## Stack

Open a terminal in the `Q1_Stack` folder and run:

```bash
gcc stack.c -o stack
```

Then:

```bash
./stack
```

On Windows, you can run:

```bash
stack.exe
```

## Circular Queue

Open a terminal in the `Q2_Circular_Queue` folder and run:

```bash
gcc circular_queue.c -o circular_queue
```

Then:

```bash
./circular_queue
```

On Windows:

```bash
circular_queue.exe
```

---

# Conclusion

This assignment implements two important data structures using arrays in C.

The first program demonstrates a stack using the LIFO principle and handles both overflow and underflow.

The second program demonstrates a circular queue using the FIFO principle and improves memory utilization by reusing positions freed at the beginning of the array.

Both implementations demonstrate the basic operations and their time and space complexities.
