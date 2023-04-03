---
description: medium 2023/04/03 每日一题
---

# 😁 881 - Boats to Save People

You are given an array `people` where `people[i]` is the weight of the `ith` person, and an **infinite number of boats** where each boat can carry a maximum weight of `limit`. Each boat carries at most two people at the same time, provided the sum of the weight of those people is at most `limit`.

Return _the minimum number of boats to carry every given person_.

&#x20;

**Example 1:**

<pre><code><strong>Input: people = [1,2], limit = 3
</strong><strong>Output: 1
</strong><strong>Explanation: 1 boat (1, 2)
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: people = [3,2,2,1], limit = 3
</strong><strong>Output: 3
</strong><strong>Explanation: 3 boats (1, 2), (2) and (3)
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: people = [3,5,3,4], limit = 5
</strong><strong>Output: 4
</strong><strong>Explanation: 4 boats (3), (3), (4), (5)
</strong></code></pre>

## Solution

```python
class Solution:
    def numRescueBoats(self, people: List[int], limit: int) -> int:

        count = 0
        l,r = 0,len(people)-1
        people.sort()
        while l<=r:
            if people[l]+people[r]<=limit:
                l += 1
            r -= 1
            count += 1 
        return count
```
