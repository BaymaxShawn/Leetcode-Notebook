---
description: easy
---

# 😚 112 - Path Sum

Given the `root` of a binary tree and an integer `targetSum`, return `true` if the tree has a **root-to-leaf** path such that adding up all the values along the path equals `targetSum`.

A **leaf** is a node with no children.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/01/18/pathsum1.jpg)

<pre><code><strong>Input: root = [5,4,8,11,null,13,4,7,2,null,null,null,1], targetSum = 22
</strong><strong>Output: true
</strong><strong>Explanation: The root-to-leaf path with the target sum is shown.
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/01/18/pathsum2.jpg)

<pre><code><strong>Input: root = [1,2,3], targetSum = 5
</strong><strong>Output: false
</strong><strong>Explanation: There two root-to-leaf paths in the tree:
</strong>(1 --> 2): The sum is 3.
(1 --> 3): The sum is 4.
There is no root-to-leaf path with sum = 5.
</code></pre>

**Example 3:**

<pre><code><strong>Input: root = [], targetSum = 0
</strong><strong>Output: false
</strong><strong>Explanation: Since the tree is empty, there are no root-to-leaf paths.
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[0, 5000]`.
* `-1000 <= Node.val <= 1000`
* `-1000 <= targetSum <= 1000`

## Solution

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def hasPathSum(self, root, targetSum):
        """
        :type root: TreeNode
        :type targetSum: int
        :rtype: bool
        """
        if not root:
            return False

        if not root.left and not root.right and root.val == targetSum:
            return True 


        return self.hasPathSum(root.left,targetSum - root.val) or self.hasPathSum(root.right,targetSum - root.val)
```
