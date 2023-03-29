---
description: Hard 2023/03/26 每日一题
---

# 🥺 2360 - Longest Cycle in a Graph

You are given a **directed** graph of `n` nodes numbered from `0` to `n - 1`, where each node has **at most one** outgoing edge.

The graph is represented with a given **0-indexed** array `edges` of size `n`, indicating that there is a directed edge from node `i` to node `edges[i]`. If there is no outgoing edge from node `i`, then `edges[i] == -1`.

Return _the length of the **longest** cycle in the graph_. If no cycle exists, return `-1`.

A cycle is a path that starts and ends at the **same** node.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2022/06/08/graph4drawio-5.png)

<pre><code><strong>Input: edges = [3,3,4,2,3]
</strong><strong>Output: 3
</strong><strong>Explanation: The longest cycle in the graph is the cycle: 2 -> 4 -> 3 -> 2.
</strong>The length of this cycle is 3, so 3 is returned.
</code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2022/06/07/graph4drawio-1.png)

<pre><code><strong>Input: edges = [2,-1,3,1]
</strong><strong>Output: -1
</strong><strong>Explanation: There are no cycles in this graph.
</strong></code></pre>

&#x20;

**Constraints:**

* `n == edges.length`
* `2 <= n <= 105`
* `-1 <= edges[i] < n`
* `edges[i] != i`

## Solution

[https://www.youtube.com/watch?v=FKqovrqFncs](https://www.youtube.com/watch?v=FKqovrqFncs)

