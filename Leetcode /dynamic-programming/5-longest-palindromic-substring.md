# 🙃 5 - Longest Palindromic Substring

Given a string `s`, return _the longest_&#x20;

_palindromic_ _substring_ in `s`.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "babad"
</strong><strong>Output: "bab"
</strong><strong>Explanation: "aba" is also a valid answer.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "cbbd"
</strong><strong>Output: "bb"
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= s.length <= 1000`
* `s` consist of only digits and English letters.



## Solution

[https://www.youtube.com/watch?v=2EPnqoD5bQQ](https://www.youtube.com/watch?v=2EPnqoD5bQQ)

#### Brute Force

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:

        def check_palindromic(s):
            return s == s[::-1]
        
        for length in range(len(s),0,-1):
            for start_index in range(0,len(s)+1-length):
                if check_palindromic(s[start_index:start_index+length]):
                    return s[start_index:start_index+length]
```
