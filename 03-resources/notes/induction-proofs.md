---
mocs:
    - "[[public-notes/03-resources/discrete-math.moc.md|Discrete Math]]"
tags:
    - math/discrete
---

# 1 - Induction Proofs
+ Is a Method for proving that a statement $P(n)$  is true for every natural number $n$ 
+ Mathematical induction can be informally illustrated by reference to the sequential effect of falling dominoes

## General Form of an Inductive Proof
Assume we wish to prove a statement $P(n)$ where $n≥c$, where $c$ is a natural number, often (but not always) $0$ or $1$. or example, our statement might be “A full binary trees of depth $n ≥ 0$ has exactly $2^{n+1} − 1$ nodes” or “$\sum_{i=1}^{n} \frac{n \cdot (n+1)}{2}$
for all $n≥1$”. The basic skeleton of an inductive proof is the following:

1. ==**State what we want to prove**==: $P(n)$ for all $n \geq c$ by induction
2.  ==**State and Proof The Base Case**==: Prove $P(c)$ (explicitly computing values)
3. ==**Inductive Hypothesis**==: Let $k≥c$ be an arbitrary integer. Assume $P(k)$ is true. (Some induction proofs require that we assume P (n) is true for all $c ≤ n ≤ k$ That proof technique is called Strong Induction.)
4. ==**Inductive Step**==: Prove $P (k + 1)$, assuming that $P (k)$ is true.
5. ==**Write the induction rule**==: $(P(c)\&P (k) \rightarrow P (k + 1) \forall k \geq c) \rightarrow P (n)\forall  n \geq c$
## Examples
![[Pasted image 20240711103523.png]]
