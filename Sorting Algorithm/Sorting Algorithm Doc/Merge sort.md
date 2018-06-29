# Merge sort
## Introduction
Conceptually, a merge sort works as follows:

* Divide the unsorted list into n sublists, each containing 1 element (a list of 1 element is considered sorted).
* Repeatedly merge sublists to produce new sorted sublists until there is only 1 sublist remaining. This will be the sorted list.

## Examples:

Scattergram：

![scattergram](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Image/MergeSort1.gif "MergeSort")

Digital simulation: 

![Digital simulation](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Image/MergeSort2.gif "MergeSort")

## Classification
* Top-down merge sort

> Top-down merge sort is to split all the elements into two continuously, until the number of elements in subarray is 1, because this subarray must be a ordered one at this time. Then two ordered sequence merged into a new ordered sequence, two new ordered sequence can be merged into another new ordered sequence, and so on, until these merged into an ordered array.

> For example:

> ![Top-down merge sort](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Image/TopDown.png "Top-down merge sort")

* Bottom-up merge sort

> Bottom-up merge sort considered the array to be sorted as a collection of subarrays of N single elements, and then merge them one by one, two by two, four by four...until the length of the merge is more than the length of the entire array when the array is ordered. Notice that the array is divided by merge length, and the last subarray may not fulfill the length requirement, which requires special treatment.

> For example:

> ![Bottom-up merge sort](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Image/BottomUp.png?raw=true "Bottom-up merge sort")

## Complexity analysis
    Worst-case performance:
                          O(n log n)
    Best-case performance:	
                          O(n log n)  typical,
                          O(n)        natural variant
    Average performance:
                          O(n log n)
    Worst-case space complexity:
                          О(n) total with O(n) auxiliary, 
                          O(1) auxiliary with linked lists
                      
## Code
        //common merge function:
        void merge(int* a, int lo, int hi)              //Merge array a;    parameters: lo: min index; hi: max index
        {
            int* temp;                                  //temp[]: Auxiliary array
            for (int i = lo; i <= hi; i++)
                temp[i] = a[i];
                
            int mid = (lo + hi) / 2;
            int i = lo, j = hi;                         //left and right "cursor"； i：0 ~ mid；  j：mid+1 ~ hi
            
            for (int k = lo; k <= hi; k++)              //get the result array
                if (i > mid)                            //At the end of the left subarray traversal, you simply assign the right subarray to the result array one by one
                    a[k] = temp[j++];
                else if (j > hi)                        //At the end of the right subarray traversal, you simply assign the left subarray to the result array one by one
                    a[k] = temp[i++];
                else if (temp[i] > temp[j])             //the "cursor" at the lower value is moved backward
                    a[k] = temp[j++];
                else if (temp[i] <= temp[j])
                    a[k] = temp[i++];
        }
* Top-down merge sort:

        void mergeSortTopDown(int* a, int lo, int hi)   //Binary splitting
        {
            int mid = (lo + hi) / 2;
            if (hi <= lo)
                return;
                
            mergeSortTopDown(a, lo, mid);               //recurse the left subarray
            mergeSortTopDown(a, mid+1, hi);             //recurse the right subarray
            merge(a, lo, hi);                           //merge sort currrent array
        }
