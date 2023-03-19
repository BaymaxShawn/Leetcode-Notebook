---
description: medium
---

# 😅 1855 - Maximum Distance Between a Pair of Values

You are given two **non-increasing 0-indexed** integer arrays `nums1`​​​​​​ and `nums2`​​​​​​.

A pair of indices `(i, j)`, where `0 <= i < nums1.length` and `0 <= j < nums2.length`, is **valid** if both `i <= j` and `nums1[i] <= nums2[j]`. The **distance** of the pair is `j - i`​​​​.

Return _the **maximum distance** of any **valid** pair_ `(i, j)`_. If there are no valid pairs, return_ `0`.

An array `arr` is **non-increasing** if `arr[i-1] >= arr[i]` for every `1 <= i < arr.length`.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums1 = [55,30,5,4,2], nums2 = [100,20,10,10,5]
</strong><strong>Output: 2
</strong><strong>Explanation: The valid pairs are (0,0), (2,2), (2,3), (2,4), (3,3), (3,4), and (4,4).
</strong>The maximum distance is 2 with pair (2,4).
</code></pre>

**Example 2:**

<pre><code><strong>Input: nums1 = [2,2,2], nums2 = [10,10,1]
</strong><strong>Output: 1
</strong><strong>Explanation: The valid pairs are (0,0), (0,1), and (1,1).
</strong>The maximum distance is 1 with pair (0,1).
</code></pre>

**Example 3:**

<pre><code><strong>Input: nums1 = [30,29,19,5], nums2 = [25,25,25,25,25]
</strong><strong>Output: 2
</strong><strong>Explanation: The valid pairs are (2,2), (2,3), (2,4), (3,3), and (3,4).
</strong>The maximum distance is 2 with pair (2,4).
</code></pre>



## Solution

#### Python

```python
class Solution:
    def maxDistance(self, nums1: List[int], nums2: List[int]) -> int:

        if not nums1 or not nums2:
            return 0
        
        res = a = 0
        for i, value in enumerate(nums2):
            while a < len(nums1) and nums1[a] > value:
                a +=1
            if a == len(nums1):
                break
            res = max(res,i-a)
        
        return res
```

```python
class Solution:
    def maxDistance(self, nums1: List[int], nums2: List[int]) -> int:

        pt1 = 0
        res = 0

        for pt2,value in enumerate(nums2):
            while pt1< len(nums1) and nums1[pt1]> value:
                pt1 +=1
            if pt1 == len(nums1):
                break
            
            res = max(res,pt2-pt1)
        
        return res
        
```
