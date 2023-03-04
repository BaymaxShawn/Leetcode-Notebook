# 😀 33 - Search in Rotated Sorted Array

There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.

Given the array `nums` **after** the possible rotation and an integer `target`, return _the index of_ `target` _if it is in_ `nums`_, or_ `-1` _if it is not in_ `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [4,5,6,7,0,1,2], target = 0
</strong><strong>Output: 4
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [4,5,6,7,0,1,2], target = 3
</strong><strong>Output: -1
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: nums = [1], target = 0
</strong><strong>Output: -1
</strong></code></pre>

## Solution:

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:

        if not nums:
            return -1

        l, r = 0, len(nums)-1

        while l <= r:
            mid = (l+r)//2
            if nums[mid] == target:
               return mid
            if nums[l] <= nums[mid]:
                if nums[l] <=target <= nums[mid]:
                    r = mid-1
                else:
                    l = mid +1
            else:
                if nums[mid] <= target <= nums[r]:
                    l = mid +1
                else:
                    r = mid-1
        
        return -1

```
