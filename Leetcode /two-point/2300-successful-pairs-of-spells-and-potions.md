---
description: Medium
---

# 😝 2300 - Successful Pairs of Spells and Potions

You are given two positive integer arrays `spells` and `potions`, of length `n` and `m` respectively, where `spells[i]` represents the strength of the `ith` spell and `potions[j]` represents the strength of the `jth` potion.

You are also given an integer `success`. A spell and potion pair is considered **successful** if the **product** of their strengths is **at least** `success`.

Return _an integer array_ `pairs` _of length_ `n` _where_ `pairs[i]` _is the number of **potions** that will form a successful pair with the_ `ith` _spell._

&#x20;

**Example 1:**

<pre><code><strong>Input: spells = [5,1,3], potions = [1,2,3,4,5], success = 7
</strong><strong>Output: [4,0,3]
</strong><strong>Explanation:
</strong><strong>- 0th spell: 5 * [1,2,3,4,5] = [5,10,15,20,25]. 4 pairs are successful.
</strong>- 1st spell: 1 * [1,2,3,4,5] = [1,2,3,4,5]. 0 pairs are successful.
<strong>- 2nd spell: 3 * [1,2,3,4,5] = [3,6,9,12,15]. 3 pairs are successful.
</strong>Thus, [4,0,3] is returned.
</code></pre>

**Example 2:**

<pre><code><strong>Input: spells = [3,1,2], potions = [8,5,8], success = 16
</strong><strong>Output: [2,0,2]
</strong><strong>Explanation:
</strong><strong>- 0th spell: 3 * [8,5,8] = [24,15,24]. 2 pairs are successful.
</strong>- 1st spell: 1 * [8,5,8] = [8,5,8]. 0 pairs are successful. 
<strong>- 2nd spell: 2 * [8,5,8] = [16,10,16]. 2 pairs are successful. 
</strong>Thus, [2,0,2] is returned.
</code></pre>

## Solution

```python
class Solution:
    def successfulPairs(self, spells: List[int], potions: List[int], success: int) -> List[int]:
        
        res = []
        potions.sort()
        for i in range(len(spells)):
            if success%spells[i] == 0:
                minvalue = success//spells[i]
            else:
                minvalue = success//spells[i] +1

            count = bisect.bisect_left(potions,minvalue)
            res.append(len(potions)-count)
        
        return res
```
