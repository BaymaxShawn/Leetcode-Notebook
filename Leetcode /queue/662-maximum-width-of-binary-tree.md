---
description: medium 2023/04/20 daily question
---

# 😂 662 - Maximum Width of Binary Tree

Given the `root` of a binary tree, return _the **maximum width** of the given tree_.

The **maximum width** of a tree is the maximum **width** among all levels.

The **width** of one level is defined as the length between the end-nodes (the leftmost and rightmost non-null nodes), where the null nodes between the end-nodes that would be present in a complete binary tree extending down to that level are also counted into the length calculation.

It is **guaranteed** that the answer will in the range of a **32-bit** signed integer.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/05/03/width1-tree.jpg)

<pre><code><strong>Input: root = [1,3,2,5,3,null,9]
</strong><strong>Output: 4
</strong><strong>Explanation: The maximum width exists in the third level with length 4 (5,3,null,9).
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2022/03/14/maximum-width-of-binary-tree-v3.jpg)

<pre><code><strong>Input: root = [1,3,2,5,null,null,9,6,null,7]
</strong><strong>Output: 7
</strong><strong>Explanation: The maximum width exists in the fourth level with length 7 (6,null,null,null,null,null,7).
</strong></code></pre>

**Example 3:**

![](https://assets.leetcode.com/uploads/2021/05/03/width3-tree.jpg)

<pre><code><strong>Input: root = [1,3,2,5]
</strong><strong>Output: 2
</strong><strong>Explanation: The maximum width exists in the second level with length 2 (3,2).
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[1, 3000]`.
* `-100 <= Node.val <= 100`

## Solution&#x20;

[https://www.youtube.com/watch?v=FPzLE2L7uHs](https://www.youtube.com/watch?v=FPzLE2L7uHs)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def widthOfBinaryTree(self, root: Optional[TreeNode]) -> int:

        res = 0 
        queue = deque([[root,1,0]]) #[node,num,level]
        preLevel,preNum = 0,1

        while queue:
   
            node,num,level = queue.popleft()
            if level > preLevel:
                preLevel = level
                preNum = num
            res = max(res, num-preNum +1)
            if node.left:          
                queue.append([node.left,num*2,level +1])
            if node.right:
                queue.append([node.right,num*2+1,level +1])
 
        return res
```
