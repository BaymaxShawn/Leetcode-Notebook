---
description: easy
---

# 😛 101 - Symmetric Tree

Given the `root` of a binary tree, _check whether it is a mirror of itself_ (i.e., symmetric around its center).

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/02/19/symtree1.jpg)

<pre><code><strong>Input: root = [1,2,2,3,4,4,3]
</strong><strong>Output: true
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/02/19/symtree2.jpg)

<pre><code><strong>Input: root = [1,2,2,null,3,null,3]
</strong><strong>Output: false
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[1, 1000]`.
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
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:

        if not root:
            return False
        
        def dfs(l,r):
            if l is None and r is None:
                return True
            if l is None or r is None:
                return False
            

            return l.val == r.val and dfs(l.left,r.right) and dfs(l.right,r.left)
        

        l = root.left
        r = root.right
        return dfs(l,r)
```
