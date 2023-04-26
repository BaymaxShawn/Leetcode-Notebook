# 😙 145 - Binary Tree Postorder Traversal

Given the `root` of a binary tree, return _the postorder traversal of its nodes' values_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/08/28/pre1.jpg)

<pre><code><strong>Input: root = [1,null,2,3]
</strong><strong>Output: [3,2,1]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: root = []
</strong><strong>Output: []
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: root = [1]
</strong><strong>Output: [1]
</strong></code></pre>

&#x20;

**Constraints:**

* The number of the nodes in the tree is in the range `[0, 100]`.
* `-100 <= Node.val <= 100`

&#x20;

**Follow up:** Recursive solution is trivial, could you do it iteratively?

## Solution

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:

        ans = []

        def dfs(node):
            nonlocal ans
            if not node:
                return
            
            dfs(node.left)
            dfs(node.right)
            ans.append(node.val)
        
        dfs(root)
        return ans
```
