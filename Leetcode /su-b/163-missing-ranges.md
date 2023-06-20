# 🥳 163 - Missing Ranges

You are given an inclusive range `[lower, upper]` and a **sorted unique** integer array `nums`, where all elements are within the inclusive range.

A number `x` is considered **missing** if `x` is in the range `[lower, upper]` and `x` is not in `nums`.

Return _the **shortest sorted** list of ranges that exactly covers all the missing numbers_. That is, no element of `nums` is included in any of the ranges, and each missing number is covered by one of the ranges.

&#x20;

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [0,1,3,50,75], lower = 0, upper = 99
</strong><strong>Output: [[2,2],[4,49],[51,74],[76,99]]
</strong><strong>Explanation: The ranges are:
</strong>[2,2]
[4,49]
[51,74]
[76,99]
</code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [-1], lower = -1, upper = -1
</strong><strong>Output: []
</strong><strong>Explanation: There are no missing ranges since there are no missing numbers.
</strong></code></pre>

&#x20;

**Constraints:**

* `-109 <= lower <= upper <= 109`
* `0 <= nums.length <= 100`
* `lower <= nums[i] <= upper`
* All the values of `nums` are **unique**.

## Solution

```python
class Solution:
    def findMissingRanges(self, nums: List[int], lower: int, upper: int) -> List[List[int]]:

        nums = [lower-1] + nums + [upper+1]
        res = []

        for i in range(1,len(nums)):
            if nums[i] -nums[i-1] >= 2:
                res.append([nums[i-1]+1,nums[i]-1])

        return res
```
