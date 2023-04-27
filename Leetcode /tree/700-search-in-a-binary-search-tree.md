---
description: easy
---

# 😚 700 - Search in a Binary Search Tree

You are given the `root` of a binary search tree (BST) and an integer `val`.

Find the node in the BST that the node's value equals `val` and return the subtree rooted with that node. If such a node does not exist, return `null`.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/01/12/tree1.jpg)

<pre><code><strong>Input: root = [4,2,7,1,3], val = 2
</strong><strong>Output: [2,1,3]
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/01/12/tree2.jpg)

<pre><code><strong>Input: root = [4,2,7,1,3], val = 5
</strong><strong>Output: []
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[1, 5000]`.
* `1 <= Node.val <= 107`
* `root` is a binary search tree.
* `1 <= val <= 107`

## Solution

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def searchBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:

        def dfs(node):
            if node:
                if node.val == val:
                    return node
                return dfs(node.left) or dfs(node.right)

        res = dfs(root)
        return res
```
