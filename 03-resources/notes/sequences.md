---
mocs:
    - "[[public-notes/03-resources/math.moc.md|Math]]"
tags:
    - math/basics
---

# Sequence
Enumerated collection of objects, repetitions allowed, order matters, can have infinite number of elements

+ frormally, a sequence can be defined as a function, from $\mathbb{N}$ (it position / index or rank) to the elements of each position
+ in mathematical analysis tipically denoted as $a_n$ or the list of all elements (1, 2, 3, 4, 5, ...), $(a_n)_{n \in \mathbb{N}}$, $(k^2)_{k=1}^{10}$
+ **Term**: Each element of the sequence
+ **Rule**: Formula to find $n$th term

**In Computer sience**
+ Finite sequences are strings or lists
+ infinite sequenceas are streams

## Progression vs Sequences
+ **Sequences** are a set of numbers that are arranged or defined according to any specific rule which mean there is something common between them.  
+ **Progressions** are a set of numbers which are defined by some definite rule. It has a specific formula to find its terms.
## Recursive Sequences
+ Defined by a rule, called **recurrence relation** to construct each element in terms of the ones before it. initial elemetns must by prqoveded. e.g Fibonacci $a_n = a_{an-1} + a_{n-2}$ where $a_0 =0$ and $a_1 = 1$

# Some sequences
## Arithmetic Progression
+ each term with the previous one has a **common difference**
+ Formula for $n$th term:
	+ $d$ is the **common difference**
$$a_n = a_1 + (n-1)d$$
e.g
+ $(3,8,13,23)$ where $d=5$ then $t_n = 3 + (n-1)5$
## Geometric Progression
+ each term with the previous one has a **common ratio** (razón)
+ Formula for $n$th term:
	+ $r$ is the ratio
$$ a_n = a_1 \cdot r^{n-1}$$
e.g
+ $(2,-6,18,-54,163)$ where $r=-3$ then $a_n = 2 (-3)^{n-1}$
## Quadratic Sequence
is a quadratic seq iff:
+ Fisrt difference is distinc between each term
+ Second difference is equal between each term
The rule is in the form:
$$ a_n = an^2+bn+c$$
replace $n$ by $1,2,3$ and equal them to $a_i$ respectively to get 3 equations to solve the equations system to get $a$, $b$ and $c$ constants

$$ \left\{
\begin{array}{lr}
a + b + c = a_1\\
4a+2b+c = a_2\\
9a+3b+c = a_3
\end{array}
\right.$$
e.g:
Find the rule of the quadratic sequence
![[Pasted image 20241221122218.png]]
