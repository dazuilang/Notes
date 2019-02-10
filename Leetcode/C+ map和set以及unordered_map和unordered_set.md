# C+ map和set以及unordered_map和unordered_set

map,set,unordered_map和unordered_set都是C++ STL中的容器，其中map和set内部结构是红黑树，元素是有序的，查找复杂度为O(logN)，unordered_map和unordered_set内部结构是哈希表，元素是无序的，查找复杂度为O(1)。

set和unordered_set使用方法类似,注意到unordered_set中并没有反向迭代器，因为元素是无序的
```
#include <iostream>
#include <string>
#include <set>
using namespace std;
int main()
{
    set<int> a {1, 2, 3};
    a.erase(3);
    a.clear();
    a.insert(5);
    a.insert(3);
    a.insert(7);

    //查找元素5是否存在
    a.count(5);
    a.find(5)!=a.end();

    a.size();
    a.empty();

    //顺序遍历
    set<int>::iterator it;
    for (it = a.begin(); it != a.end(); it++)
        cout << *it << endl;
    
    //逆序遍历，注意迭代器不同
    set<int>::reverse_iterator rit;
    for (rit = a.rbegin(); rit != a.rend(); rit++)
        cout << *rit << endl;
}
```
map和unordered_map使用方法如下 ，注意到unordered_map中并没有反向迭代器
```
#include <iostream>
#include <string>
#include <map>
using namespace std;
int main()
{
    map<string, int> a;
    a["a"] = 2;
    a.insert({"b",5});
    a.clear();
    a.empty();
    a = {{"a", 5}, {"c", 7}, {"b", 6}};
    a.erase("a");
    
    //查找元素
    a.count("a");
    a.find("a")!=a.end();

    //顺序遍历
    map<string, int>::iterator it;
    for (it = a.begin(); it != a.end(); it++)
        cout << it->first << ' ' << it->second << endl;
    
    //逆序遍历，注意迭代器不同
    map<string, int>::reverse_iterator rit;
    for (rit = a.rbegin(); rit != a.rend(); rit++)
        cout << rit->first << ' ' << rit->second << endl;
}
```
