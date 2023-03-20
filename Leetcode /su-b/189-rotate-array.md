# 😛 189 - Rotate Array

Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative.

**Example 1:**

<pre><code><strong>Input: nums = [1,2,3,4,5,6,7], k = 3
</strong><strong>Output: [5,6,7,1,2,3,4]
</strong><strong>Explanation:
</strong>rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
</code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [-1,-100,3,99], k = 2
</strong><strong>Output: [3,99,-1,-100]
</strong><strong>Explanation: 
</strong>rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
</code></pre>

&#x20;

**Constraints:**

* `1 <= nums.length <= 105`
* `-231 <= nums[i] <= 231 - 1`
* `0 <= k <= 105`

&#x20;

**Follow up:**

* Try to come up with as many solutions as you can. There are at least **three** different ways to solve this problem.
* Could you do it in-place with `O(1)` extra space?

## Solution

```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k = k%len(nums)

        nums[:len(nums)-k],nums[len(nums)-k:] = nums[len(nums)-k:],nums[:len(nums)-k]

        return nums

```
