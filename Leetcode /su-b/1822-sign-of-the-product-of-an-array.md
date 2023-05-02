# 🤩 1822 - Sign of the Product of an Array

There is a function `signFunc(x)` that returns:

* `1` if `x` is positive.
* `-1` if `x` is negative.
* `0` if `x` is equal to `0`.

You are given an integer array `nums`. Let `product` be the product of all values in the array `nums`.

Return `signFunc(product)`.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [-1,-2,-3,-4,3,2,1]
</strong><strong>Output: 1
</strong><strong>Explanation: The product of all values in the array is 144, and signFunc(144) = 1
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [1,5,0,2,-3]
</strong><strong>Output: 0
</strong><strong>Explanation: The product of all values in the array is 0, and signFunc(0) = 0
</strong></code></pre>

**Example 3:**

<pre><code><strong>Input: nums = [-1,1,-1,1,-1]
</strong><strong>Output: -1
</strong><strong>Explanation: The product of all values in the array is -1, and signFunc(-1) = -1
</strong></code></pre>

## Solution

```python
class Solution:
    def arraySign(self, nums: List[int]) -> int:
        count = 0
        for i in nums:
            if i < 0:
                count += 1
            if i == 0 :
                return 0
                
        if count%2 == 1:
            return -1
        return 1


```
