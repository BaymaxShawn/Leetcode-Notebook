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
