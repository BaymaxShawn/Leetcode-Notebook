# 🤳 1646 - Get Maximum in Generated Array

You are given an integer `n`. A **0-indexed** integer array `nums` of length `n + 1` is generated in the following way:

* `nums[0] = 0`
* `nums[1] = 1`
* `nums[2 * i] = nums[i]` when `2 <= 2 * i <= n`
* `nums[2 * i + 1] = nums[i] + nums[i + 1]` when `2 <= 2 * i + 1 <= n`

Return _the **maximum** integer in the array_ `nums`​​​.

&#x20;

**Example 1:**

<pre><code><strong>Input: n = 7
</strong><strong>Output: 3
</strong><strong>Explanation: According to the given rules:
</strong>  nums[0] = 0
  nums[1] = 1
  nums[(1 * 2) = 2] = nums[1] = 1
  nums[(1 * 2) + 1 = 3] = nums[1] + nums[2] = 1 + 1 = 2
  nums[(2 * 2) = 4] = nums[2] = 1
  nums[(2 * 2) + 1 = 5] = nums[2] + nums[3] = 1 + 2 = 3
  nums[(3 * 2) = 6] = nums[3] = 2
  nums[(3 * 2) + 1 = 7] = nums[3] + nums[4] = 2 + 1 = 3
Hence, nums = [0,1,1,2,1,3,2,3], and the maximum is max(0,1,1,2,1,3,2,3) = 3.
</code></pre>

**Example 2:**

<pre><code><strong>Input: n = 2
</strong><strong>Output: 1
</strong><strong>Explanation: According to the given rules, nums = [0,1,1]. The maximum is max(0,1,1) = 1.
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: n = 3
</strong><strong>Output: 2
</strong><strong>Explanation: According to the given rules, nums = [0,1,1,2]. The maximum is max(0,1,1,2) = 2.
</strong></code></pre>

&#x20;

**Constraints:**

* `0 <= n <= 100`

## Solution

```python
class Solution:
    def getMaximumGenerated(self, n: int) -> int:

        if n == 0:
            return 0

        dp= [0]*(n+2)
        dp[1] = 1
        m = 1
        for i in range(2,n+1):
            dp[i] = dp[i//2] + dp[i//2 +1]*(i%2)
        
        return max(dp[:])
```
