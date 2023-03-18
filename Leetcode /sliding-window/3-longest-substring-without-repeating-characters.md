# 🍑 3 - Longest Substring Without Repeating Characters

Given a string `s`, find the length of the **longest**&#x20;

**substring** without repeating characters.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "abcabcbb"
</strong><strong>Output: 3
</strong><strong>Explanation: The answer is "abc", with the length of 3.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "bbbbb"
</strong><strong>Output: 1
</strong><strong>Explanation: The answer is "b", with the length of 1.
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: s = "pwwkew"
</strong><strong>Output: 3
</strong><strong>Explanation: The answer is "wke", with the length of 3.
</strong>Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
</code></pre>

&#x20;

**Constraints:**

* `0 <= s.length <= 5 * 104`
* `s` consists of English letters, digits, symbols and spaces.

## Solution

#### Let' s see some Sliding window example

```python
// Some code
def lengthOfLongestSubstring(s: str) -> int:
    n = len(s)
    if n <= 1:
        return n

    max_len = 0
    l, r = 0, 0  # 窗口的左右边界
    window = set()  # 当前窗口中的字符集合

    while r < n:
        if s[r] not in window:
            window.add(s[r])
            r += 1
            max_len = max(max_len, r - l)
        else:
            window.remove(s[l])
            l += 1

    return max_len
```

该函数接受一个字符串`s`作为输入，返回最长无重复字符的子串的长度。该代码实现了一个滑动窗口的算法，在while循环中不断移动右边界`r`，将新的字符加入当前窗口的集合中，如果出现重复的字符，则移动左边界`l`，将窗口中第一个字符移除集合。同时不断更新最长子串的长度`max_len`，直到右边界到达字符串`s`的末尾。

需要注意的是，这里的窗口是左闭右开区间\[l, r)，所以最后返回的最长子串长度是`r - l`，而不是`r - l + 1`。

#### Solution of our questions

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:

        if len(s) <= 1:
            return len(s)

        max_len = 0
        l,r = 0,0
        window = set()

        while r< len(s):
            if s[r] not in window:
                window.add(s[r])
                r += 1
            else:
                window.remove(s[l])
                l += 1
            
            max_len = max(max_len, r-l)
        
        return max_len

```

