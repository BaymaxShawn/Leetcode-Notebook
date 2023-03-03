# 🧑💻 350 - Intersection of Two Arrays II

Given two integer arrays `nums1` and `nums2`, return _an array of their intersection_. Each element in the result must appear as many times as it shows in both arrays and you may return the result in **any order**.

**Example 1:**

<pre><code><strong>Input: nums1 = [1,2,2,1], nums2 = [2,2]
</strong><strong>Output: [2,2]
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
</strong><strong>Output: [4,9]
</strong><strong>Explanation: [9,4] is also accepted.
</strong></code></pre>

## Solution：

#### Counter

```python
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:

        num_set = collections.Counter(nums1)
        
        res = []

        for i in nums2:
            if num_set[i] > 0:
                res += i,
                num_set[i] -= 1
        
        return res
```

`res.append(i)` 和 `res += [i]` 都是将元素 `i` 作为单个元素添加到列表 `res` 中，它们的作用是一样的，只是语法不同。`res.append(i)` 是调用了列表 `res` 的 `append` 方法，将元素 `i` 直接添加到列表的末尾。而 `res += [i]` 则是使用了复合赋值运算符 `+=`，相当于将列表 `[i]` 扩展到 `res` 中。因为 `[i]` 是一个列表，所以需要使用方括号将元素 `i` 包裹起来。

而 `res += i,` 的作用是将元素 `i` 封装成一个元组 `(i,)`，然后再将这个元组添加到列表 `res` 中。如果不使用逗号 `,`，而是直接写成 `res += i`，那么 Python 会将元素 `i` 视为可迭代对象，尝试将其迭代并将其中的元素添加到列表 `res` 中。例如，如果元素 `i` 是一个字符串，那么 `res += i` 的效果相当于将字符串中的每个字符都添加到列表 `res` 中。因此，在使用复合赋值运算符 `+=` 时，如果要将一个元素作为单个元素添加到列表中，最好将其封装成元组，避免产生意外的结果。

#### Dictionary

```python
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:

        num_set = {}
        res = []

        for i in nums1:
            num_set[i] = num_set.get(i,0) +1

        for i in nums2:
            if i in nums1 and num_set[i] > 0:
                res.append(i)
                num_set[i] -=1
        
        return res
```

#### Two Pointers

```python
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:

        nums1.sort()
        nums2.sort()
        res = []

        l = r = 0

        while l< len(nums1) and r < len(nums2):
            if nums1[l] > nums2[r]:
                r += 1 
            elif nums1[l] < nums2[r]:
                l += 1
            else:
                res.append(nums1[l])
                r += 1
                l += 1
        return res
```

也可以用 try-expect 代替

```python
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:

        nums1.sort()
        nums2.sort()
        res = []

        l = r = 0

        while True:
            try:
                if nums1[l] > nums2[r]:
                    r += 1 
                elif nums1[l] < nums2[r]:
                    l += 1
                else:
                    res.append(nums1[l])
                    r += 1
                    l += 1
            except IndexError:
                break
        return re
```

在这段代码中，使用了一个 try-except 语句块来捕获 IndexError 异常。这是因为在 while 循环中使用了 pt1 和 pt2 来访问数组 nums1 和 nums2 的元素，而在数组的边界处，访问数组可能会导致 IndexError 异常。因此，使用 try-except 语句块来捕获这些异常，以避免程序崩溃。

try-except 语句块的作用是：当 try 语句块中发生异常时，程序将跳转到 except 语句块，并执行其中的代码。在这里，如果 try 语句块中的代码引发了 IndexError 异常，程序将跳转到 except 语句块，并执行其中的代码，即退出 while 循环。
