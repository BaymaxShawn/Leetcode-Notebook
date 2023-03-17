# 😆 217 - Contains Duplicate

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

<pre><code><strong>Input: nums = [1,2,3,1]
</strong><strong>Output: true
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [1,2,3,4]
</strong><strong>Output: false
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: nums = [1,1,1,3,3,4,3,2,4,2]
</strong><strong>Output: true
</strong></code></pre>

## Solution

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:

        res = set()
        for i in nums:
            if i not in res:
                res.add(i)
            else:
                return True
        return False
```
