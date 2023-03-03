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

#### Python method-1

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

####

#### Python method-2

```python
class Solution:
    def kWeakestRows(self, mat: List[List[int]], k: int) -> List[int]:

        return sorted(range(len(mat)), key=lambda x: sum(mat[x]))[:k]
```

这行代码是一个lambda函数，用来对矩阵`mat`的每一行进行求和，并将其作为排序的依据。具体来说，`range(len(mat))`表示对矩阵的每一行都进行处理；`key=lambda x: sum(mat[x])`表示对于每一行`x`，将其元素进行求和，并以此作为排序的依据；最后`sorted`函数将处理结果进行排序，返回前`k`行的索引值。

举个例子，如果矩阵`mat`为：

```csharp
csharpCopy code[
 [1,1,0,0,0],
 [1,1,1,1,0],
 [1,0,0,0,0],
 [1,1,0,0,0],
 [1,1,1,1,1]
]
```

`range(len(mat))`为`[0,1,2,3,4]`，分别表示矩阵的五行。

对于第一行，`sum(mat[0])`为2，对于第二行，`sum(mat[1])`为4，以此类推。

`sorted`函数根据这些求和结果将行的索引进行排序，返回前`k`行的索引值，比如当`k=3`时，返回`[0, 2, 3]`，表示前三行的索引为0、2、3。

在这里，索引指的是行号，即二维矩阵中每一行的标号。`sum(mat[x])`是求矩阵中第x行的所有元素之和。`sorted(range(len(mat)), key=lambda x: sum(mat[x]))`这一部分代码返回的是一个列表，列表中的每个元素是原始矩阵中每一行的索引，按行元素之和从小到大排列。

通过`[:k]`取前k个索引，就可以得到按行元素之和从小到大排序后的前k行。

由于题目要求返回的是行索引而不是行元素之和，因此最终返回的是`sorted(range(len(mat)), key=lambda x: sum(mat[x]))[:k]`，即前k个行索引组成的列表。



`range(len(mat))` 是一个 Python 内置的函数，返回一个包含指定长度范围内所有整数的可迭代对象，可以被用来在循环中遍历或者生成列表等操作。

在 `sorted` 函数中，`range(len(mat))` 表示要排序的元素的索引，这里是通过列表推导式生成的。如果需要，也可以将其单独拎出来使用，例如：

```scss
scssCopy codelst = [3, 1, 4, 2, 5]
idx = range(len(lst))
sorted_idx = sorted(idx, key=lambda x: lst[x])
```

这段代码中，`idx` 是一个 `range` 对象，表示了 `lst` 列表的索引范围。`sorted_idx` 则是按照 `lst` 列表元素大小排序后的索引列表。

因此，可以将 `range(len(mat))` 单独拎出来使用，只要在 `sorted` 函数中正确地使用它即可。



