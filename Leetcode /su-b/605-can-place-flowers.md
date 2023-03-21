---
description: easy 2023/03/20 每日一题
---

# 😿 605 - Can Place Flowers

You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in **adjacent** plots.

Given an integer array `flowerbed` containing `0`'s and `1`'s, where `0` means empty and `1` means not empty, and an integer `n`, return _if_ `n` new flowers can be planted in the `flowerbed` without violating the no-adjacent-flowers rule.

&#x20;

**Example 1:**

<pre><code><strong>Input: flowerbed = [1,0,0,0,1], n = 1
</strong><strong>Output: true
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: flowerbed = [1,0,0,0,1], n = 2
</strong><strong>Output: false
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= flowerbed.length <= 2 * 104`
* `flowerbed[i]` is `0` or `1`.
* There are no two adjacent flowers in `flowerbed`.
* `0 <= n <= flowerbed.length`

## Solution

```python
class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:


        for i in range(len(flowerbed)):
            if flowerbed[i] == 0 and (i == 0 or flowerbed[i-1] == 0) and (i == len(flowerbed)-1 or flowerbed[i+1] == 0 ):
                flowerbed[i] = 1
                n -= 1
            
        if n > 0 :
            return False
        return True
```
