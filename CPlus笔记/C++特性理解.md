### 基础

##### 结构体特性

1. 测试结构体添加函数特性。

   ```
   #include<bits/stdc++.h>
   using namespace std;
   struct ListNode {
   	int val;
   	struct ListNode *next;
   	ListNode(int x): val(x), next(nullptr) {};
   	ListNode(int a, struct ListNode *b): val(a), next(b) {};
   	void(* print)(int);
   };
   void print(int a) {
   	cout << a+1 << endl;
   }
   int main() {
   	struct ListNode *head = new ListNode(-1);
   	struct ListNode *head1 = new ListNode(1, head);
   	cout << head->val << endl;
   	cout << head1->next->val << endl;
   	head->print = print;
   	head->print(1);
   	return 0;
   }
   ```

2. 

### 进阶