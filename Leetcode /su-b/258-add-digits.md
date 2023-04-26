---
description: easy 2023/04/26 daily question
---

# 😚 258 - Add Digits

Given an integer `num`, repeatedly add all its digits until the result has only one digit, and return it.

&#x20;

**Example 1:**

<pre><code><strong>Input: num = 38
</strong><strong>Output: 2
</strong><strong>Explanation: The process is
</strong>38 --> 3 + 8 --> 11
11 --> 1 + 1 --> 2 
Since 2 has only one digit, return it.
</code></pre>

**Example 2:**

<pre><code><strong>Input: num = 0
</strong><strong>Output: 0
</strong></code></pre>

&#x20;

**Constraints:**

* `0 <= num <= 231 - 1`

## Solution&#x20;

```python
class Solution:
    def addDigits(self, num: int) -> int:

        while num >= 10:
            n = list(str(num))
            num = 0
            for i in n:
                num += int(i)
        
        return num
```

```python
class Solution:
    def addDigits(self, num: int) -> int:

        if num == 0 : return 0
        if num % 9 == 0 : return 9
        else : return (num % 9)
```

\
