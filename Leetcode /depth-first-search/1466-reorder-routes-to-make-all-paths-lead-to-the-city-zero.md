---
description: Medium
---

# 🤣 1466 - Reorder Routes to Make All Paths Lead to the City Zero

There are `n` cities numbered from `0` to `n - 1` and `n - 1` roads such that there is only one way to travel between two different cities (this network form a tree). Last year, The ministry of transport decided to orient the roads in one direction because they are too narrow.

Roads are represented by `connections` where `connections[i] = [ai, bi]` represents a road from city `ai` to city `bi`.

This year, there will be a big event in the capital (city `0`), and many people want to travel to this city.

Your task consists of reorienting some roads such that each city can visit the city `0`. Return the **minimum** number of edges changed.

It's **guaranteed** that each city can reach city `0` after reorder.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/05/13/sample\_1\_1819.png)

<pre><code><strong>Input: n = 6, connections = [[0,1],[1,3],[2,3],[4,0],[4,5]]
</strong><strong>Output: 3
</strong><strong>Explanation: Change the direction of edges show in red such that each node can reach the node 0 (capital).
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/05/13/sample\_2\_1819.png)

<pre><code><strong>Input: n = 5, connections = [[1,0],[1,2],[3,2],[3,4]]
</strong><strong>Output: 2
</strong><strong>Explanation: Change the direction of edges show in red such that each node can reach the node 0 (capital).
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: n = 3, connections = [[1,0],[2,0]]
</strong><strong>Output: 0
</strong></code></pre>

&#x20;

**Constraints:**

* `2 <= n <= 5 * 104`
* `connections.length == n - 1`
* `connections[i].length == 2`
* `0 <= ai, bi <= n - 1`
* `ai != bi`

## Solution

```python
class Solution:
    def minReorder(self, n: int, connections: List[List[int]]) -> int:

        connect = {(a,b) for a,b in connections}
        graph = defaultdict(list)
        for a,b in connections:
            graph[a].append(b)
            graph[b].append(a)
  
        print(connect,graph)

        def dfs(x):
            nonlocal visit,change,graph,connect
            for n in graph[x]:
                if n in visit :
                    continue
                if (n,x) not in connect:
                    change += 1
                visit.add(n)
                dfs(n)
                

        visit = set()
        change = 0
        visit.add(0)
        dfs(0)
        return change


```
