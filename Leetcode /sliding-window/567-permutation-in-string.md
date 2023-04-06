---
description: medium
---

# 🗣 567 - Permutation in String

Given two strings `s1` and `s2`, return `true` _if_ `s2` _contains a permutation of_ `s1`_, or_ `false` _otherwise_.

In other words, return `true` if one of `s1`'s permutations is the substring of `s2`.

&#x20;

**Example 1:**

<pre><code><strong>Input: s1 = "ab", s2 = "eidbaooo"
</strong><strong>Output: true
</strong><strong>Explanation: s2 contains one permutation of s1 ("ba").
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s1 = "ab", s2 = "eidboaoo"
</strong><strong>Output: false
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= s1.length, s2.length <= 104`
* `s1` and `s2` consist of lowercase English letters.

## Solution

```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:

        if len(s1)>len(s2):
            return False
        
        n = len(s1)
        window = Counter(s1)
        match = 0

        for i in range(len(s2)):
            if s2[i] in window:
                window[s2[i]] -= 1
                if window[s2[i]] == 0:
                    match += 1
            
            if i>=n and s2[i-n] in window:
                if window[s2[i-n]] == 0:
                    match -= 1
                window[s2[i-n]] += 1
                
            if match == len(window):
                return True
            
        return False
```
