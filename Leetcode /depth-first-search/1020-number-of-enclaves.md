---
description: medium
---

# 😂 1020 - Number of Enclaves

You are given an `m x n` binary matrix `grid`, where `0` represents a sea cell and `1` represents a land cell.

A **move** consists of walking from one land cell to another adjacent (**4-directionally**) land cell or walking off the boundary of the `grid`.

Return _the number of land cells in_ `grid` _for which we cannot walk off the boundary of the grid in any number of **moves**_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/02/18/enclaves1.jpg)

<pre><code><strong>Input: grid = [[0,0,0,0],[1,0,1,0],[0,1,1,0],[0,0,0,0]]
</strong><strong>Output: 3
</strong><strong>Explanation: There are three 1s that are enclosed by 0s, and one 1 that is not enclosed because its on the boundary.
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/02/18/enclaves2.jpg)

<pre><code><strong>Input: grid = [[0,1,1,0],[0,0,1,0],[0,0,1,0],[0,0,0,0]]
</strong><strong>Output: 0
</strong><strong>Explanation: All 1s are either on the boundary or can reach the boundary.
</strong></code></pre>

&#x20;

**Constraints:**

* `m == grid.length`
* `n == grid[i].length`
* `1 <= m, n <= 500`
* `grid[i][j]` is either `0` or `1`.

## solution

```python
class Solution:
    def numEnclaves(self, grid: List[List[int]]) -> int:

        m = len(grid)
        n = len(grid[0])
        
        total = 0

        directory = ((-1,0),(1,0),(0,-1),(0,1))

        queue = []

        for i in range(m):
            for j in range(n):
                count = 0
                if grid[i][j] == 1:
                    queue.append((i,j))
                    grid[i][j] = 0
                    is_touch = True

                    while queue:
                        count += 1
                        cur_i,cur_j = queue.pop()

                        if cur_i in (0,m-1) or cur_j in (0,n-1):
                            is_touch = False

                        for d in directory:
                            new_i = cur_i + d[0]
                            new_j = cur_j + d[1]

                            if 0<= new_i<= m-1 and 0<= new_j<= n-1 and grid[new_i][new_j] == 1:
                                queue.append((new_i,new_j))

                                grid[new_i][new_j] = 0
                    
                    if is_touch:
                        total += count
                        
        return total


```
