# 🤓 589 - N-ary Tree Preorder Traversal

Given the `root` of an n-ary tree, return _the preorder traversal of its nodes' values_.

Nary-Tree input serialization is represented in their level order traversal. Each group of children is separated by the null value (See examples)

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png)

<pre><code><strong>Input: root = [1,null,3,2,4,null,5,6]
</strong><strong>Output: [1,3,5,6,2,4]
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2019/11/08/sample\_4\_964.png)

<pre><code><strong>Input: root = [1,null,2,3,4,5,null,null,6,7,null,8,null,9,10,null,null,11,null,12,null,13,null,null,14]
</strong><strong>Output: [1,2,3,6,7,11,14,4,8,12,5,9,13,10]
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[0, 104]`.
* `0 <= Node.val <= 104`
* The height of the n-ary tree is less than or equal to `1000`.

## Solution

```python
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children


class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        output = []
        self.dfs(root,output)
        return output

    def dfs(self,node,output):
        if not node:
            return
        output.append(node.val)
        for i in node.children:
            self.dfs(i,output)
```
