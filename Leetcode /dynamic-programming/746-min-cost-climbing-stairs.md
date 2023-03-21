---
description: easy
---

# 🥳 746 - Min Cost Climbing Stairs

You are given an integer array `cost` where `cost[i]` is the cost of `ith` step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index `0`, or the step with index `1`.

Return _the minimum cost to reach the top of the floor_.

&#x20;

**Example 1:**

<pre><code><strong>Input: cost = [10,15,20]
</strong><strong>Output: 15
</strong><strong>Explanation: You will start at index 1.
</strong>- Pay 15 and climb two steps to reach the top.
The total cost is 15.
</code></pre>

**Example 2:**

<pre><code><strong>Input: cost = [1,100,1,1,1,100,1,1,100,1]
</strong><strong>Output: 6
</strong><strong>Explanation: You will start at index 0.
</strong>- Pay 1 and climb two steps to reach index 2.
- Pay 1 and climb two steps to reach index 4.
- Pay 1 and climb two steps to reach index 6.
- Pay 1 and climb one step to reach index 7.
- Pay 1 and climb two steps to reach index 9.
- Pay 1 and climb one step to reach the top.
The total cost is 6.
</code></pre>

&#x20;

**Constraints:**

* `2 <= cost.length <= 1000`
* `0 <= cost[i] <= 999`

## Solution

[https://www.bilibili.com/video/BV16G411c7yZ/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810](https://www.bilibili.com/video/BV16G411c7yZ/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810)

```python
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:

        dp = [0]*(len(cost)+1)
        dp[0]= 0
        dp[1]= 0

        for i in range(2,len(cost)+1):
            one_step = dp[i-1]+cost[i-1]
            two_step = dp[i-2]+cost[i-2]
            dp[i] = min(one_step,two_step)
            
        
        return dp[-1]on
        
        #dp数组的含义：dp的index代表的是台阶，dp数组的值代表的是所花费的最小值
```
