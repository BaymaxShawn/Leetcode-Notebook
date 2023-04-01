---
description: Hard
---

# 😜 1402 - Reducing Dishes

A chef has collected data on the `satisfaction` level of his `n` dishes. Chef can cook any dish in 1 unit of time.

**Like-time coefficient** of a dish is defined as the time taken to cook that dish including previous dishes multiplied by its satisfaction level i.e. `time[i] * satisfaction[i]`.

Return _the maximum sum of **like-time coefficient** that the chef can obtain after dishes preparation_.

Dishes can be prepared in **any** order and the chef can discard some dishes to get this maximum value.

&#x20;

**Example 1:**

<pre><code><strong>Input: satisfaction = [-1,-8,0,5,-9]
</strong><strong>Output: 14
</strong><strong>Explanation: After Removing the second and last dish, the maximum total like-time coefficient will be equal to (-1*1 + 0*2 + 5*3 = 14).
</strong>Each dish is prepared in one unit of time.
</code></pre>

**Example 2:**

<pre><code><strong>Input: satisfaction = [4,3,2]
</strong><strong>Output: 20
</strong><strong>Explanation: Dishes can be prepared in any order, (2*1 + 3*2 + 4*3 = 20)
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: satisfaction = [-1,-4,-5]
</strong><strong>Output: 0
</strong><strong>Explanation: People do not like the dishes. No dish is prepared.
</strong></code></pre>

## Solution

```python
class Solution:
    def maxSatisfaction(self, satisfaction: List[int]) -> int:
        A = satisfaction
        res = total = 0
        A.sort()
        while A and A[-1] + total > 0:
            total += A.pop()
            res += total
            print(total,res)
        return res
```
