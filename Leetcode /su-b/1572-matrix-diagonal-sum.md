---
description: 05/08/2023
---

# 😉 1572 - Matrix Diagonal Sum

Given a square matrix `mat`, return the sum of the matrix diagonals.

Only include the sum of all the elements on the primary diagonal and all the elements on the secondary diagonal that are not part of the primary diagonal.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/08/14/sample\_1911.png)

<pre><code><strong>Input: mat = [[1,2,3],
</strong><strong>              [4,5,6],
</strong><strong>              [7,8,9]]
</strong><strong>Output: 25
</strong><strong>Explanation: Diagonals sum: 1 + 5 + 9 + 3 + 7 = 25
</strong>Notice that element mat[1][1] = 5 is counted only once.
</code></pre>

**Example 2:**

<pre><code><strong>Input: mat = [[1,1,1,1],
</strong><strong>              [1,1,1,1],
</strong><strong>              [1,1,1,1],
</strong><strong>              [1,1,1,1]]
</strong><strong>Output: 8
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: mat = [[5]]
</strong><strong>Output: 5
</strong></code></pre>

&#x20;

**Constraints:**

* `n == mat.length == mat[i].length`
* `1 <= n <= 100`
* `1 <= mat[i][j] <= 100`

## Solution

```python
class Solution:
    def diagonalSum(self, mat: List[List[int]]) -> int:

        n = len(mat)
        res = 0

        for i in range(n):
            res += mat[i][i]
            res += mat[n-i-1][i]
        if n%2 != 0:
            res -= mat[n//2][n//2]
            
        return res
```
