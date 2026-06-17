---
mocs:
    - "[[public-notes/03-resources/algorithms.moc.md|Algorithms & Data Structures]]"
tags:
    - cs/algorithms
---

+ Non-linear data structure
+ a collection of elements known as nodes are connected to each other via edges
+ has a hierarchical relationship between the nodes.
+ recursive data  (T1,T2 y T3 sub-trees)
![[Pasted image 20240711124931.png]]

## Terminologies
![[Pasted image 20240711215838.png]]
- ****Parent Node:****
- ****Child Node:**** 
- ****Root Node:**** The ==topmost==, does not have any parent node is called the root node. . A non-empty tree must contain exactly one root node and exactly one path from the root to all other nodes of the tree.
- ****Leaf Node or External Node:**** 
- ****Ancestor of a Node:**** Any predecessor nodes on the path of the root to that node are called Ancestors of that node.
- ****Descendant:**** A node x is a descendant of another node y if and only if y is an ancestor of x.
- ****Sibling:**** Children of the same parent node are called siblings.
- ****Level of a node:**** The count of edges on the path from the root node to that node. The root node has level **0***.
- ****Internal node:**** A node with at least one child is called Internal Node.
- ****Neighbor of a Node:**** Parent or child nodes of that node are called neighbors of that node.
- **Sub-tree*** Any node of the tree along with its descendant.

## Other concepts
+ $n$ nodes, $n-1$ edges: 
+ **Height**:
	+ ==Other authors count nodes instead of edges==
	+ The height of a ==node== is the number of edges on the longest path from that node to a leaf.
	+ The height of the ==entire tree== is the height of the root node.
+ **Depth**:
	+ The depth of a node is the number of edges from the root to that node.
	+ The root always has a depth of 0.

```
        A         Depth: 0, Height: 3
       / \
      B   C       Depth: 1, Height: 2
     /     \
    D       E     Depth: 2, Height: 1
```
## Types of Tree
+ Binary
+ Ternary
+ N-ary tree (Generic)
## Applications
+ File System
+ Data Compression (Huffman coding)
+ Compiler Design (AST)
+ Database Indexing (B-trees and other structures)
+ Trie
+ Network Routing Algo

## Implementation
![[Pasted image 20240711125804.png]]
## Binary Tree Traversals
+ Process of visiting each node in a tree
+ unlike linear data structures which are canonically traversed in linear order, trees may be traversed in multiple ways.
+ They may be traversed in depth-first or breath-first order
### Depth-First Search (Búsqueda en profundidad)
+ Es un algoritmo utilizado para recorrer o buscar en estructuras de datos de árbol o grafo.
+ Idea:
	1. Comienza en la raíz del árbol.
	2. Explora tan lejos como sea posible a lo largo de cada rama antes de retroceder.
	3. Visita todos los nodos de un camino antes de pasar al siguiente.
+ DFS se implementa típicamente usando recursión o una pila explícita.
+ There are three common ways to traverse trees in depth-first order: ==in-order, pre-order and post-order==
+ Pre-order (N, L, R):
+ In-Order (L, N, R):
+ Post-order(L, R, N)
![[Pasted image 20240711170226.png]]
Pre-order: F, B, A, D, C, E, G, I, H
![[Pasted image 20240711202331.png]]
![[Pasted image 20240712084214.png]]

### Breath-First Search
![[Pasted image 20240717093953.png]]

+ **Level Order Traversal**: Use queue
## References
+ https://www.geeksforgeeks.org/tree-data-structure/
Profundizar más:
+ https://www.geeksforgeeks.org/bfs-vs-dfs-binary-tree/?ref=lbp : Problems and other tree traverses