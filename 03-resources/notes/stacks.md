---
mocs:
    - "[[public-notes/03-resources/algorithms.moc.md|Algorithms & Data Structures]]"
tags:
    - cs/algorithms
---

+ Linear Data Structure
+ LIFO (Last In, First Out) Principle
+ Pile of plates as an example of real life

## Types of stacks
+ **Fixed Size Stack**: Cannot grow or shrink dynamically, if is full and an element is added (overflow error) or if its empty and an element is popped and error (underflow error) occurs.
+ **Dynamic Size Stack**: Can grow or shrink dynamically.implemented using a Linked List

## Basic Operations
+ push(): $O\left(1\right)$ 
+ pop(): $O\left(1\right)$ 
+ top(): $O\left(1\right)$ (a.k.a peek())
+ isEmpty(): $O\left(1\right)$ 
+ isFull(): $O\left(1\right)$ 

## Applications
+ function calls
+  Recursion
- Expression Evaluation and Parsing - infix / postfix / prefix conversion
- Depth-First Search (DFS)
- Undo/Redo Operations
- Browser History
## Problems:
### 1. convert infix exp to postfix
1. iterate through the exp from left to right
2. use a stack for operators
3. append operands to string
4. Think :)