---
description: 06/07/2023 daily
---

# 🤓 1318 - Minimum Flips to Make a OR b Equal to c

Given 3 positives numbers `a`, `b` and `c`. Return the minimum flips required in some bits of `a` and `b` to make ( `a` OR `b` == `c` ). (bitwise OR operation).\
Flip operation consists of change **any** single bit 1 to 0 or change the bit 0 to 1 in their binary representation.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/01/06/sample\_3\_1676.png)

<pre><code><strong>Input: a = 2, b = 6, c = 5
</strong><strong>Output: 3
</strong><strong>Explanation: After flips a = 1 , b = 4 , c = 5 such that (a OR b == c)
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: a = 4, b = 2, c = 7
</strong><strong>Output: 1
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: a = 1, b = 2, c = 3
</strong><strong>Output: 0
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= a <= 10^9`
* `1 <= b <= 10^9`
* `1 <= c <= 10^9`

## Solution

[https://www.bilibili.com/video/BV1N8411Z7EM/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810](https://www.bilibili.com/video/BV1N8411Z7EM/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810)

```python
class Solution:
    def minFlips(self, a: int, b: int, c: int) -> int:
        answer = 0
        while a>0 or b>0 or c>0:
            if (c&1) == 1:
                if (a&1) or (b&1):
                    answer+= 0
                else:
                    answer+= 1
            else:
                answer += (a&1)+(b&1)
            
            a >>= 1
            b >>= 1
            c >>= 1
        return answer
```
