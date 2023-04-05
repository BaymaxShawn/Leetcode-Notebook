---
description: medium 2023/04/05 每日一题
---

# 😿 2439 - Minimize Maximum of Array

You are given a **0-indexed** array `nums` comprising of `n` non-negative integers.

In one operation, you must:

* Choose an integer `i` such that `1 <= i < n` and `nums[i] > 0`.
* Decrease `nums[i]` by 1.
* Increase `nums[i - 1]` by 1.

Return _the **minimum** possible value of the **maximum** integer of_ `nums` _after performing **any** number of operations_.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [3,7,1,6]
</strong><strong>Output: 5
</strong><strong>Explanation:
</strong>One set of optimal operations is as follows:
1. Choose i = 1, and nums becomes [4,6,1,6].
2. Choose i = 3, and nums becomes [4,6,2,5].
3. Choose i = 1, and nums becomes [5,5,2,5].
The maximum integer of nums is 5. It can be shown that the maximum number cannot be less than 5.
Therefore, we return 5.
</code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [10,1]
</strong><strong>Output: 10
</strong><strong>Explanation:
</strong>It is optimal to leave nums as is, and since 10 is the maximum value, we return 10.
</code></pre>

&#x20;

**Constraints:**

* `n == nums.length`
* `2 <= n <= 105`
* `0 <= nums[i] <= 109`

## Solution

首先求出所有的最小的可能性，从index0开始加到index（len（nums）），然后才能知道最小的最大值是什么

```python
class Solution:
    def minimizeArrayValue(self, nums: List[int]) -> int:

        res = 0
        pre_sum = 0

        for i in range(len(nums)):
            pre_sum += nums[i]
            res = max(res,math.ceil(pre_sum/(i+1)))

        return res
```

#### math.ceil(prefix\_sum / (i + 1)是什么？

`math.ceil(prefix_sum / (i + 1))` 是一个用于计算平均值的函数。

在这个问题中，我们需要找到一个最小的最大整数值，也就是说，我们需要将数组中的数字重新分配，使得数组中的最大整数最小，同时保证其他数字的和尽可能平均地分配到数组中的其他位置上。为了实现这个目标，我们需要计算出这个平均值，然后将大于平均值的数字逐渐减小，同时将小于平均值的数字逐渐增加，直到数组中的最大整数不再大于平均值。

具体地说，`prefix_sum / (i + 1)` 表示前 i+1 个数字的平均值，其中 `prefix_sum` 是前缀和，即前 i 个数字的和。我们使用 `math.ceil()` 向上取整来保证我们得到的平均值不会低于实际值。这个平均值也是我们将数组中的数字分配到其他位置上的目标值。

