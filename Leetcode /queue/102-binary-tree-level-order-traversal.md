---
description: medium
---

# 🥳 102 - Binary Tree Level Order Traversal

Given the `root` of a binary tree, return _the level order traversal of its nodes' values_. (i.e., from left to right, level by level).

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg)

<pre><code><strong>Input: root = [3,9,20,null,null,15,7]
</strong><strong>Output: [[3],[9,20],[15,7]]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: root = [1]
</strong><strong>Output: [[1]]
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: root = []
</strong><strong>Output: []
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[0, 2000]`.
* `-1000 <= Node.val <= 1000`

## Solution

```python
# Definition for a binary tree node.
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:

        queue = [(root,1)]
        res = []
        while queue:
            node,level = queue.pop(0)
            if not node:
                return res
            if node.left:
                queue.append((node.left,level+1))
            if node.right:
                queue.append((node.right,level+1))
            
            if len(res) == level:
                res[level-1].append(node.val)
            else:
                res.append([node.val])

        return res
```
