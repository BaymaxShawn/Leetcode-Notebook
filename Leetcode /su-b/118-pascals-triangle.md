---
description: easy
---

# 🥳 118 - Pascal's Triangle

easyGiven an integer `numRows`, return the first numRows of **Pascal's triangle**.

In **Pascal's triangle**, each number is the sum of the two numbers directly above it as shown:

![](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

&#x20;

**Example 1:**

<pre><code><strong>Input: numRows = 5
</strong><strong>Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: numRows = 1
</strong><strong>Output: [[1]]
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= numRows <= 30`

## Solution

```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:

        res = []

        for i in range(numRows):
            res.append([])
            for j in range(i+1):
                if j in (0,i):
                    res[i].append(1)
                else:
                    res[i].append(res[i-1][j]+res[i-1][j-1])
                
        return res

```
