### C++大数加法总结

- 大数加法就是把数字存在数组中，数组下标从小到大代表数字从小到大，例如数组arr[] = {0987654321}代表的是1234567890这个数字，要注意加法的进位；

- 算法例子：

  ````c++
  #include<iostream>
  #include<cstdio>
  #include<cstring>
  #include<algorithm>
  #define MAX 105
  using namespace std;
  
  int arr[MAX];
  
  int main()
  {
  	char str[MAX];
  	int cnt,n,m,len,idx,temp,yu;
  	scanf("%d", &cnt);
  	while(cnt--)
  	{
  		// 初始化
  		len = 0;
  		memset(arr, 0, sizeof(arr)); 
  		
  		scanf("%d", &n);
  		for(int i=0; i<n; i++)
  		{
  			scanf("%s", str);
  			m = strlen(str);
  			
  			for(int i=m-1; i>=0; i--)
  			{
  				idx = m - i - 1;
  				temp = arr[idx]	+ (str[i] - '0') + yu;
  				arr[idx] = temp%10;
  				yu = temp/10;
  			}	 
  			
  			while(yu)
  			{
  				temp = arr[m] + yu;
  				arr[m] = temp%10;
  				yu = temp/10;
  				m ++;
  			}
  			len = max(len, m);// 记录数组长度
  		} 
  		
  		for(int i=len-1; i>=0; i--)
  		{
  			printf("%d", arr[i]);
  		}printf("\n");
  	}
  	return 0;
  }
  
  /*
  2
  3
  1111
  9999
  9999
  21109
  3
  123456789012345678901234567890
  123456789012345678901234567890
  123456789012345678901234567890
  370370367037037036703703703670
  */ 
  ````
