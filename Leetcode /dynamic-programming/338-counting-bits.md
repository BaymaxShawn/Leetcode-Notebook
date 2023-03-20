# 😅 338 - Counting Bits

Given an integer `n`, return _an array_ `ans` _of length_ `n + 1` _such that for each_ `i` __ (`0 <= i <= n`)_,_ `ans[i]` _is the **number of**_ `1`_**'s** in the binary representation of_ `i`.

**Example 1:**

<pre><code><strong>Input: n = 2
</strong><strong>Output: [0,1,1]
</strong><strong>Explanation:
</strong>0 --> 0
1 --> 1
2 --> 10
</code></pre>

**Example 2:**

<pre><code><strong>Input: n = 5
</strong><strong>Output: [0,1,1,2,1,2]
</strong><strong>Explanation:
</strong>0 --> 0
1 --> 1
2 --> 10
3 --> 11
4 --> 100
5 --> 101
</code></pre>

&#x20;

**Constraints:**

* `0 <= n <= 105`

**Follow up:**

* It is very easy to come up with a solution with a runtime of `O(n log n)`. Can you do it in linear time `O(n)` and possibly in a single pass?
* Can you do it without using any built-in function (i.e., like `__builtin_popcount` in C++)?

## Solution

#### DP  Explaination&#x20;

[https://www.youtube.com/watch?v=vYquumk4nWw](https://www.youtube.com/watch?v=vYquumk4nWw)

#### Answer&#x20;

[https://www.youtube.com/watch?v=RyBM56RIWrM](https://www.youtube.com/watch?v=RyBM56RIWrM)

```python
class Solution:
    def countBits(self, n: int) -> List[int]:

        dp = [0]*(n+1)
        offset = 1

        for i in range(1,n+1):
            if offset*2 == i:
                offset = i
            dp[i] = 1+ dp[i-offset]

        return dp
```
