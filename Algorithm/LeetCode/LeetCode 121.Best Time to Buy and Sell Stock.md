> https://leetcode.com/problems/best-time-to-buy-and-sell-stock/



# LeetCode : 121. Best Time to Buy and Sell Stock﻿

﻿

: You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return *the maximum profit you can achieve from this transaction*. If you cannot achieve any profit, return 0.

**: i번째 날의 가격이 prices[i]에 저장된 prices 배열이 주어진다.**

**당신은 하루에 주식을 사서, 다른 미래의 날에 팔아 수익을 최고로 하길 원한다. 이 때, 이 거래에서 최고의 이익을 반환하라. 만약 어떠한 이익도 얻을 수 없다면 0을 반환하라.**



**Example 1:**

```python
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
```

**Example 2:**

```python
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
```



**Constraints:**

1 <= prices.length <= 105

0 <= prices[i] <= 104

---



**Submissions Code (Accepted):**

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        min_num = prices[0]
        profit = 0
        for i in prices:
            if  min_num > i:
                min_num = i
            else:
                profit = max(i - min_num, profit)
        return profit
```

첫번째 요소를 min_num에 저장하고, profit을 0으로 초기화 한다.

그리고 prices 배열을 돌면서 min_num 보다 작으면 그 값을 최소로 바꾸고,

아니라면 현재 값에서 최소값을 뺀 값과 현재 저장된 profit 중에 큰 값을 profit으로 저장한다.

이러면 O(n)의 복잡도로 해결 할 수 있다. 최종적으로 profit을 반환한다.



**Other Submissions Code:**

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        min_price = sys.maxsize
        
        for price in prices:
            min_price = min(min_price, price)
            profit = max(profit, price - min_price)
            
        return profit
```

최소 값을 시스템의 가장 큰값으로 해도 상관 없으며, min()을 사용하여 더 간단하게 할 수 있다.



**Using Keyword**

min() - 최소값 반환

max() - 최대값 반환

sys.maxsize - 시스템의 가장 높은 값 ( -를 붙이면 가장 낮은 값)



﻿