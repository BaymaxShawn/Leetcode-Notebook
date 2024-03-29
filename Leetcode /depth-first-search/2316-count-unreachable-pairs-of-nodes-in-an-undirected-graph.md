---
description: medium
---

# 🙃 2316 - Count Unreachable Pairs of Nodes in an Undirected Graph

You are given an integer `n`. There is an **undirected** graph with `n` nodes, numbered from `0` to `n - 1`. You are given a 2D integer array `edges` where `edges[i] = [ai, bi]` denotes that there exists an **undirected** edge connecting nodes `ai` and `bi`.

Return _the **number of pairs** of different nodes that are **unreachable** from each other_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2022/05/05/tc-3.png)

<pre><code><strong>Input: n = 3, edges = [[0,1],[0,2],[1,2]]
</strong><strong>Output: 0
</strong><strong>Explanation: There are no pairs of nodes that are unreachable from each other. Therefore, we return 0.
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2022/05/05/tc-2.png)

<pre><code><strong>Input: n = 7, edges = [[0,2],[0,5],[2,4],[1,6],[5,4]]
</strong><strong>Output: 14
</strong><strong>Explanation: There are 14 pairs of nodes that are unreachable from each other:
</strong>[[0,1],[0,3],[0,6],[1,2],[1,3],[1,4],[1,5],[2,3],[2,6],[3,4],[3,5],[3,6],[4,6],[5,6]].
Therefore, we return 14.
</code></pre>

\
Solution
--------

[https://www.bilibili.com/video/BV19L411D7fs/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810](https://www.bilibili.com/video/BV19L411D7fs/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810)

```python
class Solution:
    def countPairs(self, n: int, edges: List[List[int]]) -> int:

        graph =  defaultdict(list)
        for a,b in edges:
            graph[a].append(b)
            graph[b].append(a)
        
        visited = set()
        res = 0 
        rem = n

        for i in range(n):
            if i in visited :
                continue
            visited.add(i)
            s = [i]
            tem = 1
            while s:
                cur = s.pop()
                for x in graph[cur]:
                    if x not in visited:
                        s.append(x)
                        visited.add(x)
                        tem += 1
            rem -= tem 
            res += rem * tem
            #以上就是为了分类，看哪个和哪个没关系，大概分出三个团
        
        return res
```

\
