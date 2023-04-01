---
description: medium
---

# 😜 64 - Minimum Path Sum

mediumGiven a `m x n` `grid` filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

**Note:** You can only move either down or right at any point in time.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/05/minpath.jpg)

<pre><code><strong>Input: grid = [[1,3,1],[1,5,1],[4,2,1]]
</strong><strong>Output: 7
</strong><strong>Explanation: Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: grid = [[1,2,3],[4,5,6]]
</strong><strong>Output: 12
</strong></code></pre>

## Solution

{% embed url="https://www.youtube.com/watch?v=pGMsrvt0fpk" %}

#### DP

```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        row,col = len(grid),len(grid[0])
        res = [[float("inf")]* (col+1) for r in range(row+1)]
        res[row-1][col] = 0

        for i in range(row-1,-1,-1):
            for j in range(col-1,-1,-1):
                res[i][j] = grid[i][j] + min(res[i+1][j],res[i][j+1])

        return res[0][0]
        
```

这是一个 Python 的 for 循环语句，用来迭代从 r 开始递减到 -1（不包括 -1）的整数序列。

具体来说，这个语句中：

* `r` 是循环的起始值，可以是任何整数；
* `-1` 是循环的结束值，表示循环到这个值就停止，但不包括这个值本身；
* `-1` 是循环步长，表示每次迭代递减 1。

例如，如果 `r` 的值为 5，那么这个循环将会迭代 5、4、3、2、1 这些整数。可以把循环体放在这个语句的下一行，如下所示：

```css
cssCopy coder = 5
for i in (r,-1,-1):
    print(i)
```

输出：

```
Copy code5
4
3
2
1
```
