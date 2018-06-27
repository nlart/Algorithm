# Selection sort
## Introduction

> N-1 traversals of the data, each traversal to find the current minimum (or maximum), and placed in the starting (or termination) position(this is a swap operation).   

## Examples

> **0、　1、　2、　3、　4、　5、　6、　7、　8**　　//Index

> 8、　3、　2、　4、　`1`、　5、　7、　6、　9　　//Faw data

>　　　　　　　　　　　　　　　　　　　　　　　//　　　　　　　　　　　current min　　　current head

> 1、　3、　`2`、　4、　8、　5、　7、　6、　9　　//1 traversal:　　exchange　　a[4]　　and　　a[0]　　

> 1、　2、　`3`、　4、　8、　5、　7、　6、　9　　//2 traversal:　　exchange　　a[2]　　and　　a[1]

> 1、　2、　3、　`4`、　8、　5、　7、　6、　9　　//3 traversal:　　exchange　　a[2]　　and　　a[2]

> 1、　2、　3、　4、　8、　`5`、　7、　6、　9　　//4 traversal:　　exchange　　a[3]　　and　　a[3]

> 1、　2、　3、　4、　5、　8、　7、　`6`、　9　　//5 traversal:　　exchange　　a[5]　　and　　a[4]

> 1、　2、　3、　4、　5、　6、　`7`、　8、　9　　//6 traversal:　　exchange　　a[7]　　and　　a[5]

> 1、　2、　3、　4、　5、　6、　7、　`8`、　9　　//7 traversal:　　exchange　　a[6]　　and　　a[6]

> 1、　2、　3、　4、　5、　6、　7、　8、　`9`　　//8 traversal:　　exchange　　a[7]　　and　　a[7]

## Sample graph

![](https://github.com/ToyoBai/Algorithm/raw/master/Sorting-Algorithm/Sorting-Algorithm-Image/Selection_sort1.gif/) 
