# 😋 724 - Find Pivot Index

Given an array of integers `nums`, calculate the **pivot index** of this array.

The **pivot index** is the index where the sum of all the numbers **strictly** to the left of the index is equal to the sum of all the numbers **strictly** to the index's right.

If the index is on the left edge of the array, then the left sum is `0` because there are no elements to the left. This also applies to the right edge of the array.

Return _the **leftmost pivot index**_. If no such index exists, return `-1`.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [1,7,3,6,5,6]
</strong><strong>Output: 3
</strong><strong>Explanation:
</strong>The pivot index is 3.
Left sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11
Right sum = nums[4] + nums[5] = 5 + 6 = 11
</code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [1,2,3]
</strong><strong>Output: -1
</strong><strong>Explanation:
</strong>There is no index that satisfies the conditions in the problem statement.
</code></pre>

**Example 3:**

<pre><code><strong>Input: nums = [2,1,-1]
</strong><strong>Output: 0
</strong><strong>Explanation:
</strong>The pivot index is 0.
Left sum = 0 (no elements to the left of index 0)
Right sum = nums[1] + nums[2] = 1 + -1 = 0
</code></pre>

&#x20;

**Constraints:**

* `1 <= nums.length <= 104`
* `-1000 <= nums[i] <= 1000`

&#x20;

**Note:** This question is the same as 1991: [https://leetcode.com/problems/find-the-middle-index-in-array/](https://leetcode.com/problems/find-the-middle-index-in-array/)

## Solution

```python
class Solution:
    def pivotIndex(self, nums: List[int]) -> int:

        total = sum(nums)
        
        temp = 0

        for i in range(len(nums)):
           
            if temp == total-temp - nums[i]:
                return i
            print(temp)
            temp += nums[i]
            

        return -1
```