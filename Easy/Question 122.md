# Discription
You are given an integer array prices where prices[i] is the price of a given stock on the ith day.

On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it then immediately sell it on the same day.

Find and return the maximum profit you can achieve.

## Analysis
股票买卖策略：  
1. 单独交易日：  
令今天的价格 P1, 明天价格为P2， 今天买入，明天卖出，则收益为 P2-P1，负值则表示亏损。  
2. 连续交易日：  
设此上涨交易日股票价格分别为 p1,p2,p3...pn, 则第一天买最后一天卖收益最大,为 pn-p1,而其实可以看做是多个单独交易日的总和
 
 ## Algorithm
 遍历整个股票交易日价格列表 price，策略是所有上涨交易日都买卖（赚到所有利润），所有下降交易日都不买卖（永不亏钱）。
设 tmp 为第 i-1 日买入与第 i 日卖出赚取的利润，即 tmp = prices[i] - prices[i - 1] ；
当该天利润为正 tmp > 0，则将利润加入总利润 profit；当利润为 00 或为负，则直接跳过；
遍历完成后，返回总利润 profit。

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        for i in range(1, len(prices)):
            tmp = prices[i] - prices[i - 1]
            if tmp > 0: profit += tmp
        return profit

```

