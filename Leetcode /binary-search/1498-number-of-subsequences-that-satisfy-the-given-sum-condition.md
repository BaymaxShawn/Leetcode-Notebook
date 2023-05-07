# 1498 - Number of Subsequences That Satisfy the Given Sum Condition

You are given an array of integers `nums` and an integer `target`.

Return _the number of **non-empty** subsequences of_ `nums` _such that the sum of the minimum and maximum element on it is less or equal to_ `target`. Since the answer may be too large, return it **modulo** `109 + 7`.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [3,5,6,7], target = 9
</strong><strong>Output: 4
</strong><strong>Explanation: There are 4 subsequences that satisfy the condition.
</strong>[3] -> Min value + max value &#x3C;= target (3 + 3 &#x3C;= 9)
[3,5] -> (3 + 5 &#x3C;= 9)
[3,5,6] -> (3 + 6 &#x3C;= 9)
[3,6] -> (3 + 6 &#x3C;= 9)
</code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [3,3,6,8], target = 10
</strong><strong>Output: 6
</strong><strong>Explanation: There are 6 subsequences that satisfy the condition. (nums can have repeated numbers).
</strong>[3] , [3] , [3,3], [3,6] , [3,6] , [3,3,6]
</code></pre>

**Example 3:**

<pre><code><strong>Input: nums = [2,3,3,4,6,7], target = 12
</strong><strong>Output: 61
</strong><strong>Explanation: There are 63 non-empty subsequences, two of them do not satisfy the condition ([6,7], [7]).
</strong>Number of valid subsequences (63 - 2 = 61).
</code></pre>

&#x20;

**Constraints:**

* `1 <= nums.length <= 105`
* `1 <= nums[i] <= 106`
* `1 <= target <= 106`

## Solution

#### [https://www.youtube.com/watch?v=xCsIkPLS4Ls](https://www.youtube.com/watch?v=xCsIkPLS4Ls)

```python
class Solution:
    def numSubseq(self, nums: List[int], target: int) -> int:
        nums.sort()
        mod = 10**9 +7
        res = 0
        r = len(nums) -1
        
        for i,l in enumerate(nums):
            while (l+nums[r])>target and i<=r:
                r -= 1
            if i<= r:
                res += (2**(r-i))
                res %= mod

            
        return res
```
