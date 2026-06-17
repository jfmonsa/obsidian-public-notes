---
mocs:
    - "[[public-notes/03-resources/algorithms.moc.md|Algorithms & Data Structures]]"
tags:
    - cs/algorithms
---


## Tips:
+ If input array is sorted then:
	+ Binary Search
	+ Two pointers
+ If asked for all permutations/subsets then
	+ Backtracking
+ If Trees or graphs
	+ DFS
	+ BFS
+ If given linked lists
	+ Two pointers
+ If recursion is banned
	+ Stack
## 5. Divide and Conquer
In the divide-and-conquer method, if the problem is small enough --the base
case-- you just solve it directly without recursing. Otherwise --the recursive case-- you perform three characteristic steps:
+ **Divide**: the problem into one or more sub problems (Smaller instances of the same problem)
+ **Conquer**: The suproblem solutions to form a solution to the original problem
+ **Combine**: The subproblem solutions to the original problem
**Some DAC Algos:**
+ MergeSort
+ QuickSort
+ Karatsuba Algo (multiply large numbers)
+ Strassen Matrix Multiplication
+ closest pair of point
+ discrete Fourier Transform
### Decrease and Conquer

**Algo Examples:**
+ Binary search
+ maximum element in array
+ closest pair of points

## 6. Two  Pointers Technique
+ Is the optimal way to solve problems related to arrays in O(N) time.
+ With this approach we are able to process two elements per loop instead of just one
+ There are two common approaches:
	1. Two pointers, each starting from the beginning and the end until they both meet
	2. One pointer moving at a slow pace, while other pointer moves at twice the speed. Ex: (find a loop in a linked list)
+ Examples: Two sum problem (when sorted), reverse string, middle node of linked link

## 7. Sliding Window
It involves imagining a window that slides over an array or data structure, looking for a specific condition to be met within the window.
+ Time: $O(n)$

There are two types of sliding window problems:
**1. Fixed size**: 
+ length of window fixed
+ it ask to find something in the window such as: the maximum sum of each element in the window etc.
**2. Two Pointers + criteria**
+ No fixed length
+ ask for a sub-array which met the given criteria

### Tips
+ The problem involves finding a maximum, minimum, longest, or shortest something
+ The problem deals with continuous elements
### Examples of problems:
+ Maximum sum of a contiguous sub-array
+ Best time to buy sell stock
+ Longest substring with K distinct characters
+ Minimum window size containing all elements of a target subarray
## 8. Binary Search
+ find the position of a target value within a ****sorted**** array
+ dividing the search interval in half until the target value is found
+ The data structure must be sorted.
- Access to any element of the data structure should take constant time.
- time: $O(log(n))$ 

## Multhi-threading and Parallelism
## Bitwise
## Backtracking
## Dynamic
## Greedy
## Topological Sort?
