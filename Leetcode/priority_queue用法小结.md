# priority_queue用法小结
priority_queue是C++中实现了最大堆的容器，包含在queue头文件里，主要有push(),pop()和top()这三个函数，另外可以通过修改比较函数或自定义struct来修改排序规则，有以下三种方法
```
#include<iostream>
#include<queue>
using namespace std;
int main(){
    priority_queue<int,vector<int>,greater<int>> queue;
    queue.push(2);
    queue.push(3);
    queue.push(1);
    cout<<queue.top();
}
```
```
#include<iostream>
#include<queue>
using namespace std;
struct cmp{
        bool operator ()(const int &a,const int &b){
                return a>b;
        }
};
int main(){
    priority_queue<int,vector<int>,cmp> queue;
    queue.push(2);
    queue.push(3);
    queue.push(1);
    cout<<queue.top();
}
```
```
#include<iostream>
#include<queue>
using namespace std;
struct Node{
        int x,y;
        friend bool operator<(const Node &a, const Node &b);
};
bool operator <(const Node &a,const Node &b){
        return a.x>b.x;
}
int main(){
    priority_queue<Node> queue;
    queue.push({1,2});
    queue.push({3,4});
    queue.push({5,6});
    cout<<queue.top().x;
}
```
