---
description: medium
---

# 😂 74 - Search a 2D Matrix

You are given an `m x n` integer matrix `matrix` with the following two properties:

* Each row is sorted in non-decreasing order.
* The first integer of each row is greater than the last integer of the previous row.

Given an integer `target`, return `true` _if_ `target` _is in_ `matrix` _or_ `false` _otherwise_.

You must write a solution in `O(log(m * n))` time complexity.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/10/05/mat.jpg)

<pre><code><strong>Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
</strong><strong>Output: true
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/10/05/mat2.jpg)

<pre><code><strong>Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
</strong><strong>Output: false
</strong></code></pre>

&#x20;

**Constraints:**

* `m == matrix.length`
* `n == matrix[i].length`
* `1 <= m, n <= 100`
* `-104 <= matrix[i][j], target <= 104`

## Solution

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        def find_row(target):
            l,r = 0, len(matrix)-1
            while l< r:
                mid = (l+r)//2
                if matrix[mid][-1] >= target:
                    r = mid
                else:
                    l = mid+1
            return l
    
        s = matrix[find_row(target)]

        le,ri = 0, len(s)-1
        while le <= ri:
            mid = (le+ri)//2
            if s[mid] == target:
                return True
            elif s[mid] > target:
                ri = mid-1
            else:
                le = mid +1
            
        return False

```
