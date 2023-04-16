---
description: hard 2023/04/16 daily question
---

# 😤 1639 - Number of Ways to Form a Target String Given a Dictionary

You are given a list of strings of the **same length** `words` and a string `target`.

Your task is to form `target` using the given `words` under the following rules:

* `target` should be formed from left to right.
* To form the `ith` character (**0-indexed**) of `target`, you can choose the `kth` character of the `jth` string in `words` if `target[i] = words[j][k]`.
* Once you use the `kth` character of the `jth` string of `words`, you **can no longer** use the `xth` character of any string in `words` where `x <= k`. In other words, all characters to the left of or at index `k` become unusuable for every string.
* Repeat the process until you form the string `target`.

**Notice** that you can use **multiple characters** from the **same string** in `words` provided the conditions above are met.

Return _the number of ways to form `target` from `words`_. Since the answer may be too large, return it **modulo** `109 + 7`.

&#x20;

**Example 1:**

<pre><code><strong>Input: words = ["acca","bbbb","caca"], target = "aba"
</strong><strong>Output: 6
</strong><strong>Explanation: There are 6 ways to form target.
</strong>"aba" -> index 0 ("acca"), index 1 ("bbbb"), index 3 ("caca")
"aba" -> index 0 ("acca"), index 2 ("bbbb"), index 3 ("caca")
"aba" -> index 0 ("acca"), index 1 ("bbbb"), index 3 ("acca")
"aba" -> index 0 ("acca"), index 2 ("bbbb"), index 3 ("acca")
"aba" -> index 1 ("caca"), index 2 ("bbbb"), index 3 ("acca")
"aba" -> index 1 ("caca"), index 2 ("bbbb"), index 3 ("caca")
</code></pre>

**Example 2:**

<pre><code><strong>Input: words = ["abba","baab"], target = "bab"
</strong><strong>Output: 4
</strong><strong>Explanation: There are 4 ways to form target.
</strong>"bab" -> index 0 ("baab"), index 1 ("baab"), index 2 ("abba")
"bab" -> index 0 ("baab"), index 1 ("baab"), index 3 ("baab")
"bab" -> index 0 ("baab"), index 2 ("baab"), index 3 ("baab")
"bab" -> index 1 ("abba"), index 2 ("baab"), index 3 ("baab")
</code></pre>

&#x20;

**Constraints:**

* `1 <= words.length <= 1000`
* `1 <= words[i].length <= 1000`
* All strings in `words` have the same length.
* `1 <= target.length <= 1000`
* `words[i]` and `target` contain only lowercase English letters.

## Solution

[https://www.youtube.com/watch?v=\_GF-0T-YjW8](https://www.youtube.com/watch?v=\_GF-0T-YjW8)

```python
class Solution:
    def numWays(self, words: List[str], target: str) -> int:

        mod = 10**9 +7
        
        cnt = defaultdict(int) 
        for w in words:
            for i,c in enumerate(w):
                cnt[(i,c)] += 1
        
        dp = {} # (i,k) => numWays
        # i = index of target, k = index of word[j][k]
        def dfs(i,k):
            if i == len(target):
                return 1
            if k == len(words[0]):
                return 0
            if (i,k) in dp:
                return dp[(i,k)]
            
            c = target[i]
            dp[(i,k)] = dfs(i,k+1) # skip k position
            dp[(i,k)] += cnt[(k,c)]* dfs(i+1,k+1)

            return dp[(i,k)]%mod
        
        return dfs(0,0)
```
