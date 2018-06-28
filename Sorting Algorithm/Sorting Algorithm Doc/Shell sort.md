# Shell sort
## Introduction
    Optimize insertion sorting by introducing the concept of step.In other words, insertion sort is considered to be a shell sort that step is 1.
    
## Examples
    13  14  94  33  82  25  59  94  65  23  45  27  73  25  39  10    //Raw data
    
    //step = 5:
    13  14  94  33  82
    25  59  94  65  23
    45  27  73  25  39
    10
    //do insertion sort by column:
    10 14 73 25 23
    13 27 94 33 39
    25 59 94 65 82
    45
    //get new array:
    10  14  73  25  23  13  27  94  33  39  25  59  94  65  82  45    //the rusult that step = 5;
    
    //step = 3:
    10 14 73
    25 23 13
    27 94 33
    39 25 59
    94 65 82
    45
    //do insertion sort by column:
    10 14 13
    25 23 33
    27 25 59
    39 65 73
    45 94 82
    94
    //get new array:
    10  14  13  25  23  33  27  25  59  39  65  73  45  94  82  94    //the rusult that step = 3;
    
    //step = 1: (do insertion sort) get the rusult
    10  13  14  23  25  25  27  33  39  45  59  65  73  82  94  94
## Sample graph
![Sample graph](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Image/ShellSort.gif?raw=true "Sample graph")

Step is also called gap.

## Complexity analysis
    Best-case performance：
                          O（n log n）
    Worst-case performance:
                          O（n^2）        （worst known gap sequence）
                          O（n(log n)^2） （best known gap sequence）
    Average performance： 
                          depends on gap sequence;
    Worst-case space complexity:
                          O（n）, total
                          O（1）, auxiliary
                          
## How to choose the best step(gap)?
[Please click here.](https://en.wikipedia.org/wiki/Shellsort)

## Code
    void shellSort(int* a， int size)
    {
      int step = 1;
      
      while (step < size / 3)                                         //select (max) step
        step = step * 3 + 1;
        
      for (; step > 0; step /= 3)                                     //iterate the step
        for (int i = step; i < size; i++)
          for (int j = i; j >= step && a[j] < a[j - step]; j -= step)
            std::swap(a[j], a[j - step]);
    }
