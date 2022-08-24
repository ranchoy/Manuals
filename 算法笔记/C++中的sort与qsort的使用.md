## c++中的sort与qsort的使用

1. **sort函数**

   - sort(arr, arr+n,  cmp)函数有三个参数：数组首地址，数组首地址加上要排序的元素个数，比较函数cmp；如果第三个参数不写则按照降序排列。

   - cmp函数的编写：

     ```c++
     bool cmp(int a, int b)
     {
         return a > b;//按照降序排列
     }
     ```

2. **qosrt函数**

   - qsort(arr, n, sizeof(arr[0]), cmp)函数有四个参数：数组首地址，待排元素个数，单个元素长度，cmp比较函数。

   - cmp比较函数的编写：

     ```c++
     int cmp(const void *a, const void *b)
     {
         return *(int *)a - *(int *)b;//降序排列
     }
     ```
