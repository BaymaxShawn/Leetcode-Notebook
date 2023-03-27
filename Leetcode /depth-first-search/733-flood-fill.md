---
description: Easy
---

# 😣 733 - Flood Fill

An image is represented by an `m x n` integer grid `image` where `image[i][j]` represents the pixel value of the image.

You are also given three integers `sr`, `sc`, and `color`. You should perform a **flood fill** on the image starting from the pixel `image[sr][sc]`.

To perform a **flood fill**, consider the starting pixel, plus any pixels connected **4-directionally** to the starting pixel of the same color as the starting pixel, plus any pixels connected **4-directionally** to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with `color`.

Return _the modified image after performing the flood fill_.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/06/01/flood1-grid.jpg)

<pre><code><strong>Input: image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, color = 2
</strong><strong>Output: [[2,2,2],[2,2,0],[2,0,1]]
</strong><strong>Explanation: From the center of the image with position (sr, sc) = (1, 1) (i.e., the red pixel), all pixels connected by a path of the same color as the starting pixel (i.e., the blue pixels) are colored with the new color.
</strong>Note the bottom corner is not colored 2, because it is not 4-directionally connected to the starting pixel.
</code></pre>

**Example 2:**

<pre><code><strong>Input: image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, color = 0
</strong><strong>Output: [[0,0,0],[0,0,0]]
</strong><strong>Explanation: The starting pixel is already colored 0, so no changes are made to the image.
</strong></code></pre>

&#x20;

**Constraints:**

* `m == image.length`
* `n == image[i].length`
* `1 <= m, n <= 50`
* `0 <= image[i][j], color < 216`
* `0 <= sr < m`
* `0 <= sc < n`

## Solution

```python
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, color: int) -> List[List[int]]:

        R,C = len(image),len(image[0])
        target = image[sr][sc]
        if target == color:
            return image
        def dfs(r,c):
            if image[r][c] == target:
                image[r][c] = color
                if r >= 1:
                    dfs(r-1,c)
                if r+1 < R:
                    dfs(r+1,c)
                if c >= 1:
                    dfs(r,c-1)
                if c+1 <C:
                    dfs(r,c+1)
        dfs(sr,sc)
        return image
```
