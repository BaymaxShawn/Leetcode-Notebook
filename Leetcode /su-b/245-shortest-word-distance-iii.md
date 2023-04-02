---
description: medium
---

# 😁 245-Shortest Word Distance III

Given an array of strings `wordsDict` and two strings that already exist in the array `word1` and `word2`, return _the shortest distance between the occurrence of these two words in the list_.

**Note** that `word1` and `word2` may be the same. It is guaranteed that they represent **two individual words** in the list.

&#x20;

**Example 1:**

<pre><code><strong>Input: wordsDict = ["practice", "makes", "perfect", "coding", "makes"], word1 = "makes", word2 = "coding"
</strong><strong>Output: 1
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: wordsDict = ["practice", "makes", "perfect", "coding", "makes"], word1 = "makes", word2 = "makes"
</strong><strong>Output: 3
</strong></code></pre>

## Solution

```python
class Solution:
    def shortestWordDistance(self, wordsDict: List[str], word1: str, word2: str) -> int:
        
        l,r = -1,-1
        distance = inf
        for i in range(len(wordsDict)):
            if wordsDict[i] == word1:
                l = i
                if r!= -1:
                    distance = min(distance,l-r)
            if wordsDict[i] == word2:
                r = i
                if r!= l and l != -1:
                    distance = min(distance,r-l)

        return distanceython
```
