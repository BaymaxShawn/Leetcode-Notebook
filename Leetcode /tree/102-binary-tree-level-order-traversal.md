# 🤨 102 - Binary Tree Level Order Traversal

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
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:

        queue = [(root,1)]
        res = []

        while queue:
            node, level = queue.pop(0)

            if not node:
                return res
            
            if node.left:
                queue.append((node.left, level +1))
            if node.right:
                queue.append((node.right, level +1))
            
            if level == len(res):
                res[level-1].append(node.val)
            else:
                res.append([node.val])
            
        return res
        
```

`pop(0)` 是一个 Python 中列表（List）的方法，用于移除并返回列表中索引为 0 的元素。

在这里的代码中，`queue.pop(0)` 的作用是从队列（queue）中取出最先加入队列的元素并将其从队列中移除，然后将其赋值给变量 node。

相同的方式，`pop(0)` 取出列表中的第一个元素并返回，但在这段代码中，似乎缺少一个列表变量，因此无法确定该行的含义。
