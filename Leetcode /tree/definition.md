# Definition

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
