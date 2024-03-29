---
description: Medium 2023/03/28 每日一题
---

# 😉 983 - Minimum Cost For Tickets

You have planned some train traveling one year in advance. The days of the year in which you will travel are given as an integer array `days`. Each day is an integer from `1` to `365`.

Train tickets are sold in **three different ways**:

* a **1-day** pass is sold for `costs[0]` dollars,
* a **7-day** pass is sold for `costs[1]` dollars, and
* a **30-day** pass is sold for `costs[2]` dollars.

The passes allow that many days of consecutive travel.

* For example, if we get a **7-day** pass on day `2`, then we can travel for `7` days: `2`, `3`, `4`, `5`, `6`, `7`, and `8`.

Return _the minimum number of dollars you need to travel every day in the given list of days_.

&#x20;

**Example 1:**

<pre><code><strong>Input: days = [1,4,6,7,8,20], costs = [2,7,15]
</strong><strong>Output: 11
</strong><strong>Explanation: For example, here is one way to buy passes that lets you travel your travel plan:
</strong>On day 1, you bought a 1-day pass for costs[0] = $2, which covered day 1.
On day 3, you bought a 7-day pass for costs[1] = $7, which covered days 3, 4, ..., 9.
On day 20, you bought a 1-day pass for costs[0] = $2, which covered day 20.
In total, you spent $11 and covered all the days of your travel.
</code></pre>

**Example 2:**

<pre><code><strong>Input: days = [1,2,3,4,5,6,7,8,9,10,30,31], costs = [2,7,15]
</strong><strong>Output: 17
</strong><strong>Explanation: For example, here is one way to buy passes that lets you travel your travel plan:
</strong>On day 1, you bought a 30-day pass for costs[2] = $15 which covered days 1, 2, ..., 30.
On day 31, you bought a 1-day pass for costs[0] = $2 which covered day 31.
In total, you spent $17 and covered all the days of your travel.
</code></pre>

&#x20;

**Constraints:**

* `1 <= days.length <= 365`
* `1 <= days[i] <= 365`
* `days` is in strictly increasing order.
* `costs.length == 3`
* `1 <= costs[i] <= 1000`

## Solution

[https://www.bilibili.com/video/BV1Wz4y1f7hG/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810](https://www.bilibili.com/video/BV1Wz4y1f7hG/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810)

```python
class Solution:
    def mincostTickets(self, days: List[int], costs: List[int]) -> int:

         first,last = days[0],days[-1]
         days = set(days)
         dp = [0]*(last+1)
         
         for i in range(first,last+1):
               if i in days:
                  p1 = dp[i-1] if i-1 > 0 else 0
                  p7 = dp[i-7] if i -7 > 0 else 0
                  p30 = dp[i-30] if i - 30 > 0 else 0
                  dp[i] = min(p1 + costs[0],p7 + costs[1],p30 + costs[2])
                  print(dp[i])
               else:
                  dp[i] = dp[i-1]

         return dp[last]
```

```python
class Solution:
   def mincostTickets(self, days, costs):
      """
      :type days: List[int]
      :type costs: List[int]
      :rtype: int
      """
      dp=[0 for i in range(days[-1]+1)]
      for i in range(days[-1]+1):
            if i not in days:
               dp[i]=dp[i-1]
            else:
               dp[i]=min(dp[max(0,i-7)]+costs[1],dp[max(0,i-1)]+costs[0],dp[max(0,i-30)]+costs[2])
      return dp[-1]
```

