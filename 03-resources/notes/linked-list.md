---
mocs:
    - "[[public-notes/03-resources/algorithms.moc.md|Algorithms & Data Structures]]"
tags:
    - cs/algorithms
---

+ Linear data structure
+ elements not stored at contiguous location
+ form a series of connected nodes
+ Each node stores the data and the address of the next node
+ Linked list is accessed through the head node
* **Head and Tail**: The tail node points to Null indicating the end of the list
## Types of linked lists:
1. Single linked list
2. Double linked list
3. Circular linked list

## Operations
+ **insertion**: *(In the end, in the start or in a given position)* Adjusting the pointers of the existing nodes to maintain the proper sequence
+ **Deletion**: *(In the end, in the start or in a given position)adjusting*  the pointers of the neighboring nodes to bridge the gap left by the deleted node
+ **Searching**: traversing the list from the head node until the value is found or the end

## Advantages
+ **Dynamic Data Structure**: Size of memory allocated or de-allocated at run time based on the operation ***insertion*** and ***deletion***
+ Insertion and deletion operations are simpler than array since no elements need to be shifted after insertion and deletion. *just the address needed to be updated*
+ We can implement: stacks, queue, graph, hash maps, etc with this ds
## Disadvantages
* **Random access**: Unlike arrays, linked lists do not allow direct access to elements by index. Traversal is required to reach a specific node.
* Linked lists require additional memory for storing the pointers, compared to arrays.
