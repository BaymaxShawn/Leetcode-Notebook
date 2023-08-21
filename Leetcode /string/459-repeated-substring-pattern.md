---
description: Aug 20 ,2023 daily
---

# 😆 459 - Repeated Substring Pattern

Given a string `s`, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "abab"
</strong><strong>Output: true
</strong><strong>Explanation: It is the substring "ab" twice.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "aba"
</strong><strong>Output: false
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: s = "abcabcabcabc"
</strong><strong>Output: true
</strong><strong>Explanation: It is the substring "abc" four times or the substring "abcabc" twice.
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= s.length <= 104`
* `s` consists of lowercase English letters.

## Solution

```python
class Solution:
    def repeatedSubstringPattern(self, s: str) -> bool:

        for i in range(1,len(s)//2+1):
            if s[:i] * (len(s)//i) == s:
                return True
        
        return False
```
