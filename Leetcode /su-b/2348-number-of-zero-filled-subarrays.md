---
description: medium 2023/3/21 每日一题
---

# 🚅 2348 - Number of Zero-Filled Subarrays

Given an integer array `nums`, return _the number of **subarrays** filled with_ `0`.

A **subarray** is a contiguous non-empty sequence of elements within an array.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [1,3,0,0,2,0,0,4]
</strong><strong>Output: 6
</strong><strong>Explanation: 
</strong>There are 4 occurrences of [0] as a subarray.
There are 2 occurrences of [0,0] as a subarray.
There is no occurrence of a subarray with a size more than 2 filled with 0. Therefore, we return 6.
</code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [0,0,0,2,0,0]
</strong><strong>Output: 9
</strong><strong>Explanation:
</strong>There are 5 occurrences of [0] as a subarray.
There are 3 occurrences of [0,0] as a subarray.
There is 1 occurrence of [0,0,0] as a subarray.
There is no occurrence of a subarray with a size more than 3 filled with 0. Therefore, we return 9.
</code></pre>

**Example 3:**

<pre><code><strong>Input: nums = [2,10,2019]
</strong><strong>Output: 0
</strong><strong>Explanation: There is no subarray filled with 0. Therefore, we return 0.
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= nums.length <= 105`
* `-109 <= nums[i] <= 109`

## Solution

tips：[https://blog.csdn.net/kudou1994/article/details/98983359](https://blog.csdn.net/kudou1994/article/details/98983359)

```python
class Solution:
    def sub(self,n):
        a = 0
        for i in range(1,n+1):
            a += i 
        return a       

    def zeroFilledSubarray(self, nums: List[int]) -> int:

        count = 0
        l,r = 0,0
        for i in range(len(nums)):
            if nums[i] != 0 and l == r:
                l += 1
                r += 1
            elif nums[i] != 0 and l != r:
                count += self.sub(r-l)    
                l = r
            elif nums[i] == 0 and i == len(nums)-1 :  
                r += 1
                count += self.sub(r-l)    
            else:
                r += 1
        return count

```
