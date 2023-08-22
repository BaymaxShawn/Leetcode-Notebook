# 😉 168 - Excel Sheet Column Title

Given an integer `columnNumber`, return _its corresponding column title as it appears in an Excel sheet_.

For example:

```
A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
...
```

&#x20;

**Example 1:**

<pre><code><strong>Input: columnNumber = 1
</strong><strong>Output: "A"
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: columnNumber = 28
</strong><strong>Output: "AB"
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: columnNumber = 701
</strong><strong>Output: "ZY"
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= columnNumber <= 231 - 1`

## Solution

```python
class Solution:
    def convertToTitle(self, columnNumber: int) -> str:

        res = ''
        while columnNumber != 0:
            res += chr((columnNumber-1) % 26 + ord("A"))
            columnNumber = (columnNumber -1)//26

        return res[::-1]







```
