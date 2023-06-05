# 😌 1232 - Check If It Is a Straight Line

You are given an array `coordinates`, `coordinates[i] = [x, y]`, where `[x, y]` represents the coordinate of a point. Check if these points make a straight line in the XY plane.

&#x20;

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2019/10/15/untitled-diagram-2.jpg)

<pre><code><strong>Input: coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]
</strong><strong>Output: true
</strong></code></pre>

**Example 2:**

![](https://assets.leetcode.com/uploads/2019/10/09/untitled-diagram-1.jpg)

<pre><code><strong>Input: coordinates = [[1,1],[2,2],[3,4],[4,5],[5,6],[7,7]]
</strong><strong>Output: false
</strong></code></pre>

&#x20;

**Constraints:**

* `2 <= coordinates.length <= 1000`
* `coordinates[i].length == 2`
* `-10^4 <= coordinates[i][0], coordinates[i][1] <= 10^4`
* `coordinates` contains no duplicate point.

## Solution

```python
class Solution:
    def checkStraightLine(self, coordinates: List[List[int]]) -> bool:
        (x0,y0),(x1,y1) = coordinates[:2]
        for x,y  in coordinates:
            if (x1-x0)*(y-y0) != (x-x0)*(y1-y0):
                return False
        return True
```
