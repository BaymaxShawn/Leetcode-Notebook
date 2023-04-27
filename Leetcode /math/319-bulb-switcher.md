---
description: medium 2023/04/27 daily question
---

# 🤏 319 - Bulb Switcher

There are `n` bulbs that are initially off. You first turn on all the bulbs, then you turn off every second bulb.

On the third round, you toggle every third bulb (turning on if it's off or turning off if it's on). For the `ith` round, you toggle every `i` bulb. For the `nth` round, you only toggle the last bulb.

Return _the number of bulbs that are on after `n` rounds_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/05/bulb.jpg)

<pre><code><strong>Input: n = 3
</strong><strong>Output: 1
</strong><strong>Explanation: At first, the three bulbs are [off, off, off].
</strong>After the first round, the three bulbs are [on, on, on].
After the second round, the three bulbs are [on, off, on].
After the third round, the three bulbs are [on, off, off]. 
So you should return 1 because there is only one bulb is on.
</code></pre>

**Example 2:**

<pre><code><strong>Input: n = 0
</strong><strong>Output: 0
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: n = 1
</strong><strong>Output: 1
</strong></code></pre>

&#x20;

**Constraints:**

* `0 <= n <= 109`

## Solution

```python
class Solution:
    def bulbSwitch(self, n: int) -> int:

        return int(sqrt(n))
```

```php
def bulbSwitch(self, n: int) -> int:
        return int(n**(1/2))
```

There is a pattern for it\
for 1th bulb : 1\
2nd : 1 0\
3rd : 1 0 0\
4th : 1 0 0 1\
5th : 1 0 0 1 0\
6th : 1 0 0 1 0 0\
7th : 1 0 0 1 0 0 0\
8th : 1 0 0 1 0 0 0 0\
9th : 1 0 0 1 0 0 0 0 1

Meaning the **I-th bulb that is on** only on when its on **I\*\*2 turn**, for example if you want 2 bulb on then you will have to go to 4th round, 3 bulb on -> 9th round.\
so for (n-th round) you can get at most floor(square\_root(n)) bulb.

Please star it if you like my solution and explanation :), any advice or correction would be appreciated.
