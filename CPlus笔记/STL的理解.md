### STL库函数

##### vector向量

```c++
vector<int> vt;
vt.front(); // 返回第一个元素的引用
vt.back(); // 返回最后一个元素的引用
reverse(vt.begin(),vt.end()); // 将元素翻转，逆序排列
vector<it> vt2(vt.begin(),vt.end()); // 拷贝构造函数
vector<vector<int> > res(N, vector<int>(N, 0)); // 二维vector向量初始化

vt2.assign(vt.beigin(), vt.end()) // 复制，[begin, end)左闭右开区间
vt2.assign(vt.beigin(), vt.beigin()+len+1) // 复制，长度为len的数据从vt.begin()开始
sort(vt.begin(), vt.end(), less<data_type>()); // 从小到大排序
sort(vt.begin(), vt.end(), grater<data_type>()); // 从大到小排序
```

##### string字符串

```
string s = "aaa";
string s("aaa");
s.find('a') // 查找string子串，找到返回索引，未找到返回string::nops;
s.c_str(); // 转换成字符串类型
s.substr(begin, end); // 按照下标截取字符串
1）输入格式：
getline(cin, s); // string输入，遇到空格（space，tab）不会结束，直到遇到换行符（enter）才结束；
cin.getline(字符数组名，接收长度，结束符); // 字符串输入，最大允许长度为max_size；
cin.get(字符数组名，接收长度，结束符) // 读取字符，等价与getchar()，返回值为int类型，为1表示读出一个字符，否则为0；
3）cin.get()当一开始第一个输入字符(即前面无其他任何字符)就遇到结束符情况下，将不会正常输出，但缓冲区中依然有该结束符；
4）cin.get()每次读取一整行并把由Enter键生成的换行符留在输入队列中，然而cin.getline()每次读取一整行并把由Enter键生成的换行符抛弃；
5）字符串分割：
char str[80] = "This is-hello-world";
char *p = strtok(str, d);
while(p) {
	printf("%s\n", p);
	p=strtok(NULL, d);
}
6）字符串查找
str.find("ab"); // 返回字符串ab在str的位置
str.find("ab", 2); // 在区间[2,n-1]区间内查找并返回字符串ab在str的位置
str.rfind("ab", 2); // 在区间[0,2]区间内查找并返回字符串ab在str的位置
str.find_first_of("a"); // 查找首次出现的位置
str.find_last_of("a"); // 查找最后一次出现的位置
7）字符串的子串
str.substr(3); // 返回idx=3之后的子串
str.substr(2,4); // 返回区间[2,2+4-1]的子串
8）字符串替换
str.replace(2, 4, "ab"); // 替换区间[2,2+4-1]的字符串为"ab"
str.replace(2, 4, "abcd", 3); // 替换区间[2,2+4-1]的字符串"abcd"的前3个字符的子串
9）字符串插入
str.insert(1, "ab"); // 往idx=1位置插入字符串"ab"
str.insert(1, "abcd", 3); // 往idx=1位置插入"abcd"的前3个子符子串
10）字符串删除
str.erase(3); // 删除idx=3位置之后的字符
str.earse(3, 5); // 删除idx=3位置之后的5个字符
11）字符串交换
str1.swap(str2); // 字符串交换
12）取字符
str.at(n); //  取idx=n位置的字符
```

```
unsigned int npos = -1; // 计算机补码表示，0xffff
原码：第一位为符号位，其余位表示数值，如-1的原码：1,000...0001(两个1之间32个0)。
反码：负数的反码为符号位不变，数值位按位取反。如-1的补码为1,111...1110。
补码：正数的补码就是其原码。负数的补码为=反码+1。因此，-1的补码为1,111...111。
因此，unsigned(-1)=1,111...111(共32个1)。表示unsigned的最大值。
```

##### map容器

```
#include <map>
map<int, string> mp;
mp.emplace(10, "ten"); // 插入一个元素，转移构造函数
mp.emplace(make_pair(0, "ten")); // 插入一个元素, 模板构造函数

mp.insert(make_pair(0, "test")); // 插入元素
mp.insert(map<int, string>::value_type(0, "test"));
mp.erase(mp.begin(), mp.end()); // 清空所有元素
clear() // 删除所有元素
count() // 返回指定元素出现的次数
empty() // 如果map为空则返回true
begin() // 返回一个指向map头部的逆向迭代器
end()   // 返回指向map末尾的迭代器
rbegin() // 返回一个指向map尾部的逆向迭代器
rend() // 返回一个指向map头部的逆向迭代器
equal_range() // 返回特殊条目的迭代器对
insert() // 插入元素
erase() // 删除一个元素，删除成功返回1，否则返回0
find()  // 查找一个元素，找到返回iterator，否则返回mp.end()位置
get_allocator() // 返回map的配置器
key_comp() // 返回比较元素key的函数
lower_bound() // 返回键值>=给定元素的第一个位置
max_size() // 返回可以容纳的最大元素个数
size() // 返回map中元素的个数
swap() // 交换两个map
upper_bound() // 返回键值>给定元素的第一个位置
value_comp() // 返回比较元素value的函数
```

#### unorder_map

```
#include <unordered_map>
unordered_map<string, int> map;
map.insert(make_pair("c++", 100)); // 插入元素
int size = map.size(); // map大小
auto iter = map.find("c++"); // iter迭代器，找到返回目标元素的迭代器，否则返回map.end()迭代器
map.erase("c++"); // 删除元素
map.count("c++"); // 返回键对应的值，如果存在返回1，否则返回0
cout << map["c++"] << endl; // 打印元素
for(auto &v : map) // map遍历
	cout << v.first << " " << v.second << endl;
for(auto iter = map.begin(); iter!=map.end(); iter++) // map遍历
	cout << iter->first << " " << iter->second << endl;
```

##### unorder_set集合

```c++
#include<unordered_set> // 插入重复元素只算一个
unordered_set<int> set;
set.insert(3); // 插入元素
set.erase(3); // 删除元素
int size = set.size(); // 集合大小
auto iter = set.find(3); // 返回iter迭代器，找到就返回目标元素的迭代器，否则返回iter.end()迭代器
auto iter = set.begin(); // 首部iter迭代器
for(auto &v : set) // set遍历
	cout << v << endl;
for(auto iter=set.begin(); iter!=set.end(); iter++) // set遍历
	cout << *iter << endl;
```
