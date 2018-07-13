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
	    if (lo >= hi)
		return;
			
	    int i = lo, j = hi, pivot = a[lo];    //pivot：always the first element in the array

	    while (i < j)                         //place the large elements to the right of the array and the small elements to the left
	    {
		while (i < j && a[j] > pivot)     //Right traversal
		    --j;
		if (i < j)                        //A judgment statement is added here to avoid extreme cases such as "1, 4, 2, 3"
		    a[i++] = a[j];

		while (i < j && a[i] < pivot)     //Left traversal
		    ++i;
		if (i < j)
		    a[j--] = a[i];
	    }

	    a[i] = pivot;

	    quickSort(a, lo, i - 1);
	    quickSort(a, i + 1, hi);
	}	
Another implementation（algorithms 4th edition）:

	void quickSort(int* a, int lo, int hi)
	{
	    if (lo >= hi) 
		return;
	    int pivot = a[lo], i = lo, j = hi + 1;

	    while (true)
	    {	
	        while (a[++i] < pivot)		//from the second element, as long as the current element is less than pivot, keep going right, at last i end up with an element >= pivot.
		    if (i == hi)		//to avoid i crossing the boundary
			break;

		while (a[--j] > pivot);		//from the last element, as long as the current element is more than pivot, keep going left, at last j end up with an element <= pivot. 
						//Here the judgement that "j == lo ? break : ;" is omitted because it is redundant.
		if (i >= j)			//i > j: a[j] < pivot && a[i] > pivot && j + 1 == i;
		    break;			//i = j: a[i] == a[j] == pivot

		std::swap(a[i], a[j]);		//i < j: a[j] < pivot && a[i] > pivot ----> swap(a[i], a[j]);
	    }
	    std::swap(a[j], a[lo]);		//at last, a[lo+1]...a[j] <= pivot <= a[i]...a[hi] : so swap(a[lo], a[j])
	    quickSort(a, lo, j - 1);
	    quickSort(a, j + 1, hi);
	}
comparison:

	The first implementation needn't do swap operation and the operation to scan the array is almost constant, so it's more efficient, i think. :)
	
## Code deduction (just do one traversal)
                    a[]
    Index:  0   1   2   3   4   5   6
    Data:   5   1   6   2   7   9   3
     
    pivot = a[0] = 5;   
    Traverse direction: j -> i;
    
	The first implementation:
            i                       j
    Data:   5   1   6   2   7   9   3       //Traverse direction: j -> i;		a[j] < pivot: a[i++] = a[j];  
                i                   j
    Data:   3   1   6   2   7   9   3       //Traverse direction: i -> j(changed);	a[i] < pivot: i++;
                    i               j
    Data:   3   1   6   2   7   9   3       //Traverse direction: i -> j;		a[i] > pivot: a[j--] = a[i];
                    i           j
    Data:   3   1   6   2   7   9   6       //Traverse direction: j -> i(changed);	a[j] > pivot: j--;
                    i       j
    Data:   3   1   6   2   7   9   6       //Traverse direction: j -> i;		a[j] > pivot: j--;
                    i   j
    Data:   3   1   6   2   7   9   6       //Traverse direction: j -> i;		a[j] < pivot: a[i++] = a[j];
                       ij
    Data:   3   1   2   2   7   9   6       //Traverse direction: i -> j(changed);	a[i] = pivot;
                       ij
    Data:   3   1   2   5   7   9   6       //finished; then quickSort recursion
	
	The second implementation:
	    	i	          	    j
    Data:   5   1   6   2   7   9   3		//Traverse direction: i -> j;	
	            i	          	    j
    Data:   5   1   6   2   7   9   3		//a[++i] < pivot
                    i		    j
    Data:   5   1   6   2   7   9   3		//a[++i] > pivot: Traverse direction: j -> i;
			i               j
    Data:   5   1   6   2   7   9   3		//a[--j] < pivot: Traverse direction: i -> j;
	                i               j
    Data:   5   1   3   2   7   9   6		//i < j: swap(a[i], a[j]);
	                    i           j
    Data:   5   1   3   2   7   9   6		//a[++i] < pivot
	                        i       j
    Data:   5   1   3   2   7   9   6		//a[++i] > pivot: Traverse direction: j -> i;
	                        i   j
    Data:   5   1   3   2   7   9   6		//a[--j] > pivot
	                        ij
    Data:   5   1   3   2   7   9   6		//a[--j] > pivot
	                    j   i
    Data:   5   1   3   2   7   9   6		//a[--j] < pivot: Traverse direction: i -> j;
	                    j   i
    Data:   2   1   3   5   7   9   6		//i > j, swap(a[lo], a[j])
