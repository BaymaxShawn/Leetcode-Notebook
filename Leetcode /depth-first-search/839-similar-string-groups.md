---
description: hard 04/28/2023 daily question
---

# 🧐 839 - Similar String Groups

Two strings `X` and `Y` are similar if we can swap two letters (in different positions) of `X`, so that it equals `Y`. Also two strings `X` and `Y` are similar if they are equal.

For example, `"tars"` and `"rats"` are similar (swapping at positions `0` and `2`), and `"rats"` and `"arts"` are similar, but `"star"` is not similar to `"tars"`, `"rats"`, or `"arts"`.

Together, these form two connected groups by similarity: `{"tars", "rats", "arts"}` and `{"star"}`.  Notice that `"tars"` and `"arts"` are in the same group even though they are not similar.  Formally, each group is such that a word is in the group if and only if it is similar to at least one other word in the group.

We are given a list `strs` of strings where every string in `strs` is an anagram of every other string in `strs`. How many groups are there?

&#x20;

**Example 1:**

<pre><code><strong>Input: strs = ["tars","rats","arts","star"]
</strong><strong>Output: 2
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: strs = ["omv","ovm"]
</strong><strong>Output: 1
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= strs.length <= 300`
* `1 <= strs[i].length <= 300`
* `strs[i]` consists of lowercase letters only.
* All words in `strs` have the same length and are anagrams of each other.

## Solution

```python
class Solution:
    def numSimilarGroups(self, strs: List[str]) -> int:
        group = 0
        n = len(strs)
        vis= [False]*n
        for i in range(n):
            if vis[i]: continue
            group += 1
            self.dfs(i,strs,vis)
        return group
        
    def dfs(self,i,strs,vis):
        vis[i] = True
        for j in range(len(strs)):
            if vis[j]: continue
            if self.is_similar(strs[i],strs[j]):
                self.dfs(j,strs,vis)
    
    def is_similar(self,a,b):
        count = 0 
        for i in range(len(a)):
            if a[i] != b[i]:
                count +=1
        return count == 2 or count == 0 

```
