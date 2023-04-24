# 😉 387 - First Unique Character in a String

Given a string `s`, _find the first non-repeating character in it and return its index_. If it does not exist, return `-1`.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "leetcode"
</strong><strong>Output: 0
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "loveleetcode"
</strong><strong>Output: 2
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: s = "aabb"
</strong><strong>Output: -1
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= s.length <= 105`
* `s` consists of only lowercase English letters.

## Solution

```python
class Solution:
    def firstUniqChar(self, s: str) -> int:

        res = {}

        for i in s:
            if i in res:
                res[i] += 1
            else:
                res[i] = 1

        for x in res:     
            if res[x] == 1 :
                return s.index(x)
            
        return -1 
```
