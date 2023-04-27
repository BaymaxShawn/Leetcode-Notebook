---
description: easy
---

# 🥳 653 - Two Sum IV - Input is a BST

Given the `root` of a binary search tree and an integer `k`, return `true` _if there exist two elements in the BST such that their sum is equal to_ `k`, _or_ `false` _otherwise_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/09/21/sum\_tree\_1.jpg)

<pre><code><strong>Input: root = [5,3,6,2,4,null,7], k = 9
</strong><strong>Output: true
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/09/21/sum\_tree\_2.jpg)

<pre><code><strong>Input: root = [5,3,6,2,4,null,7], k = 28
</strong><strong>Output: false
</strong></code></pre>

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[1, 104]`.
* `-104 <= Node.val <= 104`
* `root` is guaranteed to be a **valid** binary search tree.
* `-105 <= k <= 105`

## Solution

```python
class Solution:
    def findTarget(self, root: Optional[TreeNode], k: int) -> bool:

        def inorder(node):
            if not node:
                return []
            return inorder(node.left) + [node.val] + inorder(node.right)
        
        num = inorder(root)
        
        l, r = 0,len(num)-1
        while l<r:
            if num[l] + num[r] == k:
                return True
            elif num[l] + num[r] > k:
                r -= 1
            else:
                l += 1

        return False
```
