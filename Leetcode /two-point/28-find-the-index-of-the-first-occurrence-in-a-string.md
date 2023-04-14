# 😁 28 - Find the Index of the First Occurrence in a String

Given two strings `needle` and `haystack`, return the index of the first occurrence of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.

&#x20;

**Example 1:**

<pre><code><strong>Input: haystack = "sadbutsad", needle = "sad"
</strong><strong>Output: 0
</strong><strong>Explanation: "sad" occurs at index 0 and 6.
</strong>The first occurrence is at index 0, so we return 0.
</code></pre>

**Example 2:**

<pre><code><strong>Input: haystack = "leetcode", needle = "leeto"
</strong><strong>Output: -1
</strong><strong>Explanation: "leeto" did not occur in "leetcode", so we return -1.
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= haystack.length, needle.length <= 104`
* `haystack` and `needle` consist of only lowercase English characters.

## Solution

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:

        for i in range(len(haystack)-len(needle) +1):
            if haystack[i:i+len(needle)] == needle:
                return i
            
        return -1
                
```

#### Two pointer

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:

        l1,l2,t1,t2 = len(haystack),len(needle),0,0

        while t1<l1:
            if t2 == l2:
                return t1 - t2
            if haystack[t1] == needle[t2]:
                t2 += 1
            else:
                t1 = t1-t2
                t2 = 0
            t1 += 1
        
        if t2 == l2 :
            return l1-l2
        
        return -1
```
