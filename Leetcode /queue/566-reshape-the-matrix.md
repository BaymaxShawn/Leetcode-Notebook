# 😁 566 - Reshape the Matrix

In MATLAB, there is a handy function called `reshape` which can reshape an `m x n` matrix into a new one with a different size `r x c` keeping its original data.

You are given an `m x n` matrix `mat` and two integers `r` and `c` representing the number of rows and the number of columns of the wanted reshaped matrix.

The reshaped matrix should be filled with all the elements of the original matrix in the same row-traversing order as they were.

If the `reshape` operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/04/24/reshape1-grid.jpg)

<pre><code><strong>Input: mat = [[1,2],[3,4]], r = 1, c = 4
</strong><strong>Output: [[1,2,3,4]]
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/04/24/reshape2-grid.jpg)

<pre><code><strong>Input: mat = [[1,2],[3,4]], r = 2, c = 4
</strong><strong>Output: [[1,2],[3,4]]
</strong></code></pre>

&#x20;

**Constraints:**

* `m == mat.length`
* `n == mat[i].length`
* `1 <= m, n <= 100`
* `-1000 <= mat[i][j] <= 1000`
* `1 <= r, c <= 300`

## Solution

```python
class Solution:
    def matrixReshape(self, mat: List[List[int]], r: int, c: int) -> List[List[int]]:

        if r*c!=len(mat)*len(mat[0]):
            return mat
        queue = []
        for i in mat:
            for j in i:
                queue.append(j)

        res = [] 
        for _ in range(r):
            res.append([queue.pop(0) for _ in range(c)])
            #queue.pop(0)弹出的是第一个数
        
        return res
```
