# 🌥 912 - Sort an Array

Given an array of integers `nums`, sort the array in ascending order and return it.

You must solve the problem **without using any built-in** functions in `O(nlog(n))` time complexity and with the smallest space complexity possible.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [5,2,3,1]
</strong><strong>Output: [1,2,3,5]
</strong><strong>Explanation: After sorting the array, the positions of some numbers are not changed (for example, 2 and 3), while the positions of other numbers are changed (for example, 1 and 5).
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [5,1,1,2,0,0]
</strong><strong>Output: [0,0,1,1,2,5]
</strong><strong>Explanation: Note that the values of nums are not necessairly unique.
</strong></code></pre>

## Solution:

#### Python

```python
class Solution(object):
    def sortArray(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """

        if len(nums) <= 1:
            return nums
        
        mid = len(nums)//2
        left = nums[:mid]
        right = nums [mid:]

        left = self.sortArray(left)
        right = self.sortArray(right)

        i = j = 0
        merge = []
        while i < len(left) and j <len(right):
            if left[i] < right[j]:
                merge.append(left[i])
                i+=1
            else :
                merge.append(right[j])
                j+=1
        
        merge += left[i:]
        merge += right[j:]
        
        return merge
```

