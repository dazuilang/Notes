# 一个由size()函数引发的BUG
今天做到了leetcode中的[122.买卖股票的最佳时机 II](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/description/),题目如下
>给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。
>
>设计一个算法来计算你所能获取的最大利润。你可以尽可能地完成更多的交易（多次买卖一支股票）。
>
>**注意**：你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。

一开始我是这样写的，题目报错了
```
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int res=0;
        for(int i=0;i<prices.size()-1;i++)
            if(prices[i]<prices[i+1])
                res+=prices[i+1]-prices[i];
        return res;
    }
};
```
报错信息如下
>reference binding to null pointer of type 'value_type'

报错测试用例为空数组，我于是在前面加了个检测数组是否为空的语句,提交成功

```
if(prices.empty)
    return 0;
```
但是还是没有找到出错的根源在哪，后来终于发现是prices.size()-1出现了问题

prices.size()的数据类型为size_t，是unsigned long，取值范围为0~2^32-1，输入为空数组时，prices.size()为0，prices.size()-1是负数，所以越界了
