# 😌 144 - Binary Tree Preorder Traversal

Given the `root` of a binary tree, return _the preorder traversal of its nodes' values_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/09/15/inorder\_1.jpg)

<pre><code><strong>Input: root = [1,null,2,3]
</strong><strong>Output: [1,2,3]
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

* The number of nodes in the tree is in the range `[0, 100]`.
* `-100 <= Node.val <= 100`

&#x20;

**Follow up:** Recursive solution is trivial, could you do it iteratively?

## Solution

在二叉树遍历中，常见的遍历方式有三种，分别是先序遍历（Preorder Traversal）、中序遍历（Inorder Traversal）和后序遍历（Postorder Traversal）。

以下是这三种遍历方式的具体描述：

1. 先序遍历（Preorder Traversal）：先访问根节点，然后递归地遍历左子树和右子树。

示例二叉树：

```markdown
markdownCopy code        1
       / \
      2   3
     / \
    4   5
```

先序遍历顺序：1, 2, 4, 5, 3

2. 中序遍历（Inorder Traversal）：先递归地遍历左子树，然后访问根节点，最后递归地遍历右子树。

示例二叉树：

```markdown
markdownCopy code        1
       / \
      2   3
     / \
    4   5
```

中序遍历顺序：4, 2, 5, 1, 3

3. 后序遍历（Postorder Traversal）：先递归地遍历左子树和右子树，最后访问根节点。

示例二叉树：

```markdown
markdownCopy code        1
       / \
      2   3
     / \
    4   5
```

后序遍历顺序：4, 5, 2, 3, 1

以上三种遍历方式都是基于递归实现的，它们在二叉树算法中都有着广泛的应用。其中，中序遍历可以帮助我们实现二叉搜索树中序遍历得到升序序列的功能；后序遍历可以帮助我们实现二叉树的后缀表达式的计算功能。

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:

        ans = []

        def dfs(node):
            nonlocal ans
            if not node:
                return 

            ans.append(node.val)
            dfs(node.left)
            dfs(node.right)
            
        dfs(root)
        return ans
```
