---
description: Hard
---

# 4 - Median of Two Sorted Arrays

Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return **the median** of the two sorted arrays.

The overall run time complexity should be `O(log (m+n))`.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums1 = [1,3], nums2 = [2]
</strong><strong>Output: 2.00000
</strong><strong>Explanation: merged array = [1,2,3] and median is 2.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums1 = [1,2], nums2 = [3,4]
</strong><strong>Output: 2.50000
</strong><strong>Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
</strong></code></pre>

&#x20;

**Constraints:**

* `nums1.length == m`
* `nums2.length == n`
* `0 <= m <= 1000`
* `0 <= n <= 1000`
* `1 <= m + n <= 2000`
* `-106 <= nums1[i], nums2[i] <= 106`

## Solution

```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
       
        res = nums1 +nums2
        res.sort()

        if len(res)%2 ==1:
            return res[len(res)//2]
        else:
            return (res[len(res)//2]+res[len(res)//2-1])/2
```
