# 🦲 509 - Fibonacci Number

The Fibonacci numbers, commonly denoted `F(n)` form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from `0` and `1`. That is,

```
F(0) = 0, F(1) = 1
F(n) = F(n - 1) + F(n - 2), for n > 1.
```

Given `n`, calculate `F(n)`.

&#x20;

**Example 1:**

<pre><code><strong>Input: n = 2
</strong><strong>Output: 1
</strong><strong>Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: n = 3
</strong><strong>Output: 2
</strong><strong>Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: n = 4
</strong><strong>Output: 3
</strong><strong>Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3.
</strong></code></pre>

&#x20;

**Constraints:**

* `0 <= n <= 30`

## Solution

```python
class Solution:
    def fib(self, n: int) -> int:
        if n > 1:
            return self.fib(n-1)+self.fib(n-2)
        else:
            return n
```
