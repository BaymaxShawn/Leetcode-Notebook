---
description: medium
---

# 🤩 1254 - Number of Closed Islands

Given a 2D `grid` consists of `0s` (land) and `1s` (water).  An _island_ is a maximal 4-directionally connected group of `0s` and a _closed island_ is an island **totally** (all left, top, right, bottom) surrounded by `1s.`

Return the number of _closed islands_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2019/10/31/sample\_3\_1610.png)

<pre><code><strong>Input: grid = [[1,1,1,1,1,1,1,0],[1,0,0,0,0,1,1,0],[1,0,1,0,1,1,1,0],[1,0,0,0,0,1,0,1],[1,1,1,1,1,1,1,0]]
</strong><strong>Output: 2
</strong><strong>Explanation: 
</strong>Islands in gray are closed because they are completely surrounded by water (group of 1s).
</code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2019/10/31/sample\_4\_1610.png)

<pre><code><strong>Input: grid = [[0,0,1,0,0],[0,1,0,1,0],[0,1,1,1,0]]
</strong><strong>Output: 1
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: grid = [[1,1,1,1,1,1,1],
</strong>               [1,0,0,0,0,0,1],
               [1,0,1,1,1,0,1],
               [1,0,1,0,1,0,1],
               [1,0,1,1,1,0,1],
               [1,0,0,0,0,0,1],
               [1,1,1,1,1,1,1]]
<strong>Output: 2
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= grid.length, grid[0].length <= 100`
* `0 <= grid[i][j] <=1`

## Solution

#### queue

[https://www.youtube.com/watch?v=uwzCdK9M1PY](https://www.youtube.com/watch?v=uwzCdK9M1PY)

```python
class Solution:
    def closedIsland(self, grid: List[List[int]]) -> int:

        queue = []
        ans = 0
        m = len(grid)
        n = len(grid[0])
        directory = ((-1,0),(1,0),(0,-1),(0,1))
        
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 0:
                    queue.append((i,j))
                    grid[i][j] = 1
                    is_closed = True

                    while queue:
                        cur_i,cur_j = queue.pop()

                        if cur_i in (0,m-1) or cur_j in (0,n-1):
                            is_closed = False

                        for d in directory:
                            new_i = cur_i + d[0]
                            new_j = cur_j + d[1]

                            if 0<= new_i <= m-1 and 0<= new_j <= n-1 and grid[new_i][new_j] == 0:
                                queue.append((new_i,new_j))
                                
                                grid[new_i][new_j] = 1

                    if is_closed:
                        ans+=1
                
        return ans
python
```
