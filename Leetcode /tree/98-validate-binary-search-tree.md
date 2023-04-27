# 😏 98 - Validate Binary Search Tree

Given the `root` of a binary tree, _determine if it is a valid binary search tree (BST)_.

A **valid BST** is defined as follows:

* The left subtree of a node contains only nodes with keys **less than** the node's key.
* The right subtree of a node contains only nodes with keys **greater than** the node's key.
* Both the left and right subtrees must also be binary search trees.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/12/01/tree1.jpg)

<pre><code><strong>Input: root = [2,1,3]
</strong><strong>Output: true
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/12/01/tree2.jpg)

<pre><code><strong>Input: root = [5,1,4,null,null,3,6]
</strong><strong>Output: false
</strong><strong>Explanation: The root node's value is 5 but its right child's value is 4.
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[1, 104]`.
* `-231 <= Node.val <= 231 - 1`

## Solution

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isValidBST(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        def preorder(node,l,r):
            if not node:
                return True
            if node.val <= l or node.val >= r:
                return False
            if not preorder(node.right,node.val,r):
                return False
            if not preorder(node.left,l,node.val):
                return False
            return True

        l = float('-inf')
        r =  float('inf')
        return preorder(root,l,r)
```

```python
class Solution(object):
    def isValidBST(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        def preorder(node,l=float('-inf'),r =float('inf')):
            if not node:
                return True
            if not l < node.val < r:
                return False
            return preorder(node.left,l,node.val) and preorder(node.right,node.val,r)

        return preorder(root)
```
