# 😅 283 - Move Zeroes

Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

**Note** that you must do this in-place without making a copy of the array.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [0,1,0,3,12]
</strong><strong>Output: [1,3,12,0,0]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [0]
</strong><strong>Output: [0]
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= nums.length <= 104`
* `-231 <= nums[i] <= 231 - 1`

## Solution

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        c = 0

        for i in range(len(nums)):
            if nums[i] != 0:
                nums[c],nums[i] = nums[i],nums[c]
                c += 1
```
