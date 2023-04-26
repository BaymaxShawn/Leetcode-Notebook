---
description: easy
---

# 🤪 226 - Invert Binary Tree

Given the `root` of a binary tree, invert the tree, and return _its root_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/03/14/invert1-tree.jpg)

<pre><code><strong>Input: root = [4,2,7,1,3,6,9]
</strong><strong>Output: [4,7,2,9,6,3,1]
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/03/14/invert2-tree.jpg)

<pre><code><strong>Input: root = [2,1,3]
</strong><strong>Output: [2,3,1]
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: root = []
</strong><strong>Output: []
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[0, 100]`.
* `-100 <= Node.val <= 100`

## Solution

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:


        if root:
            root.left,root.right = self.invertTree(root.right),self.invertTree(root.left)
            
        
        return root
```

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:

        stack = [root]
        while stack:
            node = stack.pop()
            if node:
                node.left, node.right = node.right, node.left
                stack += node.left,node.right
            
        return root
```
