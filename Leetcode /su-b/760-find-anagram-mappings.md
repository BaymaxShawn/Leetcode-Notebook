---
description: easy
---

# 😂 760 - Find Anagram Mappings

You are given two integer arrays `nums1` and `nums2` where `nums2` is **an anagram** of `nums1`. Both arrays may contain duplicates.

Return _an index mapping array_ `mapping` _from_ `nums1` _to_ `nums2` _where_ `mapping[i] = j` _means the_ `ith` _element in_ `nums1` _appears in_ `nums2` _at index_ `j`. If there are multiple answers, return **any of them**.

An array `a` is **an anagram** of an array `b` means `b` is made by randomizing the order of the elements in `a`.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums1 = [12,28,46,32,50], nums2 = [50,12,32,46,28]
</strong><strong>Output: [1,4,3,2,0]
</strong><strong>Explanation: As mapping[0] = 1 because the 0th element of nums1 appears at nums2[1], and mapping[1] = 4 because the 1st element of nums1 appears at nums2[4], and so on.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums1 = [84,46], nums2 = [84,46]
</strong><strong>Output: [0,1]
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= nums1.length <= 100`
* `nums2.length == nums1.length`
* `0 <= nums1[i], nums2[i] <= 105`
* `nums2` is an anagram of `nums1`.

## Solution

#### brute force

```python
class Solution:
    def anagramMappings(self, nums1: List[int], nums2: List[int]) -> List[int]:

        res = [0]*len(nums2)
        
        for i in range(len(nums1)):
            for j in range(len(nums2)):
                if nums1[i] == nums2[j]:
                    res[i] = j

        return res
                
```

```python
class Solution:
    def anagramMappings(self, nums1: List[int], nums2: List[int]) -> List[int]:

        res = []
        
        for i in range(len(nums1)):
            res.append(nums2.index(nums1[i]))

        return res
                
```
