---
description: easy
---

# 😏 70 - Climbing Stairs

You are climbing a staircase. It takes `n` steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

&#x20;

**Example 1:**

<pre><code><strong>Input: n = 2
</strong><strong>Output: 2
</strong><strong>Explanation: There are two ways to climb to the top.
</strong>1. 1 step + 1 step
2. 2 steps
</code></pre>

**Example 2:**

<pre><code><strong>Input: n = 3
</strong><strong>Output: 3
</strong><strong>Explanation: There are three ways to climb to the top.
</strong>1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
</code></pre>

&#x20;

**Constraints:**

* `1 <= n <= 45`

## Solution

#### two pointer

```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """

        pre,cur = 0, 1
        for i in range(n):
            pre, cur = cur, pre+cur
        
        return cur
```

#### DP

```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """

        dp = [0]*(n+1)
        if n <= 1:
            dp[0] = 0
            dp[1] = 1
        else:
            dp[0] = 0
            dp[1] = 1
            dp[2] = 2

            for i in range(3,n+1):
                dp[i] = dp[i-1]+dp[i-2]
        
        return dp[n]
```
