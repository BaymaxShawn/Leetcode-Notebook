# 🥳 94 - Binary Tree Inorder Traversal

Given the `root` of a binary tree, return _the inorder traversal of its nodes' values_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/09/15/inorder\_1.jpg)

<pre><code><strong>Input: root = [1,null,2,3]
</strong><strong>Output: [1,3,2]
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

## HIT

对于二叉树的遍历方式，需要明确一个概念，那就是「空节点（Null）」。在二叉树中，空节点是没有左右子节点的节点，也就是在代码中用 `null` 表示的那些节点。

针对你提供的示例二叉树：

```markdown
markdownCopy code     1
      \
       2
      /
     3
```

按照中序遍历的顺序，遍历顺序是：左子树 -> 根节点 -> 右子树。因为中序遍历需要先访问左子树，但是该二叉树的根节点没有左子树，只有一个右子节点，所以需要先访问根节点1，然后再访问右子节点2。节点2有一个左子节点3，所以需要先访问左子节点3，再访问根节点2。综合起来，该二叉树的中序遍历顺序为：1 -> 3 -> 2。

因此，这个二叉树的中序遍历结果是 `[1, 3, 2]`，而不是先序遍历或后序遍历的结果。

other example：

```markdown
markdownCopy code    7
   / \
  4   9
     / \
    6  13
   / \
 10 12
```

这棵二叉树的中序遍历顺序为 4 -> 7 -> 10 -> 6 -> 12 -> 9 -> 13。

中序遍历的规则是先访问左子树，再访问当前节点，最后访问右子树。按照这个规则，中序遍历的顺序应该是从最左边的叶子节点开始，一直到最右边的叶子节点结束。在这棵二叉树中，最左边的叶子节点是节点 4，因此它是中序遍历顺序的第一个节点。接下来，访问节点 4 的父节点 7，然后访问节点 7 的左子树。节点 10 是节点 7 左子树的最左边的叶子节点，因此访问它。接着访问节点 10 的右兄弟节点 6，然后访问节点 6 的左子树，即节点 12。此时，左子树访问完毕，访问当前节点 6，然后访问节点 6 的右子树，即节点 13。回到节点 7，访问节点 7 的右子树，即节点 9。访问节点 9 的左子树，即节点 6，左子树访问完毕后，访问当前节点 9，最后访问节点 13，中序遍历顺序结束。

#### solution

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:

        ans = []

        def dfs(node):
            nonlocal ans

            if not node:
                return 
            
            dfs(node.left)
            ans.append(node.val)
            dfs(node.right)
            


        dfs(root)
        return ans
```
