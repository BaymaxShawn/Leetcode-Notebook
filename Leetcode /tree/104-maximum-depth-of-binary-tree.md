---
description: easy
---

# 🥲 104 - Maximum Depth of Binary Tree

Given the `root` of a binary tree, return _its maximum depth_.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg)

<pre><code><strong>Input: root = [3,9,20,null,null,15,7]
</strong><strong>Output: 3
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: root = [1,null,2]
</strong><strong>Output: 2
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[0, 104]`.
* `-100 <= Node.val <= 100`

## Solution

#### queue

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:

        queue = [(root,1)]
        res = 0

        while queue:
            node,level = queue.pop()

            if node:
                res = max(level,res )
                queue.append((node.left,level +1))
                queue.append((node.right, level +1))
                
        return res
```

#### dfs

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def maxDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """   

        if root is None:
            return 0 

        else:
            return max(self.maxDepth(root.left),self.maxDepth(root.right))+1
```
