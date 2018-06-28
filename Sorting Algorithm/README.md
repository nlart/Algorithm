# Sorting algorithm
## Introduction

In computer science, a sorting algorithm is an algorithm that puts elements of a list in a certain order.

## Output requirements

* The output is in nondecreasing order (each element is no smaller than the previous element according to the desired total order);

* The output is a permutation (a reordering, yet retaining all of the original elements) of the input.

## Classification
* Computational complexity in terms of the size of the list (n). 
* Computational complexity of swaps.
* Memory usage.
* Recursion.
* Stability.(stable sorting algorithms maintain the relative order of records with equal keys)
* Whether or not they are a comparison sort.
* General method: insertion, exchange, selection, merging, etc. 
* Whether the algorithm is serial or parallel. 
* Adaptability.

## Popular sorting algorithms
* [Insertion sort](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Doc/Insertion%20sort.md "Insertion sort doc")
> Insertion sort is a simple sorting algorithm that is relatively efficient for small lists and mostly sorted lists, and is often used as part of more sophisticated algorithms. It works by taking elements from the list one by one and inserting them in their correct position into a new sorted list. In arrays, the new list and the remaining elements can share the array's space, but insertion is expensive, requiring shifting all following elements over by one. Shellsort (see below) is a variant of insertion sort that is more efficient for larger lists.

* [Selection sort](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Doc/Selection%20sort.md "Selection sort doc")
> Selection sort is an in-place comparison sort. It has O(n2) complexity, making it inefficient on large lists, and generally performs worse than the similar insertion sort. Selection sort is noted for its simplicity, and also has performance advantages over more complicated algorithms in certain situations.

> The algorithm finds the minimum value, swaps it with the value in the first position, and repeats these steps for the remainder of the list. It does no more than n swaps, and thus is useful where swapping is very expensive.

* [Shellsort](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Doc/Shell%20sort.md "Shellsort doc")
> Shellsort was invented by Donald Shell in 1959. It improves upon insertion sort by moving out of order elements more than one position at a time. The concept behind Shellsort is that insertion sort performs in O(kn) time, where k is the greatest distance between two out-of-place elements. This means that generally, they perform in O(n2), but for data that is mostly sorted, with only a few elements out of place, they perform faster. So, by first sorting elements far away, and progressively shrinking the gap between the elements to sort, the final sort computes much faster. One implementation can be described as arranging the data sequence in a two-dimensional array and then sorting the columns of the array using insertion sort.

> The worst-case time complexity of Shellsort is an open problem and depends on the gap sequence used, with known complexities ranging from O(n2) to O(n4/3) and Θ(n log2 n). This, combined with the fact that Shellsort is in-place, only needs a relatively small amount of code, and does not require use of the call stack, makes it is useful in situations where memory is at a premium, such as in embedded systems and operating system kernels.

