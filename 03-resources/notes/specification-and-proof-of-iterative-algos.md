---
mocs:
    - "[[public-notes/03-resources/algorithms.moc.md|Algorithms & Data Structures]]"
tags:
    - cs/algorithms
---


+ An iterative algo is a function of states such as: $S_0\to S_1\to\ldots\to S_{n}$

### Loop Invariant
+ An assertion that we prove to be true each time a loop iteration starts
+ Loop Invariants help us to proof the correctness of an iterative algorithm.

### Specification

> La especificación de un algoritmo A es la definición de un problema en términos de sus condiciones de entrada: Q (precondición) y sus condiciones de salida: R (postcondición).

+ Input
+ Output
+ Idea of iteration
+ States (Invariant)
+ Init state
+ Final State
+ State's Transformation
#### 1. Ex. Define the specification
```Python
def fact(n):
	i = 0
	result = 1
	while i <= n:
		i += 1
		result *= i
	return result
```

+ Input: $n\ge0\land n\in\mathbb{N}$
+ Output: `resutlado =` $n!$
+ State: Tuple of the form (i, result) => i <= n  and result = i!
+ Idea: Ascendant iteration: (0,1)->(1,1)->(2,2)->(n,n!)
+ $S_0$ : (0,1)
+ $S_{f}$ : i = n
+ State Transformation: (i, resultado) -> (i + 1 , resultado)
#### 2. Ex. Define the specification
```Python
def fact(n):
	i = n
	result = n
	while i >= 1:
		i -=1
		result += i
	return result
```
+ Input: $n\ge0\land n\in\mathbb{N}$
+ Output: `resutlado =` $n!$
+ State: Tuple of the form (i, result) => i >= 1  and result = n * (n-1) * (n-2) * ... * i
+ Idea: Descendant iteration: (n,n) -> (n-1, n*(n-1)) -> ... -> (1,n!)
 + $S_0$ : (n,1)
+ $S_{f}$ : i = 1
+ Status transformation: (i, result) → (i – 1, result * (i – 1))

### Verify Correctness of Algo Using Loop Invariants (Theorem, Proof)

+ There are several methods to prove correctness of algorithm, We focus on loop invariants

We have to prove the loop invariant to be true in three phases of the algorithm execution:
1. **Initialization**: Preconditions meets the invariant
	+ Invariant is true prior to the first iteration of the loop 
2. **Maintenance**: transformation of states keeps the invariant (invarianza)
3. **Termination**: in the final state postcodition is reached
---
+ A loop-invariant proof is a form of mathematical induction
+ Prove a base case and an inductive step
#### Example
```
alg(a,b):
	res = 0
	i = 0
	while i<=b:
		res += 1
		i +=1
	return res
```

**0 - Specification**
First, we have to proof that the algo meets its **Specification**, which its:
+  Pre-codition: $\{Q : a,b\in N\land b>0 \}$  also  $S_0 : res=0 ; i=1$ 
+ Post-condition: $\{ R:res=a\cdot b \}$
+ invariant: $res=\sum_{p=1}^{i-1}[a]$ - Sumar a b veces = a\*b
Then we prove the invariant for the 3 stages

**1 - Initialization**
i=0 => $res=\sum_{p=1}^{i-0}[a]$ = 0 => res=0 meeting the pre-condition (initial state, $S_0$) (empty sum)

**2 - Maintenance**
For any $k$ such as $\{1<=k<=b\}$ then
+ Replace res for the invariant
$$res=res+a  \Rightarrow   res=\sum_{p=1}^{i-1}a+a$$
+ Lo cual modificando los indices para incluir el +a exterior:
$$res=\sum_{p=1}^{k}a$$
+ Ahora para representar el paso adicional que se realiza (la transición) vamos a reemplazar $i$ por $k$ sabiendo que $k+1=i => k=i-1$ si reemplazamos esto en los indices obtenemos el invariante original, por lo tanto queda demostrada la validez del invariante en la transformación de estados
$$k=i-1$$
$$res=\sum_{p=1}^{i-1}a$$
**3 - Finalization**:
Because the ascendant nature of the loop the loop finishes thus is correct