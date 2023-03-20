# 😀 153 - Find Minimum in Rotated Sorted Array

Suppose an array of length `n` sorted in ascending order is **rotated** between `1` and `n` times. For example, the array `nums = [0,1,2,4,5,6,7]` might become:

* `[4,5,6,7,0,1,2]` if it was rotated `4` times.
* `[0,1,2,4,5,6,7]` if it was rotated `7` times.

Notice that **rotating** an array `[a[0], a[1], a[2], ..., a[n-1]]` 1 time results in the array `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]`.

Given the sorted rotated array `nums` of **unique** elements, return _the minimum element of this array_.

You must write an algorithm that runs in `O(log n) time.`

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [3,4,5,1,2]
</strong><strong>Output: 1
</strong><strong>Explanation: The original array was [1,2,3,4,5] rotated 3 times.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [4,5,6,7,0,1,2]
</strong><strong>Output: 0
</strong><strong>Explanation: The original array was [0,1,2,4,5,6,7] and it was rotated 4 times.
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: nums = [11,13,15,17]
</strong><strong>Output: 11
</strong><strong>Explanation: The original array was [11,13,15,17] and it was rotated 4 times. 
</strong></code></pre>

## Solution

#### Binary Search

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:

        l,r = 0 , len(nums)-1

        while l<r :
            mid = (l+r)//2
            if nums[mid] > nums[r]:
                l = mid+1
            else:
                r = mid 
        return nums[l]
```
