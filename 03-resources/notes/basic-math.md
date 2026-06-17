---
mocs:
    - "[[public-notes/03-resources/math.moc.md|Math]]"
tags:
    - math/basics
---

## 1 - [[sequences]]

# Axiomatic Foundations
fundamental properties of and operations on numbers can be derived. frameworks that can be used to formulate [mathematical proofs](https://en.wikipedia.org/wiki/Mathematical_proof "Mathematical proof") in a rigorous manner. Two well-known approaches are the [Dedekind–Peano axioms](https://en.wikipedia.org/wiki/Dedekind%E2%80%93Peano_axioms "Dedekind–Peano axioms") and [set-theoretic](https://en.wikipedia.org/wiki/Set-theoretic "Set-theoretic") constructions

- 0 is a natural number.
- For every natural number, there is a successor, which is also a natural number.
- The successors of two different natural numbers are never identical.
- 0 is not the successor of a natural number.
- If a set contains 0 and every successor then it contains every natural number.

# Arithmetic
+ elementary branch of maths that studies numerical the 4 operations: addition, substraction, multiplication and division.
# Number Theory
studies the structure and properties of integers as well as the relations and laws between them.
+ **Elementary Number Theory Topics**: divsibiliy, factorization, primality
## Fundamental Theorem of Arithmetic
+ every integer greater than 1 is either a prime number or can be represented as a unique product of prime numbers.

## Modular Arithmetic
+ Operates on a finite set of numbers. If an operation would result in a number outside this finite set then the number is adjusted back into the set
![[Pasted image 20241221173317.png]]
Example of modular arithmetic using a clock: after adding 4 hours to 9 o'clock, the hand starts at the beginning again and points at 1 o'clock.

## Less common multiple (LCM)
+ Minimo Comun Multiplo
+ The least common multiple of more than two integers _a_, _b_, _c_, . . . , usually denoted by lcm(_a_, _b_, _c_, . . .), is defined as the smallest positive integer that is divisible by each of _a_, _b_, _c_, . . . .

También
$$ \text{lcm}(a,b) = \frac{|ab|}{\text{gcd}(a,b)}$$

![[Pasted image 20241221180739.png]]
## Greatest Common Divisor (GCD)
also known as **greatest common factor (GCF)**, of two or more [integers](https://en.wikipedia.org/wiki/Integer "Integer"), which are not all zero, is the largest positive integer that [divides](https://en.wikipedia.org/wiki/Divides "Divides") each of the integers

> Mayor número que los divide sin dejar resto

![[Pasted image 20241221181134.png]]