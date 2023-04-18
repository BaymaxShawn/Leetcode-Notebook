---
description: easy 2023/04/18 daily quetsion
---

# 😌 1768 - Merge Strings Alternately

You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return _the merged string._

&#x20;

**Example 1:**

<pre><code><strong>Input: word1 = "abc", word2 = "pqr"
</strong><strong>Output: "apbqcr"
</strong><strong>Explanation: The merged string will be merged as so:
</strong>word1:  a   b   c
word2:    p   q   r
merged: a p b q c r
</code></pre>

**Example 2:**

<pre><code><strong>Input: word1 = "ab", word2 = "pqrs"
</strong><strong>Output: "apbqrs"
</strong><strong>Explanation: Notice that as word2 is longer, "rs" is appended to the end.
</strong>word1:  a   b 
word2:    p   q   r   s
merged: a p b q   r   s
</code></pre>

**Example 3:**

<pre><code><strong>Input: word1 = "abcd", word2 = "pq"
</strong><strong>Output: "apbqcd"
</strong><strong>Explanation: Notice that as word1 is longer, "cd" is appended to the end.
</strong>word1:  a   b   c   d
word2:    p   q 
merged: a p b q c   d
</code></pre>

&#x20;

**Constraints:**

* `1 <= word1.length, word2.length <= 100`
* `word1` and `word2` consist of lowercase English letters.

## Solution

```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:

        res = ""
        l,r = 0,0
        while l<len(word1) and r <len(word2):
            if l == r:
                res += word1[l]
                l += 1
            else:
                res +=word2[r]
                r += 1
        
        if l != len(word1) :
            res += word1[l:]
        if r != len(word2) :
            res += word2[r:]
        
        return res

```
