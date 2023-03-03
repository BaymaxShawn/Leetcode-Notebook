# 😁 1337 - The K Weakest Rows in a Matrix

You are given an `m x n` binary matrix `mat` of `1`'s (representing soldiers) and `0`'s (representing civilians). The soldiers are positioned **in front** of the civilians. That is, all the `1`'s will appear to the **left** of all the `0`'s in each row.

A row `i` is **weaker** than a row `j` if one of the following is true:

* The number of soldiers in row `i` is less than the number of soldiers in row `j`.
* Both rows have the same number of soldiers and `i < j`.

Return _the indices of the_ `k` _ **weakest** rows in the matrix ordered from weakest to strongest_.

&#x20;

**Example 1:**

<pre><code><strong>Input: mat = 
</strong>[[1,1,0,0,0],
 [1,1,1,1,0],
 [1,0,0,0,0],
 [1,1,0,0,0],
 [1,1,1,1,1]], 
k = 3
<strong>Output: [2,0,3]
</strong><strong>Explanation: 
</strong>The number of soldiers in each row is: 
- Row 0: 2 
- Row 1: 4 
- Row 2: 1 
- Row 3: 2 
- Row 4: 5 
The rows ordered from weakest to strongest are [2,0,3,1,4].
</code></pre>

**Example 2:**

<pre><code><strong>Input: mat = 
</strong>[[1,0,0,0],
 [1,1,1,1],
 [1,0,0,0],
 [1,0,0,0]], 
k = 2
<strong>Output: [0,2]
</strong><strong>Explanation: 
</strong>The number of soldiers in each row is: 
- Row 0: 1 
- Row 1: 4 
- Row 2: 1 
- Row 3: 1 
The rows ordered from weakest to strongest are [0,2,3,1].
</code></pre>

## Solution:

#### Python

```python
class Solution(object):
    def kWeakestRows(self, mat, k):
        """
        :type mat: List[List[int]]
        :type k: int
        :rtype: List[int]
        """

        idx,count = 0,0
        temp = {}
        for m in range(len(mat)): 
            for i in mat[m]:
                if i == 1:
                    count +=1
                else:
                    idx +=1     
            temp[m] = count
            count = 0

        sortTemp = sorted(temp.items(),key=lambda x:x[1])
        print(type(sortTemp))
        res = [x for x,y in sortTemp[:k]]

        return res
```

#### 注意：

2 / 2

`d.items()` 返回一个由字典中所有键值对构成的列表，每个键值对都是一个元组 (key, value)。

`sorted()` 函数用于对可迭代对象进行排序，其中 `key` 参数用于指定排序的关键字，也就是按照什么规则来排序。`key=lambda x: x[1]` 表示按照元组的第二个元素即字典中的值来进行排序。

因此，`sorted_d = sorted(d.items(), key=lambda x: x[1])` 的意思是将字典中的键值对按照值从小到大排序，返回一个由排序后的元组构成的列表

```
 res = [x for x,y in sortTemp[:k]] 是为了把list里的前k个数打印出来
```

