# 🥘 51 - N Queens

The **n-queens** puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.

Given an integer `n`, return _all distinct solutions to the **n-queens puzzle**_. You may return the answer in **any order**.

Each solution contains a distinct board configuration of the n-queens' placement, where `'Q'` and `'.'` both indicate a queen and an empty space, respectively.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/13/queens.jpg)

<pre><code><strong>Input: n = 4
</strong><strong>Output: [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
</strong><strong>Explanation: There exist two distinct solutions to the 4-queens puzzle as shown above
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: n = 1
</strong><strong>Output: [["Q"]]
</strong></code></pre>

## Solution:

#### Python&#x20;

```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:

        col = set() #colunme
        posDiag = set() # Positive Diagonal (r+c)
        negDiag = set() # Negative Diagonal  (r-c)
        res = []
        puzzle = [["."]* n for i in range(n)]

        def backtracking(r):
            if r == n :
                copy = ["".join(row) for row in puzzle]
                res.append(copy)
                return

            for c in range(n):
                if c in col or (r+c) in posDiag or (r-c) in negDiag:
                    continue

                col.add(c)
                posDiag.add(r+c)
                negDiag.add(r-c)
                puzzle[r][c] = "Q"

                backtracking(r+1)

                col.remove(c)
                posDiag.remove(r+c)
                negDiag.remove(r-c)
                puzzle[r][c] = "."
            
        backtracking(0)
        return res
```

思路：

