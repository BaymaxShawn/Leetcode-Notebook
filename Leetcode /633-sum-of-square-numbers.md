# 633 - Sum of Square Numbers

Given a non-negative integer `c`, decide whether there're two integers `a` and `b` such that `a2 + b2 = c`.

**Example 1:**

<pre><code><strong>Input: c = 5
</strong><strong>Output: true
</strong><strong>Explanation: 1 * 1 + 2 * 2 = 5
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: c = 3
</strong><strong>Output: false
</strong></code></pre>

## Solution:

#### Two Pointer

```python
class Solution:
    def judgeSquareSum(self, c: int) -> bool:

        l ,r = 0, int(sqrt(c))
        while l<=r:
            if l*l + r*r == c:
                return True
            elif l*l + r*r > c:
                r -= 1
            else:
                l += 1
        return False
```

&#x20;**HashSet**

```python
class Solution:
    def judgeSquareSum(self, c: int) -> bool:

        hashset = set()

        for i in range(int(sqrt(c))+1):
            hashset.add(i*i)
        
        for aset in hashset:
            bset = c - aset
            if bset in hashset:
                return True
        return False
```
