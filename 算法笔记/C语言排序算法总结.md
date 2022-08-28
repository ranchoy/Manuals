### C语言排序算法总结

#### qsort算法

数组、结构体、字符串的`comp`排序比较函数。

```c
// 数组
int comp(const void *a, const void *b)
{
	return *(int *)a - *(int *)b;  // 升序 
}
int comp(const void *a, const void *b)
{
	return *(int *)b - *(int *)a;  // 降序 
}
```

```c
// 结构体
struct data {
	int year, int month, int day;
}

int comp(const void *a, const void *b)
{
	if(((struct data *)a)->year == ((struct data *)b)->year)
	{
		if(((struct data *)a)->month == ((struct data *)b)->month)
		{
			return ((struct data *)a)->day > ((struct data *)b)->day;
		}
		return ((struct data *)a)->month > ((struct data *)b)->month;
	}
	return ((struct data *)a)->year > ((struct data *)b)->year;
}
```

