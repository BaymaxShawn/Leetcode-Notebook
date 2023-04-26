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

在这段代码中，`invertTree` 函数的目的是翻转（invert）一棵二叉树并返回其根节点。

在函数的主体中，使用了一个栈（stack）来进行深度优先搜索遍历二叉树。在遍历的过程中，每次从栈中取出一个节点（node），然后交换它的左右子节点，接着将其左右子节点加入到栈中。这个过程一直持续到栈为空。

最后，函数返回的是原始的根节点，因为翻转后的二叉树的根节点仍然是原始的根节点。原始的根节点的左右子树的结构已经被翻转了，但根节点本身的值并没有改变。

因此，返回的是原始根节点是正确的，而且这个根节点被修改了，但是仅仅修改了它的左右子树的指向关系，并没有修改它的值。
