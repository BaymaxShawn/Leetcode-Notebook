---
description: Easy
---

# 😅 997 - Find the Town Judge

In a town, there are `n` people labeled from `1` to `n`. There is a rumor that one of these people is secretly the town judge.

If the town judge exists, then:

1. The town judge trusts nobody.
2. Everybody (except for the town judge) trusts the town judge.
3. There is exactly one person that satisfies properties **1** and **2**.

You are given an array `trust` where `trust[i] = [ai, bi]` representing that the person labeled `ai` trusts the person labeled `bi`. If a trust relationship does not exist in `trust` array, then such a trust relationship does not exist.

Return _the label of the town judge if the town judge exists and can be identified, or return_ `-1` _otherwise_.

&#x20;

**Example 1:**

<pre><code><strong>Input: n = 2, trust = [[1,2]]
</strong><strong>Output: 2
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: n = 3, trust = [[1,3],[2,3]]
</strong><strong>Output: 3
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: n = 3, trust = [[1,3],[2,3],[3,1]]
</strong><strong>Output: -1
</strong></code></pre>

## Solution

```python
class Solution:
    def findJudge(self, n: int, trust: List[List[int]]) -> int:

        graph = [0]*(n+1)
        for a,b in trust:
            graph[a] -= 1
            graph[b] += 1
        print(graph)
        
        for i in range(1,n+1):
            if graph[i] == n-1:
                return i
            
        return -1
```
