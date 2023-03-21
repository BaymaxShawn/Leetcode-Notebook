# 😏 1137 - N-th Tribonacci Number

The Tribonacci sequence Tn is defined as follows:&#x20;

T0 = 0, T1 = 1, T2 = 1, and Tn+3 = Tn + Tn+1 + Tn+2 for n >= 0.

Given `n`, return the value of Tn.

&#x20;

**Example 1:**

<pre><code><strong>Input: n = 4
</strong><strong>Output: 4
</strong><strong>Explanation:
</strong>T_3 = 0 + 1 + 1 = 2
T_4 = 1 + 1 + 2 = 4
</code></pre>

**Example 2:**

<pre><code><strong>Input: n = 25
</strong><strong>Output: 1389537
</strong></code></pre>

&#x20;

**Constraints:**

* `0 <= n <= 37`
* The answer is guaranteed to fit within a 32-bit integer, ie. `answer <= 2^31 - 1`.

## Solution

```python
class Solution:
    def tribonacci(self, n: int) -> int:
        
        if n<= 1:
            return n
        elif n== 2:
            return 1
        else:
            t0 ,t1,t2 = 0,1,1
            i = 0
            while i < (n-2):
                t0,t1,t2 = t1,t2,t1+t2+t0
                i +=1
        return t2

```
