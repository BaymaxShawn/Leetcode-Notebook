---
description: medium
---

# 😅 2390 - Removing Stars From a String

You are given a string `s`, which contains stars `*`.

In one operation, you can:

* Choose a star in `s`.
* Remove the closest **non-star** character to its **left**, as well as remove the star itself.

Return _the string after **all** stars have been removed_.

**Note:**

* The input will be generated such that the operation is always possible.
* It can be shown that the resulting string will always be unique.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "leet**cod*e"
</strong><strong>Output: "lecoe"
</strong><strong>Explanation: Performing the removals from left to right:
</strong><strong>- The closest character to the 1st star is 't' in "leet**cod*e". s becomes "lee*cod*e".
</strong><strong>- The closest character to the 2nd star is 'e' in "lee*cod*e". s becomes "lecod*e".
</strong><strong>- The closest character to the 3rd star is 'd' in "lecod*e". s becomes "lecoe".
</strong>There are no more stars, so we return "lecoe".
</code></pre>

**Example 2:**

<pre><code><strong>Input: s = "erase*****"
</strong><strong>Output: ""
</strong><strong>Explanation: The entire string is removed, so we return an empty string.
</strong></code></pre>

## Solution

```python
class Solution:
    def removeStars(self, s: str) -> str:

        stack = []

        for i in range(len(s)):
            if s[i] != "*":
                stack.append(s[i])
            else:
                stack.pop()
                
        res = ''
        while stack:
            res += (stack.pop())
        
        return res[::-1]
```

\
