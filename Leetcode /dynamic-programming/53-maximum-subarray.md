# 😎 53 - Maximum Subarray

Given an integer array `nums`, find the&#x20;

subarray with the largest sum, and return _its sum_.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
</strong><strong>Output: 6
</strong><strong>Explanation: The subarray [4,-1,2,1] has the largest sum 6.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [1]
</strong><strong>Output: 1
</strong><strong>Explanation: The subarray [1] has the largest sum 1.
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: nums = [5,4,-1,7,8]
</strong><strong>Output: 23
</strong><strong>Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= nums.length <= 105`
* `-104 <= nums[i] <= 104`

## Solution

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:

        res = float("-inf")
        cur = 0

        for i in nums:
            cur = max(i,cur+i)
            res = max(res,cur)
        
        return res
```

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:

       
        dp = [[0]*len(nums) for i in range(2)]
        dp[0][0],dp[1][0] = nums[0],nums[0]
        
        for i in range(1,len(nums)):
            dp[1][i] = max(nums[i],nums[i]+dp[1][i-1])
            dp[0][i] = max(dp[1][i], dp[0][i-1])
        return dp[0][-1]
```
