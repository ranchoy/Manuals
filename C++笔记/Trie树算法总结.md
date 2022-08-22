### Trie树算法总结

- Trie树又称作字典树，前缀树。它主要用做处理：1.查询单词是否在词库中存在；2.查询单词是否在是词库插入时的单词；3.查询字符串作为单词的前缀在字符串中出现的次数。最常用的实现方式是通过数组trie(i,j)表示节点i的子节点j的编号，根节点root=0，编号从number=1开始。

- 查询单词是否在词库中存在，算法如下：

  ````c++
  // 查询某个字符或者单词是否在词库中
  // trie[i][j]=k,当前节点i的子节点j的编号为k 
  #include<iostream> 
  #include<cstdio>
  #include<cstring>
  #include<algorithm>
  #define MAX 20005
  using namespace std;
  
  int number;// 根节点root,编号number 
  int trie[MAX][27];
  
  // 插入字符串 
  void insert(char *str)
  {
  	int root=0;// 根节点为0 
  	for(int i=0,j=0; str[i]!='\0'; i++)
  	{
  		j = str[i] - 'a';
  		if(trie[root][j] == 0)// 未编号 
  		{
  			trie[root][j] = number ++;
  		}
  		root = trie[root][j];// 继续往下找 
  	}
  }
  
  // 查找
  bool search(char *str)
  {
  	int root = 0;// 根节点
  	for(int i=0,j=0; str[i]!='\0'; i++)	
  	{
  		j = str[i] - 'a';
  		if(trie[root][j] == 0)// 断了 
  		{
  			return false;
  		}
  		root = trie[root][j];// 未断则往下找 
  	}
  	return true; 
  } 
  
  int main()
  {
  	int n,m;
  	char str[1005];
  	while(~scanf("%d", &n))
  	{
  		// 初始化
  		number = 1;
  		memset(trie, 0, sizeof(trie));
  		
  		for(int i=0; i<n; i++)
  		{
  			scanf("%s", str);
  			insert(str);	
  		}
  		
  		scanf("%d", &m);
  		while(m--)
  		{
  			scanf("%s", &str);
  			if(search(str) == true)
  			{
  				printf("Yes\n");	
  			}	
  			else
  			{
  				printf("No\n");
  			}	
  		}
  	} 
  	return 0;
  }
  
  /*
  6
  cat
  cash
  app
  apple
  aply
  ok
  5
  c
  cat
  cash
  app
  aps
  
  Yes
  Yes
  Yes
  Yes
  No
  */
  ````

- 查询单词是否在是词库插入时的单词，算法如下：

  ````c++
  // 查询单词是否在是词库插入时的单词
  // trie[i][j]=k,当前节点i的子节点j的编号为k 
  #include<iostream> 
  #include<cstdio>
  #include<cstring>
  #include<algorithm>
  #define MAX 20005
  using namespace std;
  
  int number;// 根节点root,编号number 
  int trie[MAX][27];
  int vis[1005];// vis[i]编号为i的节点是否在词库中,往词库插单词时标记该单词
  
  // 插入字符串 
  void insert(char *str)
  {
  	int root=0;// 根节点为0 
  	for(int i=0,j=0; str[i]!='\0'; i++)
  	{
  		j = str[i] - 'a';
  		if(trie[root][j] == 0)// 未编号 
  		{
  			trie[root][j] = number ++;
  		}
  		root = trie[root][j];// 继续往下找 
  	}
  	
  	vis[root] = true;// 标记词库中存在的单词 
  }
  
  // 查找
  bool search(char *str)
  {
  	int root = 0;// 根节点
  	for(int i=0,j=0; str[i]!='\0'; i++)	
  	{
  		j = str[i] - 'a';
  		if(trie[root][j] == 0)// 断了 
  		{
  			return false;
  		}
  		root = trie[root][j];// 未断则往下找 
  	}
  	return vis[root];// 如果单词在词库中存在vis[root]为true,否则false 
  } 
  
  int main()
  {
  	int n,m;
  	char str[1005];
  	while(~scanf("%d", &n))
  	{
  		// 初始化
  		number = 1;
  		memset(trie, 0, sizeof(trie));
  		memset(vis, false, sizeof(vis));
  		
  		for(int i=0; i<n; i++)
  		{
  			scanf("%s", str);
  			insert(str);	
  		}
  		
  		scanf("%d", &m);
  		while(m--)
  		{
  			scanf("%s", &str);
  			if(search(str) == true)
  			{
  				printf("Yes\n");	
  			}	
  			else
  			{
  				printf("No\n");
  			}	
  		}
  	} 
  	return 0;
  }
  
  /*
  6
  cat
  cash
  app
  apple
  aply
  ok
  5
  c
  ca
  cat
  aps
  app
  
  No
  No
  Yes
  No
  Yes
  */
  ````

- 查询字符串作为单词的前缀在字符串中出现的次数，算法如下：

  ````c++
  // 查询前缀在词库出现次数 
  // trie[i][j]=k,当前节点i的子节点j的编号为k 
  #include<iostream> 
  #include<cstdio>
  #include<cstring>
  #include<algorithm>
  #define MAX 20005
  using namespace std;
  
  int number;// 根节点root,编号number 
  int trie[MAX][27];
  int arr[1005];// arr[i]词库中编号为i的节点,这个前缀在词库中出现的次数
  
  // 插入字符串 
  void insert(char *str)
  {
  	int root=0;// 根节点为0 
  	for(int i=0,j=0; str[i]!='\0'; i++)
  	{
  		j = str[i] - 'a';
  		if(trie[root][j] == 0)// 未编号 
  		{
  			trie[root][j] = number ++;
  		}
  		root = trie[root][j];// 继续往下找 
  	
  		arr[root] ++;// 前缀后移一个位置保存,次数加1 
  	}
  }
  
  // 查找出现次数,没有为0 
  int search(char *str)
  {
  	int root = 0;// 根节点
  	for(int i=0,j=0; str[i]!='\0'; i++)	
  	{
  		j = str[i] - 'a';
  		if(trie[root][j] == 0)// 字符串断了 
  		{
  			return 0;
  		}
  		root = trie[root][j];// 未断则往下找 
  	}
  	
  	return arr[root];// 前缀存在，返回次数 
  } 
  
  int main()
  {
  	int n,m;
  	char str[1005];
  	while(~scanf("%d", &n))
  	{
  		// 初始化
  		number = 1;
  		memset(arr, 0, sizeof(arr));
  		memset(trie, 0, sizeof(trie));
  	
  		for(int i=0; i<n; i++)
  		{
  			scanf("%s", str);
  			insert(str);	
  		}
  		
  		scanf("%d", &m);
  		while(m--)
  		{
  			scanf("%s", str);
  			printf("%d\n", search(str));	
  		} 
  	} 
  	return 0;
  }
  
  /*
  6
  cat
  cash
  app
  apple
  aply
  ok
  5
  c
  ca
  cat
  aps
  app
  
  2
  2
  1
  0
  2
  */
  ````


