# 😖 837 - New 21 Game

Alice plays the following game, loosely based on the card game **"21"**.

Alice starts with `0` points and draws numbers while she has less than `k` points. During each draw, she gains an integer number of points randomly from the range `[1, maxPts]`, where `maxPts` is an integer. Each draw is independent and the outcomes have equal probabilities.

Alice stops drawing numbers when she gets `k` **or more points**.

Return the probability that Alice has `n` or fewer points.

Answers within `10-5` of the actual answer are considered accepted.

&#x20;

**Example 1:**

<pre><code><strong>Input: n = 10, k = 1, maxPts = 10
</strong><strong>Output: 1.00000
</strong><strong>Explanation: Alice gets a single card, then stops.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: n = 6, k = 1, maxPts = 10
</strong><strong>Output: 0.60000
</strong><strong>Explanation: Alice gets a single card, then stops.
</strong>In 6 out of 10 possibilities, she is at or below 6 points.
</code></pre>

**Example 3:**

<pre><code><strong>Input: n = 21, k = 17, maxPts = 10
</strong><strong>Output: 0.73278
</strong></code></pre>

&#x20;

**Constraints:**

* `0 <= k <= n <= 104`
* `1 <= maxPts <= 104`

## Solution

```python
class Solution:
    def new21Game(self, n: int, k: int, maxPts: int) -> float:
        if k == 0:
            return 1.0
        
        windowSum = 0 
        for i in range(k,k+maxPts):
            windowSum += 1 if i<= n else 0
        
        dp = {}
        for i in range(k-1,-1, -1):
            dp[i] = windowSum /maxPts
            remove = 0
            if i+maxPts <= n :
                remove = dp.get(i+maxPts,1)
            windowSum += dp[i] - remove 
        
        return dp[0]

```
