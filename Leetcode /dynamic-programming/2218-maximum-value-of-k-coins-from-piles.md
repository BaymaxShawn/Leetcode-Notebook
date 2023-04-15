---
description: hard 2023/04/15 daily question
---

# 🤔 2218 - Maximum Value of K Coins From Piles

There are `n` **piles** of coins on a table. Each pile consists of a **positive number** of coins of assorted denominations.

In one move, you can choose any coin on **top** of any pile, remove it, and add it to your wallet.

Given a list `piles`, where `piles[i]` is a list of integers denoting the composition of the `ith` pile from **top to bottom**, and a positive integer `k`, return _the **maximum total value** of coins you can have in your wallet if you choose **exactly**_ `k` _coins optimally_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2019/11/09/e1.png)

<pre><code><strong>Input: piles = [[1,100,3],[7,8,9]], k = 2
</strong><strong>Output: 101
</strong><strong>Explanation:
</strong>The above diagram shows the different ways we can choose k coins.
The maximum total we can obtain is 101.
</code></pre>

**Example 2:**

<pre><code><strong>Input: piles = [[100],[100],[100],[100],[100],[100],[1,1,1,1,1,1,700]], k = 7
</strong><strong>Output: 706
</strong><strong>Explanation:
</strong>The maximum total can be obtained if we choose all coins from the last pile.
</code></pre>

&#x20;

**Constraints:**

* `n == piles.length`
* `1 <= n <= 1000`
* `1 <= piles[i][j] <= 105`
* `1 <= k <= sum(piles[i].length) <= 2000`

## Solution

[https://www.cnblogs.com/mozi-song/p/9615167.html#\_label0](https://www.cnblogs.com/mozi-song/p/9615167.html#\_label0)

{% embed url="https://www.youtube.com/watch?v=ZRdEd_eun8g" %}

```python
https://www.cnblogs.com/mozi-song/p/9615167.html#_label0class Solution:
    def maxValueOfCoins(self, piles: List[List[int]], k: int) -> int:
        n = len(piles)
        dp = [[-1]* (k+1) for _ in range(n)]

        def dfs(i,coins):
            if i == n:  #如果i==n意味着 out of piles，所以return 0
                return 0
            if dp[i][coins] != -1:
                return dp[i][coins]

            dp[i][coins] = dfs(i+1,coins) #如果跳过当前pile，skip the cur piles
            curPile = 0
            for j in range(min(coins,len(piles[i]))):
                curPile += piles[i][j]
                dp[i][coins] = max(dp[i][coins],curPile + dfs(i+1,coins -j-1)) #如果只需要当前pile的一部分，coins-j-1是因为j从0开始
            return dp[i][coins]
            

        
        return dfs(0,k)

```
