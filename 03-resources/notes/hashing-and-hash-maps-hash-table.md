---
mocs:
    - "[[public-notes/03-resources/algorithms.moc.md|Algorithms & Data Structures]]"
tags:
    - cs/algorithms
---

## 1. What is hashing in Data Structure
+  **store and retrieve data efficiently**.
+ It involves using a ***hash function** to map data items to a fixed-size array which is called a **hash table**.
+ It is a data structure that stores key-value pairs. It uses a hash function to map keys to a fixed-size array, called a hash table.
## 2. Hash Functions
+ must be: Fast to compute
+ should try to: avoid collisions
+ Uniform distributed
+ A hash function for security applications must meet other concerns
**Common Hash Functions**
+ Division Method: Key % Hash Table Size
+ Multiplication Method: (Key * Constant) % Hash Table Size
## 3. Load Factor
+ The load factor in a hash table is a measure of ==how full== the hash table is.
+ $m$ <- (Hash table size); $n$<- number of elements; $\alpha=\frac{n}{m}$
+ A ==higher== load factor means the hash table is ==more full==, which can lead to more collisions and thus can degrade the performance of the hash table operations
+ To maintain efficient performance, ==hash tables often resize (rehash)== themselves when the load factor exceeds a certain threshold.
## 4. Hash Collisions
Por el principio de palomar (**Pigeonhole Principle**) es posible que ocurran colisiones si:  |U|>m, |U| universo de llaves > llaves disponibles en la tabla.

### Collision Resolution Techniques
1. **Closed Addressing: (Chaining):** Store colliding keys in a linked list or binary search tree at each index
2. **Open Addressing**: Linear Probing: Search for an empty slot sequentially
### Collisions and Performance
+ En una tabla hash que resuelve las colisiones por encadenamiento la complejidad para hacer búsqueda es:
	+ Mejor caso: $O(1)$
	+ Caso Promedio: $\theta(1+\alpha)$ 
	+ Peor caso: $O(1+\alpha)$ 
## Operations $O(1)$ (On average, assuming a good hash table)
+ Search
+ Insert
+ delete
## Applications
+ Databases
+ caching systems