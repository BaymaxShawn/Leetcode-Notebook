# 😅 557 - Reverse Words in a String III

Given a string `s`, reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "Let's take LeetCode contest"
</strong><strong>Output: "s'teL ekat edoCteeL tsetnoc"
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "God Ding"
</strong><strong>Output: "doG gniD"
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= s.length <= 5 * 104`
* `s` contains printable **ASCII** characters.
* `s` does not contain any leading or trailing spaces.
* There is **at least one** word in `s`.
* All the words in `s` are separated by a single space.

## Solution

```python
class Solution(object):
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """

        l,r = 0,0
        temp = ""
        
        while r < len(s)-1:
            if s[r] != ' ':
                r += 1
            else:
                temp += s[l:r+1][::-1]
                r +=1
                l = r

        temp += ' '
        temp += s[l:r+2][::-1]

        return temp[1:]
```
