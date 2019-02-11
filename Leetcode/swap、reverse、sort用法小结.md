# swap、reverse、sort用法小结

swap、reverse和sort是C++中经常会用到的函数，其中swap的参数是引用，而reverse和sort的参数是指针，具体用法如下：

```
#include <iostream>
#include <algorithm>
using namespace std;
int main(){
    int a[]={1,2,3,4};
    swap(a[0],a[3]);
    for(int i:a)
        printf("%d",i);
    printf("\n");

    reverse(a,a+4);
    for(int i:a)
        printf("%d",i);
    printf("\n");

    sort(a,a+4);
    for(int i:a)
        printf("%d",i);
    printf("\n");
}
```

其中swap的函数原型如下
```
template <class T> void swap ( T& a, T& b )
{
  T c(a); a=b; b=c;
}
```

reverse的函数原型如下
```
template <class BidirectionalIterator>
  void reverse (BidirectionalIterator first, BidirectionalIterator last)
{
  while ((first!=last)&&(first!=--last)) {
    std::iter_swap (first,last);
    ++first;
  }
}
```

sort的函数原型如下
```
template <class RandomAccessIterator, class Compare>
  void sort (RandomAccessIterator first, RandomAccessIterator last, Compare comp);
```
其中compare函数为可选函数，可以用来比较struct等结构体，用法如下
```
#include <iostream>
#include <algorithm>
using namespace std;

struct A
{
       int c;
};

bool compare(A& a,A& b) 
{
     return a.c < b.c;
}

int main()
{
    A a[]{2,4,5,3,1};
    sort(a, a+ 5,compare); 
    for(A i:a)
        printf("%d",i.c);
}

````
