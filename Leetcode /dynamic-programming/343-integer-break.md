---
description: Medium
---

# 😂 343 - Integer Break

Given an integer `n`, break it into the sum of `k` **positive integers**, where `k >= 2`, and maximize the product of those integers.

Return _the maximum product you can get_.

&#x20;

**Example 1:**

<pre><code><strong>Input: n = 2
</strong><strong>Output: 1
</strong><strong>Explanation: 2 = 1 + 1, 1 × 1 = 1.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: n = 10
</strong><strong>Output: 36
</strong><strong>Explanation: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36.
</strong></code></pre>

&#x20;

**Constraints:**

* `2 <= n <= 58`

## Solution

#### math method

```python
class Solution:
    def integerBreak(self, n: int) -> int:

# n = 7 
# 7 -> 12(max)
# n = 8
# 8 = 2 * 3 * 3 -> 18(max)
# 8 = 2 * 4 * 2 -> 16
# n = 9
# 9 = 2 * 2 * 5  -> 20
# 9 = 2 * 3 * 4 -> 24
# 9 = 3 * 3 * 3 ->27(max)
# n = 10 
# 10 = 2*2*2*2*2 = 32
# 10 = 2*3*5 = 30
# 10 = 2*3*2*3 = 36
# 10 = 3+3+4 = 36(max)

        if n == 1:
            return 1
        elif n == 2:
            return 1
        elif n == 3:
            return 2
        else:
            k = n//3
            r = n%3
            if r ==0:
                return 3**k
            elif r == 1:
                return (3**(k-1))*4
            else:
                return 3**k *2

```

#### dp

