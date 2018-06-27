# Insertion sort

## Introduction

    Start with the second element, if less than the previous element, iterate forward until it finds the correct
    position and inserts.

## Picture examples
    Scattergram：
![Scattergram](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Image/Insertion_sort1.gif?raw=true "Scattergram")    

    Digital simulation：
![Digital simulation](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Image/Insertion_sort2.gif?raw=true "Digital simulation")

## Complexity analysis
    Comparison operation:
      Best situation:　　n-1,       O(n)     (such as: 1, 2, 3, 4)
      Worst situation:　 n(n-1)/2,  O(n^2)　 (sucn as: 4, 3, 2, 1)

## Code
    void InsertionSort(int* a)                                                  //parameter: array
    {
      for (int result = 1; result < a.size; result++)                //Backward traversal to find the starting point for forward traversal
        for (int index = result; index > 0 && a[index] < a[index - 1]; index--) //Forward traversal to find the target location
          std::swap(a[index], a[index - 1]);                                    //Element exchange
    }
