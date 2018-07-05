# Quick sort
## Introduction

Quicksort is a divide and conquer algorithm. Quicksort first divides a large array into two smaller sub-arrays: the low elements and the high elements. Quicksort can then recursively sort the sub-arrays.

The steps are:
* Pick an element, called a pivot, from the array.
* Partitioning: reorder the array so that all elements with values less than the pivot come before the pivot, while all elements with values greater than the pivot come after it (equal values can go either way). After this partitioning, the pivot is in its final position. This is called the partition operation.
* Recursively apply the above steps to the sub-array of elements with smaller values and separately to the sub-array of elements with greater values.

## Examples

Histogram:

![QuickSort](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Image/QuickSort1.gif?raw=true "QuickSort")

Digital simulation:

![QuickSort](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Image/QuickSort2.png?raw=true "QuickSort")

## Complexity analysis
    Worst-case performance:
                            O(n^2)
    Best-case performance:
                            O(n log n)  (simple partition)
                         or O(n)        (three-way partition and equal keys)
    Average performance:
                            O(n log n)
    Worst-case space complexity:
                            O(n) auxiliary (naive)
                            O(log n) auxiliary
## Partition scheme
[Please click here.](https://en.wikipedia.org/wiki/Quicksort "wikipedia")

## Code
