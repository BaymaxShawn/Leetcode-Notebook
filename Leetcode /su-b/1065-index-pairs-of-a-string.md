---
description: easy
---

# 🤩 1065 - Index Pairs of a String

Given a string `text` and an array of strings `words`, return _an array of all index pairs_ `[i, j]` _so that the substring_ `text[i...j]` _is in `words`_.

Return the pairs `[i, j]` in sorted order (i.e., sort them by their first coordinate, and in case of ties sort them by their second coordinate).

&#x20;

**Example 1:**

<pre><code><strong>Input: text = "thestoryofleetcodeandme", words = ["story","fleet","leetcode"]
</strong><strong>Output: [[3,7],[9,13],[10,17]]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: text = "ababa", words = ["aba","ab"]
</strong><strong>Output: [[0,1],[0,2],[2,3],[2,4]]
</strong><strong>Explanation: Notice that matches can overlap, see "aba" is found in [0,2] and [2,4].
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= text.length <= 100`
* `1 <= words.length <= 20`
* `1 <= words[i].length <= 50`
* `text` and `words[i]` consist of lowercase English letters.
* All the strings of `words` are **unique**.

## Solution

```python
class Solution:
    def indexPairs(self, text: str, words: List[str]) -> List[List[int]]:

        res =[]

        for i in range(len(text)):
            for j in range(i,len(text)):
                if text[i:j+1] in words:
                    res.append([i,j])
                       
        return res
```
