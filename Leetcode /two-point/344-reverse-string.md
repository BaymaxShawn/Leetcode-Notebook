# 🥲 344 - Reverse String

Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place\_algorithm) with `O(1)` extra memory.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = ["h","e","l","l","o"]
</strong><strong>Output: ["o","l","l","e","h"]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = ["H","a","n","n","a","h"]
</strong><strong>Output: ["h","a","n","n","a","H"]
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= s.length <= 105`
* `s[i]` is a [printable ascii character](https://en.wikipedia.org/wiki/ASCII#Printable\_characters).

## Solution

```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        
        for i in range(len(s)//2):
            s[i],s[-(i+1)] = s[-(i+1)],s[i]
```
