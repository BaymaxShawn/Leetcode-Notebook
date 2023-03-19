# 🌬 88 - Merge Sorted Array

You are given two integer arrays `nums1` and `nums2`, sorted in **non-decreasing order**, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.

**Merge** `nums1` and `nums2` into a single array sorted in **non-decreasing order**.

The final sorted array should not be returned by the function, but instead be _stored inside the array_ `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0` and should be ignored. `nums2` has a length of `n`.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
</strong><strong>Output: [1,2,2,3,5,6]
</strong><strong>Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
</strong>The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
</code></pre>

**Example 2:**

<pre><code><strong>Input: nums1 = [1], m = 1, nums2 = [], n = 0
</strong><strong>Output: [1]
</strong><strong>Explanation: The arrays we are merging are [1] and [].
</strong>The result of the merge is [1].
</code></pre>

**Example 3:**

<pre><code><strong>Input: nums1 = [0], m = 0, nums2 = [1], n = 1
</strong><strong>Output: [1]
</strong><strong>Explanation: The arrays we are merging are [] and [1].
</strong>The result of the merge is [1].
Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.
</code></pre>

&#x20;

**Constraints:**

* `nums1.length == m + n`
* `nums2.length == n`
* `0 <= m, n <= 200`
* `1 <= m + n <= 200`
* `-109 <= nums1[i], nums2[j] <= 109`

## Solution

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """

        while m>0 and n>0:
            if nums1[m-1]<nums2[n-1]:
                nums1[m-1+n] = nums2[n-1]
                n -= 1
            else:
                nums1[m-1+n]=nums1[m-1]
                m-=1
            
        if n>= 0:
            nums1[:n] = nums2[:n]
```

``
