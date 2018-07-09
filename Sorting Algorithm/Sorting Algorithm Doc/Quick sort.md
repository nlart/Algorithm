# Quick sort
## Introduction

Quicksort is a divide and conquer algorithm. Quicksort first divides a large array into two smaller sub-arrays: the low elements and the high elements. Quicksort can then recursively sort the sub-arrays.

The steps are:
* Pick an element, called a pivot, from the array.
* Partitioning: reorder the array so that all elements with values less than the pivot come before the pivot, while all elements with values greater than the pivot come after it (equal values can go either way). After this partitioning, the pivot is in its final position. This is called the partition operation.
* Recursively apply the above steps to the sub-array of elements with smaller values and separately to the sub-array of elements with greater values.

## Graphical representation

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
        void quickSort(int* a, int lo, int hi)
        {
            if (hi <= lo)
                return;

            int pivot = lo, i = lo + 1, j = hi;     //Here i always set the first element as the pivot; i,j: left and right scan pointer.

            while (i <= j)                          //i,j havn't met.
            {
                if (a[i] > a[pivot])                //if the left elements > 'the pivot', exchange a[i] and a[j] to make sure the bigger elements are always on the right. Then j--.
                    std::swap(a[i], a[j--]);
                else                                //if the left elements <= 'the pivot', exchange a[i] and a[pivot] to make sure the smaller elements are always on the right. Then i++.(pay attention that when the exchange happened, pivot need to be updated)
                {
                    std::swap(a[i++], a[pivot]);
                    pivot = i - 1;
                }
            }

            quickSort(a, 0, pivot - 1);
            quickSort(a, pivot + 1, hi);
        }

## Demo examples
                                    a[]
        Index：  0   1   2   3   4   5   6   7   8   9   10
        Data：   9   7   3   6   4   5   8   0   5   2   1

    a[pivot] = 9:                        //here p is pivot
        Index：  0   1   2   3   4
                 p   i           j
        Data：   9   3   6   4   3       //a[i] < a[pivot]: swap(a[i++], a[pivot]); pivot = i - 1;
                     p   i       j
        Data：   3   9   6   4   3       //a[i] < a[pivot]: swap(a[i++], a[pivot]); pivot = i - 1;
                         p   i   j
        Data：   3   6   9   4   3       //a[i] < a[pivot]: swap(a[i++], a[pivot]); pivot = i - 1;
                             p  ij
        Data：   3   6   4   9   3       //a[i] < a[pivot]: swap(a[i++], a[pivot]); pivot = i - 1;
                                 pj  i
        Data：   3   6   4   3   9       //finished
    a[pivot] = 3:
                 p   i           j
        Data:    3   6   4   3   9       //a[i] > a[pivot]: swap(a[i], a[j--]);
                 p   i       j
        Data:    3   9   4   3   6       //a[i] > a[pivot]: swap(a[i], a[j--]);
                 p   i   j
        Data:    3   3   4   9   6       //a[i] = a[pivot]: swap(a[i++], a[pivot]); pivot = i - 1;  (optimizable)
                     p  ij
        Data:    3   3   4   9   6       //a[i] > a[pivot]: swap(a[i], a[j--]);                     (optimizable)
                    pj   i
        Data:    3   3   4   9   6       //finished
        
        
