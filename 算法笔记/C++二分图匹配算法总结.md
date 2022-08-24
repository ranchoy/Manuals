### C++二分图匹配算法总结

- #### 匈牙利算法

  - 此算法是由匈牙利数学家Edmonds在1965年提出，这是一种在多项式时间求解任务分配的组合优化算法，例如男女生最大配对问题。时间复杂度是O(m*n)。

  - 再介绍算法之前介绍几个概念，二分图：把一个图中所有顶点划分成两个不相交的集合；匹配：图中任意两条边都没有公共顶点；交替路径：每一条边交替的属于匹配M或不属于匹配M；增广路径：给定一个匹配M，增广路径从M中没有用用到的顶点开始，并从M中没有用到的顶点结束的交替路径。

  - 匈牙利算法实际上就是求这个增广路径，并且反转这个增广路径，这样每次都会使得匹配M中的边数增加一条，这是算法的核心。

  - 具体代码：

    ````c++
    #include<iostream>
    #include<cstdio>
    #include<cstring>
    #include<algorithm>
    #define M 105
    #define N 55
    using namespace std;
    
    int m,n;// m男生，n女生
    int vis[N];// 每次访问过的女生不在访问 
    int map[M][N]; 
    int boys[M],girls[N];
     
    // 男生x找到女生返回true，否则返回false 
    bool dfs(int x) 
    {
    	for(int j=1; j<=n; j++)
    	{
    		if(map[x][j]==1 && vis[j]==0)
    		{
    			vis[j] = 1;
    			if(girls[j]==0 || dfs(girls[j]))// 女生没有男朋友||女生男朋友找到其她女生，则让出当前女生j 
    			{
    				girls[j] = x;
    				return true;
    			}
    		}
    	}
    	return false;
    }
    
    int main()
    {
    	int cnt,temp,k,res;
    	cin >> cnt;
    	while(cnt--)
    	{
    		// 初始化
    		res = 0;
    		memset(girls, 0, sizeof(girls));
    		memset(map, 0, sizeof(map));
    		 
    		scanf("%d %d", &m, &n);
    		for(int i=1; i<=m; i++)
    		{
    			scanf("%d", &temp);
    			while(temp--)
    			{
    				scanf("%d", &k);
    				map[i][k] = 1;
    			}
    		}
    		
    		for(int i=1; i<=m; i++)
    		{
    			memset(vis, 0, sizeof(vis));
    			if(dfs(i))// 匹配好一个男生 
    			{
    				res ++;
    			}
    		}
    		
    		if(res == m)
    		{
    			printf("YES\n");
    		}
    		else
    		{
    			printf("NO\n");
    		}
    	}
    	return 0;
    } 
    
    /*
    2
    3 3
    3 1 2 3
    2 1 2
    1 1
    3 3
    2 1 3
    2 1 3
    1 1
    
    YES
    NO
    */ 
    ````

- #### KM算法