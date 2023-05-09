---
description: medium 05/08/2023
---

# 😆 54 - Spiral Matrix

Given an `m x n` `matrix`, return _all elements of the_ `matrix` _in spiral order_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/13/spiral1.jpg)

<pre><code><strong>Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
</strong><strong>Output: [1,2,3,6,9,8,7,4,5]
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/11/13/spiral.jpg)

<pre><code><strong>Input: matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
</strong><strong>Output: [1,2,3,4,8,12,11,10,9,5,6,7]
</strong></code></pre>

&#x20;

**Constraints:**

* `m == matrix.length`
* `n == matrix[i].length`
* `1 <= m, n <= 10`
* `-100 <= matrix[i][j] <= 100`

## Solution

```python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        m,n = len(matrix),len(matrix[0])
        left ,right,top,bottom = 0,n-1,0,m-1
        res = []
        while left <= right and top <= bottom:
            
            for col in range(left,right+1):
                res.append(matrix[top][col])
            top += 1
            for row in range(top,bottom+1):
                res.append(matrix[row][right])
            right -=1
            for col in range(right,left-1,-1):
                res.append(matrix[bottom][col])
            bottom -= 1
            for row in range(bottom,top-1,-1):
                res.append(matrix[row][left])
            left += 1
            
        return res[:m*n]
```
