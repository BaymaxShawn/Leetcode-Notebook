---
description: Easy
---

# 😀 977 - Squares of a Sorted Array

Given an integer array `nums` sorted in **non-decreasing** order, return _an array of **the squares of each number** sorted in non-decreasing order_.

&#x20;

**Example 1:**

<pre><code><strong>Input: nums = [-4,-1,0,3,10]
</strong><strong>Output: [0,1,9,16,100]
</strong><strong>Explanation: After squaring, the array becomes [16,1,0,9,100].
</strong>After sorting, it becomes [0,1,9,16,100].
</code></pre>

**Example 2:**

<pre><code><strong>Input: nums = [-7,-3,2,3,11]
</strong><strong>Output: [4,9,9,49,121]
</strong></code></pre>

**Constraints:**

* `1 <= nums.length <= 104`
* `-104 <= nums[i] <= 104`
* `nums` is sorted in **non-decreasing** order.

**Follow up:** Squaring each element and sorting the new array is very trivial, could you find an `O(n)` solution using a different approach?

## Solution

#### for loop

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:

        for i in range(len(nums)):
            nums[i] = nums[i] **2
            print(nums[i])
        nums.sort()
        
        return nums
```

#### Two Point

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:

        l, r = 0,len(nums)-1
        res = [0]*len(nums)

        while l<=r:
            left_value,right_value = abs(nums[l]),abs(nums[r])
            if left_value >= right_value:
                res[r-l] = left_value **2
                l += 1
            else:
                res[r-l] = right_value **2
                r -= 1
        return res
```

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:

        l, r = 0,len(nums)-1
        res = [0]*len(nums)

        while l<=r:
            left_value,right_value = abs(nums[l]),abs(nums[r])
           
            res[r-l] = max(left_value,right_value) **2
            l,r = l+(left_value >= right_value),r-(left_value < right_value)
            

        return res

```

在这个语句中，`l = l + (left > right)` 的含义是，如果 `left` 大于 `right`，则 `l` 加1，否则不加。这是因为 `(left > right)` 的值只能是 0 或 1，相当于一个布尔类型的变量，所以 `(left > right)` 的值加到 `l` 上，相当于将布尔类型转换成了整数类型。

如果你想加 2，只需要把 `1` 改成 `2` 即可，如下所示：

```css
cssCopy codel = l + 2 * (left > right)
```

这样，当 `(left > right)` 的值为 True 时，`l` 就会加 2。

