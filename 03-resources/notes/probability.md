---
mocs:
    - "[[public-notes/03-resources/simulation.moc.md|Computational Simulation]]"
tags:
    - cs/simulation
---


![[Pasted image 20240821130356.png]]

# 1 - Random variable, expectation, variance

+ Is the mathematical framework that allow us to analyze chance events
+ **Probability of a event**: how likely that event will occur
	+ Whenever we’re unsure about the outcome of an event, we can talk about the probabilities of certain outcome
+ Is a number always ==between 0 (impossibility) and 1 (certainty)==

> P(A) = (# of ways A can happen) / (Total number of outcomes / sample space)
#### Random variable
+ Example: fair coin toss: 1/2
+ If we assign numbers for H and T (outcomes) -- say 1 for heads, 0 for tails -- then just have created a ==**random variable**==
#### Expectation
+ is a number that attempts to capture the center of that random variable's distribution
+ can be interpreted as ==the long-run average of many independent samples of the given distribution==
+ ==a measure of centrality==
$$E[x]=\sum_{x \in X}xP(x)$$
#### Variance
+ The variance of a random variable quantifies the spread of that random variable's distribution
$$Var(X)=E[(X-E[X])^2]$$

# 2 - Compound Probability: Set Theory, Counting, Conditional Probability
+ involves the likelihood of multiple events occurring together within a single experiment (several trials)
+ the analysis of the combined probability of two or more events happening simultaneously or sequentially
+ se utilizan diferentes reglas dependiendo de si los eventos son independientes o dependientes.
![[Pasted image 20240821130309.png]]
![[Pasted image 20240821130322.png]]
## a) Sets, counting and conditional probability
##### Sets ??
+ Broadly defined as a collection of objects
+ we use set notation to specify compound events
+ Is important to be familiar with algebra of sets
+ Example: we can represent the event "Roll an even number" by the set {2,4,6}
##### Counting: Permutation and Combinations
+ It can be surprisingly difficult to count the number of sequences or sets satisfying certain conditions.
+ **Example**, consider a bag of marbles in which each marble is a different color
	+ how many different ordered sequences (permutations) of the marbles are possible?
	+ How many different unordered sets (combinations)?
**Permutations**
![[Pasted image 20240819220116.png]]

![[Pasted image 20240819220129.png]]

**Combinations**
![[Pasted image 20240819220204.png]]
![[Pasted image 20240819220211.png]]

##### Conditional Probability
+ Se refiere a la probabilidad de que ocurra un evento A dado que ya ha ocurrido un evento B. Esta probabilidad se denota como $P(A|B)$
$$P(A|B)=\frac{P(A \cap B)}{P(B)}$$
ej:
> En una bolsa hay 5 bolas rojas y 3 bolas verdes. Si se saca una bola y resulta ser roja, ¿cuál es la probabilidad de que la siguiente bola también sea roja (sin reemplazar la primera bola)?
​
$$P (\text{Roja 2}|\text{Roja1})=\frac{P(\text{Roja 1 y Roja 2})}{P(\text{Roja 1})}=\frac{5/8 \times 4/7}{5/8}=4/7$$
## b) Eventos Independientes
+ Dos eventos son **independientes** si la ocurrencia de uno no afecta la ocurrencia del otro
$$P(A \cap B)=P(A) \times P(B)$$

## c) Eventos Dependientes
+ Dos eventos son **dependientes** si la ocurrencia de uno afecta la ocurrencia del otro.

Ej:
> bolsa con 4 bolas rojas y 6 bolas azules, sacar dos bolas consecutivamente (sin reemplazar la primera) ¿Cual es la probabilidad de que ambas bolas sean rojas?

paso 1: Calcular probabilidad del primer evento
+ 4/10
paso 2: Calcular probabilidad del segundo evento (condicional)
+ $P(\text{Roja 2} | \text{Roja 1})=\frac{3/9 \times 4/10}{4/10} = 1/3$
paso 3: $4/10 \times 1/3$

# Resources
+ https://seeing-theory.brown.edu/basic-probability/index.html (Recomendadisimo)
+ https://www.khanacademy.org/math/statistics-probability/probability-library/basic-theoretical-probability/v/simple-probability
+ https://www.geeksforgeeks.org/probability-in-maths/