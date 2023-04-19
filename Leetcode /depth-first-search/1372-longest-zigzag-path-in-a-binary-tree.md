---
description: medium 04/19/2023 daily question
---

# 🤣 1372 - Longest ZigZag Path in a Binary Tree

You are given the `root` of a binary tree.

A ZigZag path for a binary tree is defined as follow:

* Choose **any** node in the binary tree and a direction (right or left).
* If the current direction is right, move to the right child of the current node; otherwise, move to the left child.
* Change the direction from right to left or from left to right.
* Repeat the second and third steps until you can't move in the tree.

Zigzag length is defined as the number of nodes visited - 1. (A single node has a length of 0).

Return _the longest **ZigZag** path contained in that tree_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/01/22/sample\_1\_1702.png)

<pre><code><strong>Input: root = [1,null,1,1,1,null,null,1,1,null,1,null,null,null,1,null,1]
</strong><strong>Output: 3
</strong><strong>Explanation: Longest ZigZag path in blue nodes (right -> left -> right).
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/01/22/sample\_2\_1702.png)

<pre><code><strong>Input: root = [1,1,1,null,1,null,null,1,1,null,1]
</strong><strong>Output: 4
</strong><strong>Explanation: Longest ZigZag path in blue nodes (left -> right -> left -> right).
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: root = [1]
</strong><strong>Output: 0
</strong></code></pre>

## Solution

```python
class Solution:
    def longestZigZag(self, root: Optional[TreeNode]) -> int:

        max_len=0

        def dfs(node,goLeft,steps):
            nonlocal  max_len
            if node:
                max_len = max(max_len, steps)
                if goLeft:
                    dfs(node.left,False, steps +1)
                    dfs(node.right, True, 1)
                
                else:
                    dfs(node.left, False, 1)
                    dfs(node.right, True , steps +1)

        dfs(root,False,0)

        return max_len


        
```
