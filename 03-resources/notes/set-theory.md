---
mocs:
    - "[[public-notes/03-resources/discrete-math.moc.md|Discrete Math]]"
tags:
    - math/discrete
---

# Introduction to Sets
+ **Set**: ==Is and unordered collection of objects==
+ Objects are named ==elements==
+ There are ==Finite== and ==infinite== sets
+ ==Two sets are equal== if they contain the same elements
+ We usually use uppercase letter to ==name 
+ There are special sets: $\mathbb{N}$, $\mathbb{Z}$, $\mathbb{R}$, $\mathbb{Q}$, $\emptyset$
## Cardinality (Size)
+ The number of elements in the set
+ denoted as $|X|$, or $\text{n}(A)$, $\text{card}(A)$ or $\#(A)$.

## Empty Set
+ $\emptyset$ or $\{\}$
+ Has not elements $|\emptyset| = 0$.
+ Is the only set whose cardinality is zero
+ **Note**: $|\emptyset| \neq |\{ \emptyset\}|$
**Examples:**
+ $G=\{N,Z\},|G|=2$
+ $F =\{\emptyset,\{\emptyset\},\{\{\emptyset\}\}\},|F|=3$
## Set Builder Notation
+ We read the first brace as "the set of all things of form" and the colon "such that".
+ **Example**: $E = \{ 2n \mid n \in \mathbb{Z} \}$
	+ Other forms: $E = \{ x \in \mathbb{Z} \mid x \text{ is even} \} = \{ n \in \mathbb{Z} \mid n = 2k, k \in \mathbb{Z} \}$
+ **In general**: $X = \{ x \mid \text{proposition, rule } x \}$
## Roaster Enumeration Notation
+ Defined a set by listing its elements between curly braces
**Examples**
+ $\{1, 2, 3\}$
- $\{n^2 : n \in \mathbb{Z} \} = \{0, 3, 9, 16, 25, \ldots \}$
- $\{ x \in \mathbb{R} : x^2-2 = 0\} = \{\sqrt{2} \text{,} -{\sqrt{2}}\}$
## Intervals
+ Can contain infinity numbers
![[Pasted image 20240717101459.png]]