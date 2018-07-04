# Selection sort
## Introduction
        N-1 traversals of the data, each traversal to find the current minimum (or maximum), and placed in the starting (or termination) position(this is a swap operation).   

## Examples
        0、　1、　2、　3、　4、　5、　6、　7、　8　　//Index
        8、　3、　2、　4、　1、　5、　7、　6、　9　　//Raw data
                                                  //　　　　　　　　　       current min　　　current head
        1、　3、　2、　4、　8、　5、　7、　6、　9　　//1 traversal:　　exchange　　a[4]　　and　　a[0]　　
        1、　2、　3、　4、　8、　5、　7、　6、　9　　//2 traversal:　　exchange　　a[2]　　and　　a[1]
        1、　2、　3、　4、　8、　5、　7、　6、　9　　//3 traversal:　　exchange　　a[2]　　and　　a[2]
        1、　2、　3、　4、　8、　5、　7、　6、　9　　//4 traversal:　　exchange　　a[3]　　and　　a[3]
        1、　2、　3、　4、　5、　8、　7、　6、　9　　//5 traversal:　　exchange　　a[5]　　and　　a[4]
        1、　2、　3、　4、　5、　6、　7、　8、　9　　//6 traversal:　　exchange　　a[7]　　and　　a[5]
        1、　2、　3、　4、　5、　6、　7、　8、　9　　//7 traversal:　　exchange　　a[6]　　and　　a[6]
        1、　2、　3、　4、　5、　6、　7、　8、　9　　//8 traversal:　　exchange　　a[7]　　and　　a[7]

## Sample graph
        Scattergram：
![Scattergram](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Image/Selection_sort1.gif?raw=true "scattergram")

        Digital simulation：

![Digital simulation](https://github.com/ToyoBai/Algorithm/blob/master/Sorting%20Algorithm/Sorting%20Algorithm%20Image/Selection-sort2.gif?raw=true "Digital simulation")

## Complexity analysis
    Exchange operation:
      Best situation:　　0       (such as: 1, 2, 3, 4)
      Worst situation:　n-1      (sucn as: 3, 1, 4, 2)
      
    Comparison operation:
                        n-1 + n-2 + ... + 1
                        = (1 + n-1) * (n - 1) / 2
                        = n(n-1)/2
                        = O（n^2）                   
## Code
    void SelectionSort(int* a, int size)                          //parameter: array                
    {
      for (int result = 0; result < size - 1; result++)           //result: resultArray_index (sorted)
      {
        int currentMin = result;                                  //currentMin: currentMin_index
        
        for (int index = result + 1; index <= size - 1; index++)  //index: "cursor" to traversing the array
          if (a[index] < a[currentMin])
            currentMin = index;                                   //currentMin update
          
          std::swap(a[result], a[currentMin]);                    //element exchange
      }
    }
