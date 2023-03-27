---
description: Medium
---

# 😂 1319 - Number of Operations to Make Network Connected

There are `n` computers numbered from `0` to `n - 1` connected by ethernet cables `connections` forming a network where `connections[i] = [ai, bi]` represents a connection between computers `ai` and `bi`. Any computer can reach any other computer directly or indirectly through the network.

You are given an initial computer network `connections`. You can extract certain cables between two directly connected computers, and place them between any pair of disconnected computers to make them directly connected.

Return _the minimum number of times you need to do this in order to make all the computers connected_. If it is not possible, return `-1`.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/01/02/sample\_1\_1677.png)

<pre><code><strong>Input: n = 4, connections = [[0,1],[0,2],[1,2]]
</strong><strong>Output: 1
</strong><strong>Explanation: Remove cable between computer 1 and 2 and place between computers 1 and 3.
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/01/02/sample\_2\_1677.png)

<pre><code><strong>Input: n = 6, connections = [[0,1],[0,2],[0,3],[1,2],[1,3]]
</strong><strong>Output: 2
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: n = 6, connections = [[0,1],[0,2],[0,3],[1,2]]
</strong><strong>Output: -1
</strong><strong>Explanation: There are not enough cables.
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= n <= 105`
* `1 <= connections.length <= min(n * (n - 1) / 2, 105)`
* `connections[i].length == 2`
* `0 <= ai, bi < n`
* `ai != bi`
* There are no repeated connections.
* No two computers are connected by more than one cable.

## Solution

```python
class Solution:
    def makeConnected(self, n: int, connections: List[List[int]]) -> int:

        if len(connections)<n-1:
            return -1

        tem = defaultdict(list)
        for a,b in connections:
            tem[a].append(b)
            tem[b].append(a)

        visit = [0]*n

        def dfs(i):
            if visit[i] == 1:
                return 
            visit[i] = 1
            for x in tem[i]:
                dfs(x)
            return 
        
        count = 0
        for i in range(n):
            if visit[i] == 0:
                dfs(i)
                count+= 1

        return count-1
            
```
