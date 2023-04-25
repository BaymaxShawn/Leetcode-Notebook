---
description: easy
---

# 😉 20 - Valid Parentheses

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "()"
</strong><strong>Output: true
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "()[]{}"
</strong><strong>Output: true
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: s = "(]"
</strong><strong>Output: false
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= s.length <= 104`
* `s` consists of parentheses only `'()[]{}'`.

## Solution&#x20;

```python
class Solution:
    def isValid(self, s: str) -> bool:

        stack = []
        mapping = {")":"(" , "}":"{" , "]":"["}

        for i in s:
            if i in mapping:
                top = stack.pop() if stack else "#"

                if top != mapping[i] :
                    return False
            else:
                stack.append(i)
            
        return not stack
```

if stack else "#"

这段代码是一个Python三元表达式，可以理解为简化版的`if-else`语句。

在这个三元表达式中，`stack`是一个栈（stack）对象。如果`stack`非空，那么三元表达式返回`stack`，否则返回`'#'`。换句话说，如果`stack`不为空，那么返回`stack`，否则返回字符串`'#'`。

这种写法通常用来简化代码，避免出现过多的`if-else`语句，使代码更加简洁易懂。在本例中，它的作用是将栈的顶部元素弹出并返回，如果栈为空则返回一个特定的占位符`'#'`

`也可以将#换成任何字符`
