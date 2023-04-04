---
description: medium
---

# 😝 2405 - Optimal Partition of String

Given a string `s`, partition the string into one or more **substrings** such that the characters in each substring are **unique**. That is, no letter appears in a single substring more than **once**.

Return _the **minimum** number of substrings in such a partition._

Note that each character should belong to exactly one substring in a partition.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "abacaba"
</strong><strong>Output: 4
</strong><strong>Explanation:
</strong>Two possible partitions are ("a","ba","cab","a") and ("ab","a","ca","ba").
It can be shown that 4 is the minimum number of substrings needed.
</code></pre>

**Example 2:**

<pre><code><strong>Input: s = "ssssss"
</strong><strong>Output: 6
</strong><strong>Explanation:
</strong>The only valid partition is ("s","s","s","s","s","s").
</code></pre>

## Solution

```python
class Solution:
    def partitionString(self, s: str) -> int:

        temp = [0]* 26
        res = 1

        for i in s:
            i = ord(i)- ord('a')
            if temp[i] == res:
                res += 1
            temp[i] = res 
        
        return res 

```

```python
class Solution:
    def partitionString(self, s: str) -> int:

        temp = [-1]* 26
        count = 1
        start = 0

        for i in range(len(s)):
            if temp[ord(s[i])- ord('a')] >= start:
                count += 1
                start = i
            temp[ord(s[i])- ord('a')] = i
        
        return count
```
