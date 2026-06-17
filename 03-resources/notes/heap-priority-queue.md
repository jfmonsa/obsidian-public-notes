---
mocs:
    - "[[public-notes/03-resources/algorithms.moc.md|Algorithms & Data Structures]]"
tags:
    - cs/algorithms
---

+ (Monticulos)
+ Is used to implement a ==Priority Queue== (The most efficient way)
	+ A **Priority Queue** is and ADT (Abstract Data Type) elements with high priority are served before elements with low priority
	+ priority queues are often referred to as "heaps", regardless of how they may be implemented
## Binary Heap
+ Is a ==Complete Binary Tree==
+ that ==satisfies the heap property==: for every node, the value of its children is less than or equal to its own value.
+ his property makes sure that the root node contains the **maximum*** or **minimum** value
![[Pasted image 20240717213926.png]]

## Types of Heaps
We are focusing in Binary heaps
+ **Min-heaps**: The children keys are less than or equal to the para key
+ **Max-heap**: viceversa
There are other types of heaps
### Variants
- [2–3 heap](https://en.wikipedia.org/wiki/2%E2%80%933_heap "2–3 heap")
- [B-heap](https://en.wikipedia.org/wiki/B-heap "B-heap")
- [Beap](https://en.wikipedia.org/wiki/Beap "Beap")
- [Binary heap](https://en.wikipedia.org/wiki/Binary_heap "Binary heap")
- [Binomial heap](https://en.wikipedia.org/wiki/Binomial_heap "Binomial heap")
- [Brodal queue](https://en.wikipedia.org/wiki/Brodal_queue "Brodal queue")
- [_d_-ary heap](https://en.wikipedia.org/wiki/D-ary_heap "D-ary heap")
- [Fibonacci heap](https://en.wikipedia.org/wiki/Fibonacci_heap "Fibonacci heap")
- [K-D Heap](https://en.wikipedia.org/wiki/K-D_Heap "K-D Heap")
- [Leaf heap](https://en.wikipedia.org/w/index.php?title=Leaf_heap&action=edit&redlink=1 "Leaf heap (page does not exist)")
- [Leftist heap](https://en.wikipedia.org/wiki/Leftist_tree "Leftist tree")
- [Skew binomial heap](https://en.wikipedia.org/wiki/Skew_binomial_heap "Skew binomial heap")
- [Strict Fibonacci heap](https://en.wikipedia.org/wiki/Strict_Fibonacci_heap "Strict Fibonacci heap")
- [Min-max heap](https://en.wikipedia.org/wiki/Min-max_heap "Min-max heap")
- [Pairing heap](https://en.wikipedia.org/wiki/Pairing_heap "Pairing heap")
- [Radix heap](https://en.wikipedia.org/wiki/Radix_heap "Radix heap")
- [Randomized meldable heap](https://en.wikipedia.org/wiki/Randomized_meldable_heap "Randomized meldable heap")
- [Skew heap](https://en.wikipedia.org/wiki/Skew_heap "Skew heap")
- [Soft heap](https://en.wikipedia.org/wiki/Soft_heap "Soft heap")
- [Ternary heap](https://en.wikipedia.org/wiki/Ternary_heap "Ternary heap")
- [Treap](https://en.wikipedia.org/wiki/Treap "Treap")
- [Weak heap](https://en.wikipedia.org/wiki/Weak_heap "Weak heap")

## Array Representation
+ We use an array to represent the tree
+ Given $i$ index of a element in the tree
	+ $2i+1$ to left child
	+ $2i+2$ to right child
	+ $\lfloor (i-1)/2 \rfloor$ to get its parent
![[Pasted image 20240717214707.png]]
## Operations
**Note:** Operations focusing on minheap, for maxheap invert the comparisson
+ **Aux operations** $O(log(n))$
	+ **siftdown**:
		+ Keep swapping the node with its children when they're smaller
		+ if both are smaller we swap with the smaller one
	+ **siftup**
		+ Keep swapping the node with its parent if it greater than current node
+ Insert:  $O(log(n))$
+ update: $O(log(n))$
+ Extract $O(log(n))$
+ Heapify $O(n)$
+ min / max element $O(1)$
## Applications
+ Priority queues:
	+  In a priority queue elements has priority related
	+ elements with the highest priority come at the front
	+ to implement a P.Q. we use a MinHeap or MaxHeap
	+ Operations in PQ:
		+ enequeue $O(logn)$,
		+ dequeue $O(long n)$,
		+ peek $O(1)$,
		+ change priority O(log n) if we have the index else $O(n)$,
		+ is_empy $O(1)$
			![[Pasted image 20240718140515.png]]
+ Heapsort $O(nlog(n))$ Heapsort heapifies the array that we want to sort then keeps extracting min until it becomes empty
+ Dijkstra's and Prim's algos
## Resources
+ https://www.geeksforgeeks.org/heap-data-structure/
+ https://www.youtube.com/watch?v=pLIajuc31qk&t=192s Best video, explain visual, code and also some mathematical proofs on time complexity