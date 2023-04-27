---
description: medium
---

# 😝 235 - Lowest Common Ancestor of a Binary Search Tree

Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest\_common\_ancestor): “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow **a node to be a descendant of itself**).”

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2018/12/14/binarysearchtree\_improved.png)

<pre><code><strong>Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
</strong><strong>Output: 6
</strong><strong>Explanation: The LCA of nodes 2 and 8 is 6.
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2018/12/14/binarysearchtree\_improved.png)

<pre><code><strong>Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
</strong><strong>Output: 2
</strong><strong>Explanation: The LCA of nodes 2 and 4 is 2, since a node can be a descendant of itself according to the LCA definition.
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: root = [2,1], p = 2, q = 1
</strong><strong>Output: 2
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[2, 105]`.
* `-109 <= Node.val <= 109`
* All `Node.val` are **unique**.
* `p != q`
* `p` and `q` will exist in the BST.

## Solution

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':

        if q.val < root.val and p.val < root.val:
            return self.lowestCommonAncestor(root.left,p,q)
        elif root.val < p.val and root.val < q.val:
            return self.lowestCommonAncestor(root.right,p,q)
        else:
            return root
        
```
