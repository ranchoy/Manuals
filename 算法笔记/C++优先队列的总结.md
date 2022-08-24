### c++优先队列的总结

- 如下代码，优先队列是按照元素由大到小排列的，a.x > b.x则a < b，排列顺序是：ba，所以x越小越排在前面。 

```c++
#include<queue>
using namespace std;
struct node{
	int x,y;
    bool operator < (const node &a) const {
        return x > a.x;//x越小优先级越高
    }
};
priority_quue<struct node> pq;
```

- less和greater优先队列

````c++
#include<queue>
using namesapce std;

priority_queue<int, vector<int>, less<int> > pq;
priority_queue<int, vector<int>, greater<int> > pq;

输出：
less<int> : 5,4,3,2,1
greater<int> : 1,2,3,4,5 
````

