---
description: easy
---

# 😅 1025 - Divisor Game

easyAlice and Bob take turns playing a game, with Alice starting first.

Initially, there is a number `n` on the chalkboard. On each player's turn, that player makes a move consisting of:

* Choosing any `x` with `0 < x < n` and `n % x == 0`.
* Replacing the number `n` on the chalkboard with `n - x`.

Also, if a player cannot make a move, they lose the game.

Return `true` _if and only if Alice wins the game, assuming both players play optimally_.

&#x20;

**Example 1:**

<pre><code><strong>Input: n = 2
</strong><strong>Output: true
</strong><strong>Explanation: Alice chooses 1, and Bob has no more moves.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: n = 3
</strong><strong>Output: false
</strong><strong>Explanation: Alice chooses 1, Bob chooses 1, and Alice has no more moves.
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= n <= 1000`

## Solution

[https://www.bilibili.com/video/BV1pK411J7ph/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810](https://www.bilibili.com/video/BV1pK411J7ph/?spm\_id\_from=333.337.search-card.all.click\&vd\_source=62329035e2ecd83b592d19bbbf232810)

```python
class Solution:
    def divisorGame(self, n: int) -> bool:

# 1：F
# 2: T
# 3: F
# 4: T
# 5: F
# if n is F, n+1 is T

        return n%2==0
```
