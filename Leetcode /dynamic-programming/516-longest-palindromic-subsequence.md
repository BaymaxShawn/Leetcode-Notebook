---
description: medium  2023/04/13 daily question DP经典题 可反复练习
---

# 🙁 516 - Longest Palindromic Subsequence

Given a string `s`, find _the longest palindromic **subsequence**'s length in_ `s`.

A **subsequence** is a sequence that can be derived from another sequence by deleting some or no elements without changing the order of the remaining elements.

&#x20;

**Example 1:**

<pre><code><strong>Input: s = "bbbab"
</strong><strong>Output: 4
</strong><strong>Explanation: One possible longest palindromic subsequence is "bbbb".
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: s = "cbbd"
</strong><strong>Output: 2
</strong><strong>Explanation: One possible longest palindromic subsequence is "bb".
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= s.length <= 1000`
* `s` consists only of lowercase English letters.

## Solution

```python
class Solution:
    def longestPalindromeSubseq(self, s: str) -> int:

        n = len(s)
        dp = [[0]*n for _ in range(n)]

        for i in range(n-1,-1,-1):
            dp[i][i] = 1
            for j in range(i+1,n):
                if s[i] == s[j]:
                    dp[i][j] = dp[i+1][j-1] + 2
                else:
                    dp[i][j] = max(dp[i+1][j],dp[i][j-1])
        
        return dp[0][n-1]

```

在这个问题中，我们需要从后往前遍历字符串，是因为在使用动态规划算法求解最长回文子序列时，需要用到从前往后已经计算好的值，而这些值在计算时是按照从前往后的顺序依次计算的。

因此，为了方便使用已经计算好的值，我们从后往前遍历字符串，计算每个子问题的最优解，最终得到整个问题的最优解。这样做的好处是，在计算子问题时可以直接使用已经计算好的值，不需要再进行逆序或反转等操作。

所以循环语句为 `for i in range(n - 1, -1, -1)`，从 `n-1` 开始往前遍历，直到 `0`。

`for i in range(n - 1, -1, -1)` 中的第三个参数 `-1` 表示循环的步长，也就是每次循环的时候 `i` 的值减少的量，即每次循环后 `i` 的值都会减去 `1`。所以，循环会一直进行到 `i=-1`，但是不包括 `i=-1`，因为 Python 中的下标是从 `0` 开始的。

在这个题目中，从后往前遍历字符串是因为我们使用的是动态规划算法，需要从后往前计算子问题的最优解，并且在计算每个子问题时，需要用到已经计算好的子问题的最优解。因此，我们从后往前遍历字符串，以便在计算当前子问题时，能够使用已经计算好的子问题的最优解。
