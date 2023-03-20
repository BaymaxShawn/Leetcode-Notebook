# 😅 392 - Is Subsequence

Given two strings `s` and `t`, return `true` _if_ `s` _is a **subsequence** of_ `t`_, or_ `false` _otherwise_.

A **subsequence** of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., `"ace"` is a subsequence of `"abcde"` while `"aec"` is not).

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "abc", t = "ahbgdc"
</strong><strong>Output: true
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "axc", t = "ahbgdc"
</strong><strong>Output: false
</strong></code></pre>

&#x20;

**Constraints:**

* `0 <= s.length <= 100`
* `0 <= t.length <= 104`
* `s` and `t` consist only of lowercase English letters.

## Solution

#### Two pointer

```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:

        l , r = 0,0

        while l< len(s) and r < (len(t)):
            if s[l] == t[r]:
                l += 1
            r += 1
        
        return l == len(s)
```
