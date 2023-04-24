---
description: easy 2023/04/24 daily question
---

# 😚 1046 - Last Stone Weight

You are given an array of integers `stones` where `stones[i]` is the weight of the `ith` stone.

We are playing a game with the stones. On each turn, we choose the **heaviest two stones** and smash them together. Suppose the heaviest two stones have weights `x` and `y` with `x <= y`. The result of this smash is:

* If `x == y`, both stones are destroyed, and
* If `x != y`, the stone of weight `x` is destroyed, and the stone of weight `y` has new weight `y - x`.

At the end of the game, there is **at most one** stone left.

Return _the weight of the last remaining stone_. If there are no stones left, return `0`.

&#x20;

**Example 1:**

<pre><code><strong>Input: stones = [2,7,4,1,8,1]
</strong><strong>Output: 1
</strong><strong>Explanation: 
</strong>We combine 7 and 8 to get 1 so the array converts to [2,4,1,1,1] then,
we combine 2 and 4 to get 2 so the array converts to [2,1,1,1] then,
we combine 2 and 1 to get 1 so the array converts to [1,1,1] then,
we combine 1 and 1 to get 0 so the array converts to [1] then that's the value of the last stone.
</code></pre>

**Example 2:**

<pre><code><strong>Input: stones = [1]
</strong><strong>Output: 1
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= stones.length <= 30`
* `1 <= stones[i] <= 1000`

## Solution

```python
class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        
        first_max, second_max = 0,0

        while len(stones)> 1:
            first_max = max(stones)
            stones.remove(first_max)
            second_max = max(stones)
            if first_max == second_max:
                stones.remove(second_max)
            else:
                stones.remove(second_max)
                stones.append(first_max-second_max)
        
        if len(stones) == 0:
            return 0
        else:
            return stones[0]

```

```python
class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        
        
        while len(stones) > 1:
            stones.sort()
            first = stones.pop()
            second = stones.pop()
            if first == second :
                continue
            else:
                stones.append(first-second)
            
        if stones:
            return stones[0]
        else:
            return 0
```

```python
class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        
        stones.sort()
        while len(stones) > 1:
            first = stones.pop()
            second = stones.pop()
            if first != second :
                bisect.insort(stones,first-second)
            
        if stones:
            return stones[0]
        else:
            return 0
```
