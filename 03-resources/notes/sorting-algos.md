---
mocs:
    - "[[public-notes/03-resources/algorithms.moc.md|Algorithms & Data Structures]]"
tags:
    - cs/algorithms
---

TARGET DECK: DSA - sorting
# 1- Basic $O(n²)$
## 1. Insertion Sort
Implement insertion sort in paper and then code it #flashcard
1. Work left or right
2. Examine each item and compare it to items on its left
3. insert the item in the correct position in the array
time O(n²) ; aux space O(1)
```Python
def insertionSort(arr):
	for i in range(1,len(arr)):
		current = arr[i]
		j = i - 1
		while j > 0 and current < arr[j]:
			arr[j+1] = arr[j]
			j -= 1
		arr[j+1] = current
	return arr
```
<!--ID: 1719699597464-->



## 2. Selection Sort
implement selection sort in papera and the code it #flashcard 
+ current_item arr[i], current_minimum (key)
+ swap the current_item with current minimum
+ tener una particion ordenada y otra desordenada, ir iterando en la parted desordenada
    el menor el elemento swappea el actual
sorted. time comp: O(n²) ; space comp (Auxiliary space): O(1)
<!--ID: 1719699597587-->


```Python
def selectionSort2(arr):
    i = 0
    while i < len(arr):
        key = i  # key of the current minimun element
        j = i + 1
        while j < len(arr):
            if arr[j] < arr[key]:
                key = j
            j += 1
        aux = arr[i]
        arr[i] = arr[key]
        arr[key] = aux
        i += 1
    return arr
```


## 3. Bubble Sort
implement bubble sort in papera and the code it #flashcard 
1. Work left or rigth
2. Examine each item and compare it to items on its left
3. insert the item in the correct position in the array
time O(n²) ; aux space O(1)
```Python
def bubbleSort(arr: list[int]) -> list[int]:
    swapped = True
    while swapped:
        swapped = False
        i = 0
        while i < len(arr) - 1:
            if arr[i] > arr[i + 1]:
                # swap
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
                swapped = True
            i += 1
    return arr
```
<!--ID: 1719699775938-->

# 2- Divide and conquer
## 1. Merge Sort
**Approach: Merge Sort with indexes, in-place operations** #flashcard
**(conquer)**
+ if start >= end: return 
**(divide)**
+ else: mid = (start+end)//2
+ order right and left mergeSort(arr,start,mid) mergeSort(arr,mid+1,end)
**(combine)**
+ merge(arr,start,mid,end)
+ 2 subarrays Left\[start:mid+1] and Right\[mid+1 : end]
+ i and j pointers for Left and Right subarrays
+ k=start pointr for original arr
+ while L and R are not empty compare if L\[i]<=R\[j]
+ while L is not empty append to arr
+ while R is not empty append to R
$T(n) = 2T(n/2)+O(n) <-> T(n)=O(nlog(n))$
```Python
def mergeSort(arr):
    mergeSort_aux(arr, 0, len(arr) - 1)
    return arr
    
def mergeSort_aux(arr, start, end):
    # conquer
    # Note: in-place operations, thus we don't have to return anything
    if start >= end:
        return
    # divide
    mid = (start + end) // 2
    mergeSort_aux(arr, start, mid)
    mergeSort_aux(arr, mid + 1, end)
    # combine
    merge(arr, start, mid, end)
    
def merge(arr, start, mid, end):
    # subarrays
    L = arr[start : mid + 1]
    R = arr[mid + 1 : end + 1]
    i = 0
    j = 0
    # index to the original array
    k = start
    while i < len(L) and j < len(R):
        if L[i] <= R[j]:
            arr[k] = L[i]
            i += 1
        else:
            arr[k] = R[j]
            j += 1
        k += 1
    while i < len(L):
        arr[k] = L[i]
        i += 1
        k += 1
    while j < len(R):
        arr[k] = R[j]
        j += 1
        k += 1
```
<!--ID: 1720202635398-->
END
# 3- Linear Time
## 4. Counting Sort
implement counting sort #flashcard 
+ Non-comparison-based algorithm
+ Works well with limited range of input values (small range of integers)
+ Count frequency of each element
General idea:
0. min y max elements to create count_arr of m size m = max-min+1
1. dos arrays auxiliares count_arr y output
2. cumulative sum  in count_arr. each value marks the final index of a certain value
3. iterate from n-1 to 0 in input array and output\[count_arr\[index]-1] where index = arr\[i]-min_elm and decrease count_arr\[index]-=1
* Note: We iterate from Right to Left in the sorting steps in order to guarantee the algorithm stability keep the relative order of the elements with equal values
```Python
def countingSort(arr):
    n = len(arr)
    # min and max
    if n <= 1:
        return arr
    min_elm = max_elm = arr[0]
    for i in range(1, n):
        if arr[i] < min_elm:
            min_elm = arr[i]
        if arr[i] > max_elm:
            max_elm = arr[i]
    # count
    k = max_elm - min_elm + 1
    count_arr = [0] * k
    for i in range(n):
        count_arr[arr[i] - min_elm] += 1
    # cumulative sum
    for i in range(1, k):
        count_arr[i] += count_arr[i - 1]
    # sort
    output_arr = [0] * n
    for i in range(n - 1, -1, -1):
        index = arr[i] - min_elm
        output_arr[count_arr[index] - 1] = arr[i]
        count_arr[index] -= 1
    return output_arr
```
<!--ID: 1720200657955-->
END
## 5. Bucket Sort
## 6. Radix Sort
