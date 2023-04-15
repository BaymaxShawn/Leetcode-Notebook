---
description: easy
---

# ☀ 1 - Two Sum

easyGiven an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have _**exactly**_** one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [2,7,11,15], target = 9
</strong><strong>Output: [0,1]
</strong><strong>Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [3,2,4], target = 6
</strong><strong>Output: [1,2]
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: nums = [3,3], target = 6
</strong><strong>Output: [0,1]
</strong></code></pre>

&#x20;

**Constraints:**

* `2 <= nums.length <= 104`
* `-109 <= nums[i] <= 109`
* `-109 <= target <= 109`
* **Only one valid answer exists.**

&#x20;

**Follow-up:** Can you come up with an algorithm that is less than `O(n2)` time complexity?

## Solution

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:

        for i in range(len(nums)):
            if target-nums[i] in nums and nums.index(target-nums[i]) != i :
                return [i,nums.index(target-nums[i])]
        

```

虽然代码中没有显式地使用哈希表，但实际上在这个解法中，使用了 Python 中的内置列表数据类型，其在实现上就是使用哈希表。

具体来说，在代码中 `if target-nums[i] in nums` 这行中，Python 会通过哈希表的查找操作来判断 `target-nums[i]` 是否在 `nums` 中。Python 中的列表实际上是通过哈希表来实现的，因此这个解法使用了哈希表的实现机制。

#### HashTable

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:

        hashtable = {}

        for i in range(len(nums)):
            if nums[i] not in hashtable:
                hashtable[nums[i]] = i
            if target - nums[i] in hashtable and hashtable[target - nums[i]] != i:
                return [i,hashtable[target - nums[i]]]
            
```
