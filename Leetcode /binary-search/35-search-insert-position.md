# ☝ 35 - Search Insert Position

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with `O(log n)` runtime complexity.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [1,3,5,6], target = 5
</strong><strong>Output: 2
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [1,3,5,6], target = 2
</strong><strong>Output: 1
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: nums = [1,3,5,6], target = 7
</strong><strong>Output: 4
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= nums.length <= 104`
* `-104 <= nums[i] <= 104`
* `nums` contains **distinct** values sorted in **ascending** order.
* `-104 <= target <= 104`

## Solution

```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:

        l,r = 0,len(nums)

        while l< r:
            mid = (l+r)//2
            if nums[mid] == target:
                return mid
            elif nums[mid] > target:
                r = mid
            else:
                l = mid+1
        
        return l
            
```
