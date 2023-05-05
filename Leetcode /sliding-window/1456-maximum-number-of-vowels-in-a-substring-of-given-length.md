---
description: medium 05/05/2023 daily question
---

# ❤ 1456 - Maximum Number of Vowels in a Substring of Given Length

Given a string `s` and an integer `k`, return _the maximum number of vowel letters in any substring of_ `s` _with length_ `k`.

**Vowel letters** in English are `'a'`, `'e'`, `'i'`, `'o'`, and `'u'`.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "abciiidef", k = 3
</strong><strong>Output: 3
</strong><strong>Explanation: The substring "iii" contains 3 vowel letters.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "aeiou", k = 2
</strong><strong>Output: 2
</strong><strong>Explanation: Any substring of length 2 contains 2 vowels.
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: s = "leetcode", k = 3
</strong><strong>Output: 2
</strong><strong>Explanation: "lee", "eet" and "ode" contain 2 vowels.
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= s.length <= 105`
* `s` consists of lowercase English letters.
* `1 <= k <= s.length`

## Solution

```python
class Solution:
    def maxVowels(self, s: str, k: int) -> int:

        max_vowel,count  = 0 ,0
        vowel = ['a','e','i','o','u']

        for i in range(len(s)):
            if s[i] in vowel:
                count += 1
            if i >= k and s[i-k] in vowel:
                count -= 1
            max_vowel = max(count,max_vowel)
        
        return max_vowel
        

```
