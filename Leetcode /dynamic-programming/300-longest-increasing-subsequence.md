---
description: medium
---

# 😖 300 - Longest Increasing Subsequence

Given an integer array `nums`, return _the length of the longest **strictly increasing**_&#x20;

_**subsequence**_.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [10,9,2,5,3,7,101,18]
</strong><strong>Output: 4
</strong><strong>Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [0,1,0,3,2,3]
</strong><strong>Output: 4
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: nums = [7,7,7,7,7,7,7]
</strong><strong>Output: 1
</strong></code></pre>

## Solution

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:

        dp = [1]*len(nums)

        for i in range(1,len(nums)):
            for j in range(i):
                if nums[i] >nums[j]:
                    dp[i]= max(dp[i],dp[j]+1)
                
        return max(dp)

```

\
